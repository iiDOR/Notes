# Machine Learning for Cybersecurity
## Problems ML Can Solve:

ML solves **~={green}security problems that are too complex=~** for **rule-based systems.**

**Example:** Detecting spam emails with fixed rules is hard:

- Spammers constantly change tactics
- New attack patterns emerge daily
- Manual rule updates can't keep up
- ML adapts and learns new patterns

## ML Viewpoint:

Instead of writing rules like "if email contains 'FREE' → spam," ML learns from data:

**Traditional approach:** Write 1000 rules manually  
**ML approach:** Show model examples of spam/ham → it learns patterns automatically.

## Selecting features requires domain knowledge
- A strong **understanding of the problem itself.** What is the attack, how does it work. 
- What is the **data we can get which represents the attack?**
- You need a way to extract a **numerical representation of your data**
- You also need to have some idea what would help the algorithms learn to differentiate between the classes 

# Phishing Detection with ML
## What is Phishing?

**Phishing = Masquerading attack**

Attacker pretends to be a legitimate website to steal credentials.

**Attack flow:**

1. Attacker sends lure (email, SMS, message) with a link
2. Link directs to fake phishing website
3. User thinks it's real (looks like Facebook, Google, bank, etc.)
4. User signs in with username/password
5. Attacker captures credentials

**Goal:** Steal email, bank account, social media passwords, etc.

## Traditional Approach: Blacklists

**Idea:** Maintain a list of known malicious websites and block them.

**Problem:** Fails quickly because:

- Phishing websites go up and down very fast
- New phishing sites created constantly
- Blacklists require **manual effort** to maintain
- **Outdated before you finish building them**

Example: List phishing site on Monday → it's gone by Tuesday → wasted effort.

## ML Automation Solution:

### Build a model that automatically detects phishing:

**Input:** URL  
**Output:** "Phishing" or "Benign"

**Training data needed:**

- List of benign (safe) websites with their URLs
- List of phishing websites with their URLs

Model learns from these examples → predicts on new URLs.

### Feature Extraction: 
#### What makes a URL phishing?

**Safe URLs:**

- [https://www.facebook.com](https://www.facebook.com)
- [https://www.google.com](https://www.google.com)

**Phishing URLs:**

- [http://www.facebook.com](http://www.facebook.com) (no 's' = suspicious)
- [https://facebook.com/give-me-your-login](https://facebook.com/give-me-your-login) (suspicious path)
- [https://abc.nyz.faceb00k.com/sign-in](https://abc.nyz.faceb00k.com/sign-in) (typo domain: "faceb00k" not "facebook")

**Key insight:** The domain is most important!

#### HTML Features: 
Look at the **page content**, not just URL.

**What to check:**

- **Is it asking you to login?** Extract forms from page
- **Are there logos?** Phishing pages mimic real sites
- **Number of images** — Phishing pages often have fewer images
- **Amount of text/source code** — Statistically, phishing websites have **less text** and **less source code** than legitimate sites
- **Number of JavaScript tags** — Different patterns in phishing vs benign pages

#### WHOIS Features:
WHOIS = database with domain registration info.

**What to extract:**

- **Geographic location** — Where is server hosted?
- **Domain age** — How old is the domain? (New domains more suspicious)
- **Identifying information** — Who registered it? (Legitimate companies have proper registration)

#### Considerations
1. Speed
2. Confidence
3. Metric Selection:
4. Labeled Data:
	- Which model to use? try all of it.