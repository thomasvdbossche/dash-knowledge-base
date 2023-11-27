Methodology
===========

Steps
-----

Step 1: Pick your model framework
Step 2: Determine the network mechanism
Step 3: Build the centralized service
Step 4: Design the client system
Step 5: Set up the training process
Step 6: Establish the model management system
Step 7: Addressing privacy and security

Step 1: Pick your model framework
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
A framework must be selected that has some support for federated learning.

Selection criteria includes items like:
- Domain (e.g. imaging, NLP, or tabular data)
- Team familiarity with the technology
- Compatibility of the framework with existing infrastructure.

PyTorch or TensorFlow are popular choices; these libraries provide some facilities for federated learning but additional production ready components need to be added for a complete solution.

Step 2: Determine the network mechanism
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Next, you need to determine what networking mechanism to use. This mechanism is the messaging format and framework for passing the instructions between each participant in the federated learning network.

- PySyft with PyTorch: a PyTorch focused framework from OpenMined to enable federated learning
- Flower: a generic framework that abstracts the messaging flow to support multiple modeling frameworks
- Tensorflow Federated: Tensorflow’s approach to distributing model operations

Deciding on which option is right for you usually comes down to how flexible you need the networking mechanism to be across modeling frameworks. For example, if your team wants to work mainly in PyTorch and needs lower level access to modeling operations, then PySyft may be a good choice.

If you want to prioritize flexibility, then Flower is a good choice because it enables federated learning on different modeling frameworks.

Both the networking and core model framework choices are also dependent on the application being within an organization, or between multiple organizations. In the latter case, choices need to be acceptable across all participating organizations.

Step 3: Build the centralized service
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Once you have picked your model framework and networking mechanism, you need to establish a centralized service to manage the participants. This service will be responsible for coordinating communication between the participants, as well as monitoring the training progress.

From an operational perspective, this service will likely need to:

1. Have authentication and authorization mechanisms built in, along with the support structure to keep it reliable; this includes ensuring that the service is stateless to aid in load balancing, which means that a storage mechanism needs to be chosen to hold intermediate information passing between clients.

2. Be deployed, and maintained to meet the demand of the federated learning system.
3. Be able to administer the training sessions.

There are additional key design considerations from a functional perspective, to take into account as well. For example:

- Does authorization or service isolation need to be added to separate different data networks? That is, some groups of participants that can collaborate together, but not between groups.
- Can a client trigger a training session or does it have to be centrally administered?
- How will clients disconnecting and reconnecting affect the training? This problem is compounded by the number of parties participating in the training.
- What statistics should be collected during the training session and how will monitoring be set up so that the system can measure the quality of the model being trained?
- How will the service manage participating clients operating at different speeds?
- How will the system know when to drop a client if they become unreliable so that the model can still continue to be trained?

Taking the time to design a system that takes these considerations into account is critical to ensure that the system you will implement will be reliable, flexible and valuable.

Step 4: Design the client system
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Now it’s time to consider a possible design for the client system. This system needs to be able to perform client side training operations, and coordinate the model parameters with the central service. The client system will also need to fetch new parameters from other clients in the network to update the local model.

To design and deliver a reliable client application, you should seek to answer the following questions:

- Should the client system be a package that’s installable or should it be something like a docker image? How will dependency versioning be managed?
- How will the client authenticate and communicate with the server?
- How will monitoring the training process work?
- How will error recovery be handled during the model training process?

Step 5: Set up the training process
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The federated learning system needs to know what private data should be used from each client to train the local models for a particular session.

This information needs to come from another user, or the central service. Therefore, the meta information about available data has to be managed in some form; this is typically done by the central service.

This also requires that clients register this meta information about what datasets are available for other clients. Similarly, metadata for each client will need to be retrieved from the central service about which datasets should be used for a training session.


Step 6: Establish the model management system
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
The output of a training session is a machine learning model. The federated learning system needs to manage model metrics and access so that the appropriate users can use the trained model.

The following questions can be used to guide how the system will manage models:

- Should all participants be able to access a copy of the model or do only some participants get access to it?

- Where will the model be stored (typically this will be by the centralized service)?

Step 7: Addressing privacy and security
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The final model is available locally to one or more of the participants. Because this model was trained by sharing weights between different parties, inverting the model to retrieve insights about the underlying training data is possible.

Therefore, determining the acceptable risks for the model itself is important. These risks could include being able to re-identify an individual in a particular training set or regenerate the training set itself, which could contain sensitive IP that a participant does not want to expose.

Different methods for mitigating these risks exist; one example would be applying differential privacy to the model weights before transmission to the central service. By adjusting the privacy budget, it’s possible to balance the utility of the final model with the amount of risk that you find acceptable.

Optimizing model risk versus model performance is use case dependent so it’s important to engage the right stakeholders when making this decision.