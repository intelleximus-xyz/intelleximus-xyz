# 02. Statistical Methods (1980s-1990s)

## Overview

Statistical methods marked a paradigm shift in NLP, moving from hand-crafted rules to learning patterns from data. These approaches use probability theory and statistical inference to model language phenomena.

## Historical Context

- **Era**: 1980s-1990s
- **Key Motivation**: Handle language variability and ambiguity through probabilistic modeling
- **Notable Milestones**: Hidden Markov Models, IBM translation models, Penn Treebank

## Core Concepts

### 1. Probabilistic Models
Language is modeled as a probabilistic process. Instead of deterministic rules, systems calculate the probability of linguistic events:
- P(word | context)
- P(tag | word)
- P(translation | source)

### 2. Learning from Data
Models are trained on large corpora to estimate probabilities:
- Frequency counts from annotated data
- Maximum likelihood estimation
- Smoothing techniques for unseen events

### 3. Statistical Inference
Decision-making based on probability calculations:
- Choose the most likely interpretation
- Handle ambiguity through probability distributions
- Trade-off between different hypotheses

## Key Methods

### N-gram Language Models
Model the probability of a word given the previous n-1 words:
- Unigram: P(word)
- Bigram: P(word | previous_word)
- Trigram: P(word | previous_two_words)

**Applications**: Speech recognition, machine translation, text generation

### Hidden Markov Models (HMMs)
Sequential probabilistic models with hidden states:
- Part-of-speech tagging
- Named entity recognition
- Speech recognition

**Key Algorithms**: Forward-backward algorithm, Viterbi algorithm

### Probabilistic Context-Free Grammars (PCFGs)
Grammars with probabilities assigned to production rules:
- Syntactic parsing
- Learning grammar from treebanks
- Handling structural ambiguity

### Naive Bayes Classifiers
Simple probabilistic classifiers using Bayes' theorem:
- Text classification
- Sentiment analysis
- Spam filtering

### Maximum Entropy Models
Models that make minimal assumptions beyond observed constraints:
- Sequence labeling
- Feature-rich classification
- Conditional probability modeling

## Strengths

1. **Robustness**: Handle noisy and variable input
2. **Data-Driven**: Learn patterns automatically from examples
3. **Ambiguity Resolution**: Naturally handle multiple interpretations
4. **Quantifiable Uncertainty**: Provide probability distributions
5. **Scalability**: Can process large volumes of text
6. **Graceful Degradation**: Performance degrades smoothly with difficult inputs

## Limitations

1. **Data Requirements**: Need large annotated corpora
2. **Independence Assumptions**: Often assume features are independent (which they're not)
3. **Context Limitations**: N-grams have limited context windows
4. **Feature Engineering**: Still require manual design of features
5. **Sparse Data Problem**: Many possible events never observed in training
6. **Linear Relationships**: Cannot model complex non-linear patterns well

## Mathematical Foundations

### Bayes' Theorem
```
P(A|B) = P(B|A) × P(A) / P(B)
```
Foundation for probabilistic inference in NLP.

### Maximum Likelihood Estimation
Choose parameters that maximize the probability of observed data.

### Smoothing Techniques
- Laplace smoothing
- Good-Turing estimation
- Kneser-Ney smoothing

Handle zero probabilities for unseen events.

## Applications

- **Machine Translation**: IBM Models 1-5
- **Speech Recognition**: HMM-based systems
- **Information Retrieval**: TF-IDF, BM25
- **Text Classification**: Naive Bayes classifiers
- **POS Tagging**: HMM taggers
- **Parsing**: Probabilistic parsers

## Legacy and Influence

Statistical methods:
- Demonstrated the power of learning from data
- Established evaluation methodologies and benchmarks
- Introduced the concept of separating model from data
- Showed that linguistic expertise could be complemented by statistics
- Laid groundwork for machine learning approaches

## Key Insight

Statistical methods revealed that **language patterns can be learned from data**, but also that **simple statistical models have limitations** in capturing the full complexity of language, especially long-range dependencies and semantic relationships.

## Transition to Next Era

While statistical methods succeeded in many tasks, their reliance on hand-crafted features and limited context modeling motivated the development of **machine learning** approaches that could automatically learn feature representations and handle more complex patterns.
