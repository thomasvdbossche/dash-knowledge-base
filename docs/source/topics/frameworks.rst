=================
Frameworks
=================

TensorFlow Federated
-----------------------------------
Developed by Google, TensorFlow Federated (TFF) is a Python-based, open-source framework for training machine learning models on decentralized data. This framework has been pioneering the experimentation with federated learning as an approach.

TFF performs in two main API layers:

- Federated Learning (FL) API offers high-level interfaces that enable developers to plug existing machine learning models to TFF without the need to dive deeply into how federated learning works.
    
- Federated Core (FC) API offers low-level interfaces that provide opportunities to build novel federated algorithms.


OpenFL
-----------------------------------
Developed by Intel, OpenFL (Open Federated Learning) is an open-source framework that leverages the data-private federated learning paradigm for training ML algorithms. The framework comes with a command-line interface and a Python API. Open FL can work with training pipelines built with PyTorch and TensorFlow while it can go beyond and work with other frameworks.


IBM Federated Learning
-----------------------------------
IBM Federated Learning is a framework that promises data scientists and machine learning engineers an easy integration of federated learning workflows within the enterprise environment. This federated learning framework supports a variety of algorithms, topologies, and protocols out-of-the-box, including

- Linear classifiers/regressions,
- Deep Reinforcement Learning algorithms,
- Naïve Bayes,
- Decision Tree, and
- Models written in Keras, PyTorch, and TensorFlow, to name a few.

Not to mention that researchers in the field of federated learning can use the existing functionality of the framework to fit the specific needs of their organization or the particular application domain.

Flower
-----------------------------------
Flower (flwr) is a framework for building federated learning systems. The design of Flower is based on a few guiding principles:

- Customizable: Federated learning systems vary wildly from one use case to another. Flower allows for a wide range of different configurations depending on the needs of each individual use case.

- Extendable: Flower originated from a research project at the University of Oxford, so it was built with AI research in mind. Many components can be extended and overridden to build new state-of-the-art systems.

- Framework-agnostic: Different machine learning frameworks have different strengths. Flower can be used with any machine learning framework, for example, PyTorch, TensorFlow, Hugging Face Transformers, PyTorch Lightning, MXNet, scikit-learn, JAX, TFLite, or even raw NumPy for users who enjoy computing gradients by hand.

- Understandable: Flower is written with maintainability in mind. The community is encouraged to both read and contribute to the codebase.