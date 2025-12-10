# 07. Transformers (2017+)

## Overview

The Transformer architecture, introduced in "Attention Is All You Need" (Vaswani et al., 2017), revolutionized NLP by relying entirely on attention mechanisms, eliminating recurrence and enabling parallel training at unprecedented scale.

## Historical Context

- **Era**: 2017-present
- **Key Motivation**: Overcome sequential bottleneck of RNNs while maintaining long-range dependencies
- **Seminal Paper**: "Attention Is All You Need" (Vaswani et al., 2017)

## Core Concepts

### 1. Self-Attention as Primary Operation
Replace recurrence with self-attention:
- Each position attends to all other positions
- Parallel computation across sequence
- Direct connections between all elements

### 2. Positional Encoding
Since there's no recurrence, inject position information:
- Sinusoidal functions
- Learned positional embeddings
- Relative position representations

### 3. Encoder-Decoder Architecture
- **Encoder**: Process input sequence into representations
- **Decoder**: Generate output sequence autoregressively
- **Cross-Attention**: Decoder attends to encoder outputs

## Architecture Components

### Multi-Head Self-Attention

**Scaled Dot-Product Attention**:
```
Attention(Q, K, V) = softmax(QK^T / √d_k) V
```

**Multi-Head**:
```
MultiHead(Q, K, V) = Concat(head_1, ..., head_h) W^O
where head_i = Attention(QW_i^Q, KW_i^K, VW_i^V)
```

**Benefits**:
- Multiple representation subspaces
- Attend to different positions and relationships
- h=8 heads typical in practice

### Position-wise Feed-Forward Networks

Applied to each position independently:
```
FFN(x) = max(0, xW_1 + b_1)W_2 + b_2
```

**Properties**:
- Two linear transformations with ReLU
- Same across positions, different across layers
- Typically expand then compress dimensionality

### Positional Encoding

**Sinusoidal (Original)**:
```
PE(pos, 2i) = sin(pos / 10000^(2i/d_model))
PE(pos, 2i+1) = cos(pos / 10000^(2i/d_model))
```

**Properties**:
- Deterministic
- Can extrapolate to longer sequences
- Encodes relative positions

**Alternatives**:
- Learned positional embeddings
- Relative positional encodings
- Rotary position embeddings (RoPE)

### Residual Connections and Layer Normalization

Each sub-layer has:
```
output = LayerNorm(x + Sublayer(x))
```

**Benefits**:
- Facilitate gradient flow
- Stabilize training
- Enable deeper networks

### Masking

**Padding Mask**: Ignore padding tokens

**Causal Mask**: Prevent attending to future tokens in decoder
- Essential for autoregressive generation
- Maintains left-to-right dependencies

## Encoder Architecture

Stack of N identical layers (N=6 in original):

**Each layer contains**:
1. Multi-head self-attention
2. Feed-forward network
3. Residual connections and layer norm around each

**Computation Flow**:
```
x = LayerNorm(x + MultiHeadAttention(x, x, x))
x = LayerNorm(x + FFN(x))
```

## Decoder Architecture

Stack of N identical layers:

**Each layer contains**:
1. Masked multi-head self-attention (causal)
2. Multi-head cross-attention (to encoder)
3. Feed-forward network
4. Residual connections and layer norm

**Computation Flow**:
```
x = LayerNorm(x + MaskedMultiHeadAttention(x, x, x))
x = LayerNorm(x + CrossAttention(x, encoder_output, encoder_output))
x = LayerNorm(x + FFN(x))
```

## Key Innovations

### 1. Parallelization
- All positions processed simultaneously
- No sequential dependencies in forward pass
- Dramatically faster training than RNNs

### 2. Constant Path Length
- Any two positions connected directly
- O(1) operations to relate distant elements
- Better gradient flow for long-range dependencies

### 3. Scalability
- Computational complexity clear and manageable
- Efficient on modern hardware (GPUs/TPUs)
- Can scale to very large models

### 4. Flexibility
- Encoder-only (BERT): bidirectional context
- Decoder-only (GPT): autoregressive generation
- Encoder-decoder (T5): sequence-to-sequence

## Computational Complexity

**Self-Attention**: O(n² · d)
- n: sequence length
- d: model dimension

**Feed-Forward**: O(n · d²)

**RNN (for comparison)**: O(n · d²) but sequential

**Trade-off**: Memory for speed and performance

## Training Techniques

### Optimization
- Adam optimizer with β₁=0.9, β₂=0.98
- Learning rate warm-up then decay
- Gradient clipping

### Regularization
- Dropout on attention weights
- Dropout on feed-forward layers
- Label smoothing

### Initialization
- Xavier/Glorot for weights
- Careful initialization crucial for deep models

## Variants and Extensions

### Encoder-Only (BERT-style)
- Bidirectional self-attention
- Masked language modeling
- Best for understanding tasks

### Decoder-Only (GPT-style)
- Causal (masked) self-attention
- Autoregressive language modeling
- Best for generation tasks

### Encoder-Decoder (T5-style)
- Full original architecture
- Sequence-to-sequence tasks
- Translation, summarization

### Efficient Transformers
- Sparse attention patterns
- Linear attention
- Local attention windows
- Reduce O(n²) complexity

## Strengths

1. **Parallelization**: Dramatically faster training
2. **Long-Range Dependencies**: Direct connections between all positions
3. **Scalability**: Can scale to billions of parameters
4. **Flexibility**: Adaptable to many tasks
5. **State-of-the-Art**: Best performance on most benchmarks
6. **Transfer Learning**: Excellent pre-training then fine-tuning

## Limitations

1. **Quadratic Complexity**: O(n²) memory and computation
2. **Fixed Context**: Limited by maximum sequence length
3. **Data Hungry**: Need large datasets for training
4. **Computational Cost**: Expensive to train large models
5. **Interpretability**: Complex attention patterns hard to understand
6. **Positional Encoding**: Various schemes with trade-offs

## Applications

### Machine Translation
- Original Transformer use case
- State-of-the-art translation quality
- Parallel training enables larger models

### Language Modeling
- Foundation for GPT series
- Unsupervised pre-training
- Text generation

### Text Classification
- BERT and variants
- Sentence pair tasks
- Question answering

### Summarization
- Abstractive and extractive
- Long document understanding
- Encoder-decoder models

### Code Generation
- Programming language understanding
- Code completion and synthesis
- Software engineering applications

## Legacy and Influence

Transformers:
- Became the dominant architecture in NLP
- Enabled pre-trained language models at scale
- Inspired applications beyond NLP (vision, speech, multimodal)
- Established new paradigm: pre-training + fine-tuning
- Led to emergence of foundation models

## Key Insight

Transformers demonstrated that **recurrence is not necessary for sequence modeling**, and that **attention alone, combined with parallelization and scale**, can achieve superior results. This enabled the **pre-trained model era**, where massive models trained on enormous corpora could be fine-tuned for specific tasks.

## Transition to Next Era

The Transformer architecture enabled training at unprecedented scale. This led to the development of **large pre-trained models** (BERT, GPT-2, GPT-3) that could be fine-tuned for downstream tasks, establishing the transfer learning paradigm that dominates modern NLP.
