========================
Dataset Anonymization
========================

Unlike differential privacy, which acts on functions or queries on databases, dataset anonymization impacts the dataset itself. The goal of the anonymization process is to create a new, modified version of the dataset that can be shared with third parties without revealing sensitive information about specific individuals.

Types of attributes
-------------------
Before we can dive deeper into the techniques enabling dataset anonymization, first a distinction needs to be made between four different types of attributes: identifying attributes, quasi-identifying attributes, sensitive attributes and insensitive attributes.

- **Identifying attributes** directly identify an individual within a dataset. Examples are the name, social security number and email address. When anonymizing data, these attributes should always be removed.

- **Quasi-identifying attributes** do not directly identify an individual. However, they contain information that, combined with other (quasi-identifying) attributes can be used to identify an individual. Examples are ZIP-code, age, gender and occupation. Because of the potential to combine these attributes, operations on these attributes are required to guarantee the privacy of the individuals in the dataset (see next section)

- **Sensitive attributes** contain information that is personal or confidential. Disclosing these attributes can negatively impact an individual (e.g. blackmail). Examples are medical conditions, financial data and criminal records. It is often desirable to protect individuals in the dataset against attribute linkage. This means that it should be prevented that a sensitive attribute value can be linked to an individual with certainty.

- **Insensitive attributes** are attributes that are harmless to disclose as they contain no personal or confidential information and do not contribute to identifying a person. Examples are a favorite book or movie, sport interests and music preferences. Caution needs to be taken that, when classifying an attribute as insensitive, it cannot be linked with other data to aid in re-identification of an individual. In case of doubt, it is better to categorize an attribute as quasi-identifying. 

Anonymization tactics: Generalization and suppression
-----------------------------------------------------
The previous section established that quasi-identifying attributes require processing to prevent re-identification attacks. In general, two key techniques are combined to achieve this namely generalization and suppression.

**Generalization** involves replacing specific values or attributes in the data with a less-precise representation of that value. It helps to make individuals in the dataset less unique but comes at the cost of detail (and thus data utility). 

Some examples: 

- | The attribute age can be generalized by replacing the exact age with a rage of ages. 
  | *Example: age 21 can first be generalized in ranges of size 5 (20 to 25) and further in ranges of 10 (20 to 30) or 20 (20 to 40) if required.*

- | The attribute ZIP-code can be generalized by increasingly masking (replacing with an asterisk \*) digits. 
  | *Example: ZIP-code 9820 can be generalized into 982\*, and further into 98\*\* and even 9\*\*\*.*

**Suppression** removes specific data records. When a record is too unique in a dataset, it is sometimes impossible to ensure sufficient privacy guarantees, even after generalization. In this case, the record needs to be removed from the dataset completely to prevent re-identification of that respective individual. 

Privacy models
--------------
When sharing data, strong privacy guarantees (i.e. a minimal privacy level for each individual in the dataset) are desirable. To achieve these strong guarantees, generalization and suppression are combined to apply privacy models to a dataset. The most well-known and often-used privacy model is k-anonymity. 

K- anonymity.
~~~~~~~~~~~~~
The k-anonymity privacy model states that -- when considering the quasi-identifying attributes -- every individual in the dataset should be indistinguishable from at least k – 1 other individuals. K-anonymity is achieved by finding a balance between generalizing attributes (up to a certain level) to form groups of (at least) k records and suppressing the records which do meet the required group size. A group of at least k records is called an equivalence class. 

While k-anonymity provides protection against direct record linkage between a record and an individual, certain risks remain. For instance, every record in an equivalence class could have the same value for a sensitive attribute. While an attacker cannot map the individual to one specific record in that equivalence class, he is able to deduce the value of the sensitive attribute as they are all equal. Other privacy models – such as l-diversity -- aim to solve this kind of problems. 

L-diversity.
~~~~~~~~~~~~~
This privacy model is used in combination with k-anonymity. It adds the additional constraint that each equivalence class should at least show l different values for each sensitive attribute. This way, an attacker cannot make the aforementioned sensitive attribute deduction anymore. The l-diversity privacy model is also achieved by generalizing records. In many cases, harsher generalizations are required to fulfill the requirement of having l sensitive attribute values in each equivalence class. 

Other models.
~~~~~~~~~~~~~
Many more privacy models exist. Examples are t-closeness, β-Likeness and δ-Presence. Each of these models boasts different constraints to which the resulting datasets should adhere. Note that harsher constraints, while providing increased and stronger privacy guaranties, could have a detrimental impact on the utility of the resulting anonymized dataset.

ARX – a tool for data anonymization
-----------------------------------
Tool support exists to help users to anonymize data. Without this tool support, finding a suitable (i.e., with a good balance of privacy) combination of generalization and suppression would be like trying to find a needle in a haystack. One of the most well-known tools for data anonymization is the ARX Data Anonymization Tool, developed by Fabian Prasser et. al. at the Berlin Institute of Health. 

The remainder of this section provides a short overview of how the tool works, for more information and an in-depth guide, we refer you to the resources section, which links to an ARX tutorial we created in the context of this project. 

- **STEP 1: Load the data in the tool.** The tool supports a variety of data formats such as .csv and .xlsx, and even allows direct connections to a set of database technologies. 
- **STEP 2: categorize the attributes.** After the data is loaded in the tool, the user must categorize each attribute in one of the four attribute types: identifying, quasi-identifying, sensitive and insensitive attributes. 
- **STEP 3: provide the tool with generalization hierarchies.** The tool needs information on how it is expected to generalize the quasi-identifying attributes. For each quasi-identifying attribute, the user must provide a generalization hierarchy.  This can be represented as a tree structure that gives the tool multiple options (low to harsh generalizations) on how to generalize each quasi-identifying attribute. The tool has a wizard for this, but also allows users to load their own hierarchies using a .csv file. 
- **STEP 4: select and apply the desired privacy model and other settings.** The tool supports a wide range of privacy models and other settings (such as limiting the number of suppressed records or giving weights of importance to attributes).  
- **STEP 5: Let the tool do the work.** After all settings are applied by the user, the tool returns the anonymized dataset within seconds. The user is presented with an exhaustive overview of all privacy and utility related characteristics of the dataset, and can, if required adjust the anonymization parameters. 
