
# Main Attack Types:

### Evasion Attack:
- What is it: ~={green}An attack where the **~={cyan}attacker modifies input data to fool the model=~** into **~={blue}making wrong predictions=~**, while **evading detection systems**.=~
### Poisoning attack:
- **~={orange}Attacker poisons (corrupts) the dataset during training.=~** This affects all **downstream ML tasks because the model learns from bad data.**
### Model inversion
- Attacker ~={green}uses the **models output to scores**=~ ~={yellow}**to reverse engineer and retrieve the actual training data**=~
### Membership inference
- Attacker **~={yellow}tries to determine whether a specific data sample was used in the model's training set or not.=~**
### Model stealing
- **~={yellow}Attacker steals the actual model itself=~** (the trained weights, architecture, everything).
### Reprogramming
- Attacker **modifies the model's behavior by feeding it specific inputs** that cause it to **behave differently than intended**. The attacker essentially "reprograms" the model without changing the code.
### ML backdoors
- Attacker **plants a "backdoor" in the model during training or after deployment.** When a **specific trigger input is given, the model behaves maliciously.** For normal inputs, it works fine.
# Defenses Against Evasion Attacks
## Detection
- Detects if an input is adversarial or not.
- **Detection defense against evasion attacks:**
	1. Input comes in
	2. Detection model checks: "Is this input adversarial/malicious?"
	3. If YES (detected as adversarial) → Quarantine it for further examination
	4. If NO (normal input) → Pass to ML model
## Robustness
- Robustness is the **~={green}practice of making a model unaffected=~** (or less affected) by the adversarial inputs 
- In the case of robustness, **~={cyan}the model will simply correctly classify the adversarial example=~**

### Robustness Techniques:
- **Adversarial training:** 
	- ~={yellow}Create **Adversarial** sample and label them correctly, add them to training data.=~ Now the model learns "when i see input like this".
	- We use **Projected Gradient Descent (PGD)** -- technique to create adversarial samples that fool the model effectively.
- **Feature denoising**
	- **~={yellow}Removes features that are strongly correlated with adversarial perturbations=~** (input). By removing those features the adversarial attacks become less affective.

### Detection Techniques:
- **Detection - Feature Squeezing**
	- **Create a bassline feature space from the original images**.
	- When **new input comes in**, **~={yellow}it compare it to baseline we created.=~**
	- If the new input is very different from baseline --> then it flagged as adversarial.
- **Detection - Uncertainty**
	- In this techniques **~={green}we detect adversarial inputs is to ~={yellow}look at the models confidence / uncertain=~ is it in its predictions.=~**