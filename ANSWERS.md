# Midterm 1: answers

GitHub username: karinainamkhodzhayeva-sh 
Session code: zebra-28 generator v1
Fingerprint: b3354d9d

## AI-use declaration

I used Gemini AI to explain the midterm condition. The data was taken from Google Colab. 

## Part 1: Retrieval and cost decision

### 1a. Metrics (all 60 questions)

| config | recall@1 | recall@3 | recall@5 | MRR@10 |
|---|---|---|---|---|
| A |0.6000 |0.7333 |0.8167 |0.6756 |
| B |0.3500 |0.4833 |0.6667 |0.4555 |

### 1b. Recall and 95 % Wilson interval of each candidate (recall at its own k)

| candidate | recall@k | lower | upper |
|---|---|---|---|
| A, k=3 |0.7333 |0.6099 |0.8287 |
| A, k=5 |0.8167 |0.7008 |0.8944 |
| B, k=3 |0.4833 |0.3617 |0.6069 |
| B, k=5 |0.6667 |0.5406 |0.7727 |

### 1c. Annual model cost in USD

| candidate | annual cost |
|---|---|
| A, k=3 |$10151.11 |
| A, k=5 |$13266.59 |
| B, k=3 |$6610.10 |
| B, k=5 |$7364.90 |

### 1d. Decision (at most 150 words)

Chosen candidate:B, k = 5

Candidate A, k=5 ($13,266.59/year) exceeds the annual budget limit of $11,700. Among affordable candidates, A, k=3 achieves the highest point recall (0.7333, interval [0.6099, 0.8287]). However, candidate B, k=5 achieves 0.6667 recall with interval [0.5406, 0.7727]. Because their 95 % Wilson confidence intervals overlap, A, k=3 and B, k=5 are statistically indistinguishable. Therefore, following decision rules, we select B, k=5 as the cheapest candidate in the top statistically tied pool, saving $2,786.21 annually compared to A, k=3.

Recall for condidate(B, k=5) by language:
EN: 0,5500 (55%)
RU: 0,9500 (95%)
KK: 0,5000 (50%)

### 1e. Next measurement (at most 60 words)
Expand the evaluation dataset from 60 to 300 test questions (100 per language). This will narrow the 95 % Wilson confidence intervals, resolving the statistical overlap between A, k=3 and B, k=5 to verify whether A's higher point recall justifies its additional cost.


## Part 2: A document pipeline you can defend

### 2a. Numbers

| pipeline | overall accuracy | weakest cell (language, condition) | accuracy there | lower | upper | annual cost |
|---|---|---|---|---|---|---|
| H | | | | | | |
| L | | | | | | |

Personal-data pages per year sent abroad under H:

### 2b. Memo (at most 300 words)

## Part 3: Explain your own numbers

### Q1

Number:
Why (at most 40 words):

### Q2

Number:
Why (at most 40 words):

### Q3

Number:
Why (at most 40 words):

### Q4

Number:
Why (at most 40 words):

### Q5

Number:
Why (at most 40 words):
