=================
Frameworks
=================

TensorFlow Federated
--------------------
Developed by Google, TensorFlow Federated (TFF) is a Python-based, open-source framework for training machine learning models on decentralized data. This framework has been pioneering the experimentation with federated learning as an approach.

TFF performs in two main API layers:

- Federated Learning (FL) API offers high-level interfaces that enable developers to plug existing machine learning models to TFF without the need to dive deeply into how federated learning works.
    
- Federated Core (FC) API offers low-level interfaces that provide opportunities to build novel federated algorithms.

The library consists of two components: the collaborator, which uses a local dataset to train global models and the aggregator, which receives the model updates and combines them to create the global model. OpenFL comes with a Python API and a command-line interface.

The communication between the nodes is done using mTLS, and hence certificates are required. It is necessary to certify each node in the federation. OpenFL supports lossy and lossless compression of data to reduce communication costs. OpenFL allows developers to customize logging, data split methods, and aggregation logic.

The OpenFL design philosophy is based on the Federated Learning (FL) Plan. It is a YAML file that defines required collaborators, aggregators, connections, models, data, and any required configuration. OpenFL runs on docker containers to isolate federation environments.


OpenFL
------
Developed by Intel, OpenFL (Open Federated Learning) is an open-source framework that leverages the data-private federated learning paradigm for training ML algorithms. The framework comes with a command-line interface and a Python API. Open FL can work with training pipelines built with PyTorch and TensorFlow while it can go beyond and work with other frameworks.


IBM Federated Learning
----------------------
IBM Federated Learning is a framework that promises data scientists and machine learning engineers an easy integration of federated learning workflows within the enterprise environment. This federated learning framework supports a variety of algorithms, topologies, and protocols out-of-the-box, including

- Linear classifiers/regressions,
- Deep Reinforcement Learning algorithms,
- Naïve Bayes,
- Decision Tree, and
- Models written in Keras, PyTorch, and TensorFlow, to name a few.

Not to mention that researchers in the field of federated learning can use the existing functionality of the framework to fit the specific needs of their organization or the particular application domain.

Flower
------
Flower (flwr) is a framework for building federated learning systems. The design of Flower is based on a few guiding principles:

- Customizable: Federated learning systems vary wildly from one use case to another. Flower allows for a wide range of different configurations depending on the needs of each individual use case.

- Extendable: Flower originated from a research project at the University of Oxford, so it was built with AI research in mind. Many components can be extended and overridden to build new state-of-the-art systems.

- Framework-agnostic: Different machine learning frameworks have different strengths. Flower can be used with any machine learning framework, for example, PyTorch, TensorFlow, Hugging Face Transformers, PyTorch Lightning, MXNet, scikit-learn, JAX, TFLite, or even raw NumPy for users who enjoy computing gradients by hand.

- Understandable: Flower is written with maintainability in mind. The community is encouraged to both read and contribute to the codebase.

easyFL: A Lightning Framework for Federated Learning
----------------------------------------------------
EasyFL is a strong and reusable experimental platform for research on federated learning (FL) algorithm, which has provided a few easy-to-use modules to hold out for those who want to do various federated learning experiments. In short, it is easy for FL-researchers to

- quickly realize and compare popular centralized federated learning algorithms

transform traditional machine learning tasks into federated tasks by following our paradigm of constructing data pipeline

make interesting observations during training time to get a deeper insight of federated learning in a code-incremental manner without destorying the original realization
- efficiently manage and analyze the experiment records with utils/result_analysis.py

FATE
----
FATE (Federated AI Technology Enabler) is an open-source project that aims to support a secure and federated AI ecosystem. FATE is available for standalone and cluster deployment setups. The open-source framework is backed by WeBank, a private-owned neo bank based in Shenzhen, China.

For using and writing custom models for it, you need to have some knowledge of protocol buffers. Besides that it has several components, such as:

- FATEFlow

FATEFlow is the main component of FATE, and it represents the end-to-end machine learning orchestration pipeline. The pipeline supports machine learning tasks such as data preprocessing, model training and testing, publishing, and serving. FATEFlow supports DAG, scheduling, monitoring, and custom pipeline components.

- FederatedML

FederatedML is the component responsible for implementing many standard machine learning algorithms and other utility tools. Supported algorithms include but are not limited to DataIO, Intersect, and OneHot Encoder.

