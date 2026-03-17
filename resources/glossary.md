# 4.1 AI Glossary
:::{dropdown} **A**
:open:
- **AI assistant:**  a conversational interface that uses large language models to support users in various tasks and decision-making processes across multiple domains within an enterprise environment.
- **Agents:** autonomous or semi-autonomous AI entities that can perform tasks, make decisions, and call tools or APIs based on goals. In academic and enterprise settings, agents are often used to automate workflows like document summarization, task routing, or multi-step reasoning.
- **AGI:** Artificial General Intelligence (AGI) refers to an AI system that possesses a wide range of cognitive abilities, much like humans, enabling them to learn, reason, adapt to new situations, and devise creative solutions across various tasks and domains, rather than being limited to specific tasks as narrow AI systems are.
- **AI:** The simulation of human intelligence in machines that are programmed to think and learn like humans. Example: A self-driving car that can navigate and make decisions on its own using AI technology.
- **AI Ethics:**  the issues that AI stakeholders such as engineers and government officials must consider to ensure that the technology is developed and used responsibly.
- **Automation:** use of technology to perform tasks with minimal human intervention.
- **Algorithm:** a set of instructions or rules to follow in order to complete a specific task.
- **Associative memory:**  a system's ability to store, retrieve, and process related information based on connections between elements, enabling it to efficiently identify and use relevant data for decision-making.
- **Attention:** Attention mechanisms in large language models (LLMs) are fundamental components that allow these models to process and understand text more effectively. Introduced by Vaswani et al. in the paper “[Attention is All You Need](https://arxiv.org/abs/1706.03762),” the attention mechanism enables the model to focus on different parts of the input sequence dynamically.
- **Activation Function:** A function applied to the output of a neural network layer, introducing non-linearity into the model (e.g., ReLU, Sigmoid).
:::

:::{dropdown} **B**
:open:
- **Backpropagation:** The algorithm used to adjust the weights in a neural network during training by propagating the error backward through the network.
- **Batch size:** The number of training examples used in one iteration of training.
- **Beam Search:** A search algorithm used to generate sequences by keeping track of multiple sequences at each step and only keeping the best ones.
- **Benchmarking:** process of evaluating and comparing products or systems using standardized tests to gauge performance and capabilities.
- **Bias:** output errors caused by skewed training data. Such bias can cause models to produce inaccurate, offensive, or misleading predictions. Biased AI models arise when algorithms prioritize irrelevant or misleading data traits over meaningful patterns
- **Big data:** large data sets that can be studied to reveal patterns and trends to support business decisions. It’s called “big” data because organizations can now gather massive amounts of complex data using data collection tools and systems
- **Bayesian Optimization:** a powerful optimization technique that leverages the principles of Bayesian inference to find the minimum (or maximum) of an objective function efficiently. Unlike traditional optimization methods that require extensive evaluations, Bayesian Optimization is particularly effective when dealing with expensive, noisy, or black-box functions.
- **Binary Cross Entropy:**  a loss function used in binary classification problems ([learn more](https://www.geeksforgeeks.org/deep-learning/binary-cross-entropy-log-loss-for-binary-classification/))
:::

:::{dropdown} **C**
:open:
- **Chatbot:** a software application that is designed to imitate human conversation through text or voice commands
- **ChatGPT:** A chat interface built on top of OpenAI’s models. They are trained on a massive amount of internet text data and fine-tuned to perform a wide range of natural language tasks.
- **Chain-of-thought Prompting:** when you write prompts to encourage the AI model to reason step-by-step before arriving at an answer. This technique can improve the accuracy of AI output.
- **Chunking:** a process used to enhance the efficiency and accuracy of information retrieval in natural language processing tasks. For example, in RAG, the input text is broken down into smaller, manageable units called “chunks.” These chunks can be sentences, paragraphs, or some other application specific breakdown of a larger text into smaller units.
- **Context window:** maximum number of tokens (words or parts of words) that an AI model can process and consider simultaneously when generating a response. It is essentially the “memory” capacity of the model during an interaction or task.
- **Cognitive computing:** essentially the same as AI. It’s a computerized model that focuses on mimicking human thought processes such as understanding natural language, pattern recognition, and learning.
- **Computer vision:** an interdisciplinary field of science and technology that focuses on how computers can gain understanding from images and videos
- **Cross-Entropy Loss:** A common loss function used in classification problems that measures the difference between the predicted and actual distributions.
:::

:::{dropdown} **D**
:open:
- **Data Augmentation:**  a technique used to artificially increase the size and diversity of a training set by creating modified copies of the existing data.
- **Data mining:** the process of closely examining data to identify patterns and glean insights.
- **Data science:** an interdisciplinary field of technology that uses algorithms and processes to gather and analyze large amounts of data to uncover patterns and insights that inform business decisions.
- **Decoder**: The part of a transformer model responsible for generating output sequences from encoded inputs.
- **Deep Learning:** A subfield of ML that uses neural networks with multiple layers to learn from data.
- **Deterministic Model:** A deterministic model follows a specific set of rules and conditions to reach a definite outcome, operating on a cause-and-effect basis.
- **Dropout:** A regularization technique where random units in the network are ignored during training to prevent overfitting.
:::

:::{dropdown} **E**
:open:
- **Embeddings:** vector embeddings are a type of representation that captures the semantic meaning or context of words or sentences in a compact form. They are essentially vectors of real numbers (floats), where each dimension could represent a different feature that captures something about that concept’s meaning. Word embeddings are embedding vectors that map each word to a vector embeddings, whereas sentence embeddings map a complete sentence, paragraph or any text chunk into a vector embedding.
- **Emergent behavior:**  also called emergence, is when an AI system shows unpredictable or unintended capabilities that only occur when individual parts interact as a wider whole.
- **Evaluation:** The process of evaluating the capabilities and quality of the LLM, typically against a benchmark dataset or by humans.
- **Explainability:** techniques that make AI model decisions and predictions interpretable and understandable to humans. i.e.  explainability means the system can show you exactly how it came to its answer, including linking back to the original sources it used.
- **Encoder:** The component of a transformer that processes the input sequence and encodes it into a format suitable for decoding.
- **Epoch:** One complete pass through the entire training dataset.
:::

:::{dropdown} **F**
:open:
- **Few-shot learning:** a machine learning approach where models can learn concepts from just a few labeled examples, often 5 or less per category. Commonly used in LLM prompts to improve a model’s performance.
- **Finetuning:** The process of adapting a pre-trained model to a specific task by training it on a smaller dataset. For example, an image classification model trained on all intersection pictures can be fine turned to detect when a car runs a red light.
- **Foundation models:** a broad category of AI models which include large language models and other types of models such as computer vision and reinforcement learning models. They are called "foundation" models because they serve as the base upon which applications can be built, catering to a wide range of domains and use cases. Or most acceptedly because they are trained on large corpuses of data.
:::

:::{dropdown} **G**
:open:
- **GANs (generative adversarial networks):**  a powerful type of neural network capable of generating new, never-seen-before data that closely resembles the training data.
- **Generative AI:** an advanced technological approach that enables the creation of content including text, images, and videos
- **Generation:**  the ability of a generative model to create brand new, original content such as text, images, audio or video from scratch.
- **GPU:** short for Graphics Processing Unit, is a specialized electronic circuit originally designed to speed up the creation of images and videos. However, its remarkable ability to perform vast numbers of calculations rapidly has led to its adoption in diverse fields, including AI. scientific computing. While CPUs, or Central Processing Units, excel at sequential processing, handling tasks one instruction at a time, GPUs are designed for processing multiple tasks at the same time.
- **Gradient Descent:** An optimization algorithm used to minimize the error in the model by iteratively adjusting the model's parameters.
- **GPT:** short for Generative Pre-trained Transformer. A series of LLMs developed by OpenAI that are pre-trained on a large corpus of text and fine-tuned for specific tasks.
:::

:::{dropdown} **H**
:open:
- **Hallucinations:** When an LLM generates text that is nonsensical or unfaithful to the provided source content
- **Hyperparameters:** The parameters of a model that are set before training begins, such as learning rate, batch size, and the number of layers.
:::

:::{dropdown} **I**
:open:
- **Image recognition:** the process of identifying an object, person, place, or text in an image or video.
- **Inference:** the process of using a trained AI model to make predictions or decisions on new, unseen data
- **Intelligence amplification:** empowering human capabilities through synergistic combinations of AI systems and traditional tools.
- **Instruction-tuning:** an approach where a pre-trained model is adapted to perform specific tasks by providing a set of guidelines or directives that outline the desired operation.
- **Interpretability:** same thing as explainability
:::

:::{dropdown} **J**
:open:
- **JSON Schema:** a content specification language used for validating the structure of a JSON data.
:::

:::{dropdown} **K**
:open:
- **Knowledge Distillation:** A technique where a smaller model (student) is trained to mimic the behavior of a larger model (teacher) to reduce complexity while maintaining performance.
- **K-shot learning:** a machine learning approach where models learn from only k labeled examples per class, where k is a small number like 1-5. See few-shot learning.
- **Knowledge graph:** data structures that connect information in a web of relationships, allowing AI systems to navigate and understand complex datasets.
:::

:::{dropdown} **L**
:open:
- **Labels:** In machine learning labels are the target values or outputs that a model learns to predict.
- **Large language model:** an AI model that has been trained on large amounts of text so that it can understand natural language and generate human-like text.
- **Latency:** the time delay between when an AI system receives an input and generates the corresponding output.
- **Latent Space:** The abstract, multi-dimensional space where the model represents different features or concepts learned during training.
- **Learning:** a system's ability to improve its performance or knowledge based on experience and data analysis.
- **Learning Rate:** A hyperparameter that controls how much to change the model in response to the estimated error each time the model's weights are updated.
- **Logits:** The raw, unnormalized scores output by a model before applying a softmax function.
:::

:::{dropdown} **M**
:open:
- **Machine learning:** A subfield of AI that involves the development of algorithms and statistical models that enable machines to improve their performance with experience.
- **Max Marginal Retrieval Ranking (MMR):** A technique by which relevant facts provided by the retrieval step are reordered to create a more diverse set of facts. MMR is often implemented as a reranking step, post retrieval.
- **Multi-hop reasoning:**  A term often used in natural language processing and, more specifically, machine reading comprehension tasks. It refers to the process by which an AI model retrieves answers to questions by connecting multiple pieces of information present in a given text or across various sources and systems, rather than directly extracting the information from a single passage.
- **Multimodal Language Models:** A type of deep learning model trained on large datasets of both textual and non-textual data.
:::

:::{dropdown} **N**
:open:
- **Natural Language Processing (NLP):** A subfield of artificial intelligence and computational linguistics that focuses on enabling machines to understand, interpret, and generate human language to be understood by humans.
- **Neural Network:** A machine learning model inspired by the human brain's structure and function that's composed of layers of interconnected nodes or "neurons."
:::

:::{dropdown} **O**
:open:
- **Overfitting**: occurs in machine learning training when the algorithm can only work on specific examples within the training data, rendering it unable to make accurate predictions on new data.
- **Optimization**: The process of adjusting the parameters of a model to minimize a loss function that measures the difference between the model's predictions and the true values.
:::

:::{dropdown} **P**
:open:
- **Parameters:** the internal variables that the model learns from training data. These parameters, such as weights and biases in neural networks, determine how the model processes input and generates outputs.
- **Parameter-Efficient Fine-Tuning (PEFT):** an approach that helps you improve the performance of large AI models while optimizing for resources like time, energy, and computational power. To do this, PEFT focuses on adjusting a small number of key parameters while preserving most of the pretrained model's structure.
- **Perplexity:** A measurement of how well a language model predicts a sample; lower perplexity indicates better performance.
- **Pretraining:** Training a model on a large dataset before fine-tuning it to a specific task.
- **Prompt:** The input that a user feeds to an AI system in order to get a desired result or output.
- **Prompt Engineering:** Identifying inputs — prompts — that result in meaningful outputs. As of now, prompt engineering is essential for LLMs.
- **Probabilistic Model:** A probabilistic AI model makes decisions based on probabilities or likelihoods.
- **Position embedding: T**he technique used to add information about the position of words in a sequence to the model, since transformers don’t inherently understand word order.
:::

:::{dropdown} **Q**
:open:
- **Q-learning:** a reinforcement learning algorithm that trains an agent to assign values to its possible actions based on its current state, without requiring a model of the environment (model-free). 
:::

:::{dropdown} **R**
:open:
- **Reasoning:** The process by which artificial intelligence systems solve problems, think critically, and create new knowledge by analyzing and processing available information, allowing them to make well-informed decisions across various tasks and domains.
- **Reinforcement Learning:** A type of machine learning in which a model learns to make decisions by interacting with its environment and receiving feedback through rewards or penalties.
- **Reinforcement Learning from Human Feedback (RLHF):** A technique used to train LLMs by incorporating human preferences into the training process. Instead of relying solely on pre-defined datasets, RLHF allows models to learn from direct human feedback on their outputs, making them more aligned with human expectations and preferences.
- **Representation learning:** Methods that allow models to automatically learn useful features or representations of data instead of relying on manually designed features.
- **Retrieval augmented generation (RAG):** an AI framework that enhances LLMs by integrating external knowledge sources. It combines the strengths of traditional information retrieval systems with generative AI models. RAG helps LLMs generate more accurate, up-to-date, and relevant text by retrieving relevant information from databases, uploaded documents, or web sources before generating a response.
- **Reranking:** In RAG a reranker plays a crucial role in enhancing the relevance of retrieved documents in a two-stage retrieval model.
:::

:::{dropdown} **S**
:open:
- **Sequence modeling:** A subfield of NLP that focuses on modeling sequential data such as text, speech, or time series data.
- **Sequence-to-Sequence Model (Seq2Seq):** A model architecture used for tasks where the input is a sequence of tokens and the output is another sequence, like translation.
- **Stable diffusion:** An artificial intelligence system that uses deep learning to generate images from text prompts.
- **Supervised learning:** A type of machine learning in which a model is trained on labeled data to make predictions about new, unseen data.
- **Structured data:** information that is organized and labeled in a standardized format.
- **Sentiment analysis:** Also known as opinion mining, sentiment analysis is the process of using AI to analyze the tone and opinion of a given text.
- **Semantic search:** A method used in search algorithms that considers the searcher’s intent and the contextual meaning of terms as they appear in documents. Instead of merely looking at the keywords in a search, a semantic search engine tries to understand the underlying concepts, context, and meaning to deliver more precise results.
- **Softmax:** An activation function often used in the output layer of a classifier to convert logits to probabilities.
- **Self-learning:** Systems that can autonomously acquire knowledge and improve their performance over time without explicit programming for each new task.
:::

:::{dropdown} **T**
:open:
- **Token:** A basic unit of text that an LLM uses to understand and generate language. A token may be an entire word or parts of a word.
- **Tokenization:** A process by which a text string is broken down into tokens.
- **Training data:** The information or examples given to an AI system to enable it to learn, find patterns, and create new content.
- **Transfer learning:** A machine learning system that takes existing, previously learned data and applies it to new tasks and activities.
- **Turing test:** A test to evaluate a machine’s ability to exhibit intelligence equal to humans, especially in language and behavior.
- **Transfer learning:** A type of neural network architecture designed to process sequential data, such as text.
- **Temperature:** An AI tool’s **temperature** setting controls how deterministic or creative that AI model’s output is. Lower values (e.g., 0.2) lead to more focused and consistent answers, while higher values (e.g., 0.8) produce more varied or imaginative responses.
:::

:::{dropdown} **U**
:open:
- **Unstructured data:** data that is not organized in any apparent way. In order to analyze unstructured data, you’ll typically need to implement some type of structured organization.
- **Unsupervised learning:** A machine learning type that looks for data patterns. Unlike supervised learning, unsupervised learning doesn’t learn from labeled data.
- **Underfitting:** When a model is too simple to capture the underlying patterns in the data, leading to poor performance on both training and test data.
:::

:::{dropdown} **V**
:open:
- **Vector store:**  A type of database that stores high-dimensional vector data and provides query capabilities on those vectors such as similarity search, where the goal is to find the most similar documents or items to a given query. The most common types of vector stores are Faiss, ChromaDB amd NMSLiB
:::

:::{dropdown} **W**
:open:
- **Whisper:** An AI system developed to perform automatic speech recognition (ASR), the task of transcribing spoken language into text.
- **Weak AI:** narrow systems that excel at specific tasks within limited contexts, but lack generalized intelligence and adaptability outside their domain.
:::

:::{dropdown} **W**
:open:
- **Zero-shot learning:** a technique in which a machine learning model can recognize and classify new concepts without any labeled examples.
:::