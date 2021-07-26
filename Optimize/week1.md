## Advanced Model Traning and Tuning
#### Popular Algorithms for Automatic Model Tuning
Grid search
- Define sets of hyperparameters
- Test **every** combination
- Select the best performing hyperparameters
- **Doesn't scale to large numbers of parameters**

Random search
- Define sets of hyperparameters
- Define search speace and stop criteria
- Test random combination within search space
- Select the best performing hyperparameters
- **Faster but might miss better performing hyperparameters**

Bayesian optimization
- Treat HPT like a regression problem(surrogate model)
- Start from random hyperparameters
- Narrow down searh space around better performing hypterparameters
- **More efficient in finding best hyperparameters**
- **Requires sequential execution**
- **Might get stuck in local minima**

Hyperband
- Bandit-based approach
- Start from random hyperparameters
- Explore sets of hyperparameters for few iterations
- Choose best and explore longer
- Repeat until max_iterations reched or one candidate left
- **Spend time efficient, might discard good candidates early that converge slowly**

AWS SageMaker Hyperparamter Tuning(HPT)
![image](/pic/aws_hpt.png)
