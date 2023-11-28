========================
Differential Privacy
========================

Differential privacy is an approach used to protect privacy of individuals when performing functions on a dataset. It provides strong guarantees that sensitive information (specific sensitive attributes or membership) about any individual in the dataset remains secret. It is important to note that differential privacy is always applied to a query (or function/analysis/calculation) and not to a dataset. The result of such query should be a value (e.g. the average age of every individual in the dataset), and never a set of records (e.g. a set of individuals with their respective age). The concept of differential privacy was first introduced in 2006 by Cynthia Dwork et. al. in a paper titled "Calibrating Noise to Sensitivity in Private Data Analysis".


Basic Concepts
--------------

How does differential privacy work?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Differential privacy is achieved by adding a certain amount of noise to the result of a query. The amount of noise should be calculated in such a way that it is sufficient to mask the contribution of any single individual to the result of the query/function. However, note that adding too much noise is undesirable as it is detrimental for accuracy. Laplace noise is commonly used for this purpose. 
 
Parametrization of the noise
~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Depending on the sensitivity of the query, a privacy parameter called "epsilon" (ε) is defined. This parameter defines how much the query result may change when an individual is added to -- or removed from -- the dataset. The smaller ε, the more noise is added, and the stronger the privacy guarantees.
 
Privacy budget
~~~~~~~~~~~~~~
The privacy budget defines the maximal amount of information that can be disclosed. It becomes relevant when not one, but a sequence of queries/functions is executed on the dataset. In this case, the predefined privacy parameter ε represents the total privacy budget, which needs to be divided over the multiple queries. As each of the requests is only allowed a fraction of the total value of ε, the results of the queries will become nosier with an increasing amount of queries.

A simple example…
-----------------
 
Imagine a farm with hundreds of rabbits. Each day, the farmer feeds the rabbits as many carrots as they desire. In order to service the animals in the best way possible, the farmer frequently asks all rabbits to tell him how many carrots they ate that day. In order to keep track of their food intake, the rabbits created a database in which each rabbit has a record containing the amount of carrots it required that specific day. The rabbits are, however, skeptical to share this information as they fear that the ones requiring the most carrots will be removed from the pen and eaten by the farmer.  
 
Whenever the farmer requests the carrot data, the rabbits calculate the sum of all carrots. To protect themselves, they apply differential privacy and add noise to their result before sharing it with the farmer. While the results are accurate enough to ensure that all rabbits are fed adequately, the noise protects the sensitive data in the following ways: 
 
**Some rabbits told the farmer how much they eat.** Even if the farmer knows the amount of carrots that every other rabbit ate, he can still not deduce the amount of carrots eaten by the one unknown rabbit as a result of the noise that was added to the result.
 
**The farmer adds a new rabbit to the pen.** Similar to the previous case, because noise was added to current and previous results, the farmer cannot accurately deduce how many carrots the new rabbit eats. 
 
**Sometimes, a rabbit-friend from another farm comes by to play in secret.** Even this rabbit-friend can enter its data to the database. Because differential privacy is applied, the farmer has no way to deduce whether the data of the extra rabbit friend was part of the query result. 
 
*(inspired by Google: https://github.com/google/differential-privacy/blob/main/examples/cc/README.md)*
