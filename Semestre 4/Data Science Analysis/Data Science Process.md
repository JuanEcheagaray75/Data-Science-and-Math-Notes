# Data Science Process (Life-cycle) 

---

1. [[#Basic life-cycle|Basic life-cycle]]
1. [[#CRISP-DM Cross-industry standard process for data mining|CRISP-DM Cross-industry standard process for data mining]]
	1. [[#Business understanding|Business understanding]]
	1. [[#Data understanding|Data understanding]]
	1. [[#Data preparation|Data preparation]]
	1. [[#Modeling|Modeling]]
	1. [[#Evaluation|Evaluation]]
	1. [[#Deployment|Deployment]]
1. [[#KDD Knowledge discovery in databases|KDD Knowledge discovery in databases]]
1. [[#SEMMA Sample, Explore, Modify, Model and Assess|SEMMA Sample, Explore, Modify, Model and Assess]]
1. [[#Microsoft: The Team Data Science Process Life Cycle|Microsoft: The Team Data Science Process Life Cycle]]
	1. [[#Business understanding|Business understanding]]
	1. [[#Data acquisition and understanding|Data acquisition and understanding]]
	1. [[#Modeling|Modeling]]
	1. [[#Deployment|Deployment]]
	1. [[#Customer acceptance|Customer acceptance]]

---

## Basic life-cycle

- Setting the research goal: to establish the research goal, how the company will benefit, what data resources are needed, a timetable and deliverables
- Retrieving data: checking the existence of, quality and access to the data
- Data preparation
	- Data cleansing: remove false values and inconsistencies
	- Data integration: combining information from multiple data sources
	- Data transformation: ensures that the data is in a suitable format for use in models
- Data exploration: building a deeper understanding of the data, understand how the variables interact with each other, check the distribution of the data, find outliers and so on. This is usually done through descriptive statistics, visualizations and simple models. This process is also called **EDA** (Exploratory Data Analysis)
- Data modeling: use of models, domain knowledge and insights about the data to answer the research question
- Presentation and automation: present results to the business and sometimes automate the use of your model

![[Pasted image 20220220181745.png]]

---

## CRISP-DM Cross-industry standard process for data mining

### Business understanding

What does the business need?
	1. Determine business objectives: understand what the customer is trying to achieve
	2. Assess situation: determine resources availability, project requirements, risks and contingencies
	3. Determine project goals: define what success looks like from a technical perspective
	4. Produce project plan: select technologies and tools and define a plan for each of the next stages
	
### Data understanding

What data do we have / need? Is it clean?
	1. Collect initial data: acquire the necessary data
	2. Describe data: examine the data and document its surface properties
	3. Explore data: dig deeper into the data, query it and visualize it
	4. Verify data quality: document any quality issues
	
### Data preparation

How do we organize the data for modeling?
	1. Select data: determine which data sets will be used and document reasons
	2. Clean data: correct, impute or remove erroneous values
	3. Construct data: derive new attributes that will be helpful
	4. Integrate new data: create new datasets by combining data from multiple sources
	5. Format data: reformat data as necessary, eg. convert string values that store numbers to a numeric format

### Modeling

What modeling techniques should we apply?
	1. Select modeling techniques: determine which algorithms to try
	2. Generate test design: split the data into 2, a training set and a test set
	3. Build model: eg. `lreg = LinearRegression.fit(X, y)`
	4. Assess model: interpret the model results based on domain knowledge, the predefined success criteria and the test design
	
### Evaluation

What best meets the business objectives?
	1. Evaluate results: Do the models meet success criteria?
	2. Review process: Summarize findings and correct anything if needed
	3. Determine next steps: determine whether to proceed to deployment, iterate further or initiate new projects (_fancy words for surrendering_)
	
### Deployment

How do stakeholders access the results
	1. Plan deployment: develop and document a plan for deploying the model
	2. Plan monitoring and maintenance
	3. Produce final report: summarize the project, it might include a presentation of the project's results
	4. Review project: conduct a project retrospective about the overall performance of the project

![[Pasted image 20220220224300.png]]

---
## KDD Knowledge discovery in databases

- Selection: determine the targeted data, and choose the variables that will be used
- Pre-processing: improving the data and cleaning it
- Transformation: converting the pre-processed data to be fully utilizable
- Data mining: sifting through the transformed data to unveil hidden patterns. These patterns are then graphed and visualized. This step also includes grouping, clustering and regression
- Interpretation/evaluation: the data is handed off for interpretation and documentation

---

## SEMMA Sample, Explore, Modify, Model and Assess

- Sample
	- Choose a subset of the whole dataset
	- Identify variables and factors that influence the process
	- Separate the data into preparation and validation categories
- Explore
	-  Univariate: to look at each factor individually and understand its part in the whole
	-  Multivariate: study the interconnections between data elements
	-  Data visualization
- Modify
	- Data parsing and cleaning
- Model
	- Use of a wide range of modeling techniques to produce a model that describes how the data achieves the business goal
- Assess
	- Evaluate how useful the model is for the business. Evaluate its efficiency and performance

https://www.datascience-pm.com/semma/

---

## Microsoft: The Team Data Science Process Life Cycle
<!--- So far my favorite --->

> This life cycle is designed for data-science projects that are intended to ship as part of intelligent applications.

![[Pasted image 20220221233608.png]]

### Business understanding

- Goals
	- Specify the key **model targets** (target variables for models) and their metrics. Can we call them KPIs?
	- Identify relevant data sources
- Tasks
	- Define objectives: understand and identify the business problem. Formulate specific research goals
		- Central objective
		- Project goals
		- Define the project team and their roles
		- Define the success metrics (**SMART** metrics)
	- Identify data sources: find relevant data to answer the business problem
		- Data that's relevant to the question
		- Data that's an accurate measure of the **model target**
- Deliverables
	- Charter document
	- Data sources
	- Data dictionaries: provides a description of the data

### Data acquisition and understanding

- Goals
	- Produce clean high-quality data
	- Develop a solution architecture for a data pipeline
- Tasks
	- Ingest the data: move the data from the source locations to where your analytics operations will be performed
	- Explore the data
		- Use data summarization and visualization to audit the quality of the data
		- Perform an EDA to develop a strong understanding of the data
	- Set up a data pipeline: to set up a process to score new data (refreshing)
		- Batch based
		- Streaming or real time
		- Hybrid
- Deliverables
	- Data quality report
	- Solution architecture: description of the data pipeline
	- Checkpoint decision: before diving further, check if you have enough data, reevaluate the project. It's usually more expensive to correct data needs by the end of the project, invest a little more into collecting more and higher quality data from the very beginning

### Modeling

- Goals
	- Determine optimal data features
	- Create an _informative_ ML model
	- Create a ML model suitable for production
- Tasks
	- Feature engineering: inclusion, aggregation and transformation of raw variables to create new features to be used on the analysis, understand how the features relate to each other
	- Model training: there are many modeling algorithms available, choose the one that performs the best
		- Split the input data into _train_ and _test_ subsets
		- Build the models using the _training_ set
		- Evaluate the model. Do not stop with one iteration, try diverse ML models
		- Determine the best model based on some type of performance metric
	- Model evaluation
		- Checkpoint decision: evaluate whether the model performs sufficiently well for deployment 
		- Interpreting the model: explain the model behavior, enable interpretability techniques
		- Assessing fairness: make sure that there is no bias in the data, and therefore bias in the model

### Deployment

- Goal
	- Deploy models with a data pipeline to a production environment for customer acceptance
- Task
	- Operationalize the model: operationalize them for other apps to consume, you may need real time predictions or on a batch basis
- Deliverables
	- Dashboard
	- Modeling report
	- Final solution architect

### Customer acceptance

- Goal: finalize project deliverables. Make sure that the pipeline, the model and the deployment satisfy the customer's needs
- Tasks
	- System validation: confirm that the deployed model and pipeline satisfy the customer's needs
	- Project hand-off
- Deliverable: exit report

For more in depth documentation, please visit https://docs.microsoft.com/en-us/azure/architecture/data-science-process/lifecycle

---