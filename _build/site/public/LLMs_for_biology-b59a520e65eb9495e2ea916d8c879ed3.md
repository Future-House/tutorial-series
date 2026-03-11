# 1.3 Large Language Models In Biology

Most modern AI models used in biology are sequence-based language models. These models can also be considered foundation models because they are trained on very large datasets and can be adapted to many downstream biological tasks.

Instead of processing natural language, these models are trained on biological sequences such as proteins, DNA, or RNA. By learning statistical patterns within these sequences, they can capture information about structure, function, and evolutionary relationships.

The table below provides a comparative overview of several major foundation models used in biological research.

```{table} Table 1.3.1: Example of foundation models in biology
| Model Name | Type | Architecture | Key Application | Scale / Data |
| :--- | :--- | :--- | :--- | :--- |
| **ESM-2** | Protein | Transformer Encoder (BERT-style) | Structure prediction, variant effect prediction, representation learning | Up to 15B parameters; trained on ~65M UniRef sequences (pqac-00000032, pqac-00000034, pqac-00000039) |
| **ESMFold** | Protein | ESM-2 + Folding Trunk | Atomic-level protein structure prediction from single sequence (no MSA) | 3B to 15B parameters; trained on PDB + 12M AlphaFold predictions (pqac-00000033, pqac-00000036) |
| **AlphaFold2** | Protein | Evoformer + Structure Module | High-accuracy structure prediction using Multiple Sequence Alignments (MSAs) | Trained on PDB; utilizes large MSA databases (BFD, MGnify) (pqac-00000031, pqac-00000036) |
| **DNABERT / DNABERT-2** | Genomic | Transformer Encoder | Promoter identification, splice site prediction, transcription factor binding | Human genome; DNABERT-2 uses BPE tokenization and multi-species data (pqac-00000024, pqac-00000029) |
| **Enformer** | Genomic | Transformer with long-range attention  | Predicting gene expression from sequence, enhancer-promoter interactions | Long context window (100kb); trained on human/mouse genome data (pqac-00000026, pqac-00000029) |
| **HyenaDNA** | Genomic | Hyena hierarchy (Long Convolution) | Modeling long-range genomic patterns, variant classification | Up to 1M token context window; trained on human reference genome (pqac-00000026, pqac-00000029) |
| **scGPT** | Single-Cell | Generative Transformer | Cell type annotation, perturbation prediction, batch correction | Trained on >10M single-cell profiles (pqac-00000024, pqac-00000026) |
| **Geneformer** | Single-Cell | Transformer | Dosage sensitivity, chromatin dynamics, gene network modeling | Trained on ~30M single-cell transcriptomes (pqac-00000026) |
| **ProtGPT2** | Protein | Transformer Decoder (GPT-style) | De novo protein sequence generation | Trained on UniRef50; 738M parameters (pqac-00000027, pqac-00000029) |
| **ProGen** | Protein | Transformer Decoder (Conditional) | Controllable protein sequence generation | Trained on ~280M protein sequences with taxonomic/functional tags (pqac-00000026) |
| **ProteinBERT** | Protein | Transformer Encoder (BERT-style) | Protein function prediction, GO term classification | Trained on UniRef90 + Gene Ontology annotations (pqac-00000024, pqac-00000029) |
```

--- 

# Transformers: The Architecture Behind Modern LLMs

Most modern natural language models including those in biology—are built using a neural network architecture called the "transformer" [@Vaswani].

Before transformers, many sequence models relied on architectures such as recurrent neural networks (RNNs) [@rumelhart1986learning] that processed sequences one element at a time. While effective, these models struggled to capture long-range relationships within sequences.

:::{note}
Transformers address the limitation to capture long-range relationship using a mechanism called **attention**.
:::

**Attention** allows the model to examine all positions in a sequence simultaneously and determine which elements are most relevant to one another. For example, in a protein sequence, the model can learn relationships between amino acids that are far apart in the sequence but may interact in the folded structure.

Because transformers process sequences in parallel and capture long-range dependencies effectively, they have become the dominant architecture for modern language models.

```{figure} ../figures/plm_explained_2.png
:alt: plm
:align: center
:figclass: caption-centered

Figure 1.3.1: Attention mechanism in Transformers allow the model to learn relationships between amino acids that are far apart. (Created with gpt-image-1.5-2025-12-16)
```

# Training Language Models

Language models are typically trained using a strategy known as **self-supervised** learning.

In this setup, the model learns from large amounts of unlabeled data by solving tasks that are automatically generated from the data itself.

Two common training objectives are:

**1) Next-token prediction**

The model learns to predict the next element in a sequence given the preceding elements.

```
For example:

M A D K T L E _
```

The model predicts the most likely next amino acid.

This is the training strategy used by models such as GPT-style language models.

**2) Masked token prediction**

Another common training approach is masked language modeling, where parts of a sequence are hidden and the model must predict the missing elements.

Example:

M A D [MASK] T L E

The model learns to predict the masked amino acid.

This approach is commonly used in protein language models such as ESM.

What Do These Models Learn?

By training on millions or billions of sequences, language models learn rich representations of biological sequences.

Remarkably, these models often learn biological properties that were never explicitly provided during training. For example, researchers have found that protein language models can capture signals related to:

protein structure

evolutionary relationships

functional domains

mutational effects

These learned representations can then be used for many downstream biological tasks.

From Pretraining to Biological Applications

Once trained, foundation models can be adapted to specific tasks using a process called fine-tuning.

Examples of downstream applications include:

predicting protein structure

estimating mutation effects

identifying functional motifs

annotating genes

designing novel proteins

Because the model has already learned general patterns from massive sequence datasets, fine-tuning often requires far less labeled data than training a model from scratch.