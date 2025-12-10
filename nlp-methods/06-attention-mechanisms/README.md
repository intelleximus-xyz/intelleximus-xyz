# 06. Attention Mechanisms (2014-2017)

## Overview

Attention mechanisms revolutionized sequence modeling by allowing neural networks to dynamically focus on relevant parts of the input, overcoming the fixed-length bottleneck of traditional encoder-decoder architectures.

## Historical Context

- **Era**: 2014-2017
- **Key Motivation**: Enable models to selectively focus on relevant information
- **Seminal Paper**: "Neural Machine Translation by Jointly Learning to Align and Translate" (Bahdanau et al., 2014)

## Core Concepts

### 1. Selective Focus
Rather than compressing all information into a fixed-size vector, attention allows the model to:
- Look at different parts of input at different times
- Weight the importance of each input element
- Dynamically determine what's relevant

### 2. Alignment
Learn soft alignments between input and output:
- In translation: which source words relate to each target word
- In reading comprehension: which passage parts answer the question
- In summarization: which sentences to focus on

### 3. Context Vectors
Compute weighted combinations of input representations:
- Weights determined by attention scores
- Different context for each output step
- Adaptive information aggregation

## Attention Mechanisms

### Additive (Bahdanau) Attention (2014)

**Mechanism**:
```
score(h_i, s_j) = v^T tanh(W_1 h_i + W_2 s_j)
attention_weights = softmax(scores)
context = Σ attention_weights_i * h_i
```

**Properties**:
- Uses feedforward network for scoring
- Learns alignment through backpropagation
- First successful attention for NMT

### Multiplicative (Luong) Attention (2015)

**Variants**:
- Dot product: `score(h_i, s_j) = h_i^T s_j`
- General: `score(h_i, s_j) = h_i^T W s_j`
- Concat: similar to additive

**Properties**:
- Simpler computation than additive
- Often faster and more efficient
- Performs similarly on many tasks

### Self-Attention

Attention where input is compared to itself:
- Each position attends to all positions
- Captures dependencies within a sequence
- Foundation for Transformer architecture

**Applications**:
- Sentence encoding
- Document understanding
- Dependency parsing

### Multi-Head Attention

Multiple attention mechanisms in parallel:
- Different heads learn different relationships
- Attend to different positions
- Richer representations

**Benefits**:
- Capture multiple types of dependencies
- More expressive than single attention
- Key component of Transformers

## Attention Computation

### Standard Attention Flow

1. **Score Computation**: Calculate relevance of each input
```
scores_i = score(query, key_i)
```

2. **Normalization**: Convert scores to probabilities
```
attention_weights = softmax(scores)
```

3. **Weighted Sum**: Aggregate values
```
output = Σ attention_weights_i * value_i
```

### Query, Key, Value Framework

- **Query**: what we're looking for
- **Key**: what each input represents
- **Value**: actual information to retrieve

This framework generalizes to various attention types.

## Attention Types

### Soft Attention
- Weighted average over all inputs
- Differentiable
- Can be trained with backpropagation

### Hard Attention
- Select single input element
- Non-differentiable
- Requires reinforcement learning

### Local Attention
- Focus on a window of inputs
- Compromise between global and hard
- More efficient than global

### Global Attention
- Attend to all input positions
- Most common in practice
- Captures long-range dependencies

### Hierarchical Attention
- Attention at multiple levels
- Word-level and sentence-level
- For document classification

## Applications

### Neural Machine Translation
- Align source and target words
- Handle different word orders
- Overcome fixed-length bottleneck
- Dramatic improvement over seq2seq

### Reading Comprehension
- Focus on relevant passage parts
- Match questions to contexts
- Extract answer spans

### Image Captioning
- Attend to image regions while generating words
- Visual question answering
- Multimodal understanding

### Summarization
- Select important sentences/phrases
- Focus on salient content
- Abstractive and extractive

### Speech Recognition
- Align acoustic features to text
- Handle variable-length audio
- Robust to timing variations

## Visualization and Interpretability

### Attention Weights as Explanations
- Visualize what model focuses on
- Understand decision-making process
- Debug model behavior

**Caution**: Attention weights don't always explain predictions reliably

### Alignment Visualization
- Show correspondences between sequences
- Particularly useful in translation
- Reveals model's learned alignments

## Strengths

1. **Long-Range Dependencies**: Can connect distant elements
2. **Dynamic Focus**: Adapt to input content
3. **Interpretability**: Attention weights show focus
4. **Flexibility**: Apply to various architectures
5. **Performance**: Significant improvements on benchmarks
6. **No Fixed Bottleneck**: Information flows directly from input

## Limitations

1. **Computational Cost**: O(n²) for self-attention
2. **Memory**: Store attention weights
3. **Spurious Attention**: May focus on irrelevant parts
4. **Attention ≠ Explanation**: Weights don't always explain predictions
5. **Still Sequential**: In RNN-based models, processing is still sequential

## Key Variants

### Scaled Dot-Product Attention
```
Attention(Q, K, V) = softmax(QK^T / √d_k) V
```
Scaling prevents saturation of softmax

### Cross-Attention
Attention between two different sequences:
- Encoder-decoder attention
- Multimodal fusion

### Causal (Masked) Attention
Prevent attending to future positions:
- Language modeling
- Autoregressive generation

## Legacy and Influence

Attention mechanisms:
- Became fundamental building block of modern NLP
- Enabled the Transformer architecture
- Improved interpretability of neural models
- Demonstrated value of dynamic information routing
- Inspired attention in computer vision and other domains

## Key Insight

Attention showed that **allowing models to dynamically focus on relevant information** is more powerful than forcing everything through a fixed bottleneck. Combined with parallelization, this insight led to the **Transformer architecture**, which would dominate NLP.

## Transition to Next Era

While attention in RNN-based models was powerful, the sequential nature of RNNs limited training speed. The **Transformer** architecture took attention further by removing recurrence entirely, using only attention mechanisms for both encoding and decoding, enabling massively parallel training and better performance.
