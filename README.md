# Spaceship Titanic

This repository is the holding place of all data and subsequent trained models from a publicly available Kaggle competition [here](https://www.kaggle.com/competitions/spaceship-titanic/overview). The ML algorithms used will be classification based.

_These notebooks have been developed for Project 2 of COMP-4730 (Advanced AI Concepts I) at the University of Windsor, Fall 2023._

# How To Run

**These instructions assume Python and Jupyter have both been properly installed!**

When attempting to run any Jupyter Notebook file, first ensure that the appropriate libraries have been installed. This can be done by running:

```
pip install -r requirements.txt
```

This will automatically install all Python libraries listed within the `requirements.txt` file.

The algorithms run off of the training and testing data available under the data folder.

# Encoding for Data

Due to a good chunk of the data consisting of strings/booleans, it had to be converted over into mapped integer values.

## Booleans

Any boolean column such as `CryoSleep`, `VIP`, and `Transported` were mapped respectively:

| Value | Encoding |
| ----- | -------- |
| nan   | -1       |
| False | 0        |
| True  | 1        |

## `HomePlanet`

The first unique case, `HomePlanet` was mapped as follows:

| Value  | Encoding |
| ------ | -------- |
| nan    | 0        |
| Earth  | 1        |
| Mars   | 2        |
| Europa | 3        |

## `Cabin`

The Cabin column was split into three separate pieces of data; `Deck`, `Num`, and `Side`. This is due to the `Cabin` column's values containing three pieces of data in the form of `deck/num/side`. While `num` was always a number and therefore didn't require encoding, `deck` and `side` would still always be letter.

### `Deck`

The encodings for `Deck` were as follows:

| Value | Encoding |
| ----- | -------- |
| A     | 1        |
| B     | 2        |
| C     | 3        |
| D     | 4        |
| E     | 5        |
| F     | 6        |
| G     | 7        |
| T     | 8        |

### `Side`

The encodings for `Side` were as follows:

| Value | Encoding |
| ----- | -------- |
| P     | 1        |
| S     | 2        |

## `Destination`

The next unique case, `Destination` was encoded as follows:

| Value         | Encoding |
| ------------- | -------- |
| nan           | 0        |
| 55 Cancri e   | 1        |
| PSO J318.5-22 | 2        |
| TRAPPIST-1e   | 3        |

## `Name`

The final unique case was a bit more complicated. Values in `Name` were comprised of data in the form `FirstName LastName` and obviously this caused nearly every row to have a unique value, making any encoding pointless. What was ultimately decided was to split the `Name` column into two columns, `FirstName` and `LastName`. When checking for uniqueness of names, 2884 first names were found to be unique, and 2407 last names were found to be unique, so both `FirstName` and `LastName` values were encoded to a number from 0 to 2884 and 0 to 2407 respectively, with no particular order in mind.

# Main Files/Folders

[`data`](https://github.com/CadenQ/comp4730-p2/tree/main/data) - contains all training and testing data found from the spaceship titanic dataset, along with enumerated versions of said data.

[`results`](https://github.com/CadenQ/comp4730-p2/tree/main/results) - contains all submission CSV files used when submitting to the Kaggle website.

[`data_prep.ipynb`](https://github.com/CadenQ/comp4730-p2/blob/main/data_prep.ipynb) - all data enumeration/mapping was done within this file (see "Encoding for Data" for more info), converting any strings, booleans, etc. into a numerical counterpart.

[`DTC.ipynb`](https://github.com/CadenQ/comp4730-p2/blob/main/DTC.ipynb) - contains all code written for the Decision Tree Classifier.

[`logistic_regression.ipynb`](https://github.com/CadenQ/comp4730-p2/blob/main/logistic_regression.ipynb) - contains all code written for the Logistic Regression algorithm.

[`neural_network.ipynb`](https://github.com/CadenQ/comp4730-p2/blob/main/neural_network.ipynb) - contains all code written for the Neural Network algorithm.

[`Pycaret.ipynb`](https://github.com/CadenQ/comp4730-p2/blob/main/Pycaret.ipynb) - This file contains data such as what generic algorithms performed best with the training dataset, and even automatically optimizes one, which wasn't ultimately used. It contains a great table to see what possible algorithms would be great to use for the given dataset.

[`quiring_algo.ipynb`](https://github.com/CadenQ/comp4730-p2/blob/main/quiring_algo.ipynb) - contains all code written for the Random Forest Classifier.

[`requirements.txt`](https://github.com/CadenQ/comp4730-p2/blob/main/requirements.txt) - Helpful file for installing all required dependencies.

[`submission_example.ipynb`](https://github.com/CadenQ/comp4730-p2/blob/main/submission_example.ipynb) - contains a template/blueprint for running an algorithm, and recording predicted results into a CSV file to be verified by Kaggle.
