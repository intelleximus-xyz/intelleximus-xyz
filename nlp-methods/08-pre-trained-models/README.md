# 08. Pre-trained Models (2018-2020)

## Overview

Pre-trained language models revolutionized NLP by demonstrating that models trained on massive amounts of unlabeled text can learn general language understanding that transfers to diverse downstream tasks with minimal task-specific training.

## Historical Context

- **Era**: 2018-2020
- **Key Motivation**: Leverage vast amounts of unlabeled text through transfer learning
- **Notable Models**: ELMo (2018), BERT (2018), GPT-2 (2019), RoBERTa (2019), T5 (2019)

## Core Concepts

### 1. Transfer Learning Paradigm
- **Pre-training**: Learn general language representations from large unlabeled corpora
- **Fine-tuning**: Adapt to specific tasks with limited labeled data
- Analogous to ImageNet pre-training in computer vision

### 2. Contextual Representations
Unlike static word embeddings, generate different representations based on context:
- "bank" in "river bank" vs. "financial bank"
- Captures polysemy and context-dependent meaning
- Dynamic embeddings for each occurrence

### 3. Self-Supervised Learning
Pre-train on tasks that don't require human labels:
- Masked language modeling
- Next sentence prediction
- Autoregressive language modeling

## Major Pre-trained Models

### ELMo (2018)
**Embeddings from Language Models**

**Architecture**:
- Bidirectional LSTM
- Character-level CNN for input
- Contextual word representations

**Pre-training**:
- Forward and backward language modeling
- Predict next/previous word

**Usage**:
- Freeze ELMo, use as feature extractor
- Concatenate with task-specific models

**Impact**: First major success with contextualized embeddings

### BERT (2018)
**Bidirectional Encoder Representations from Transformers**

**Architecture**:
- Transformer encoder (12 or 24 layers)
- 110M (base) or 340M (large) parameters

**Pre-training Tasks**:
1. **Masked Language Modeling (MLM)**:
   - Randomly mask 15% of tokens
   - Predict masked tokens from bidirectional context
   
2. **Next Sentence Prediction (NSP)**:
   - Predict if sentence B follows sentence A
   - Learn sentence relationships

**Key Innovation**: Bidirectional context through masking

**Fine-tuning**:
- Add task-specific layer
- Fine-tune entire model
- Works for classification, QA, NER, etc.

**Impact**: Set new benchmarks across 11 NLP tasks

### GPT-2 (2019)
**Generative Pre-trained Transformer 2**

**Architecture**:
- Transformer decoder (48 layers for largest)
- 1.5B parameters (largest version)

**Pre-training**:
- Autoregressive language modeling
- Predict next word from left context
- Trained on WebText (40GB)

**Key Innovation**: Zero-shot task performance
- No fine-tuning required
- Task description in prompt
- Demonstrated emergence of capabilities

**Controversy**: Initially not fully released due to concerns about misuse

### RoBERTa (2019)
**Robustly Optimized BERT Approach**

**Improvements over BERT**:
- Train longer with bigger batches
- Remove next sentence prediction
- Use dynamic masking
- More data (160GB vs. 16GB)
- Byte-level BPE tokenization

**Impact**: Showed that training procedure matters as much as architecture

### ALBERT (2019)
**A Lite BERT**

**Key Techniques**:
- Factorized embedding parameterization
- Cross-layer parameter sharing
- Sentence-order prediction (instead of NSP)

**Benefits**: Fewer parameters, faster training, similar performance

### XLNet (2019)

**Key Innovation**: Permutation language modeling
- Overcome BERT's mask artifact
- Autoregressive yet bidirectional
- Generalized autoregressive pre-training

### T5 (2019)
**Text-to-Text Transfer Transformer**

**Unified Framework**:
- All tasks as text-to-text
- Translation: "translate English to German: text"
- Classification: "sentiment: text" → "positive"

**Pre-training**:
- Span corruption (mask spans, predict)
- Trained on C4 (750GB)

