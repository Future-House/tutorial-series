# 1.1 Why AI?

***This page provides  background literature on AI. You may skip to Chapter 2 or Chapter 3 to see more hands-on applications.***

From genome sequencing to single-cell transcriptomics to high-content imaging and protein structure prediction, modern biology generates data at a scale and complexity that exceeds traditional analytical approaches. Artificial intelligence (AI)has emerged as a powerful set of tools for extracting patterns, generating hypotheses, and accelerating discovery from biological data. 

While AI can feel like black magic it is only a collection of statistical principles, mathematical models, and computational tools. These must be understood, applied and evaluated carefully, especially in high-stakes scientific contexts.

We’ll begin with the history and basic ideas behind AI—how the field started, how it evolved, and the key concepts that shape modern systems today. Understanding this background helps demystify AI and gives us the tools to think critically about how these systems work.

From there, we’ll shift toward practical applications of modern AI in biology, focusing on large language models (LLMs) and AI agents. We’ll explore how these tools can be used in everyday scientific workflows, with a particular focus on biological research. The goal is to move beyond the buzz words and understand how AI can actually help scientists ask better questions, analyze data more efficiently, and accelerate discovery.

# 1.1.1 History of AI

```{figure} ../figures/history_timeline.png
:alt: Evolution of AI
:align: center
:figclass: caption-centered

Figure 1.1.1: Evolution of AI (Created with gemini-3-flash-preview)
```

**1950s - Can Machines Think?:** AI didn’t start with code; it started with a question. In the 1950s, scientists began to ask if machines could think. Alan Turing famously reframed the question into something more practical: instead of debating what “thinking” is, could a machine behave intelligently enough to be indistinguishable from a human? In the summer of 1956, a small group of researchers gathered at Dartmouth College for what would later be called the birth of Artificial Intelligence. John McCarthy coined the term "Artificial Intelligence" and proposed what he described as a "2-month, 10-man study" [@mccarthy1955dartmouthworkshop]. The proposal was ambitious. It suggested that key aspects of intelligence, including learning, might be described so precisely that a machine could simulate them. The topics they outlined sound surprisingly modern: natural language processing, neural networks, abstraction, creativity, and the theory of computation.


**1960s - From Big Dreams to Expert Knowledge:** As the field matured, researchers realized that general intelligence was harder than it looked. By the late 1960s, the focus shifted. Instead of trying to build machines that could reason about everything, scientists started building systems that reasoned about very specific domains — chemistry, medicine, mathematics. The key insight was practical: AI systems worked much better when they were packed with expert knowledge. This gave rise to "expert systems"; programs such as MACSYMA: for symbolic mathematics, DENDRAL: for chemical structure inference and MYCIN: for clinical decision support [@shortliffe1986medicalexpertsystems]. These systems didn’t "learn" in the modern sense. They encoded human expertise directly. And in scientific domains that approach worked surprisingly well. But it also revealed a bottleneck: extracting and formalizing expert knowledge was incredibly difficult. Building intelligence by hand was slow and brittle.

**1990s - Let the Data Speak:** By the 1990s, a new perspective gained momentum. Instead of hand-coding intelligence, maybe we could learn it from data. Statistical learning theory (SLT) provided a mathematical framework for understanding when learning from examples would generalize beyond the training data [@vapnik1999anoverviewof]. This wasn’t just philosophical, it addressed a deep scientific question: When can we trust a model trained on finite data?
Support Vector Machines (SVMs) emerged as one of the first widely used algorithms built directly from this theory. They showed that you could combine mathematical guarantees with practical performance. This era marked a shift from rule-based systems to data-driven learning. Instead of encoding expertise directly, we began building systems that could extract structure from data themselves. It was this shift that laid the groundwork for modern machine learning (ML) and eventually, the deep learning (DL) systems transforming biology today. 

**2010s - The Deep Learning Comeback:** For a while, neural networks were out of fashion. They had been explored since the 1980s, but training large networks was difficult, datasets were small, and computers were slow. Many researchers shifted toward other approaches. Then three things changed at once: 1) We had massive datasets, 2) We had powerful GPUs, and 3) We had a few key algorithmic improvements. DL reframed AI problems as representation learning. Instead of hand-designing features, multilayer neural networks could learn hierarchical features directly from raw data — pixels, audio signals, sequences. The moment that made everyone pay attention came in 2012. A team led by Alex Krizhevsky trained a large deep convolutional neural network on the ImageNet dataset — about 1.2 million images across 1000 categories [@krizhevsky2012imagenetclassificationwith]. Their model dramatically outperformed competitors in the ImageNet Large Scale Visual Recognition Challenge (ILSVRC). The top-5 error rate dropped from 26.2% (runner-up) to 15.3%. That wasn’t a small improvement. It was a shock. The system — later known as AlexNet — relied on GPU training, rectified linear units (ReLUs), architectural depth, and dropout regularization. But more importantly, it showed that deep neural networks could scale — and that performance improved as data and compute increased [@lecun2015deeplearning]. The lesson of the 2010s was clear: scale matters. With enough data and compute, neural networks could learn powerful representations directly from raw inputs.

