## Advanced model deployment and monitoring
### Model Deployment Overview
Deployment options
![image](pic/deployment_options.png)



### Model Deployment Strategies
Blue/Green: shift all traffic to the new model
- Swap prediction request traffic
- Easy Rollback
![image](pic/blue_green.png)

Shadow/Challenger: run multiple versions in parallel with one serving live traffic
- Parallel prediction request traffic
- Validate new version without impact
![image](pic/shadow_challenger.png)

Canary: split traffic to compare model versions with target groups/users
- Split traffic
- Target smaller special userssss/groups
- Shorter validation cycles
- Minimize risk of low performing model
![image](pic/canary.png)

A/B
- Split traffic
- Target larger users/groups OR distribute % of traffic
- Longer validation cycles
- Minimize risk of low performing models

Multi-Armed Bandits (Dynamic Approach): Multi-armed bandits use reinforcement learning as a way to dynamically shift traffic to the winning model versions by rewarding the winning model with more traffic but still exploring the nonwinning model versions in the case that those early winners were not the overall best models. 
- Dynamic testing method for model version using Reinforcement learning
- Exploit & Explore
  - Exploit: reward the winning model with more traffic
  - Explore: continue to send traffic the the non-winning models in case behavior changes
![image](pic/mab.png)

### Amazon SageMaker Hosting: Real-Time Inference
Deploy models to serve predictions in real-time
- Optimized for low latency of model predictions
- Example: as product reviews are coming in through channels, you want to predict sentiment for immediate actions

#### Build in Algorithm: pre build code & serving container
![image](pic/build_in.png)
#### Bring your own container: bring your own code & custom container
![image](pic/own_container.png)
#### Autoscaling Endpoints: allows you to scale the number of machine learning instances that are hosting your endpoints up or down based on your workload demands.
- Ensure you can meet the demands of your workload
- Cost optimization
![image](pic/utoscaling_endspoints.png)
#### Multi-Model Endspoints: host multiple models behind a single endpoint
![image](pic/multi_model_endspoints.png)
#### Inference Pipeline:
Inference pipeline allows you to host multiple models behind a single endpoint. But in this case, the models are sequential chain of models with the steps that are required for inference. This allows you to take your data transformation model, your predictor model, and your post-processing transformer, and host them so they can be sequentially run behind a single endpoint.
![image](pic/inference_pipeline.png)

### Amazon SageMaker: Real-time Inference Production Variants
Product Variant:
A production variant is a package SageMaker model combined with the configuration that defines how that model will be hosted.
![image](pic/product_variant.png)


### Amazon SageMaker Batch Transform: Batch Inference
Package model
![image](pic/package_model.png)
Configure batch transformer job
![image](pic/configure_batch_transformer_job.png)
Start batch transform job

![image](pic/start_batch_transform_job.png)

### Model Integration: prepare data for inference in client application
Implement data transformations in client application
- difficult to scale and mange
- response may need to be transformed (1=>positive)
![image](pic/integration1.png)

Implement transformations code before calling hosted model
- need to ensure tranformation code stays in sync with training code
![image](pic/integration2.png)

Implement data transformers in Inference Pipeline
- keep training and inference code in sync
![image](pic/integration3.png)

### Monitoring ML Workloads
#### Why model monitoring: model degrade over time
![image](pic/model_monitor.png)
- Concept Drift
- Data Drift
![image](pic/concept_drift.png)
![image](pic/data_drift.png)


#### System monitoring: ensure your model and supporting resources are functioning as expected
- eg model latency, system metrics, ml pipeline

#### Monitoring Impact on Business Objectives: ensure your model ahs impact on business object

### Model Monitoring using Amazon SageMaker Model Monitor
![image](pic/monitor_type.png)

Data Quality Monitor
- Monitor when inference data drifts away from baseline(training) data
- Model Monitor uses, Deequ, an open source libaray built on Apache Spark
![image](pic/data_quality_monitor.png)

Model Quality Monitor
- Monitor model quality by comparing model predictions with ground truth labels

Statistical Bias Drift
- Monitor predictions for statistical bias
- Amazon SageMaker Clarify integrates with Amazon SageMaker Model Monitor to detect statistical bias drift

Feature Attribution Monitor
- Monitor features contributing to predictions over time
- Amazon SageMaker Clarify Clarify integrates with Amazon SageMaker Model Monitor to detect feature attribution drift
- Utilizes SHAP for baselining