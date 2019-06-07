Data Science Specialization Capstone Project
========================================================
author: Ayah Fouad
date: June 7th '19
autosize: true

Project Overview
========================================================

This presentation was created as the final step in the Capstone project for the Data Scientist specialization offered through Coursera / Johns Hopkins.  

The project goal was to build a predictive model of English text.  The skills needed to complete this task include natural language processing and text mining.  The model was created using the Shiny Application in RStudio.

The source data for this project can be found at: https://d396qusza40orc.cloudfront.net/dsscapstone/dataset/Coursera-SwiftKey.zip

My Shiny App can be found at: https://ctarsenault.shinyapps.io/word_prediction_application

If you would like to review my source code, it is located on GitHub at:https://github.com/ayahfouad/Shiny-Final-App

Working with the Data
========================================================

In order to build a prediction algorithm, data was scraped from blogs, twitter and the news.  This data was provided as part of the assignment.  There are several processes that need to be completed before the model can be built.

- The data was read into R
- Data cleaning was performed: stripping out of numbers and punctuation, changing all text to lowercase and removing the whitespace.
- N-grams were created, these are a sequence of items collected from a corpus.  The N refers to the number of items within the sequence.  For this project, bigrams, trigrams and quadgrams were used.
- The N-grams were sorted and the metadata saved as an .rds file.

The Prediction Model
========================================================

The model for the next word prediction was based on the Katz Back-off algorithm.  This process works as follows:

- The .rds files containing the metadata are loaded.
- Quadgram is the first N-gram to be used.  This takes into account the first three words that user has provided.
- If no match is found, the trigram is used.  This takes the last two words of the user input into account.
-  If there is still no match found, bigram is used next. Bigram only uses the last word of the user input. 
- When no match is found, the application will return a comment that no match is found due to the small sample size.
