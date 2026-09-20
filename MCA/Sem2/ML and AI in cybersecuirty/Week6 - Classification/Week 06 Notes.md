# Classification
## Diff b/w classification and regression
- **Regression** predicts continuous numbers like **house prices (or any number from 0 to infinity)**
- **Classification** predicts categories or classes like **spam or ham, cat or dog, yes or no**
## Binary classification
- Here we are ~={yellow}predicting exactly two classes. Like email is either spam or not spam=~. **Like BINARY**
## Multi-class classification
- **One thing belongs to exactly ONE CLASS out of many options.**
	- **Example**: ~={green}Classifying a movie into ONE genre. It's either "Action" OR "Drama" OR "Comedy" OR "Horror"—just one category per movie.=~
## Multi-Label classification
- **One thing can belong to MULTIPLE classes at the same time.**
	- **Example**: ~={green}A movie can be tagged as BOTH "Action" AND "Drama" AND "Thriller" all at once. One movie gets multiple labels, not just one.=~

# Metrics
## What is Metrics
- Metrics are measurements that tell you how well your model is performing.
### Why we care:
- We care about metrics because they **tell us if our model is actually useful or not**.
## What kinds of things do we want to measure in MODEL
### Correctness of the model
- Accuracy, Precision, Mean Squared Error, R2-score.
### Speed of the model
- Time to make prediction — inference
- Time to train the model — training
### Resource Consumption
- Ram, disk space, cpu speed, gpu cores 
- Dollars/prediction or dollars/training
### Data
- Amount of data required to build your model 
- Cost to acquire the data

# Accuracy and Confusion
## Accuracy Equation
- $$TruePositives+TrueNegatives \div TruePositives+TrueNegatives+FalsePositives+FalseNegatives $$
### Accuracy for Cat's and Dops
- We have a 100 pictures, 50 are dogs, 50 are cats 
- Model found, 49 cats, 51 dogs 
- We said 49 things were cats, 47 were actually cats = 47 True Positives(TP)
- But… 2 things we said were cats, were not = 2 False Positives (FP)
- We said 51 things were dogs, 48 were actually dogs = 48 True Negatives (TN)
- But… 3 things we said were dogs, were cats = 3 False Negatives (FN)
- 47(TP) 48(TN) = 95 
- 47(TP) 48(TN) + 3(FN) + 2(FP) = 100 
	- **95/100 = 95% accuracy**

# Precision and Recall and F-Score
### Precision
- **Precision:** **Out of all the predictions** you made as "positive," **how many were actually correct?**.
- Formula: **Precision = TP / (TP + FP)**

Example: Out of 49 cats you predicted, 47 were actually cats. Precision = 47 / (47 + 2) = 47/49 = **96%**
### Recall
- **Recall:** **Out of all the actual positives** in your data, **how many did you correctly identify?**
- Formula: **Recall = TP / (TP + FN)**

Example: There were 50 actual cats. You found 47 of them. Recall = 47 / (47 + 3) = 47/50 = **94%**
### F-Score
- **F1-Score:** A balance between precision and recall. It combines both into one score.
- Formula: **F1 = 2 × (Precision × Recall) / (Precision + Recall)**

It's useful when you care about both precision and recall equally.
**Simple difference:**
- Precision = "How many of my predictions were right?"
- Recall = "How many actual cases did I find?"

# Choosing a Metric
## Choosing Good Metrics is a Paramount
- **How to choose a metric:**
	1. **Understand your problem:** What's the cost of different types of errors?
	    - Is a false positive bad?
	    - Is a false negative bad?
	    - Which one is worse?
	2. **Think about real-world impact:**
	    - Spam filter: False positive (blocking good email) is annoying
	    - Medical diagnosis: False negative (missing disease) is dangerous
	    - Different problems = different priorities
	3. **Choose based on priority:**
	    - If false positives are bad → Use Precision
	    - If false negatives are bad → Use Recall
	    - If both matter equally → Use F1-Score
	    - If everything matters equally → Use Accuracy
- **Example:**
	- **Email spam:** Precision matters more (don't block good emails)
	- **Tumor detection:** Recall matters more (don't miss tumors)
	- **General classification:** F1-Score (balance both)
