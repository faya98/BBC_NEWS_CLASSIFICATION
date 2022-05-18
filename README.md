# BBC_NEWS_CLASSIFICATION
## Dataset Description
Consists of 2225 documents from the BBC news website corresponding to stories in five topical areas from 2004-2005.
Natural Classes: 5 (business, entertainment, politics, sport, tech)

If you make use of the dataset, please consider citing the publication: 
- D. Greene and P. Cunningham. "Practical Solutions to the Problem of Diagonal Dominance in Kernel Document Clustering", Proc. ICML 2006.

All rights, including copyright, in the content of the original articles are owned by the BBC.

Contact Derek Greene <derek.greene@ucd.ie> for further information.
http://mlg.ucd.ie/datasets/bbc.html
## Functionalities of the code
1. Extracts the raw text from bbc_news_dataset.zip file and converts it into bbc.csv file
2. Pre-processes the data by lowercase conversion, removal of stopwords, removal of punctuations, and lemmatization
3. Split the data into train/development/test - 80%/10%/10%
4. Three feature entities are used - count, one-hot and tf-idf
5. For every feature entity number of features and feature selection methods are tuned using development set
6. For each feature entity a model is trained
7. Each model make predictions on test dataset
8. All 3 predictions are combined using majority voting
9. Accuracy, macro-averaged precision, macro-averaged recall, macro-averaged f1-score are calculated

