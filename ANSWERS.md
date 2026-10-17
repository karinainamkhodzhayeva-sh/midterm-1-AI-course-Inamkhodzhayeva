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
| H |0.8889 |KK, degraded |0.8000 |0.6269 |0.9050 |$8923.34 |
| L |0.8056 |RU, degraded |0.7333 |0.5555 |0.8582 |$5400.00 |

Personal-data pages per year sent abroad under H:217,175

### 2b. Memo (at most 300 words)
I recomend adopting Po]ipline L , the self-hosted open vision- language model in Kazakhstan.
While Pipeline H achieves higher overall accuracy (88.89% vs 80.56%), Pipeline L provides an acceptable accuracy baseline (80.56% overall, 73.33% in its weakest cell). 

Financially, Pipeline L requires only 1 local server ($450/month) to handle the 3,500 daily pages (capacity up to 6,000 pages/day), resulting in an annual cost of $5,400. This saves $3,523.34 per year compared to Pipeline H ($8,923.34/year).

Most importantly, 17% of processed documents (217,175 pages annually) contain personal identification data (PII: individual names and IINs). Transmitting this sensitive personal data to overseas data centers under Pipeline H presents significant legal and regulatory compliance risks under Kazakh data protection legislation. Pipeline L keeps all data strictly on-premise within Kazakhstan, guaranteeing data sovereignty and privacy compliance while remaining significantly more cost-effective.


## Part 3: Explain your own numbers

### Q1

Number:0.96
Why (at most 40 words): The token ratio ( 2.16) divided by byte ratio (2.25) equals 0.96. Being close to 1.0 indicates that the Kazakh token premium stems primarily from UTF-8 byte expansion (2-byte Cyrillic encoding) rather than tokenizer fragmentation.

### Q2

Number:22.1%
Why (at most 40 words): Only English is cut, because 640 cl100k tokens expand to 657.5 e5 tokens (>512 limit), whereas RU (320) and KK (190) stay under 512. The cut tail is silently ignored during embedding generation.

### Q3

Number: 81.8%
Why (at most 40 words): Top-p = 0.8 retains tokens until cumulative probability reaches 80% (Monday and Friday), then renormalizes. Unlike temperature scaling which reshapes all probabilities, top-p dynamically truncates the low-probability tail without altering relative logit ratios.

### Q4

Number: 0 
Why (at most 40 words): Under penalties (+1 correct, -1 wrong), Model X (75-25=50) and Y (69-19=50) tie (difference 0). Public leaderboards prefer X (75 vs 69) because unpenalized accuracy rewards aggressive guessing over saying "I don't know". 

### Q5

Number:5.35 
Why (at most 40 words): The model is over-trained relative to Chinchilla's compute-optimal ratio, with about 5.35 times more tokens per parameter. Chinchilla argued that models such as GPT-3 were under-trained and that smaller models trained on more data could achieve better performance for the same compute budget.
