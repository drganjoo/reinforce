# Reinforce Algorithm

## Toy Example

This is a toy example showing reinforce algorithm. The environment is seeded to 0 to always get the same steps

## Reinforce - Policy Gradient

Policy gradients also use a Neural Network but it is used as a policy rather than a Q table.

### Selecting an Action (Difference from DQN)
Both DQN and Policy Gradient use a neural network that has as many outputs as possible actions.

**DQN**: Given a state, the output from neural network represents the expected reward for each possible action. The action having the maximum reward is selected.

**Policy Gradient**: Given a state, the output from neural network represents the probability of choosing an action. The action is selected based on its probability (e.g. use PyTorch's Categorical.sample or Numpy's np.choice)

### Training Algorithm in Summary
Run for M episodes   
1. In each episode keep on saving: log probability (of choosing an action) and rewards:
2. Stop an episode when **maximum T steps** have been taken in an episode **or episode is done**.
3. Define **R** = Sum up discounted rewards for the episode
4. Multiply each saved `log_probability by -R` (*negative because we want to do gradient ascent not descent*)
5. Sum each of the `log_probability * -R` and call it policy_loss
6. Run *adam optimizer* on the policy_loss

Training Algorithm In Detail
Define a neural network and call it Policy

2. Run an episode and save log_probability and rewards
3. Sum up discounted rewards for the episode:
4. Multiply each log_reward by -R and then sum it up
5. Optimize policy_sum
Git Hub Implementation