# 04. Deep Learning (2010s)

## Overview

Deep learning revolutionized NLP by introducing neural networks that could automatically learn hierarchical representations from raw text, eliminating the need for manual feature engineering.

## Historical Context

- **Era**: 2010s
- **Key Motivation**: Learn features automatically through multiple layers of abstraction
- **Notable Milestones**: Word2Vec (2013), Neural Machine Translation (2014), LSTM networks

## Core Concepts

### 1. Representation Learning
Neural networks learn to represent words, phrases, and sentences as dense vectors:
- Embeddings capture semantic and syntactic properties
- Hierarchical representations at multiple levels
- End-to-end learning from raw text to task

### 2. Neural Network Architecture
Multiple layers of interconnected neurons:
- Input layer: raw text or embeddings
- Hidden layers: learned representations
- Output layer: task-specific predictions

### 3. Backpropagation
Gradient-based optimization:
- Compute gradients through the network
- Update weights to minimize loss
- Learn from errors

## Key Architectures

### Feedforward Neural Networks
Simple multi-layer networks:
- Fully connected layers
- Non-linear activations (ReLU, tanh, sigmoid)
- Applied to fixed-size inputs

**Applications**: Text classification, language modeling

### Recurrent Neural Networks (RNNs)
Process sequences with hidden state:
- Maintain memory of previous inputs
- Share parameters across time steps
- Handle variable-length sequences

**Challenges**: Vanishing/exploding gradients, limited long-term memory

### Long Short-Term Memory (LSTM)
Advanced RNN with gating mechanisms:
- Cell state for long-term memory
- Input, output, and forget gates
- Better at capturing long-range dependencies

**Applications**: Language modeling, machine translation, text generation

### Gated Recurrent Units (GRU)
Simplified version of LSTM:
- Update and reset gates
- Fewer parameters than LSTM
- Often similar performance

### Bidirectional RNNs
Process sequences in both directions:
- Forward and backward passes
- Access to full context
- Better for tasks requiring full sentence understanding

### Convolutional Neural Networks (CNNs)
Apply convolutions to text:
- Capture local patterns (n-grams)
- Parallel processing
- Efficient feature extraction

**Applications**: Text classification, sentence modeling

### Encoder-Decoder Architecture
Two networks for sequence-to-sequence tasks:
- Encoder: compress input to fixed representation
- Decoder: generate output from representation

**Applications**: Machine translation, summarization, question answering

## Training Techniques

### Optimization Algorithms
- Stochastic Gradient Descent (SGD)
- Adam: adaptive learning rates
- RMSprop, AdaGrad

### Regularization
- Dropout: randomly disable neurons
- L2 regularization (weight decay)
- Early stopping
- Batch normalization

### Initialization
- Xavier/Glorot initialization
- He initialization
- Pre-trained embeddings

### Learning Rate Scheduling
- Step decay
- Exponential decay
- Cosine annealing

## Word Embeddings

Dense vector representations of words:

### Word2Vec (2013)
- Skip-gram: predict context from word
- CBOW: predict word from context
- Learn semantic relationships

### GloVe (2014)
- Global vectors for word representation
- Matrix factorization on co-occurrence statistics
- Combines global statistics with local context

### FastText (2016)
- Subword embeddings
- Handle out-of-vocabulary words
- Better for morphologically rich languages

## Strengths

1. **Automatic Feature Learning**: No manual feature engineering
2. **Hierarchical Representations**: Learn multiple levels of abstraction
3. **End-to-End Training**: Optimize for task directly
4. **Transfer Learning**: Pre-trained embeddings transfer across tasks
5. **State-of-the-art Performance**: Superior results on benchmarks
6. **Semantic Representations**: Capture meaning in vector space

## Limitations

1. **Data Hungry**: Require large amounts of labeled data
2. **Computational Cost**: Training is computationally expensive
3. **Black Box**: Difficult to interpret decisions
4. **Hyperparameter Sensitivity**: Many parameters to tune
5. **Sequential Bottleneck**: RNNs process sequences slowly
6. **Fixed Context**: Limited by encoder capacity
7. **Local Optima**: Non-convex optimization

## Applications

### Neural Machine Translation
- Sequence-to-sequence models
- Attention mechanisms
- Significant improvement over phrase-based systems

### Language Modeling
- Predict next word in sequence
- Foundation for many NLP tasks
- Capture syntax and semantics

### Text Classification
- Sentiment analysis
- Document categorization
- Intent detection

### Named Entity Recognition
- Bidirectional LSTM-CRF
- Character-level models
- No hand-crafted features

### Question Answering
- Reading comprehension
- Memory networks
- Neural reasoning

## Legacy and Influence

Deep learning:
- Eliminated feature engineering bottleneck
- Unified many NLP tasks under similar architectures
- Demonstrated the power of representation learning
- Established neural networks as dominant paradigm
- Enabled transfer learning through embeddings

## Key Insight

Deep learning proved that **neural networks can learn effective representations automatically**, but also revealed limitations: RNNs struggle with long sequences, and **fixed-size representations can't capture all context**. This motivated the development of **attention mechanisms** that could dynamically focus on relevant parts of the input.

## Transition to Next Era

While deep learning achieved impressive results, the sequential nature of RNNs and the bottleneck of fixed-size representations limited performance. **Word embeddings** emerged as a foundational component, and **attention mechanisms** provided a way to access relevant information dynamically, paving the way for the transformer revolution.
