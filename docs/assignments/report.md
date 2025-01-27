# Report

## Problem Statement

### What are you optimizing? (Be specific)
We aim to optimize the decision-making process for allocating renewable energy between a Battery Energy Storage System (BESS) and direct delivery to users within an energy grid. The objective is to maximize the amount of renewable energy being provided to the nodes demanding energy while ensuring minimal wastage and efficient energy storage for later use.

### Why does this problem matter?
Renewable energy production is inherently variable, influenced by weather and other environmental factors. Ensuring that renewable energy is consistently available to meet demand is critical for reducing reliance on non-renewable sources, lowering operational costs, and maintaining grid stability. This optimization is particularly important for transitioning to sustainable energy systems in areas dependent on renewable sources.

### How will you measure success?
Success metrics include:
1. **Energy Utilization**: Proportion of renewable energy effectively utilized.
2. **Demand Fulfillment**: Proportion of user demand met with renewable energy, especially during peak hours.
3. **Grid Stability**: Consistent energy supply without major fluctuations or outages.

### What are your constraints?
1. **Energy Produced**: Limited and variable based on renewable generation.
2. **Energy Demanded**: Dynamic, varying hourly and seasonally, potentially influenced by weather conditions.
3. **BESS Capacity**: Storage and charge/discharge limitations.

### What data do you need?
1. Weather data from the renewable energy production plants (e.g., solar and wind conditions).
2. Historical energy production data from the renewable energy plants.
3. Historical energy demand data from the state.
4. BESS specifications, including storage capacity, charge/discharge rates, and operational constraints.

### What could go wrong?
1. Poor allocation decisions leading to energy wastage or unmet demand.
2. Overloading or underutilizing the BESS, reducing its lifespan or operational efficiency.
3. Failure to account for variations in user energy demand due to weather conditions, leading to grid instability.
4. Inaccurate weather forecasts impacting energy production estimates.

## Technical Approach

### Mathematical Formulation
Objective function:
$$
\max \sum_{t} \Big( U_t(E_{direct}) + S_t(E_{BESS}) \Big)
$$
Subject to:
- $$ E_{direct} + E_{BESS} \leq E_{produced} $$: Total energy allocated cannot exceed renewable energy produced.
- $$ E_{direct} \leq E_{demanded} $$: Direct energy allocation must not exceed user demand.
- $$ E_{BESS} \leq \text{BESS capacity} $$: Energy stored in the BESS must respect its storage capacity.

Where:
- $$ U_t(E_{direct}) $$: Utility of energy delivered directly to users at time $$ t $$.
- $$ S_t(E_{BESS}) $$: Benefit of storing energy in the BESS at time $$ t $$.

### Algorithm/Approach Choice and Justification
A reinforcement learning (RL) approach was chosen for its adaptability to dynamic and stochastic environments. The RL agent can:
- Learn allocation policies through interaction with a simulated environment.
- Adapt decisions in real time based on energy generation, demand fluctuations, and BESS capacity constraints.

### PyTorch Implementation Strategy
1. Define the RL model architecture using `torch.nn.Module`, focusing on a policy network.
2. Simulate the grid environment, including renewable energy production, user demand (influenced by weather), and BESS dynamics.
3. Train the agent using Proximal Policy Optimization (PPO) for stable and efficient learning.
4. Evaluate the model on simulated and historical data to assess its performance under various scenarios.

### Validation Methods
1. Simulated scenarios using historical and synthetic data.
2. Evaluation metrics: Energy utilization, demand fulfillment, and grid stability.
3. Comparison with rule-based or heuristic allocation strategies to benchmark performance.

### Resource Requirements and Constraints
1. **Hardware**: Single GPU for model training and simulation.
2. **Software**: PyTorch, simulation libraries, and grid operation datasets.
3. **Time**: Real-time decision-making capability with sub-second latency for deployment.

## Initial Results

### TBD

## Next Steps

### TBD
