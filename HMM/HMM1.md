# HMM
Model that helps us understand sequences of things we can't observe (directly see), but can indirectly. For example, we can observe the weather, but can't observe the process that leads to the weather changing (assuming we are meteorolgist).

## Hidden Layer
In this model, we assume that there is some underlying process (sequence of hidden states) that generates the observer. The hidden states can only be inferred from the observations we see.

For example speech recongition:

- Goal is to analyze a person's speech pattern.
- Can observe the sounds they make. (acoustic features of the speech signal, such as pitch, intensity, and duration)
- Can't observe the internal mental process that generates those sounds. (units are combined in specific ways to form words and phrases.)

HMM can be used to model the probabilty of . These units and the way they are combined are not directly observable but can be inferred from the observed speech signal.


## Markov Assumption
*Probabilty of what happens next depends on what is happening right now. Not what's in the past*

This is a way of simplifying the model by assume that future states only depend on it's current next state and on any past states. This helps by reducing amount of information necessary for predictions.

So for Markov Models, we use this:

```math
$P(q_i = a | q_1 ... q_{i-1}) = P(q_i = a | q_{i-1})$
```

## Graphical Model for Markov
We can represent the model as a directed graph. 
- States as nodes
- Transitions as edges: probabilities, these leaving a node must sum to 1


| Math Definition | Text Description |
| --- | --- |
| $$Q = q_1q_2 . . . q_N$$ | a set of N states |
| $$A = a_{11}a_{12} . . . a_{n1} . . . a_{nn}$$ | a transition probability matrix A, each $a_{ij}$ representing the probability of moving from state i to state j, s.t. $\sum_{j=1}^n a_{ij} = 1 \forall i$ |
| $$\pi = \pi_1, \pi_2, ..., \pi_N$$ | an initial probability distribution over states. $\pi_i$ is the probability that the Markov chain will start in state i. Some states j may have $\pi_j = 0$, meaning that they cannot be initial states. Also, $\sum_{i=1}^N \pi_i = 1$ |



