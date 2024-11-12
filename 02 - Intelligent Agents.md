# Intelligent Agents

- Anything that **perceives** its **environment** through **sensors** and acts upon that environment through **actuators**.

## Agent Function

- A mathematical function that maps from _percept sequence_ to an action.
  - **Percept**: the agent's perceptual inputs at any given instant.
  - **Percept sequence**: the complete history of everything the agent has ever perceived.
- **Agent program**: an implementation of the agent function.

## Rational Agent

- An agent that does the right thing.
- The right thing depends on:
  - The **performance measure** that defines what is desirable.
  - The **agent's prior knowledge** of the environment.
  - The **actions** that the agent can perform.
  - The **percepts** that the agent receives.

## Performance Measures

- **Consequantialism**: the right action is the one that leads to the best outcome.
- The performance measure for an agent must be designed on what is desirable in the environment not on how to achieve it.

## Rationality

- **Perfect rationality**: the agent knows the outcome of each possible action and chooses the best one.
- **Bounded rationality**: the agent chooses the best action given the information it has.

## Omniscience, Learning, and Autonomy

- **Omniscience**: an agent that knows the actual outcome of its actions.
- **Learning**: an agent that improves its performance over time.
- **Autonomy**: How much the agent's actions are determined by its own experience, rather than by its designers.

## Task Environments

- Defines the problems and criteria for a rational agent.
- When designing an agent, try to specify the task environment as fully as possible.

### Fully Observable vs. Partially Observable

- **Fully observable**: the agent's sensors give it access to the complete state of the environment at each point in time.
- **Partially observable**: the agent's sensors give it access to only a partial state of the environment.

- Only need to consider aspects of the environment that are relevant to the agent's decision-making.
- Environment can be partially observable because:
  - Sensors are noisy/inaccurate.
  - No way to sense the environment completely.

### Single Agent vs. Multiagent

- **Single agent**: the agent is the only entity acting in the environment.
- **Multiagent**: other agents are acting in the environment.

- Multiagent environments can be:
  - **Competitive**: agents are in competition with each other.
  - **Cooperative**: agents are working together.

### Deterministic vs. non-deterministic vs. Stochastic

- **Deterministic**: the next state of the environment is completely determined by the _current state_ and the _action executed_ by the agent.
- **Non-deterministic**: the next state of the environment is not completely determined by the _current state_ and the _action executed_ by the agent nor the probability of each possible outcome.
- **Stochastic**: the next state of the environment is a probabilistic function of the _current state_ and the _action executed_ by the agent.

### Episodic vs. Sequential

- **Episodic**: the agent's experience is divided into episodes. Episoides are exclusive sequences of percepts and actions that does not depend on previous episodes.
- **Sequential**: the agent's experience is a single continuous stream of percepts and actions. The current decision depends on the previous decisions.

- Episodic environments are easier to deal with because the agent can forget everything after each episode. No think ahead is required either.

### Static vs. Dynamic

- **Static**: the environment does not change while the agent is deciding what to do.
- **Dynamic**: the environment changes while the agent is deciding what to do.

### Discrete vs. Continuous

- **Discrete**: there are a limited number of distinct, clearly defined states.
- **Continuous**: there are an infinite number of states.

### Examples

- **Chess**:

  - **Fully observable**: the state of the board is completely visible.
  - **Deterministic**: the next state of the board is completely determined by the current state and the action taken.
  - **Sequential**: the current decision depends on the previous decisions.
  - **Static**: the board does not change while the agent is deciding what to do.
  - **Discrete**: there are a limited number of distinct, clearly defined states.

- **Taxi driver**:
  - **Partially observable**: the driver cannot see the entire city.
  - **Stochastic**: the traffic is unpredictable yet there are probabilities of each possible outcome.
  - **Sequential**: the current decision depends on the previous decisions.
  - **Dynamic**: the traffic changes while the driver is deciding what to do.
  - **Continuous**: there are an infinite number of states.

## Agent Structure

- _Agent = Architecture + Program_
- **Architecture**: the machinery that the program runs on.
- **Program**: the implemented agent function.

## Types of Agents

### Simple Reflex Agents

- Selects actions based only on the current percept.
- Used when,
  - Environment is fully observable.
  - Actions are governed by simple condition-action rules.
- **Condition-action rule**: if _condition_ then _action_.

![Simple Reflect Agents](images/Simple%20Reflect%20Agent.png)

### Model-Based Reflex Agents

- Keeps track of the state of the world by updating an internal model.
- Used when,
  - Environment is partially observable.
  - Actions are governed by stateful condition-action rules.

![Model-Based Reflex Agents](images/Model-Based%20Reflex%20Agents.png)

### Goal-Based Agents

- Given a goal, the agent searches for a sequence of actions that will achieve the goal.
- Used when,
  - The agent has a goal.
  - The agent can plan ahead.
- vs. Reflex agents:
  - Reflex agents are less flexible because they cannot plan ahead.
  - Goals are more general than condition-action rules.
  - Goals are easier to change than condition-action rules.

![Goal-Based Agents](images/Goal-Based%20Agents.png)

### Utility-Based Agents

- Given a utility function, the agent maps from states to real numbers.
- Used when,
  - Conflicting goals. (Utility function can be used to balance them.)
  - Choosing the best-fit out of many possible goals.

![Utility-Based Agents](images/Utility-Based%20Agents.png)

### Learning Agents

- The agent learns from its experience and tries to improve its performance over time.
- **Performance element**: selects external actions and give data to the learning element.
- **Critic**: gives feedback on how well the agent is doing.
- **Learning element**: improves the agent's performance based on the critic's feedback and data from the performance element.
- **Problem generator**: suggests exploratory actions that will lead to new and informative experiences.
- **Exploration vs. Exploitation**: the agent must balance between trying new things and exploiting what it already knows.
- Actions might be suboptimal in the short term but optimal in the long term.
- Used when,
  - The agent has to adapt to a changing environment.
  - The agent has to improve its performance over time.

![Learning Agents](images/Learning%20Agents.png)

## Componets of agent programs

![Agent Program Representations](images/Agent%20Program%20Representations.png)

### Atomic Representation

- State is represented as a single entity.
- Algorithms used:
  - **Standard search algorithms**: used to find the best action given the current state of the environment.
  - **Hidden Markov Models**: used to predict the next state of the environment.
  - **Markov Decision Processes**: used to find the best action given the current state of the environment.

### Factored Representation

- State consists of multiple variables.
- Algorithms used:
  - **Constraint satisfaction algorithms**: used to find the best action given the current state of the environment.
  - **Bayesian networks**: used to predict the next state of the environment.
  - **Machine learning algorithms**: used to find the best action given the current state of the environment.

### Structured Representation

- State includes objects and relationships between them.
- Algorithms used:
  - **First-order logic**: used to find the best action given the current state of the environment.
  - **First-order probabilistic models**: used to predict the next state of the environment.