- FATEBoard

FATEBoard is a collection of visualization/dashboarding tools for federated learning to explore, analyze, and understand models easily. FATEBoard supports both standalone and distributed deployment setups.

- FATE Serving

FATE Serving is the component responsible for serving federated learning models for production usage. It supports online inferencing, dynamic loading of models, A/B testing scenarios, and caching.

- Federated Network

Federated Network is the communication means between federated learning parties

- KubeFATE

KubeFATE is the distributed systems infrastructure required to manage federated workloads. KubeFATE supports docker-compose and Kubernetes cluster deployment setups.

- FATE-Client

FATE-Client is an optional component used to interact with different FATE components.


Substra
-------
Substra is a federated learning software framework developed by a multi-partner research project around Owkin, a French startup founded in 2016. Substra is focused on the medical field with the purpose of data ownership and privacy. Today, it is used in the MELLODY project for drug discovery in the pharmaceutical industry.

Substra supports a wide variety of interfaces for different types of users. It has a python library for data scientists, command-line interfaces for admins, and graphical user interfaces for project managers and other high-level users. In terms of deployment, Substra involves a complex Kubernetes setup for every node.

The key features of Substra are:
- Privacy: Substra uses trusted execution environments (also called enclaves) that enables setting aside private regions for code and data
- Traceability: Substra writes all operations on the platform to an immutable ledger
- Security: Substra encrypts model updates, data on rest, and network communication

PySyft + PyGrid
---------------
PySyft is an open-source Python 3 based library that enables federated learning for research purposes and uses FL, differential privacy, and encrypted computations. It was developed by the OpenMined community and works mainly with deep learning frameworks such as PyTorch and TensorFlow.

PySyft supports two types of computations:
- Dynamic computations over data that cannot be seen
- Static computations, which are graphs of computations that can be executed later on in a different computing environment

PySyft defines objects, machine learning algorithms, and abstractions. With PySyft, you can't work on real data science problems that involve communication across networks. This would require another library, called PyGrid.

PyGrid implements federated learning on web, mobile, edge devices, and different types of terminals. PyGrid is the API to manage and deploy PySyft at scale. It can be controlled using PyGrid Admin.

PyGrid consists of three different components:
- Domain: A Flask based application used to store private data and models for federated learning
- Worker: An ephemeral compute instance managed by domain components to perform computations on data
- Network: A Flask based application to monitor and control different domain components

NVIDIA Clara
------------
NVIDIA CLARA is an application framework designed for healthcare use cases. It includes full-stack GPU-accelerated libraries, SDKs, and reference applications for developers, data scientists, and researchers to create real-time, secure, and scalable federated learning solutions. Active deployment of CLARA can be found at the French startup Therapixel, which is using NVIDIA’s technology to improve the accuracy of breast cancer diagnosis.

NVIDIA CLARA supports the following use cases:
- Clara AGX for medical devices
- Clara Discovery for Drug Discovery
- Clara Guardian for Hospitals
- Clara Imaging for Medical Images
- Clara Parabricks for Genomics

Enterprise-grade Federated Learning Platforms
---------------------------------------------
Federated learning is a powerful technique to train machine learning data while maintaining privacy, and without ever having to share data. Many industries benefit from this approach, such as the healthcare sector, where patient data are considered highly confidential, or in manufacturing, where strong IP protection is needed.

When looking at examples and tutorials of open-source software for federated learning, one is tempted to think to get good results quickly. This is mostly because the data sets provided are clean, you can easily split the data across clients, and get started with simple FL experiments. However, in the real world you face other complexities.

If you are working in an industry that has the highest requirements in compliance, security, and availability, you might need to work with an enterprise-grade platform for federated & privacy-preserving data science, such as Apheris.

We take care of the full end-to-end process, starting from contractual, legal, and compliance frameworks, role-based authentication, privacy controls, traceability via a logging solution, and supporting the full data science workflow. Apheris provides the fastest and most secure way to progress from experimentation to high-impact collaborations with partners that drive tangible business results from AI.

To securely collaborate with partners on AI and sensitive data in an enterprise context, Federated Learning must be seen from a broader perspective. We go more into depth on what it takes to implement federated learning into enterprise MLOps pipelines in our whitepaper.