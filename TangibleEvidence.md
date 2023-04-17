Alan Nguyen  
Junction of Statistics and Biology  
C&S Biology 199  
005-565-753  


# Tangible Evidence  


## Purpose  
Christy Lee is a UCLA PhD student and conducts research at The Junction of Statistics and Biology. One of her ongoing projects includes investigating automatic cell annotation methods, which classify cells by their gene expression. Two types of classifications were used: general classification, meaning fewer classes of cells, and specific classification, meaning more classes of cells. Interestingly, in some cases, she observed that the specific classification outperformed the general classification, which is contrary to what she expected. My role is to assist Christy in finding out why this occurs; if this phenomenon can be quantified or predicted, it can be used as a tool to help users with automatic annotation methods and estimate if subtypes are likely to be accurately identified or not.


## Additional Questions  
Besides understanding why the specific classification outperformed the general classification, there are a few additional questions that we aim to answer that fall into the scope of this investigation, which I will list here:
What is the best way to evaluate classifier performance?
What is the relationship of the classes?
Does this apply to other algorithms?


## Methods  
The course of the project (so far) is as follows:
1. Remove individual classes from the training data used by the support vector machine (SVM). There should be as many data sets as there are individual cell classes; this should be done with specific and general classes.
2. Train the SVM with the training data missing a specific class.
3. Run the SVM to predict the classes of the cells in the test data.
4. Compute the F1 scores to assess the model performance.


## Programs Written  
I will be discussing each of the programs I have written, and some of the elements I took into consideration while constructing them. My descriptions will provide an overview, and then the code with explanations in the markdown cells. The time and space complexity of my programs may not be ideal, and I might have hardcoded some of the processes that have existing built-in functions. My coding background is from the courses CS 31-33 and CS 35L, which do not focus on data analysis and manipulating data sets; I did my best to write optimal and efficient programs, often referring to online documentation for assistance.

## *remove.ipynb*  
The goal of this program is to accomplish the first step in the methods section, removing each of the classes in the training data. The most challenging part of writing this program was removing the columns that represented the cells in the training data, but I was able to accomplish this by using an intermediate array to retrieve the column labels, then using the DataFrame *drop function*. This function outputs the training data and labels with specific cell classes removed, which are to be used in *SVM_Full_Data_Function.ipynb*.

    
## *SVM_Full_Data_Function.ipynb*  
As previously mentioned, this program consists of a function that uses the output files from *remove.ipynb* that hold the training data and the training data labels with a specific class removed. The code for passing the files through the SVM was provided by Christy, but I had to adapt it into a function form to make it more efficient to repeat.


## *compare.ipynb*  
This program uses the csv outputs from *SVM_Full_Data_Function.ipynb* and outputs the macro and micro F1 scores for each of the specific classes. I used the *f1_score* function, imported from *sklearn*, but I had to take some preliminary steps like organizing the classes into an array and setting up a storage container for the values. The output of the function is two DataFrames, one storing macro F1 scores for each class and the other storing micro F1 scores.


## Measuring the SVM’s Efficacy  
Although we ended up using F1 scores, determining how to best measure the SVM’s efficacy was one of the challenges encountered during the project. Christy and I discussed this extensively, and weighed the pros and cons of each measure. Accuracy alone captures how many instances the SVM was right, but it does not note the times it was wrong and how it was wrong (false positive or a false negative), which should be considered. We decided upon F1 scores because they consider both precision and recall, but we have not yet decided whether we will be using the micro or macro F1 score. Christy suggested that we address another aspect of the model performance: missing data.  
When we say missing data, we refer to how the machine responds to a certain class when the class was not present in its training data. This is, of course, inevitable, because there are rare cases in which all possible scenarios can be predicted and simulated. If the model is never taught to identify a certain cell class, when it encounters it, it will not know how to respond. The machine may incorrectly identify the unknown cell as a known class, but which class and why is the question, or throw an alert. The machine’s response could be a multitude of things, and is worth noting in our analysis.


## Continuation of the Project  
This quarter was a period of gathering the necessary values in order to begin assessing the SVM’s performance. As noted earlier in the paper, the main goal is to note why the specific classification outperformed the general classification. As next quarter approaches, I will be delving more intensely into this question, comparing the F1 scores to one another, looking into why removing specific classes leads to less effective predictions, and if these observations can be quantified or predicted. I am currently unsure of how to best compare the F1 scores, considering that there are so many for each set of training data. Christy mentioned taking an average F1 score from each set to consolidate the number of values present from the data analysis.
Christy provided a number of papers on classification and its most effective measures, which I have begun and will continue reading through, and I will be searching for my own articles for additional insight. I will present my progress to Christy and Dr. Li, and I am open to suggestions for the direction of this project and any revisions on my work so far.


## Acknowledgements  
Thank you to Dr. Li and Christy for your mentorship and direction; I am amazed by your true desire to uplift rising researchers and students. I am excited for what is to come!  
Thank you to Alicia, who has been a great help in navigating this project. I look forward to our continued collaboration!
