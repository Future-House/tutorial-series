# 1.3 Large Language Models In Biology

Many modern AI models used in biology are sequence-based language models. These models can also be considered foundation models, as they are trained on very large datasets and can be adapted to a wide range of downstream biological tasks.

While language models were originally developed for natural language processing, the same approaches can be applied to biological sequences such as proteins, DNA, and RNA. In this setting, sequences of amino acids or nucleotides are treated similarly to sequences of words in a sentence, allowing models to learn patterns and relationships within biological data.

Recent advances in **model architectures**, **large-scale datasets**, and **computing hardware** have significantly accelerated the application of AI methods in biology and enabled researchers to train large models capable of capturing complex biological signals from sequence data.

--- 

# Transformers: The Architecture Behind Modern LLMs

Most modern natural language models including those in biology—are built using a neural network architecture called the "transformer" [@Vaswani].

Before transformers, many sequence models relied on architectures such as recurrent neural networks (RNNs) [@rumelhart1986learning] that processed sequences one element at a time. While effective, these models struggled to capture long-range relationships within sequences.

:::{note}
The  **attention** mechanism in Transformers address the limitation in capturing long-range relationships.
:::

**Attention** allows the model to examine all positions in a sequence simultaneously and determine which elements are most relevant to one another. For example, in a protein sequence, the model can learn relationships between amino acids that are far apart in the sequence but may interact in the folded structure.

Because transformers process sequences in parallel and capture long-range dependencies effectively, they have become the dominant architecture for modern language models.

```{figure} ../figures/plm_explained_2.png
:alt: plm
:align: center
:figclass: caption-centered

Figure 1.3.1: Attention mechanism in Transformers allow the model to learn relationships between amino acids that are far apart. (Created with gemini-3.1-flash-image-preview)
```

---

# Training Language Models

Language models are typically trained using a strategy known as [self-supervised learning](https://www.ibm.com/think/topics/self-supervised-learning). Training and LLM is less like "teaching a chatbot facts" and more like building a *very large*, *very flexible* pattern-recognizer, then gradually steering it toward helpful behaviors. 

The first two stages of training are known as **pre-training** and **fine-tuning**. For conversational language models, an additional step called **Reinforcement Learning from Human Feedback (RLHF)** is often used. 


```{figure} ../figures/steps_training.png
:alt: training_steps
:align: center
:figclass: caption-centered

Figure 1.3.2: Training an LLM is a multi-step process: pre-training, fine-tuning, and RLHF. These steps allow large language models to first learn general patterns from massive datasets and then become more specialized and aligned with human expectations. (Created with gemini-3.1-flash-image-preview)
```

Together, these stages—pre-training, fine-tuning, and RLHF allow large language models to first learn general patterns from massive datasets and then become more specialized and aligned with human expectations.

## Pre-training

Pre-training is the first stage in training a language model. During this stage, the model is trained on very large collections of sequences. These sequences can be natural language, protein sequences, DNA sequences, or other structured data. For example, if a foundation model is trained only on protein sequences, it is often referred to as a Protein Language Model (PLM). 

Here, the model learns general statistical patterns present in the data. Because pre-training does not require manually labeled data, it is possible to train models on extremely large datasets.

As pre-training is typically performed using self-supervised learning, the model learns by solving "prediction tasks" that are automatically derived from the data itself. These prediction tasks are known as **training objectives**. The objective defines what the model is asked to predict and provides the learning signal used to update the model’s parameters.

Two common training objectives are used in language models.

**1) Next-token prediction**

Here, the model learns to predict the next element in a sequence given the elements that come before it. During training, the model repeatedly observes partial sequences and attempts to predict the next token.

For example if you're working with an amino acid sequence, the model learns to predict the next amino acid.

```
M A D K T L E V K → ?
```

**2) Masked token prediction**

Another common objective is masked token prediction, also known as masked language modeling. In this approach, some tokens in the sequence are randomly hidden, and the model must predict the missing elements using the surrounding context [@devlin2019bertpretrainingof].

Here the model must infer the missing amino acid in the given sequence.
```
M A D [MASK] T L E V K

Correct prediction: K
```

By performing this task across millions or billions of sequences, the model gradually learns patterns in the data. In natural language, this includes grammar and semantic relationships between words. In biological sequences, the model may learn signals related to protein structure, evolutionary constraints, and functional motifs [@gu2021domain]. This objective is commonly used in autoregressive language models, such as GPT-style models.

## Fine-tuning
After pre-training, language models can be adapted to specific tasks through a process known as fine-tuning. During fine-tuning, the pre-trained model is further trained on a smaller, task-specific dataset. Unlike pre-training, these datasets often contain labeled examples, where the correct output for each input is known [@luo2022biogpt;@gu2021domain].

The purpose of this step is to teach the model to specialize in particular applications while retaining the general knowledge it learned during pre-training. For example, a protein language model that has been pre-trained on millions of protein sequences can be fine-tuned to perform tasks such as predicting protein function, identifying structural features, or estimating the effects of mutations.

Because the model already learned general patterns during pre-training, fine-tuning typically requires much less data and compute than training a model from scratch.

## Reinforcement Learning from Human Feedback (RLHF)

For many *conversational AI systems*, an additional training stage called RLHF is used to improve the quality and safety of model responses [@ouyang2022training].

In RLHF, human evaluators review multiple outputs generated by the model and rank them according to criteria such as helpfulness, accuracy, and clarity. These rankings are then used to train a reward model that scores model outputs. The language model is subsequently optimized to produce responses that receive higher reward scores.

This process helps align the model’s behavior with human expectations and improves its ability to generate responses that are useful and safe in real-world applications.

---

# Examples of foundational models in biology

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

# Additional Reading

- [Hugging Face LLM Course](https://huggingface.co/learn/llm-course/chapter0/1):  is a great resource for getting started on LLMs
- [Databricks blog post on LLM pre-training](https://www.databricks.com/blog/llm-pre-training-and-custom-llms)
- [OpenAI blog post on aligning language models](https://openai.com/index/instruction-following/)
- [A Comprehensive Introduction to Fine-Tuning LLMs](https://medium.com/@sahin.samia/a-comprehensive-introduction-to-fine-tuning-llms-4d1bcc95a83a)
- [Andrej Karpathy's Intro to LLMs](https://www.youtube.com/watch?v=zjkBMFhNj_g)
-[A YouTube video explaining the Transformer model](https://www.youtube.com/watch?v=wjZofJX0v4M)
- [Attention mechanism in transformers](https://www.youtube.com/watch?v=eMlx5fFNoYc)

- [IBM blog post on fine-tuning](https://www.ibm.com/think/topics/fine-tuning)

-  [7 AI Terms You Need to Know](https://www.youtube.com/watch?v=VSFuqMh4hus)