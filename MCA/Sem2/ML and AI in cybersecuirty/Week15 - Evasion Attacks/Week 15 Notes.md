# Adversarial Evasion Attacks
## What is an adversary
- An **adversary** is an ~={yellow}**attacker**=~ or **threat actor**—~={green}**someone who intentionally tries to fool, break, or compromise an ML model**=~ through attacks like evasion, poisoning, model stealing, backdoors, etc.

## Is Machine Learning Secure?
- **NO**

## What Domains are Affected from Adversarial ?
1. Computer Vision (images, facial recognition)
2. Malware (malware detection)
3. Spam (spam filters)
4. Phishing (phishing detection)
5. Voice (voice recognition, speech-to-text)
6. Text (NLP models, text classification)

# How Adversarial Evasion Attacks are Performed
- Techniques for performing adversarial evasion attacks:

## Fast Gradient Descent Sign Method (FGSM)
1. Model makes a prediction on input
2. Algorithm calculates which direction to perturb (modify) the input to fool the model most
3. Add small perturbations in that direction
4. Model gets fooled

**Why "fast"?** It's computationally quick compared to other methods like PGD.

- Principles of Evasion Attacks
	- The attack should work
	- It should be imperceptible.
	- It should be functional
	- Ideally the perturbations are small (to avoid detection). 


## Mimicry Attack
Attacker makes the malicious input **look like normal/legitimate input** so it mimics good behavior.

**Example:**

- Normal spam filter sees: "Click here to get FREE money!!!" → Detects as spam
- Mimicry attack: Spammer rewrites it to look normal: "Check out our new product offers" → Looks legitimate, bypasses filter

**Key:** Attacker hides malicious intent by copying patterns of normal, good inputs.

# Threat Modeling Adversarial Evasion Attacks
- These are **~={yellow}Threat models based on how much information the attacker=~** has about the model.

## Perfect Knowledge
- **You know everything!**
- **Algorithm used** to train defending model
	- hyper-parameters
	- model weights
- **Training data**
- **Testing / Evaluation data**
- **Feature representation**
- You just don’t know the password to the users computer 
## Limited Knowledge
- **You know … something** 
- **You don’t know the feature representation**, but you have **access to some samples**.
- You know **what kind of model is defending**, but you don’t the model weights (or hyper-parameters)
- You are able to collect some data that is probably very similar to the defending models data.
## Zero Knowledge
- **You don’t know anything … Except you do know**
- **What the model is defending or doing** (malware detector, image classifier, etc.)
- **You are able to query the model** – imagine it is a cloud API, you can ask it questions and get back answers
- You may get **model probabilities or hard labels**
- You have to **make your own assumptions about the feature representation** of the mode
## Kerckhoff's Principle
**"Security should not depend on the secrecy of the system."**

**Meaning**: Don't assume your model is safe just because attacker doesn't know how it works. Assume attacker has perfect knowledge (white-box) and design defenses accordingly.

**Why?** Because attackers might eventually figure it out, so don't rely on secrecy.

# Zero Knowledge Black Box Evasion Attacks

## Principle of Transferability
- ~={orange}**Adversarial examples that fool one model**=~ **~={green}often fool other models too,=~** even if those models have different architectures.
- **Example:** An adversarial image **~={yellow}that fools a CNN might also fool a different CNN=~** or even a different model type.
## Surrogate Models
- Attacker **doesn't have the target model**, so they:
	1. Build their own "fake" model (surrogate) with similar architecture
	2. Generate adversarial examples on their fake model
	3. Use those examples on the real target model
	4. Works because of transferability!
## Hard Labels vs Probabilities
- **Hard labels:** Model outputs only the class. Example: "SPAM"
- **Probabilities:** Model outputs confidence scores. Example: "SPAM: 95%, HAM: 5%"

**Why it matters:** With probabilities, attacker gets more info to craft better adversarial examples.
## Assumptions
Assumptions the attacker makes:

- Model has similar structure to surrogate model
- Transferability principle holds
- Can query model multiple times

# Heterogeneous vs Homogeneous Data
## Homogeneous Data
All features are the same type. Continuous, numeric values in a uniform space.

**Example:** Images

- Pixel values (0-255) for R, G, B channels
- All features are continuous numbers
- Can add small perturbations smoothly
- FGSM and gradient-based attacks work well

**Why "homogeneous"?** You can treat the entire space uniformly. Add noise anywhere; it's mathematically consistent.
## Heterogeneous Data
Mixed feature types. Some continuous, some categorical, some discrete.

**Heterogeneous features** **may be immutable** (the attacker cannot control it

**Example:** Credit card fraud detection

- Age: 35 (continuous)
- Gender: Male (categorical)
- Transaction amount: $150.50 (continuous)
- Number of transactions today: 5 (discrete/count)
- Country: USA (categorical)

**Why "heterogeneous"?** Can't just add random perturbations everywhere. "Gender: Male + 0.01 = ?" doesn't make sense.