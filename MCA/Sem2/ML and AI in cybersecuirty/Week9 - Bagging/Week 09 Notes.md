# Introduction to Ensemble Methods
## What's an ensemble ?

Simple idea: Instead of trusting one model, you build **multiple models** and combine their predictions.

**Why does this work?**

**Each model makes different mistakes**. When you combine them:

- Good predictions reinforce each other
- Bad predictions cancel out
- Overall accuracy gets better

## Types of Ensemble Methods
So the hierarchy is:  
- **Ensemble Methods** (big category)  
- **Bagging** (type)  
- **Random** **Forest** (specific algorithm using bagging)  
- **Boosting** (type)  
- **Gradient** **Boosting** (specific algorithm using boosting)  
- **Stacking** (type)

## Bagging
- It's an **ensemble method that combines multiple models** to **~={cyan}reduce overfitting and improve accuracy.=~**

### Bootstrap Sampling:
- Randomly **~={yellow}resample from original data to=~** ~={orange}**create multiple "bags"**=~ (subsets).

- **Original set:** ~={purple}**[apple_1, orange, melon, watermelon, apple_2, pineapple]**=~

- You create multiple bags by random sampling.
- **Two types of sampling:**

	~={blue}**1. Without Replacement:**  =~
	Once you pick an item, you can't pick it again. **in the same bag**
	
	**Bag1:** ~={purple}[apple_1, orange, melon, watermelon]=~ ← each item appears once max  
	**Bag2:** ~={purple}[apple_2, pineapple, orange, melon]=~ ← different selection, no duplicates
	
	**Problem:** Limited diversity. Bags are too similar to original.

	~={blue}**2. With Replacement:**  =~
	You can pick the same item multiple times.
	
	**Bag1:** ~={purple}[apple_1, apple_1, orange, melon, watermelon]=~ ← apple_1 picked twice  
	**Bag2:** ~={purple}[orange, orange, melon, apple_2, apple_2]=~ ← duplicates allowed
	
	**Advantage:** Creates diversity. Each bag has different distribution. This is what bagging actually uses.

# Bagging + Tree = Random Forest
## What is Random Forest
- Random Forest is an ensemble method that builds on **bagging data** ~={cyan}but adds an extra layer of randomness.=~

## Workflow of Random Forest
- **Create multiple bootstrap samples** (bags) from training data
- Build a **Decision Tree** on each bag
- **Each tree makes a prediction**
- **Combine predictions** (voting for classification, averaging for regression)
## Bootstrapping Features:

When building each decision tree, at every node, the tree only considers a **random subset of features** (not all features).

**Example:**  
Original features: [age, income, credit_score, employment_length, debt]

Tree1 might use: [age, credit_score, debt]  
Tree2 might use: [income, employment_length, credit_score]  
Tree3 might use: [age, income, debt]

Each tree sees different features → makes different decisions → **more diversity!**

## Voting
- Classification (Majority Vote):
- Regression (Average):

**Pros:**

✓ Reduces overfitting (multiple trees + randomness)  
✓ Fast (trees trained in parallel)  
✓ Works with both numerical and categorical data  
**Cons:**

✗ Memory intensive (stores many trees)  
✗ Slower prediction time (must query all trees)  
✗ Can overfit if trees too deep  

# Boosting: An Ensemble That Gets Smarter
- Train a **series of models that slowly get smarter.**
- **~={orange}Each model will learn from the mistakes of the previous model=~** (gets boosted!)
- The **~={cyan}final model is a combination of all these models=~.**

- **AdaBoost (Adaptive Boosting):**

- **How it works:**
	1. **Build first model** (weak learner) **on original data**
	2. Identify samples it got **wrong**
	3. **~={green}Increase weight on those wrong samples=~**
	4. **Build second model focusing** more on those **hard samples**
	5. Identify new mistakes
	6. Build third model focusing on those
	7. Continue...
	8. **Combine:** Weighted vote (better models get higher weight).

- **Example:**
	- Model1 trained on all data equally → gets 80% right
	- Model2 trained with high weight on those 20% failures → focuses on hard cases
	- Model3 trained on remaining failures
	- Final prediction: Weighted combination of all three.

- **Pros:**

	✓ **Better Performance** — Often beats random forest and bagging  
	✓ **Handles complex** patterns well  
	✓ **Sequential learning** = smarter models

- **Cons:**

	✗ **More things to manage** — Many hyperparameters to tune (learning rate, depth, iterations, etc.)  
	✗ **Computationally expensive** — Can't parallelize easily (models built sequentially, not in parallel)  
	✗ Slower to train than bagging  
	✗ Harder to interpret.


**Gradient Boosting:**  
Sequential boosting that uses mathematical gradients to guide improvement. Each tree "steps" in the direction of better predictions.  
  
**XGBoost:**  
Optimized implementation of gradient boosting. Faster, handles larger datasets, prevents overfitting better.  
  
**LightGBM:**  
Another optimized gradient boosting implementation. Similar to XGBoost but uses different tricks for speed and efficiency.