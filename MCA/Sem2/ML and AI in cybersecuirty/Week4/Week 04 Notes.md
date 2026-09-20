# 4.1
## The need for Test Sets
- **What is it:** data that you use to check if your trained model works well on **new data it hasn't seen before**.
## How do we create it
### Train Test Split
- Dividing your data in **Training Data (70-80%)** and **Test Data (20-30%)**
- With the **training data we train the model** and **~={green}then we make the model make predictions use this Training data and Test Data.=~**
- By doing so we will know the **Train Score** and **Test Score** and **~={cyan}these scores are the Evaluation Metrics.=~**
- And then we evaluate both the scores.
### How often can we evaluate.
- Remember for evaluating we will use TEST DATA set.
- so normally WE - 
	- **Train Model** 
	- **Evaluate the model** 
	- **Make changes to your model**

- So here the test score is bad then we make changes to the model and train it again the cycle goes on like a loop.
- The problem here is *If you keep evaluating on TEST DATA repeatedly and making changes based on it, your model will overfit to the test data.*
## When is it appropriate to use them
### We USE TEST DATA only once.
- Train Model on TRAIN data
- Evaluate on VALIDATION data
- Make changes to model
- Train again on TRAIN data
- Evaluate on VALIDATION data again
- Repeat steps 2-5 as many times as you want
- **Only at the very end, evaluate once on TEST data** (final score)

# 4.2 Train Test Split Options
## train_test_split
- Scikit-learn has an excellent module that splits ur data into 2 sets.
- train_test_split will take input as:
	- **data (x)**
	- **label (y)**
- train_test_split will return these:
	- **training_data    ==> x_train**
	- **training_labels ==> y_train**
	- **testing_data     ==> x_test**
	- **testing_labels   ==> y_test**
## Test set size
- It refers to how much do you want to split training set and testing set.
- You need enough data to train reliably.
- But you also need enough to test.
- Generally more is needed for training.
- **20-30%** for testing is common.
## Shuffling Your Data
- Randomizing your data during split.
- It is a good idea because if your data is organized in any kind of fashion - we probably don't want that order preserved.
	- `aaaaaabbbbbbbbbbb`--> we want a mix of both cases in **training** and **testing** **set.**
- **Edge case:**
	- Time-Series data should never be shuffled.
	- You don't want to mix the future and the past up.
## Stratification
- Classes are the **~={yellow}categories you're trying to predict=~**. For example, in **~={green}email classification, your classes are "spam" and "ham" (not spam).=~** In disease prediction, classes might be "sick" and "healthy."

- **Problem without stratification** Imagine you have 100 emails — 70 are ham and 30 are spam. If you randomly split into training and test without stratification, you might accidentally put all 30 spams in training and zero in test. Now your test data has no spam examples, so you can't properly evaluate if your model detects spam!

- **What Stratification does** It makes sure both your training and test sets have the same ratio. So if your original data is 70 percent ham and 30 percent spam, both your training and test sets will also be 70-30. This way, each dataset has examples of all classes to learn from and evaluate properly. Does that make sense now?
## Random States
- **What is Random State** When you split data randomly, you might get different splits each time you run the code. Setting random state to a number (like random state equals 42) makes it reproducible—you get the exact same split every single time. It's like locking in the randomness so it's consistent.
