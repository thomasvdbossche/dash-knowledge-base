Basic concepts
======================================

Introduction
--------------

Federated learning or FL (sometimes referred to as collaborative learning) is an emerging approach used to train a decentralized machine learning model (e.g., deep neural networks) across multiple edge devices, variously from smartphones to medical wearables to vehicles to IoT devices, etc. They collaboratively (hence the second name) train a shared model while keeping the training data locally without exchanging it with a central location.

This creates an alternative to the traditional centralized approach to building machine learning models where data from different sources is collected and stored on one server, and then the model is trained on a single server too.

In simple terms, with federated learning, it is not data that moves to a model but it is a model that moves to data, meaning training is happening from user interaction with end devices.

A relatively new and continuously researched topic, federated learning has been actively driven by scientists from Google during recent years. The tech giant has applied this approach to improve next-word prediction models in their Gboard on Android.

Owing to federated learning, the company takes advantage of data from millions of smartphones while keeping users’ private text messages safe. Quoting Google, “Federated Learning processes that history on-device to suggest improvements to the next iteration of Gboard’s query suggestion model.”

Centralized vs decentralized vs federated machine learning
---------------------------------------------

Centralized machine learning approach
-------------------------
Traditionally, the data for machine learning models is first collected from multiple sources into one centralized repository. This central location can be a data warehouse, a data lake, or even a new, combined version of both — lakehouse. You pick an algorithm like the decision tree (or a set of algorithms like the aforementioned neural networks) to train it on the collected data. Then you can run the resulting model right on the central server or distribute it across devices.

While it’s a relatively easy, standard approach, it has some disadvantages — especially if applied to modern IoT infrastructures, with new data constantly generated at the periphery of computer networks. The main modern challenges related to centralized ML are as follows:

- Network latency. Real-time apps require almost instant response from the model. If it’s run on the server, there is always a risk of delays in data transmission.

- Connectivity issues. Again, you need a stable Internet connection to ensure smooth data exchange between myriads of devices from one side and the central server from the other.

- Data privacy concerns. Some data such as images and text messages may be useful for making intelligent apps but it may contain private information and can’t be freely shared.


Centralized machine learning approach
~~~~~~~

One idea to solve some of the problems mentioned above is to do all machine learning on-site. This means that each individual device or local server trains the model on its own data and in its own environment, not communicating with the central location at all. As a result, ML stays independent of the quality of the Internet connection and can use confidential information as it doesn’t have to be sent to the cloud.

The downside of the approach is that one device doesn’t obtain sufficient data to make accurate predictions and other sources do not contribute to the model training. So, the question is left open. Is there a chance for companies to create an efficient machine learning model while keeping all things on-device? In short, yes. Federated learning is here for those reasons.

Federated machine learning approach
-------------------------
Federated learning also enables learning at the edge, meaning it brings model training to the data distributed on millions of devices. At the same time, it allows you to enhance results obtained at the periphery, in the central location.