**Sizes**: Small to XXL (11B parameters)

**Impact**: Unified framework for understanding and generation

### ELECTRA (2020)

**Key Innovation**: Replaced token detection instead of masked LM
- Generator: small MLM model produces replacements
- Discriminator: detect which tokens are replaced
- More sample-efficient training

## Pre-training Objectives

### Masked Language Modeling (MLM)
```
Input:  "The [MASK] sat on the [MASK]"
Target: "cat", "mat"
```
Learn bidirectional representations

### Causal Language Modeling (CLM)
```
Input:  "The cat sat"
Target: "on"
```
Autoregressive, left-to-right

### Denoising Autoencoding
```
Input:  "The [MASK] [MASK] on the mat"
Target: "The cat sat on the mat"
```
Reconstruct corrupted text

### Contrastive Learning
Learn to distinguish similar from dissimilar examples

## Fine-tuning Strategies

### Full Fine-tuning
- Update all parameters
- Requires computational resources
- Best performance typically

### Feature Extraction
- Freeze pre-trained model
- Train only task-specific layers
- Faster, less prone to overfitting

### Adapter Layers
- Insert small trainable modules
- Keep most parameters frozen
- Parameter-efficient fine-tuning

### Prompt Tuning
- Keep model frozen
- Optimize continuous prompts
- Very parameter-efficient

## Training Considerations

### Data
- Corpus size: billions of tokens
- Quality vs. quantity trade-offs
- Domain relevance
- Data cleaning and filtering

### Compute
- Multiple GPUs/TPUs
- Days to weeks of training
- Significant energy consumption
- Batch sizes in thousands

### Hyperparameters
- Learning rate schedules
- Warmup steps
- Weight decay
- Dropout rates

## Evaluation

### Benchmarks
- **GLUE**: General Language Understanding Evaluation
- **SuperGLUE**: More challenging tasks
- **SQuAD**: Question answering
- **RACE**: Reading comprehension

### Metrics
- Task-specific: accuracy, F1, exact match
- Perplexity for language modeling
- Human evaluation for generation

## Strengths

1. **Transfer Learning**: Leverage unlabeled data at scale
2. **Sample Efficiency**: Excellent performance with limited labeled data
3. **General Representations**: Work across diverse tasks
4. **State-of-the-Art**: Significant improvements on benchmarks
5. **Democratization**: Pre-trained models available publicly
6. **Contextual Understanding**: Handle polysemy and context

## Limitations

1. **Computational Cost**: Expensive to train from scratch
2. **Carbon Footprint**: Significant energy consumption
3. **Data Biases**: Inherit biases from training data
4. **Domain Mismatch**: May not transfer well to specialized domains
5. **Model Size**: Large models difficult to deploy
6. **Fine-tuning Required**: Most still need task-specific adaptation
7. **Interpretability**: Complex and opaque

## Societal Considerations

### Bias and Fairness
- Models reflect training data biases
- Gender, racial, and cultural stereotypes
- Mitigation strategies needed

### Environmental Impact
- Large carbon footprint
- Calls for more efficient methods
- Green AI movement

### Access and Inequality
- Training requires significant resources
- Concentration of power in well-resourced organizations
- Democratization through model sharing

## Legacy and Influence

Pre-trained models:
- Established transfer learning as dominant paradigm
- Made NLP accessible to those without massive compute
- Demonstrated scaling laws
- Inspired similar approaches in other domains
- Led to foundation model concept

## Key Insight

Pre-trained models showed that **language understanding emerges from scale**: large models trained on massive text corpora develop surprisingly general capabilities. However, the trend toward **ever-larger models** raised questions about efficiency, accessibility, and environmental impact, setting the stage for **large language models**.

## Transition to Next Era

The success of pre-trained models like BERT and GPT-2 demonstrated that scaling up—both model size and training data—yields impressive capabilities. This observation led to the development of **large language models** (GPT-3, GPT-4) that push scale to extreme levels, exhibiting emergent abilities like few-shot learning and reasoning.
