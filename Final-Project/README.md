# FINAL REPORT

Each part (1-4) contains a detailed description of each step we did.  
In this report we link to these parts and we will explain in detail what is happening in each part.

### PART 1 - data collection

* we used gmail api to collect emails of five different senders. (for this, we used some new libraries such as: email,imaplib,csv more information in part1 file) 
* we save the data locally as csv file.
* we clean signs the were not relevant for our goal, by using re library (such as links to emoji)
* we explore the data: number of messages/words/characters for each type and plit graphs that show these details more clearly.


### PART 2 - Build a text data classifier

* we read the data from the file we save locally
* we change number characters to NUM , we did it after we check the frequency use of numbers for each type and we got to conclude that there are some types that use more than others.
* to convert the data from unstructured data to structured data we used 2 different methods BOW and TFIDF (parameter tuning of each one of them you welcome to see at PART 2 section 2.1).
* we trained the models by 2 different training types , train/test and k-fold (k=10) because our data is very small and we didnt want to waste data on test while we training our models we decide to use k-fold, and we gave more attention during the proccess to k-fold results.
* we trained 3 different machine learning by both TFIDF and BOW, at the end we plot a graph that compare the results with each one of them and got to the conclude that TFIDF gave us better results, so we continue with using only TFIDF.
* we train the fourth model - Random Forest, in order to get the best result for this model we wrote a function plot_evaluate_parameter that take range of values for each parameter and plot a graph gthat describes the accuracy for this value. and them by choosing best value for each parameter we trained our model.
* at last we tried one more ensemble model: VotingClassifer in order to get even better moel then we already found.
* we plot graph with the results of all the models (6 different models) and chose the vest one: LINEARSVC (highest accuracy and lowest std)
* we saved the model and the tfidf vectorizer for future use (in part 4)

(models we used: LogisticRegressionClassifier, GuassianNB, LinearSVC, Random forst, VotingClassifier)

### PART 3 - DEEP NETWORK & TEXT GENERATION

* we used tabulate library in order to plot tables.
* we read the data in order to generate new data from it.
* we made Preprocessing, by cleaning the data, we cleaned links , and not rellevant signs.
* we used n-seq-architecture that we study at lecture.
* we decided to clean characters that are not common in order to reduce the size of the vocabulary, we did it buy building a function that counts the follwing details for each type: number of words, number of caracters,capital letters appearance (%) , number of unique capital letters, number of unique lower letters, digit appearance (%) and also for each punctuation character the number of times it used. this function gave us very strong tool to decide wisely which character we want to clear and which not. (we clear only uncommon characters that will not have significant effect on the generated data.
* we trained n-seq-architecture for each type. (parameter tuning for each one you are welcome to see at PART 3 section 3.3)
* we generated data for each type, we decided how many and how long the data should be by the conclusions we reached at when we explore the data part 1.
* we saved the generated data locally.

### PART 4 - Classification of generated text

* we used pickle library to load the classifier and vectorizer we trained in part 2.
* we read the generated data.
* we cleaned the data in the same way we cleaned when we train the model.
* we predict the new rsults for each type. (3 of them were with 100% accurate and 2 others with 66%,77% accurate)
* we found that this is happend because these messages were significantly longer than others, so they were more prone to mistakes.
* we printed confusion_matrix that summarize the results.


