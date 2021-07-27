## Advanced model deployment and monitoring
### Model Deployment Overview
Deployment options
![image](pic/deployment_options.png)

#### Model Monitoring using Amazon SageMaker Model Monitor
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

#### Model Deployment Strategies
Blue/Green: shift all traffic to the new model
- Swap prediction request traffic
- Easy Rollback
![image](pic/blue_green.png)

Shadow/Challenger: run multiple versions in parallel with one serving live traffic
- Parallel prediction request traffic
- Validate new version without impact
![image](pic/shadow/challenger.png)

Canary: split traffic to compare model versions with target groups/users
- Split traffic
- Target smaller special userssss/groups
- Shorter validation cycles
- Minimize risk of low performing model
![image](pic/shadow/canary.png)

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
![image](pic/shadow/mab.png)
