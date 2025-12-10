# 05. Word Embeddings (2013-2015)

## Overview

Word embeddings represent a breakthrough in representing language as dense, continuous vectors that capture semantic and syntactic relationships. This approach transformed how machines understand word meaning and relationships.

## Historical Context

- **Era**: 2013-2015 (foundational work)
- **Key Motivation**: Learn distributed representations that capture word meaning
- **Notable Papers**: Word2Vec (Mikolov et al., 2013), GloVe (Pennington et al., 2014)

## Core Concepts

### 1. Distributional Hypothesis
"You shall know a word by the company it keeps" - words appearing in similar contexts have similar meanings.

### 2. Dense Vector Representations
Instead of sparse one-hot vectors (vocabulary size), represent words as dense vectors (typically 100-300 dimensions).

### 3. Semantic Space
Words with similar meanings are close in vector space:
- Vector arithmetic captures relationships
- Analogies: king - man + woman ≈ queen
- Semantic similarity via cosine distance

## Major Approaches

### Word2Vec (2013)

Two architectures for learning word embeddings:

#### Skip-gram
- Input: center word
- Output: predict surrounding context words
- Better for rare words
- More training data required

#### Continuous Bag of Words (CBOW)
- Input: context words
- Output: predict center word
- Faster training
- Better for frequent words

**Training Techniques**:
- Negative sampling: distinguish real context from random words
- Hierarchical softmax: efficient for large vocabularies
- Subsampling of frequent words

**Key Innovation**: Simple, efficient, scalable training on large corpora

### GloVe (2014)

Global Vectors for Word Representation:

**Approach**:
- Construct word co-occurrence matrix from corpus
- Factorize matrix to learn vectors
- Objective: word vectors encode probability ratios

**Key Innovation**: Combines global statistics (matrix factorization) with local context (window-based)

**Advantages**:
- Captures both global corpus statistics and local context
- Efficient training
- Often better performance on word analogy tasks

### FastText (2016)

Extension of Word2Vec with subword information:

**Approach**:
- Represent words as bags of character n-grams
- Word vector = sum of its n-gram vectors
- Learn vectors for n-grams, not just words

**Advantages**:
- Handle out-of-vocabulary words
- Better for morphologically rich languages
- Capture internal word structure
- Robust to spelling variations

**Example**: "reading" = <re + rea + ead + adi + din + ing + ng>

## Mathematical Foundations

### Skip-gram Objective
Maximize the log probability of context words:
```
max Σ Σ log P(w_context | w_center)
```

### GloVe Objective
Minimize weighted least squares:
```
min Σ f(X_ij) (w_i^T w_j + b_i + b_j - log X_ij)²
```
where X_ij is co-occurrence count

### Cosine Similarity
Measure semantic similarity:
```
similarity(w1, w2) = (w1 · w2) / (||w1|| ||w2||)
```

## Properties of Word Embeddings

### Semantic Relationships
- Synonyms are close: "happy" ≈ "joyful"
- Antonyms have consistent relationships
- Hierarchies: "animal" → "dog" → "terrier"

### Syntactic Relationships
- POS patterns: adjective ↔ adverb ("quick" ↔ "quickly")
- Verb tenses: "walking" ↔ "walked"
- Singular/plural: "car" ↔ "cars"

### Analogical Reasoning
Vector arithmetic captures analogies:
- King - Man + Woman ≈ Queen
- Paris - France + Germany ≈ Berlin
- Walking - Walk + Swim ≈ Swimming

### Compositionality
Combine word vectors for phrases:
- Simple addition or averaging
- More sophisticated: neural composition

## Strengths

1. **Semantic Capture**: Encode meaning in continuous space
2. **Unsupervised Learning**: Learn from raw text without labels
3. **Transfer Learning**: Use across different tasks
4. **Computational Efficiency**: Fast inference
5. **Dimensionality Reduction**: Compact representation
6. **Analogical Reasoning**: Capture relationships through arithmetic

## Limitations

1. **Polysemy**: Single vector per word, can't handle multiple meanings
2. **Context Independence**: Static representations regardless of context
3. **Rare Words**: Poor representations for infrequent words
4. **Bias**: Capture societal biases from training data
5. **Evaluation**: Quality assessment is task-dependent
6. **Compositionality**: Simple addition doesn't capture complex phrases

## Applications

### Downstream Tasks
Word embeddings as input features for:
- Text classification
- Named entity recognition
- Machine translation
- Sentiment analysis

### Semantic Similarity
- Document similarity
- Information retrieval
- Question answering

### Recommendation Systems
- Content-based recommendations
- Similar item discovery

### Linguistic Analysis
- Studying semantic change over time
- Cross-lingual comparisons
- Bias detection

## Training Considerations

### Corpus Selection
- Size: larger corpora generally better
- Domain: affects learned representations
- Cleaning: preprocessing impacts quality

### Hyperparameters
- Vector dimension (typically 100-300)
- Context window size
- Learning rate
- Negative samples
- Training epochs

### Evaluation
- Intrinsic: word similarity, analogies
- Extrinsic: performance on downstream tasks

## Legacy and Influence

Word embeddings:
- Became standard input representation for neural NLP
- Demonstrated unsupervised pre-training value
- Inspired contextual embeddings (ELMo, BERT)
- Enabled transfer learning in NLP
- Made semantic reasoning computationally tractable

## Key Insight

Word embeddings showed that **semantic meaning can be captured as geometry in vector space**, and that **unsupervised learning from raw text is powerful**. However, **static representations can't handle polysemy and context**, motivating the development of **contextual representations** and **attention mechanisms**.

## Transition to Next Era

While word embeddings were revolutionary, their static nature (one vector per word regardless of context) was limiting. The next evolution combined embeddings with **attention mechanisms** that could dynamically focus on relevant context, leading to context-aware representations.
