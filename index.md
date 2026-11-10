---
layout: default
title: DSC 180A Methodology Assignment 4
---

# Sam Ouyang

**Email:** saouyang@ucsd.edu

**Section:** D12, NLP Credit Score Development

**Mentor:** Goutham Valeti

---

**What is the most interesting topic covered in your domain this quarter?**
The most interesting topic in my domain has been using natural language processing to turn short, messy transaction memos into structured signals about credit risk. A memo is often just a few words — a merchant name, a payment app, or an abbreviation — yet classifying it into the right spending category can reveal behavior, such as gambling, buy-now-pay-later use, or frequent peer-to-peer transfers, that traditional credit variables don't capture directly. What makes this especially interesting is that the labels themselves are not obvious: human coders can reasonably disagree on ambiguous memos, so the quality and consistency of the categorization matters just as much as the model built on top of it. It showed me that in applied NLP, defining the problem and the labels carefully is a large part of the actual data science.

**Describe a potential investigation you would like to pursue for your Quarter 2 Project.**
For Quarter 2, I would like to do a deep dive on gambling and prediction market classification within transaction memos. These transactions are easy to confuse with neighboring categories — a payment to a prediction market can look like an investment, a sportsbook payment routed through a payment app can look like a peer-to-peer transfer, and a casino charge can look like entertainment — so they are a natural stress test for our classifier. I would build and evaluate a dedicated approach for distinguishing gambling and prediction market transactions from investments, transfers, and entertainment, and then analyze the transactions it finds: how common they are, which categories they are most often confused with, and how they co-occur with other potential risk signals such as BNPL activity and bank fees. The goal would be to learn whether gambling and prediction market activity forms a distinct, measurable pattern that is useful for understanding credit risk tendencies, with the results presented in a report and on a project website. This would be a good extension if our core Quarter 1 classification pipeline works well, and a useful focused case study even if we need to narrow the broader project.

**What is a potential change you'd make to the approach taken in your current Quarter 1 Project?**
One change I would make to our Quarter 1 approach is to treat the human labels less as ground truth and more as something that needs to be validated first. In our manual categorization, different coders used different shorthand and sometimes made different calls on the same memo — for example, classifying a payment by the payment channel used rather than by what the payment was actually for. Before training a model, I would write explicit decision rules for these recurring ambiguous cases (such as "purpose over payment method"), measure inter-coder agreement, and adjudicate disagreements to build a smaller gold-standard labeled set. I would expect this to produce cleaner training data and a more honest evaluation, since a model cannot be more reliable than the labels it is graded against.

**What other techniques would you be interested in using in your project?**
I am interested in moving beyond a TF-IDF and traditional classifier baseline in a few ways. First, I would like to try text embeddings and a fine-tuned transformer model, which should handle short, ambiguous memo text and unseen merchant names better than word counts alone. Second, I would like to use embedding-based clustering to discover subcategories inside broad labels — for example, separating sportsbooks, casinos, and prediction markets within "gambling" rather than treating them as one group. Third, I am interested in uncertainty quantification: having the model report confidence, routing low-confidence memos to human review, and using those reviewed cases as new training examples through active learning. Together, these techniques would make the classifier both more accurate and more trustworthy for a credit-risk application.
