# Domain 1: Fundamentals of Machine Learning (ML) and Artificial Intelligence (AI)
# (1A: Fundamentals and Taxonomy of AI)

## Artificial Intelligence (AI)
### Overview
* AI is a broad field that encompasses the development of intelligent systems capable of performing tasks that typically require human intelligence, such as:
  * Perception
  * Reasoning
  * Learning
  * Problem-Solving
  * Decision-Making
* AI serves as an umbrella term for various techniques and approaches, including:
  * Machine Learning
  * Deep Learning
  * Generative AI
* AI is all around us including everything from smart assistants like Alexa or Siri to robotic vacuum cleaners and self-driving cars.

## Machine Learning (ML)
### Overview
* **ML is a subset of AI** focused on creating systems that learn from data to make ***predictions*** or ***decisions***.
* ML is the science of developing ***algorithms*** and ***statistical models*** that computer systems use to perform complex tasks **WITHOUT** explicit instructions:
  * ML relies on ***patterns*** and ***inference***.
  * ML algorithms process large quantities of historial data and identify data patterns.  
* **IMPORTANT:** ML is AI, BUT not all AI activities are ML.

## Deep Learning (DL)
### Overview
* **DL is a specialized subset of ML** using ***neural networks*** with multiple layers (deep neural networks).
* **Deep Neural Networks** mimic the way the human brain processes information allowing the DL model to handle very complex tasks.
* Excels at analyzing large volumes of complex, unstructured data such as images and text (it's what allows image recongition software to identify objects in photos and voice assistants to understand natural speech).
* DL has the ability to uncover intricate patterns in unstructured data is what sets it apart from ML.

## Generative Artificial Intelligence (Gen AI)
### Overview
* **GenAI is a subset of DL** because it can adapt models built using deep learning, but without retraining or fine tuning.
* GenAI systems are capable of generating new content (e.g., text, images, audio, etc.) based on the patterns and structures learned from training data.
* So while traditional AI is focused on recognizing patterns or making decisions, GenAI is all about creating new content.
* Enabled by advances in computing power, data availability, and algorithmic innovation.

### Taxonomy
```mermaid
flowchart TD
    A["`**Artificial intelligence (AI)**
    Any technique that allows computers to mimic human intelligence using logic,
    if-then statements, and machine learning`"]
    
    B["`**Machine learning (ML)**
    A subset of AI that uses machines to search for patterns in data to build logic
    models automatically`"]
    
    C["`**Deep learning (DL)**
    A subset of ML composed of deeply multi-layered neural networks that
    perform tasks like speech and image recognition`"]
    
    D["`**Generative AI**
    Powered by large models that are pretrained on vast corpora of data
    and commonly referred to as foundation models (FMs)`"]

    A --> B
    B --> C
    C --> D

    %% Apply the pink styling via a class definition
    classDef pinkNode fill:#fff,stroke:#ff69b4,stroke-width:2px,color:#000;
    class A,B,C,D pinkNode
```

## Similarities: AI vs. ML
### Human-like Problem Solving
* Both AI and ML excel at complex , precise tasks (e.g., self-driving cars, property pricing algorithms, etc).
### Fields of Computer Science
* AI and ML are branches of computer science that enable advanced data analysis and self-learning.
### Cross-Industry Applications
* Used in supply chain, predicitive maintenance, demand forecasting, and personalized recommendations.

## Differences: AI vs. ML
### Objectives
* **AI:** Completes complex human tasks (learning, problem-solving, recognizing patterns).
* **ML:** Analyzes data to identify patterns with statistical models, giving results with a probability of correctness (learns from the data to make predictions or decisions).
### Methods
* **AI:** Utilizes genetic algorithms, neural networks, deep learning, search algorithms, rule-based systems, and ML.
* **ML:** Divided into two (2) broad categories:
  * **Supervised Learning:** Training data is labeled (predicts outcomes)
  * **Unsupervised Learning:** Training data is unlabeled (uncovers hidden patterns in the data)
### Implementations
* **AI:** Uses complex, prebuilt solutions, often via APIs for integration (AI has gone through extensive R&D to be built, allowing it to be integrated)
* **ML:** Involved dataset selection, model choice (e.g., linear regression), and refinement with error checking
### Requirements
* **AI:** Infrastructure varies; high-computing tasks may need **thousands** of machines
* **ML:** Needs **hundreds of data points** and moderate computational power (single server/small cluster)

## Summary Table: AI vs. ML (Similarities and Differences)
```mermaid
graph LR
    %% Column 1: Labels
    subgraph Labels [" "]
        direction TB
        L1["**What is it?**"]
        L2["**Best suited for**"]
        L3["**Methods**"]
        L4["**Implementation**"]
    end

    %% Column 2: Artificial Intelligence
    subgraph AI ["**Artificial Intelligence**"]
        direction TB
        A1["AI is broad term for machine-based applications that mimic human intelligence. Not all AI solutions are ML."]
        A2["AI is best for completing a complex human task with efficiency."]
        A3["AI may use a wide range of methods, like rule-based, neural networks, computer vision, and so on."]
        A4["AI implementation depends on the task. AI is often prebuilt and accessed via APIs."]
    end

    %% Column 3: Machine Learning
    subgraph ML ["**Machine Learning**"]
        direction TB
        M1["ML is an artificial intelligence methodology. All ML solutions are AI solutions."]
        M2["ML is best for identifying patterns in large sets of data to solve specific problems."]
        M3["For ML, people manually select and extract features from raw data and assign weights to train the model."]
        M4["You train new or existing ML models for your specific use case. Prebuilt ML APIs are available."]
    end

    %% Aligning the rows
    L1 --- A1 --- M1
    L2 --- A2 --- M2
    L3 --- A3 --- M3
    L4 --- A4 --- M4

    %% Styling
    style Labels fill:none,stroke:none
    style AI fill:#f9f9f9,stroke:#333,stroke-width:2px
    style ML fill:#f9f9f9,stroke:#333,stroke-width:2px

%% This line forces the text in the "AI" and "ML" subgraph titles to black
    style AI color:#000, stroke:#333, stroke-width:2px
    style ML color:#000, stroke:#333, stroke-width:2px
```
## Similarities ML vs. DL
### Pattern Identification
* Both train algorithms on large datasets to find correlations for predicting new data.
### AI Techniques
* ML and DL are AI subsets capable of handling complex computational tasks.
### Statistical Basis
* Use statistical methods like regression analysis; require strong statistics knowledge for development.
### Large Datasets
* Both need extensive training data for accuracy:
  * ML: 50-100 points/feature
  * DL: thousands of points
 


