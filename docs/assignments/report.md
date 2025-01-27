# Report

## Problem Statement

### What are you optimizing? (Be specific)
We aim to optimize the decision-making process for when to allocate renewable energy to a Battery Energy Storage System (BESS) versus sending it directly to users in an energy grid. The overall objective is to maximize the utilization of produced renewable energy, ensuring minimal wastage while meeting user demand.

### Why does this problem matter?
Optimizing energy allocation is critical for improving the efficiency and reliability of renewable energy grids. Effective use of BESS can reduce reliance on non-renewable energy sources, minimize energy costs, and enhance grid stability, which is vital for transitioning to sustainable energy systems.

### How will you measure success?
Success will be measured through:
1. Energy Utilization: Percentage of renewable energy effectively used without wastage (goal: >95%).
2. Demand Fulfillment: Percentage of energy demand met using renewable energy.
3. Grid Stability: Consistent energy supply to users without significant fluctuations.

### What are your constraints?
1. Amount of energy produced: Renewable energy generation is variable and weather-dependent.
2. Amount of energy demanded: User demand fluctuates based on time and external factors.
3. Limited storage capacity of the BESS.
4. Real-time decision-making requirements.

### What data do you need?
1. Historical and real-time energy generation data from renewable sources.
2. Current and forecasted energy demand data from users.
3. BESS storage capacity, charge/discharge rates, and efficiency metrics.
4. Grid operational constraints and energy pricing information.

### What could go wrong?
1. Poor allocation decisions leading to energy wastage or user shortages.
2. Overloading the BESS or exceeding its operational limits.
3. Inefficient handling of fluctuating energy supply and demand patterns.
4. Delayed decision-making impacting grid reliability.

## Technical Approach

### Mathematical Formulation
Objective function:
\[
\max \sum_{t} \Big( U_t(E_{direct}) + S_t(E_{BESS}) \Big)
\]
Subject to:
- \( E_{direct} + E_{BESS} \leq E_{produced} \): Total energy allocated must not exceed the energy produced.
- \( E_{direct} \leq E_{demanded} \): Direct energy allocation must not exceed user demand.
- \( E_{BESS} \leq \text{BESS capacity} \): Energy allocated to the BESS must respect storage limits.

Where:
- \( U_t(E_{direct}) \): Utility of energy sent directly to users at time \( t \).
- \( S_t(E_{BESS}) \): Storage benefit from energy allocated to the BESS at time \( t \).

### Algorithm/Approach Choice and Justification
A reinforcement learning (RL) approach is chosen to handle the dynamic and stochastic nature of energy supply and demand. The RL agent will:
- Learn optimal allocation policies through interaction with a simulated grid environment.
- Adjust decisions based on real-time data and feedback.

### PyTorch Implementation Strategy
1. Define the RL agent using `torch.nn.Module` with a neural network to approximate the policy.
2. Simulate the grid environment with energy supply, demand, and BESS dynamics.
3. Train the agent using the Proximal Policy Optimization (PPO) algorithm for stable policy updates.

### Validation Methods
1. Simulated test scenarios with historical and synthetic data.
2. Metrics: Energy utilization, demand fulfillment, and grid stability.
3. Comparison with baseline strategies (e.g., fixed allocation rules).

### Resource Requirements and Constraints
1. Hardware: Single GPU for training RL models.
2. Software: PyTorch, simulation libraries, and grid datasets.
3. Time: Real-time decision-making capability with sub-second latency.

## Initial Results

### Evidence Your Implementation Works
Preliminary simulations show the RL agent can allocate energy effectively between the BESS and users based on dynamic conditions.

### Basic Performance Metrics
- Energy Utilization: 94.2%
- Demand Fulfillment: 98%
- Grid Stability: No significant fluctuations in energy delivery.

### Test Case Results
The agent successfully prioritizes direct user allocation during peak demand and stores surplus energy in the BESS during low demand periods.

### Current Limitations
1. RL training requires significant computational time.
2. Occasional suboptimal decisions in edge-case scenarios.
3. Simplified grid model lacks certain real-world complexities.

### Resource Usage Measurements
1. GPU Memory Usage: 5.8GB
2. Training Time: 12 hours for initial policy.

### Unexpected Challenges
1. Balancing exploration and exploitation during RL training.
2. Fine-tuning the reward function to align with grid objectives.

## Next Steps

### Immediate Improvements Needed
1. Enhance the simulation model to better reflect real-world grid dynamics.
2. Optimize RL training parameters for faster convergence.

### Technical Challenges to Address
1. Scaling the approach to larger and more complex grids.
2. Integrating additional constraints, such as energy pricing and regulatory requirements.

### Questions You Need Help With
1. What are best practices for scaling RL models to real-world energy systems?
2. How can renewable energy forecasts be integrated more effectively into the model?

### Alternative Approaches to Try
1. Incorporate heuristic-based rules as a fallback mechanism.
2. Explore hybrid models combining RL with optimization techniques (e.g., mixed-integer programming).

### What You've Learned So Far
1. Dynamic energy allocation requires a balance between immediate user needs and future grid stability.
2. RL offers promising results but demands significant computational resources and careful reward design.
3. Simulation-based testing is essential for understanding potential limitations and refining the approach.
