# Final-Project-Rec-System

## Outline

- Background

- Dataset Introduction

- EDA

- Model

- Front End

- Further Exploration

## Project Goal

The goal of this project is to create a content-based item-to-item recommendation system for books. 

## Data Introduction

The data was collected from Figshare, originally web scrapped from audible.com by Figshare account XinYuan Wang 2020. The data obtained 2 CSV files which covers all released books in the second half year of 2019. Important features in data includes book title, book author, book genre and book description.The files contain approximately 30,000 observations. 

## EDA

The graphic below shows distribution of each genre.
![Distribution_of_genres.png](Pictures/Distribution_of_genres.png)

The graphic below shows average description word counts of each genre.
![Average_description_word_count_by_genre.png](Pictures/Average_description_word_count_by_genre.png)

The graphic below shows the top 30 frequent words in 1000 randomly chosed samples with no limitation.

![Most_frequent_words_in_1000_samples_(original).png](Pictures/Most_frequent_words_in_1000_samples_(original).png)

The graphic below shows the top 30 frequent words in 1000 randomly chosed samples captures noun only.

![Most_frequent_words_in_1000_samples_(noun_only).png](Pictures/Most_frequent_words_in_1000_samples_(noun_only).png)

The graphic below shows the different top 20 frequent nouns between fiction and nonfiction.

![Most_frequent_words_in_fiction_vs_nonfiction.png](Pictures/Most_frequent_words_in_fiction_vs_nonfiction.png)

The graphic below shows the different word cloud between fiction and nonfiction.

![Fiction_word_cloud.png](Pictures/Fiction_word_cloud.png.png)
![Nonfiction_word_cloud.png](Pictures/Nonfiction_word_cloud.png.png)

## Data Prepping

- Create labels for both training set and testing set.

- Turn both training set and testing set into matrix(reshape), flatten, and standardize(divide by 255).

- Split the training set into training and validating sets.

- Set number of classes to 25 (26 letters - 2(no J,Z) +1(label))

- Trun train_label, validate_label into single row matrixes.

## MLP

### Sigmoid

- Test set Accuracy: 0.29, Epochs = 15

![acc_sigmoid.png](Pictures/acc_sigmoid.png)

### Softmax

- Test set Accuracy: 0.59, Epochs = 15

![acc_softmax.png](Pictures/acc_softmax.png)

### Hypertuned Softmax

- Test set Accuracy: 0.63, Epochs = 15

![acc_hypertuned_softmax.png](Pictures/acc_hypertuned_softmax.png)

## CNN 2D

- Adopt 3 layer convolution 2D and Maxpooling 2D

- Dropout 10% of observations

- Save model for future usage

- Test set accuracy: 0.81, Epochs = 18

![acc_cnn.png](Pictures/acc_cnn.png)

## Extracting Feature Map

- Extract model layer outputs

- Create a model for displaying the feature maps

- Extract Layer Names for Labelling

- Post-process the feature to make it visually palatable
 
 The graphics below show the transformation of Conv2D --> Max Pooling2D for each 3 layers.
 
 - Layer 1:
 
 ![Conv2D_1.png](Pictures/Conv2D_1.png)
 ![Max_Pooling2D_1.png](Pictures/Max_Pooling2D_1.png)
 
 - Layer 2:
 
 ![Conv2D_2.png](Pictures/Conv2D_2.png)
 ![Max_Pooling2D_2.png](Pictures/Max_Pooling2D_2.png)
 
 - Layer 3:
 
 ![Conv2D_3.png](Pictures/Conv2D_3.png)
 ![Max_Pooling2D_3.png](Pictures/Max_Pooling2D_3.png)
 
 ## Confusion Matrix
 
 - Create a 24X24 confusion matrix for each letter.
 
 - Calculate False Nagative error % to get top letters most misclassified to other letters.
 
 - Calculate False Positive error % to get top letters most misclassified by other letters.
 
 The graphic below shows the confusion matrix.
 ![confusion_matrix.png](Pictures/confusion_matrix.png)
 
 ## Insightful Analysis
 
 - 'R', 'T', and 'V' were the most miss predicted
 - Other signs were incorrectly predicted as 'U' and 'T' most often
 ![amer_sign2.png](Pictures/amer_sign2.png)
 
 ## Further Exploration
 
- Enlarge the database to make recommendations more precise

- Use A/B testing to examine recommendation system performances

- Create a user-friendly searching environment by returning recommendations based on the closest input 

