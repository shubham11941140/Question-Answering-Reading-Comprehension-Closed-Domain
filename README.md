# Question-Answering-Reading-Comprehension-Closed-Domain
Implements the Q/A Task where it finds answer from a relevant passage using Coreference Resolution

## Introduction

**Question Answering (QA)** is a task in Natural Language Processing (NLP) that aims to automatically answer questions based on a given passage of text. It is a subtask of Information Retrieval that aims to find the answer to a question in a given passage of text. It is a challenging task in NLP because of the ambiguity of the language and the need to generalize to new questions.

## Closed Domain

**Closed Domain QA is a subtask of QA that aims to answer questions about a specific domain**. The domain is defined by a set of documents that are relevant to the questions. The domain is closed because the set of documents is fixed and does not change.

### Our focus is on Closed Domain QA

## Dataset

The text file given to us is the passage from which we have to find the answer to the question.

The question is given to us as a string.

Q1: What causes precipitation to fall?

Passage:
Sent1: In meteorology, precipitation is any product of the condensation of atmospheric water vapor.
Sent2: Precipitation falls under the effect of gravity.

Ans: [Gravity]

Q2: What group in the Periodic table oxygen belongs?

Passage:
Sent1: Oxygen is a chemical element with symbol O and atomic number 8.
Sent2: It is a member of the chalcogen group on the periodic table.

Ans: [chalcogen]

Q3: Who was the coach of Sachin Tendulakar?

Passage:
Sent1: Ramakant Vitthal Achrekar was a famous coach.
Sent2: He was most famous for coaching young cricketers at Shivaji Park, most notably Sachin Tendulkar.
Sent3: He had also been a selector for the Mumbai cricket team.

Ans: [Ramakant Vitthal Achrekar, Vasu Paranjape, John Wright]

## Approach

1. Perform **POS tagging** on the question and only extract the nouns and verbs (all tags starting with NN, VB except auxiliary verbs like is, was).

2. Perform **Coreference Resolution on the passage to find the entities that are referred to by the nouns and verbs** in the question.

### Coreference Resolution

```
Coreference Resolution is a task in Natural Language Processing (NLP) that aims to automatically determine the coreference relations between the entities in a text. It is a subtask of Information Extraction that aims to find the mentions of the entities in a text and the coreference relations between them. It is a challenging task in NLP because of the ambiguity of the language and the need to generalize to new questions.
```

3. Perform **adequate normalization on the question and the passage such that words match** even if they differ in case, tense, singular/plural etc.

4. Find the sentences in the passage that contain the **maximum overlap with the nouns and verbs extracted** from the question.

5. **Extract the noun phrases** (combinations of consecutive nouns, adjectives and determiners) from the matched sentences excluding the words present in the question.

### These noun phrases are the possible answers to the question.

6. If multiple sentences happen to have the same overlap and that is the maximum, extract potential answers from all these sentences.

## Evaluation

Evaluation is done by comparing the predicted answers with the ground truth answers.

**Precision** - The percentage of predicted answers that are correct.

**Recall** - The percentage of ground truth answers that are predicted correctly.

**F1 Score** - The harmonic mean of precision and recall.

## Results

### We will return the scores for each of the questions in the dataset.

### Q1

![image](https://user-images.githubusercontent.com/63910248/207375008-d58250ec-a730-4202-9986-cf721db620e2.png)


### Q2

![image](https://user-images.githubusercontent.com/63910248/207375058-42c0447d-9a31-4d9c-9b6f-4aee3232c823.png)


### Q3

![image](https://user-images.githubusercontent.com/63910248/207375096-976e7fab-7d7e-4e0e-959d-3af4e69cd59b.png)

