# Alzheimer's Disease Classification from MRI Images

A 2D convolutional neural network (CNN), built with Keras, that classifies brain MRI images into four classes:

- `NonDemented`
- `VeryMildDemented`
- `MildDemented`
- `ModerateDemented`

## Background

Alzheimer's disease is a progressive neurodegenerative disease and [the most common form of dementia (WHO)](https://www.who.int/news-room/fact-sheets/detail/dementia). It causes memory loss, cognitive decline and changes in behaviour that get worse over time.

Many people first go through a stage of [mild cognitive impairment (NIA)](https://www.nia.nih.gov/health/memory-loss-and-forgetfulness/what-mild-cognitive-impairment), between normal age-related changes and dementia: memory or other cognitive problems are more noticeable than usual, but daily life is still largely independent. Some people in this stage later develop Alzheimer's disease, others remain stable.

Brain MRI scans can show changes linked to the disease. Classifying them automatically is an active research area for supporting early detection. This project is an educational exercise and not a diagnostic tool.

## Data

- **Inspiration:** [Classification of Alzheimers 95% TOTW (Kaggle)](https://www.kaggle.com/code/schorsi/classification-of-alzheimers-95-totw) by Neil Kloper.
- **Dataset:** `alzheimers-dataset-4-class-of-images`, by Sarvesh Dubey ([tourist55 on Kaggle](https://www.kaggle.com/tourist55)), as credited in that notebook. The folder name `Alzheimer_s Dataset` is the same. The dataset page is no longer publicly available, so the origin of the images could not be verified.
- The dataset is not included in this repository. It is expected in a folder named `Alzheimer_s Dataset` with a `train` and a `test` subfolder, each containing one folder per class.
- The classes are very unbalanced. Number of images in the copy used for this project:

| Class | `train` | `test` |
|---|---:|---:|
| `NonDemented` | 2,560 | 640 |
| `VeryMildDemented` | 1,792 | 448 |
| `MildDemented` | 717 | 179 |
| `ModerateDemented` | 52 | 26, of which 14 duplicates excluded by the notebook (see **Limitations**) |

## Approach

1. **Split:** 80% of the `train` folder for training, 20% for validation. The `test` folder is used only for the final evaluation.
2. **Augmentation:** rotation, shift, zoom and horizontal flip, as layers of the model that are active only during training.
3. **Model:** five convolutional blocks (Conv2D, BatchNormalization, MaxPooling) followed by a dense layer with dropout and a softmax output.
4. **Training:** Adam optimizer, categorical cross-entropy; the best epoch is saved by validation accuracy.
5. **Evaluation:** confusion matrix, per-class precision, recall and F1, and macro averages on the test set.

## Why these choices

| Choice | Reason |
|---|---|
| Separate `test` folder, used only at the end | The final score must come from images that played no part in training or in choosing the best epoch. |
| Test images identical to training images are excluded | A model must not be evaluated on images it has already seen. |
| Augmentation only during training | Validation and test must measure the model on unmodified images. |
| Same `seed` for the training and validation split | With [`image_dataset_from_directory`](https://keras.io/api/data_loading/image/), the same seed keeps the two parts from overlapping. |
| `shuffle=False` for the test set | Predictions stay in the same order as the true labels. |
| `image_dataset_from_directory` and augmentation layers | `ImageDataGenerator` is no longer available in Keras 3. |
| Per-class metrics and macro averages | With unbalanced classes, overall accuracy can look good while a rare class is missed. Micro averages would simply repeat the accuracy. |
| Original model and hyperparameters | The goal of this revision was to correct the evaluation, not to tune the model. |
| Four-class public dataset instead of ADNI | [ADNI](https://adni.loni.usc.edu/) data requires an application and a data use agreement. A first experiment with ADNI's three groups was stopped before completion and is not part of this project. |

## How to run

1. Open `Alzheimers_Classification.ipynb` in [Google Colab](https://colab.research.google.com/) and choose a GPU runtime.
2. Put the dataset in your Google Drive.
3. Set `DATA_DIR` in the notebook to the dataset folder.
4. Run all cells.

## Results

To be updated after running the corrected notebook. The notebook saves the training curves and the confusion matrix as `training_curves.png` and `confusion_matrix.png`, to be added to the `images` folder of this repository.

## Limitations

- **Possible patient overlap:** the dataset does not say which patient each image belongs to. Images from the same patient may be in both `train` and `test`, which would make the results look better than they are.
- **Duplicates in the test set:** in the copy used for this project, 14 images in `test/ModerateDemented` (`moderateDem*.jpg`) are identical to images in `train/ModerateDemented`. The notebook compares the content of the files and excludes them from the evaluation, leaving 12 test images for this class. The original folders are not changed.
- **Very few `ModerateDemented` images:** results for this class are based on very few examples and are not stable.
- **No external validation:** the model is tested on a single dataset, not on data from other hospitals or scanners.

## Possible next steps

Not implemented yet:

- [Class weights](https://www.tensorflow.org/tutorials/structured_data/imbalanced_data) for the unbalanced classes.
- Transfer learning with a pre-trained network, as in [Alzheimer-dementia-prediction (Kaggle)](https://www.kaggle.com/code/apalladi/alzheimer-dementia-prediction), a related project on the same four classes. When using pre-augmented datasets, it is important to check that test images are not the source of the augmented training images.
- External validation on independent data, as done for lung cancer in [Sybil (Mikhael et al., 2023)](https://pubmed.ncbi.nlm.nih.gov/36634294/).

## Files

- `Alzheimers_Classification.ipynb`: the notebook
- `Presentation.pdf`: project presentation
- Other notebooks: [Google Drive folder](https://drive.google.com/drive/folders/1e4up9-G1HTpSjSQmT2x0KHsVQdUfx5-G?usp=sharing)

## License

[MIT](LICENSE)
