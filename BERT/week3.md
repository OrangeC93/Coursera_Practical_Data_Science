## MLOps Overview
Path to production for ML models:
- Machine learning development != Software development lifecycle
- A model may be a small part of an overall solution
- Mutiple personas spanning the MLDC
- Integration with traditional IT practice

Path to Prod:
![image](pic/path_to_prod.png)
Accelerate Path to Prod:
![image](pic/accelerate_path_to_prod.png)
Automation vs Orchestration
![image](pic/automation_orchestration.png)
Improve the quality of deployed models
![image](pic/automated_quality_gates.png)
## Creating ML Pipelines
#### Ingest & Analyze:
- It's generally recommended to establish a data lake that provides governed access to data scientists or automated processes. Take that raw data. And then transform it into a format that the algorithm can understand and that you can use for your model training or building activities.
![image](pic/pipeline_ingest.png)
- This allows data scientists to **quickly start** a model development activities, and it also ensures there's **traceability** for that data because you know which data scientists have checked out specific data sets. 
- This also allows you to create a model **retraining workflow** as well where the consumer in this particular case is the actual deployment pipeline or the machine learning pipeline, as opposed to the data scientist. 



#### Train & Tune:
Prepare Transform:
- data preprocessing & feature engineering
- data versioning
- data validation(data quality, data schema, statistical bias)
![image](pic/pipeline_train.png)

#### Deploy Models:
- model deployment & consumption
![image](pic/pipeline_deploy2.png)
  - This can take two different forms, you can either deploy in batch mode where you're basically wanting to send in batch records for prediction, and then receive batch responses back. Or you can deploy your model for a real-time or persistent endpont. An endpoint can consistently serve prediction requests and responses through a serving stack. And the serving stack typically includes a proxy, a web server, that can then accept and respond to your requests coming in on input. 
- logging & monitoring
![image](pic/pipeline_deploy.png)
- Additional_feedback_mechanism
![image](pic/additional_feedback_mechanism.png)
## Model Lineage & Artifact Tracking
Model Lineage:
- Model lineage essentially refers to understanding and tracking all of the inputs that were used to create a specific version of a model.
- For EACH version of a trained model: 
  - Versions of data used
  - Versions of code/hyperparameters used
  - Versions of algorithm/framework
  - Versions of training docker image
  - Versions of packages/libraries

Model Registry:
- A model registry is a central store for managing model metadata and model artifacts. 
- When you incorporate a model registry into your automated pipeline, it can provide traceability and auditability for your models, allowing you to effectively manage models, especially when you begin to manage at scale and you have tens or hundreds or even thousands of models.
- A model registry also gives you the visibility into how each of the model versions was built. It also typically includes other metadata, such as information about environments where a particular version of a model is deployed into. 
- Keep in mind though, that a model is one artifact that's produced as part of your machine learning pipelines. There's other outputs and artifacts that are produced that you also want to consider for complete end-to-end traceability. 

Aritifacts:
- Artifacts can be the output of a step or a task that can be consumed by the next step in your pipeline. Or they can even be deployed directly for consumption by other applications or systems.
![image](pic/artifacts.png)

## Amazon SageMaker Pipelines
SageMaker Pipelines has 3 components:
- pipeline, model registry, project
![image](pic/component.png)

Pipelines:
- Create pipelines to build and evaluate models
- Python SDK for building workflows
- Pipeline visualization available through Amazon SageMaker Studio
- Fully managed pipelines-no servers to manage

Model Registry:
- Catalog models for production
- Manage model versions & metadata
- Manage the approval status of a model
- Trigger model deployment pipeline

![image](pic/configure_pipeline.png)
