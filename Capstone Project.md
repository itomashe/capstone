Capstone Project/Coursera
========================================================
author: Igor Tomashevskiy
date: 04/18/2016

Objectives
========================================================

The objective of this presentation is to highlight the prediction algorithm that was built in the Capstone project and to provide an interface that can be accessed via a Shiny app.

- The dataset for the project was provided by Coursera and consists of data from twitter, news and blogs.  
- Exploratory analysis of the data set can be found at [http://rpubs/itomashe/162583](http://rpubs/itomashe/162583)
- Text Mining and data processing was conducted using R programming language.
- The problem we examine is the classic task of language modeling - predict the next word given the previous words.
 

Applied Methods
========================================================
- Words are not independent events. Language modeling employs conditional probabilities.
- N-gram language model uses the previous N-1 words to predict the next one. In our case the N=3, we created trigrams, bigrams and unigrams from the data set provided for the project, then we can estimate probabilities of partiular word sequence using counts from N-grams. This method is called Maximum Lekelihood Estimate(MLE)
- The problem with MLE is that it assigns zero probabilty to any N-gram not in the Corpus.
To avoid this problem a small but non-zero probability is assigned to these "zero probability n-grams"
Backoff is another method for dealing with unseen n-gram, for example Katz back-off method.


Applied Methods (continued)
========================================================
- Katz's back-off model and news data set will be used to create the Shiny application.
The estimate for n-gram is allowed to back off through shorter histories.
If N-gram has appeared more than k times(k is set to 0), then an N-gram estimate is used, if N-gram did not appear, then we will use an estimate from a shorter N-gram. This recursion can continue down, so that we can start with a trigram model and end up estimating the next word based on unigram frequencies.
- The selection of this model was based on the fact that such models are simple and in practice work well.
- The simple Shiny application was created, it can be seen at [https://itomashe.shinyapps.io/ShinyApp2](https://itomashe.shinyapps.io/ShinyApp2/)

Shiny Application  
========================================================
 ![text](NextWord.png) 
 
 ***
- Please note that initial load of the application can take several minutes. After the initial load, words can be entered in provided field. Next words will appear in blue color.
- Only news data set is loaded, so the 
- The R scripts related to the application, milestone report, references to used materials, etc can be found in the GitHub repo:

 
