# 1.2 An Overview of AI Models


# First things first, what is a "model"?

An model is simply an algorithm (a function) that has been trained on data in order to recognize patterns and make predictions. The data used to train a model typically consists of examples. Each example may contain:

- an **input** (e.g., a protein sequence, microscopy image, gene expression profile)

- optionally a **label** describing the correct answer (e.g., the protein's function, the cell type in an image, or whether a mutation is pathogenic)


:::{admonition} Algorithm vs Model
:class: tip

An *Algorithm* is a precise set of instructions or rules to solve a specific problem or task. Often written in mathematical formulation.

A *Model* is a specific algorithm applied to a dataset.
:::

During training, the **model** examines many such examples and gradually learns statistical relationships between the inputs and outputs. 
Once trained, the model can then be used to make predictions on new data it has never seen before. For instance, it might predict the function of a newly discovered protein or identify structures in a microscopy image.


It is also useful to distinguish between **supervised** and **self-supervised** training approaches.

- **Supervised learning:** the training data includes both inputs and labels. The model learns by comparing its predictions to the correct answers and adjusting itself to reduce errors. For example, a dataset might contain protein sequences along with experimentally determined functions, and the model learns to predict the function from the sequence.

- **Self-supervised learning:** the model learns patterns from data without explicit labels. Instead, part of the data is hidden or modified and the model learns to predict the missing information. For instance, a model trained on protein sequences might learn to predict masked amino acids within sequences. By solving this task across millions of sequences, the model learns useful representations of proteins that can later be applied to many biological problems.

You may refer to Andrew White's [Deep Learning for Molecules & Materials](https://dmol.pub/index.html#)[@white2021deep] for an in-depth overview on machine learning. 

# Relationship between AI, ML, DL and GenAI

```{figure} ../figures/Ai_categories.png
:alt: ai_cats
:align: center
:figclass: caption-centered

Figure 1.2.1: AI is a super class of learning algorithms which encompases ML, DL and GenAI. (Created with gpt-image-1.5-2025-12-16)
```

- **Artificial Intelligence (AI):** The broad field of creating systems that perform tasks requiring human-like intelligence (reasoning, perception, decision-making).

- **Machine Learning (ML):** A subset of AI where systems learn patterns from data instead of being explicitly programmed.

- **Deep Learning (DL):** A subset of ML that uses multi-layer neural networks to learn complex patterns, especially from large datasets.

- **Generative AI (GenAI):** A type of deep learning model designed to generate new content (e.g., text, images, proteins) by learning patterns from large datasets.

# An overview on the models we see in science

Not only AI model but computational models are foundational to modern biology and science, spanning a continuum from first-principles physics-based simulations to data-driven machine learning. Let's take a look at the major categories of AI and computational models encountered in biological research. 

- **Physics-Based Models:** encode known physical laws, conservation principles, and mechanistic understanding directly into mathematical formulations. The oldest class of computational models. eg: Ordinary and Partial Differential Equations (ODEs/PDEs), Molecular dynamics

- **Traditional ML Models:** the recommended starting point for many biological tasks. Faster to develop, easier to interpret, and often appropriate when datasets are modest in size. eg: Support vector machines (SVMs), Radom Forest (RF) models. 

- **Deep Learning Models:** automatically learns hierarchical representations from raw data. Most advantageous when large datasets, many features, or highly structured inputs are available. eg:  Graph Neural Networks (GNNs), Recurrent Neural Networks (RNNs)

- **Foundation Models:** represents a paradigm shift in computational biology. Large-scale AI systems pre-trained on vast, often unlabeled datasets using self-supervised or generative objectives. FMs address longstanding challenges in bioinformatics, including limited annotated data, data noise, and the need for generalizable representations across biological domains. Large language models belong to this category.

```{table} Table 1.2.1: Commonly encountered computational and AI models in science.
| Model Category | Methods/Architectures | Key Characteristics | Primary Applications | 
|---|---|---|---|
| Physics-Based Models  | Ordinary/Partial Differential Equations (ODEs/PDEs), reaction–diffusion, continuum mechanics | Deterministic time/space dynamics; handles feedback, stiffness, diffusion and transport; extendable to multiscale couplings | Gene regulatory and signaling networks; tissue/organ-level diffusion–reaction and biomechanics [@materi2007comp;@zhou2024dynamicmodelingin] |
| Physics-Based Models  | Molecular dynamics (atomistic, coarse-grained), molecular mechanics force fields | Newtonian/Langevin dynamics with bonded/non-bonded forces; atomistic detail to coarse-grained scales; ensemble/dynamics focus | Protein folding and conformational dynamics; protein–ligand binding; free-energy and mechanistic studies [@huggins2019biomolecularsimulationsfrom;@schmidt2008thesimbiosnational] | 
| Physics-Based Models  | Agent-based/multicellular (cellular automata, Cellular Potts, center-based/off-lattice); hybrid discrete–continuum | Explicit single-cell agents with mechanical/biochemical rules; often coupled to PDE transport; stochasticity supported | Tumor growth, angiogenesis, cell–cell and cell–ECM interactions; virtual tissues and therapy testing [@metzcar2019areviewof] | 
| Traditional Machine Learning  | Random Forest (RF), Support Vector Machines (SVM), k-Nearest Neighbors (kNN), Logistic/Regularized Regression | Supervised learners for tabular/omics; RF provides feature importance; SVM handles non-linear kernels; kNN is simple baseline; linear models offer interpretability | Disease/phenotype prediction; SNP–trait and GWAS interaction discovery; sequence/site classification; proteomics/microarray sample classification [@qi2012randomforestfor;@greener2022aguideto;@touw2013dataminingin;@tarca2007machinelearningand;@ahmed2013] | 
| Deep Learning  | Convolutional Neural Networks (CNNs), Recurrent NNs (RNNs/LSTM/GRU) | CNNs capture local spatial patterns (images, 1D motifs); RNNs model sequences/time; improved with residual/attention add-ons | Histopathology and biomedical imaging; DNA/RNA motif discovery; protein secondary structure; temporal gene expression [@greener2022aguideto] | 
| Deep Learning | Generative models (GANs, VAEs), Autoencoders | Synthetic data generation; latent-space modeling; denoising/imputation for noisy omics | Synthetic biology (sequence/design), single-cell denoising/imputation, metabolomics feature learning | GAN/AE/ VAE in sequence generation and single-cell omics [@kumar2023;@goshisht2024] |
| Deep Learning | Graph Neural Networks (GNN/GCN), Transformers | GNNs operate on molecular/interaction graphs; Transformers capture long-range dependencies in sequences and structures | Drug–target/response prediction, PPI networks, single-cell graphs; protein contacts/structures; regulatory genomics [@hein2025aiandmachine;@kumar2023] | 
| Foundation Models | Protein language models (e.g., ESM-2) and structure FMs (e.g., ESMFold, AlphaFold) | Large-scale self-supervised pre-training on sequences/MSAs; zero-/few-shot transfer; sequence-to-structure heads | Protein property/function prediction; atomic-level structure prediction; design scaffolding [@lin2022languagemodelsof;@li2024progress;@guo2025foundationmodelsin] |
| Foundation Models | Genomic foundation models (DNABERT, DNABERT-2, Enformer, HyenaDNA, Nucleotide Transformer) | Masked LM, long-context and supervised pre-training for regulatory signals; model long-range genomic interactions | Promoter/enhancer and variant-effect prediction; gene expression forecasting; regulatory annotation [@li2024progress] |
| Foundation Models | Single-cell foundation models (scGPT, Geneformer, scFoundation/LCMs) | Pre-trained on millions of cells; mitigate batch effects; model gene–gene interactions and perturbations | Cell-type annotation; expression imputation; perturbation response; multi-omics integration [@guo2025foundationmodelsin;@li2024progress] |
| Hybrid/Integrative | Physics-Informed Neural Networks (PINNs) | Embed ODE/PDE residuals and physical constraints into NN loss; solve forward/inverse problems with sparse/noisy data | Tumor growth curves; gene expression kinetics; epidemiology (SIR) with parameter inference [@farea2025using] |
| Hybrid/Integrative | Differentiable biology (differentiable programming with simulators + deep nets) | End-to-end autodiff of mechanistic + learnable components; integrate priors (symmetries, simulators) with data-driven modules | Molecular mechanism modeling; differentiable dynamics; end-to-end folding/energy landscapes; uncertainty-aware inference [@alquraishi2021] |
```
---


# Additional materials

- [Deep Learning for Molecules & Materials](https://dmol.pub/index.html#)
- [IBM's primer on AI models](https://www.ibm.com/think/topics/ai-model)
- [A Medium article on ML beginner's guide](https://medium.com/@dimas.wrdntx/machine-learning-for-dummies-a-beginners-guide-dee643f983b8)
- [Every Flagship AI Model Explained](https://www.youtube.com/watch?v=DsKZpgoy830)