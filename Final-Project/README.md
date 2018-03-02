# FINAL REPORT

Each part (1-4) contains a detailed description of each step we did.  
In this report we link to these parts and we will explain in detail what is happening in each part.

### PART 1 - data collection

* we used gmail api to collect emails of five different senders. (for this, we used some new libraries such as: email,imaplib,csv more information in part1 file) 
* we save the data locally as csv file.
* we clean signs the were not relevant for our goal, by using re library (such as links to emoji)
* we explore the data: number of messages/words/characters for each type and plit graphs that show these details more clearly.

[a link](Part1.ipynb)

### PART 2 - Build a text data classifier

* we read the data from the file we save locally
* we change number characters to NUM , we did it after we check the frequency use of numbers for each type and we got to conclude that there are some types that use more than others.
* to convert the data from unstructured data to structured data we used 2 different methods BOW and TFIDF (parameter tuning of each one of them you welcome to see at PART 2 section 2.1).
* we trained the models by 2 different training types , train/test and k-fold (k=10) because our data is very small and we didnt want to waste data on test while we training our models we decide to use k-fold, and we gave more attention during the proccess to k-fold results.
* while training we used GridSearchCV to examine different values to parameters.
* we trained 3 different machine learning by both TFIDF and BOW, at the end we plot a graph that compare the results with each one of them and got to the conclude that TFIDF gave us better results, so we continue with using only TFIDF.
* we train the fourth model - Random Forest, in order to get the best result for this model we wrote a function plot_evaluate_parameter that take range of values for each parameter and plot a graph gthat describes the accuracy for this value. and them by choosing best value for each parameter we trained our model.
* at last we tried one more ensemble model: VotingClassifer in order to get even better moel then we already found.
* we plot graph with the results of all the models (6 different models) and chose the **best one**: LINEARSVC (highest accuracy and lowest std ,92% acc)
* we saved the model and the tfidf vectorizer for future use (in part 4)

(models we tried: LogisticRegressionClassifier, GuassianNB, LinearSVC, Random forst, VotingClassifier)

[a link](Part2.ipynb)

### PART 3 - DEEP NETWORK & TEXT GENERATION

* we used tabulate library in order to plot tables.
* we read the data in order to generate new data from it.
* we made Preprocessing, by cleaning the data, we cleaned links , and not rellevant signs.
* we used n-seq-architecture that we study at lecture.
* we decided to clean characters that are not common in order to reduce the size of the vocabulary, we did it buy building a function that counts the follwing details for each type: number of words, number of caracters,capital letters appearance (%) , number of unique capital letters, number of unique lower letters, digit appearance (%) and also for each punctuation character the number of times it used. this function gave us very strong tool to decide wisely which character we want to clear and which not. (we clear only uncommon characters that will not have significant effect on the generated data.
* we trained n-seq-architecture for each type. 
we define a single hidden LSTM layer with 128 memory units. (units recommended to be in jump of 32 units)
The network uses dropout probability of 0.2.
The output layer is a Dense layer using the softmax activation, this function calculate for each character a prediction between 0 and 1.
for one type we used 256 memory units this type has the longest messages and therefore the vocabulary is bigger, we tried to train the model with 128 mu but the results were not good as with 256. We also used categorical_crossentropy as the losing function on the RNN.
for optimizer we tried both rmprop and adam. 
(more particular details about parameter tuning for each one you are welcome to see at PART 3 section 3.3)
* we used checkpoints wwhile training to always save the best weights. (we used this because for some types it took more than 6 hours to train, so in case of failure we will not lose the data.
* we generated data for each type by taking a seed from the data and each step decide the next characters depend on the last n characters. 
* we decided how many and how long the data should be by the conclusions we reached at when we explore the data part 1.
* we saved the generated data locally.

[a link](Part3.ipynb)


### PART 4 - Classification of generated text

* we used pickle library to load the classifier and vectorizer we trained in part 2.
* we read the generated data.
* we cleaned the data in the same way we cleaned when we train the model.
* we predict the new rsults for each type. (3 of them were with 100% accurate and 2 others with 66%,77% accurate)
* we found that this is happend because these messages were significantly longer than others, so they were more prone to mistakes.
* we printed confusion_matrix that summarize the results.

[a link](Part4.ipynb)

the confusion matrix:

![alt text](./image/)

