# 03. Machine Learning (1990s-2000s)

## Overview

Machine learning methods brought more sophisticated algorithms to NLP, enabling systems to learn complex patterns from data through feature-based representations and discriminative training.

## Historical Context

- **Era**: 1990s-2000s
- **Key Motivation**: Learn more complex patterns and decision boundaries than simple statistical models
- **Notable Developments**: Support Vector Machines, Decision Trees, Conditional Random Fields

## Core Concepts

### 1. Feature Representation
Transform text into numerical feature vectors:
- Bag of words
- TF-IDF weights
- Linguistic features (POS tags, dependencies)
- N-gram features
- Context windows

### 2. Discriminative Training
Learn to directly distinguish between classes:
- Optimize decision boundaries
- Focus on classification accuracy
- Use labeled training data

### 3. Structured Prediction
Predict structured outputs (sequences, trees):
- Consider dependencies between output elements
- Learn joint models of input-output pairs

## Key Algorithms

### Support Vector Machines (SVMs)
Maximum margin classifiers that find optimal separating hyperplanes:
- Text classification
- Sentiment analysis
- Named entity recognition

**Key Concepts**:
- Kernel methods (linear, polynomial, RBF)
- Maximum margin principle
- Support vectors

### Decision Trees and Random Forests
Tree-based models that partition feature space:
- Feature importance analysis
- Non-linear decision boundaries
- Ensemble methods

**Advantages**:
- Interpretable rules
- Handle non-linear relationships
- Robust to irrelevant features

### Conditional Random Fields (CRFs)
Discriminative models for sequence labeling:
- Named entity recognition
- POS tagging
- Segmentation tasks

**Key Properties**:
- Model conditional probability P(labels|text)
- Capture label dependencies
- Feature-rich representations

### Maximum Entropy Models
Log-linear models that combine features:
- Text classification
- Sequence labeling
- Feature weighting

### Logistic Regression
Probabilistic linear classifiers:
- Binary and multi-class classification
- Interpretable coefficients
- Probability estimates

### K-Nearest Neighbors (KNN)
Instance-based learning:
- No explicit training phase
- Classification by similarity
- Memory-based approaches

## Feature Engineering

Critical aspect of machine learning NLP:

### Lexical Features
- Words and n-grams
- Character n-grams
- Word shapes and patterns

### Syntactic Features
- Part-of-speech tags
- Parse tree structures
- Dependency relations

### Semantic Features
- Word lists and dictionaries
- Semantic classes
- Distributional similarity

### Contextual Features
- Surrounding words
- Document-level features
- Discourse features

## Strengths

1. **Powerful Decision Boundaries**: Model complex non-linear patterns
2. **Feature Combinations**: Automatically learn feature interactions
3. **Generalization**: Better generalization than simple statistical methods
4. **Structured Outputs**: Handle sequence and tree structures
5. **Theoretical Foundations**: Strong mathematical and statistical theory
6. **Versatility**: Applicable to many NLP tasks

## Limitations

1. **Feature Engineering Burden**: Requires extensive manual feature design
2. **Domain Dependence**: Features often task and domain-specific
3. **Limited Context**: Fixed-size context windows
4. **Sparse Representations**: Bag-of-words loses word order and meaning
5. **Scalability**: Some algorithms don't scale well to large datasets
6. **No Representation Learning**: Cannot learn features automatically

## Applications

### Text Classification
- Sentiment analysis
- Topic categorization
- Spam detection

### Information Extraction
- Named entity recognition
- Relation extraction
- Event extraction

### Sequence Labeling
- POS tagging
- Chunking
- Semantic role labeling

### Parsing
- Dependency parsing
- Constituency parsing

## Important Concepts

### The Kernel Trick
Map data to higher-dimensional spaces where it becomes linearly separable, without explicitly computing the transformation.

### Ensemble Methods
Combine multiple models for better performance:
- Bagging
- Boosting
- Model averaging

### Regularization
Prevent overfitting through:
- L1 regularization (Lasso)
- L2 regularization (Ridge)
- Early stopping

## Legacy and Influence

Machine learning methods:
- Achieved state-of-the-art results on many benchmarks
- Established the importance of learning algorithms
- Highlighted the feature engineering bottleneck
- Demonstrated the value of discriminative training
- Created standard evaluation frameworks

## Key Insight

Machine learning showed that **sophisticated algorithms can learn complex patterns**, but also revealed that **manual feature engineering is a bottleneck**. The features still encode human knowledge, limiting what can be learned. This motivated the development of **deep learning** approaches that could learn features automatically.

## Transition to Next Era

The success of machine learning in NLP was limited by the quality of hand-crafted features. The promise of **deep learning** was to automatically learn hierarchical feature representations directly from raw text, eliminating the feature engineering bottleneck.
