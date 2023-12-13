# Cars Price Prediction

## Project description 
The goal of the project is to create a model that predicts the prices of US cars by utilizing information about cars with already known prices.

## Dataset 
The dataset is stored as a CSV file named cars.csv, and it comprises information about 51,793 cars.

### Overview

![brand_distribution](https://github.com/CherryMagic/Cars-price-prediction/assets/120610986/62985769-959a-4557-94fa-9cfdfb04f8da)

The features of the dataset are:
1. Brand
2. Model
3. Year
4. Status
5. Mileage
6. Dealer
7. Price

All the values in the dataset have been transformed into numerical format, as it is necessary for working with decision trees that perform well with tabular data.

### Train-Test split
The dataset has been divided into the training and test sets with a ratio of 0.7 to 0.3.

## Model

The metric employed for evaluating the decision trees was mean absolute percentage error. Cross-validation with 4 sections was applied. Four types of models were experimented with: two LGB models, one incorporating all features and the other excluding 'Status' as it was deemed the least important. Additionally, two XGB models were tested, one with all parameters and the other excluding the 'Dealer' parameter, as that omission yielded the best result.

### Tuning

There was an initial tuning phase where only the number of estimators and the number of leaves were adjusted for LGB models, and only the number of estimators for XGB models.

The best models underwent advanced tuning. The tuning of LGB models included learning_rate, min_child_samples, min_child_weight, subsample_for_bin, and n_estimators. Three possible values were tried for each parameter. The search was repeated five times, and each time the step was halved, with the center being the best model from the previous iteration. For XGB models, only subsample_for_bin was tuned using the same approach.

The scores of the four best models for each type:

![scores](https://github.com/CherryMagic/Cars-price-prediction/assets/120610986/118d78d1-5978-4618-8fba-a3a242eca0dc)

These are the parameters of the best model found:

![model_parameters](https://github.com/CherryMagic/Cars-price-prediction/assets/120610986/e2553d74-4426-4162-9abd-ee3cc0f57f3d)

## Results

MAPE scores of the best model:

![train_test](https://github.com/CherryMagic/Cars-price-prediction/assets/120610986/d26eb7ee-36a8-4e33-bbea-ad3e8f8fb4e9)

Comparison between the true and predicted prices for a random instance of each brand:

![true_pred](https://github.com/CherryMagic/US-Cars-Price-Prediction/assets/120610986/e1cc1470-cbe4-4100-a45a-4a849b4757f3)

## Setup 

To load the project:

Download the cars.csv file.
Change the file_path variable to point to the dataset location.
