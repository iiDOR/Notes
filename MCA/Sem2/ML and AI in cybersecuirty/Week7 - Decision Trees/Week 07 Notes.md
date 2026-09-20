# Decision Trees
- **What is a Decision Tree?**
	- A decision tree is an algorithm **~={orange}that makes decisions by asking a series of yes/no questions=~** about your data. It splits the data into groups based on these questions until it can classify things.
```txt
                Start
                  |
         Is it Action?
           /           \
         Yes            No
         |              |
      LIKE        Is it Horror?
                   /        \
                 Yes        No
                 |          |
              DISLIKE      LIKE
              
              
## SPAM DETECTION

              Email
                |
         Contains "FREE"?
           /           \
         Yes            No
         |              |
       SPAM       Contains "Click here"?
                    /            \
                  Yes            No
                  |              |
                SPAM          NOT SPAM
```

## Spam Tree
## Pseudocode
**Decision Tree Algorithm - Full Process:**  
  
**Step 1: Check Base Cases**  
Look at your data. Ask: "Are all emails the same class (all spam or all not spam)?" If yes, stop. If no, continue.  
  
**Step 2: List all features you have**  
Example: Contains FREE, Contains Click here, Contains Urgent, From unknown sender  
  
**Step 3: For EACH feature, calculate Gini Impurity**  
You must test every single feature. For each one:  
- Calculate parent Gini  
- Split the data on that feature  
- Calculate left child Gini (yes branch)  
- Calculate right child Gini (no branch)  
  
**Step 4: Compare results**  
Look at all the Gini values from all features. Which feature gave the best split (lowest Gini)?  
  
**Step 5: Pick the best feature**  
Use that feature as your decision node.  
  
**Step 6: Repeat**  
Take each branch (left and right) and repeat Steps 1-5 until you reach base cases.

# Splitting Criterion
## Gini Impurity - 0 - 0.5
You're right, let me slow down and be clearer.

**What is Gini Impurity?**  
It measures how "mixed" or "impure" a group is. If all emails are spam, Gini is 0 (pure). If it's half spam, half not spam, Gini is higher (mixed).

**Original Data:**  
100 emails total: 30 spam, 70 not spam  
  
**Step 1: Calculate Parent Gini**  
- Proportion spam = 30 / 100 = 0.30  
- Proportion not spam = 70 / 100 = 0.70  
- Square each: (0.30)² = 0.09, (0.70)² = 0.49  
- Add squares: 0.09 + 0.49 = 0.58  
- Parent Gini = 1 - 0.58 = 0.42  
  
**Step 2: Now we decide to split on "Contains FREE"**  
  
Here's where left and right come from. We go through all 100 emails and count:  
- How many spam emails contain "FREE"? Answer: 25 spam  
- How many not-spam emails contain "FREE"? Answer: 5 not spam  
- Total in left branch: 30 emails  
  
- How many spam emails don't contain "FREE"? Answer: 5 spam  
- How many not-spam emails don't contain "FREE"? Answer: 65 not spam  
- Total in right branch: 70 emails  
  
**Step 3: Calculate Left Child Gini (emails that contain FREE)**  
- Proportion spam = 25 / 30 = 0.83  
- Proportion not spam = 5 / 30 = 0.17  
- Square each: (0.83)² = 0.69, (0.17)² = 0.03  
- Add squares: 0.69 + 0.03 = 0.72  
- Left Gini = 1 - 0.72 = 0.28  
  
**Step 4: Calculate Right Child Gini (emails that don't contain FREE)**  
- Proportion spam = 5 / 70 = 0.07  
- Proportion not spam = 65 / 70 = 0.93  
- Square each: (0.07)² = 0.005, (0.93)² = 0.86  
- Add squares: 0.005 + 0.86 = 0.865  
- Right Gini = 1 - 0.865 = 0.13  
  
**Summary:**  
- Parent Gini: 0.42  
- Left Child Gini: 0.28  
- Right Child Gini: 0.13  
  
Both children have lower Gini than parent, so "Contains FREE" is a good feature to split on.

## Information gain Ratio
**What is Entropy?**  
- Entropy measures **how mixed or disordered a group is**. Similar to Gini, **but uses a different formula.**

**Entropy Formula:**  
~={green}**Entropy = -Σ(p_i × log2(p_i))**=~

Where p_i is the proportion of each class.

**Example with 100 emails (30 spam, 70 not spam):**

Entropy = -(0.30 × log2(0.30)) - (0.70 × log2(0.70))  
Entropy = -(0.30 × -1.74) - (0.70 × -0.51)  
Entropy = 0.52 + 0.36  
Entropy = 0.88

This 0.88 is the parent entropy. **Higher entropy means more mixed.** **Lower means pure dataset**