**2020s - Generative AI and Foundation Models:** If the 2010s were about learning powerful representations, the 2020s became about learning general-purpose models. The key technical breakthrough that made this possible was the transformer architecture, introduced in 2017 [@Vaswani]. Unlike earlier sequence models such as RNNs [@rumelhart1986learning], LSTMs [@hochreiter1997long], transformers relied on a mechanism called attention, which allowed models to weigh relationships between all parts of an input at once. This made them dramatically better at modeling long-range dependencies in language, code, and even biological sequences. Just as importantly, transformers scaled extremely well. As researchers increased model size, dataset size, and compute, performance improved in a surprisingly smooth and predictable way. This "scaling behavior" made it feasible to train very large models on massive datasets. Instead of training a separate model for each problem, researchers began pretraining large transformer models on vast corpora (text from the internet, millions of protein sequences, genomic data) and then adapting them to specific tasks through fine-tuning or prompting. These became known as foundation models. In natural language, this led to large language models capable of reasoning, summarizing, coding, and assisting with scientific writing.

# 1.1.2 AI in Science: From Data Overload to Discovery

Modern biology (and science in general) is overflowing with data. We can sequence genomes at scale. We can measure gene expression in millions of single cells. We can generate high-content imaging datasets that capture cellular morphology in extraordinary detail. But there’s a catch: biological data is messy, high-dimensional, and often incomplete [@ruffolo2024designing;@ovchinnikov2017protein].

Many assays are destructive. Some measurements can’t be taken on the same cell. Others can’t be measured simultaneously at all [@bialek2005physical;@ten2016fundamental]. Time-series experiments are expensive. Perturbations are constrained. In practice, we observe fragments of a much larger biological system [@uhler2022machinelearningapproaches].
So the challenge isn’t just generating data anymore, it’s stitching it together.

This is where AI has become essential. Machine learning methods like representation learning, generative modeling, and optimal transport allow us to integrate different data modalities, align measurements across conditions, and build models that infer what we cannot directly measure.  In this sense, AI isn’t just analyzing biology, it’s filling in the missing pieces. 

```{figure} ../figures/41586_2021_3819_Fig1_HTML.webp
:alt: AlphaFold
:align: center
:figclass: caption-centered

Figure 2: The performance of AlphaFold on the CASP14 dataset [Copied from Jumper et al., 2021]
```

AlphaFold is one example that demonstrates the impact of AI in biology [@jumper2021highly]. Protein structure is foundational to understanding function and mechanism. But experimentally determining structure is slow, expensive, and feasible for only a fraction of known sequences. Using deep neural networks trained on structural and evolutionary data, AlphaFold demonstrated that protein structures could be predicted with near-atomic accuracy, even in cases where no close structural template exists [@jumper2021highly]. Its performance in the CASP14 blind assessment made it clear that structure prediction had entered a new era.

This didn’t just solve a benchmark problem. It unlocked a new regime of large-scale structural bioinformatics. Suddenly, millions of proteins could be modeled computationally. Researchers could explore binding sites, generate hypotheses about function, and reason mechanistically at scale.

Zooming out, what’s happening in biology reflects a broader shift across the sciences. AI has evolved from early expert systems that encoded human knowledge, to statistically grounded learning frameworks that formalized generalization, to DL systems capable of automatically extracting task-relevant representations from massive datasets, to generating new sequences to optimize a specific activity [@nussinov2022alphafoldartificialintelligence;@greener2022aguideto]. 

AI has proven capable of extracting intricate patterns from large datasets in genomics, drug discovery, imaging, and beyond. The same methods that power image recognition and speech systems are now being adapted to understand genomes, proteins, and cellular systems.

# 1.1.3 Additional materials
- Vaswani, Ashish, et al. "Attention is all you need." Advances in neural information processing systems 30 (2017).

- Kaplan, Jared, et al. "Scaling laws for neural language models." arXiv preprint arXiv:2001.08361 (2020).

- Chapter 4.1: AI glossary for more definitions.

- [The future of chemistry is language](https://www.nature.com/articles/s41570-023-00502-0)

- [Ilya Sutskever’s Reading List](https://aiconnections.substack.com/p/ilya-sutskevers-reading-list) 

- [Recurrent Neural Networks (RNNs): Architectures, Training Tricks, and Introduction to Influential Research](https://www.ncbi.nlm.nih.gov/books/NBK597502/)

- [An interview with Alex Krizhevsky](https://www.youtube.com/watch?v=gwzwkv2hO5k)

- [Geoffrey Hinton: The 60 Minutes Interview](https://www.youtube.com/watch?v=Rl9nHNeketE)

```{bibliography}
:filter: docname in docnames
```