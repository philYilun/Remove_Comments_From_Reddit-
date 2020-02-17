# Remove_Comments_From_Reddit-
Analyzing whether comments got removed from Reddit feeds, an NLP analysis

## Objective:<br>
The analysis target to use text to predict the comment in reddit to be removed or not <br>
 
#### Part 1. Draw a baseline for simple regression classifier   <br>
- the data showing imbalance sample issue -- fix by downsampling
- the outcome showing overfitting with high accuracy(80%) for train and (69%) for test<br>
#### Part 2. Model building and tuning <br>
a. Methods with simple normalization <br>
- Tf-idf, 
- n-gram
- characters/words as unit token
- change the threshold : min_df, max_feature, stop_words, and scaling  
- Using different encodding to deal with foreigh words/characters

b. Latent semantic analysis with dimention reduction techniques:  <br>
- SVD 
- LDA  
 
c. Refining the model by adding derived features <br>
 - Length of the comment
 - Whether it include a website, what website is included
 - whether include number
 - Number of non-english words, etc.
#### Part 3. <br>
Using existing word dictionary to distill the corpus <br>
- Gensim corpora output is tuple and can not be applied to TF-IDF vectorizer
- Build a customized tokenizer, leave only words after lematization that is in the corpora word dictionary
- Use trained Word2Vec directly, the model could be another baseline model

### Conclusion:<br>
The analysis focused on modeling text and predicting the item got removed from the stream or not 
Words/Features closely associated with the result 
  - comments with 'Upvote', 'Feminist' (discriminated word), words that is not polite are highly associated with deleting
  - comments with 'Edit', 'Recommends', and words related to research terminology are associated to not deleting

To yeild better predictive power
  - More cleaning, derive new features on the text, fine tuning on model help providing better insights of what the characteristics of the comments that got removed.  
  - However, not necessary to yield better result. 
  - Dimension reduction (SVD) will also provide a good result given the less space and computing power it take 
  - Leveraging existing trained model Word2Vec could also serve as a baseline
