# HMM
Model that helps us understand sequences of things we can't observe (directly see), but can indirectly. For example, we can observe the weather, but can't observe the process that leads to the weather changing (assuming we are meteorolgist).


## Markov chain 

Markov chain is a way to model a sequence of events where what happens next depends only on what's happening right now. The likelihood of what will happen next is based on the current state of the system and the probability of transitioning to the next state. This means that the future state of the system can be predicted based on the current state, and the past history of the system does not affect its future behavior.

This is mainly useful for computing probabilites for a sequence of observable events. 


### Markov Assumption
*Probabilty of what happens next depends on what is happening right now. Not what's in the past*

This is a way of simplifying the model by assume that future states only depend on it's current next state and on any past states. This helps by reducing amount of information necessary for predictions.

So for Markov Models, we use this:

```math
$P(q_i = a | q_1 ... q_{i-1}) = P(q_i = a | q_{i-1})$
```

or

```math
P(s_1s_2...s_n) = P(s_1) * P(s_2|s_1) * P(s_3|s_2) * ... * P(s_n|s_{n-1})
```
where $s_i$ represents the $i$-th state in the sequence and P($s_i$∣$s_{i−1}$) represents the transition probability from state $s_{i−1}$ to state $s_i$.


### Graphical Model for Markov
We can represent the model as a directed graph. 
- States as nodes
- Transitions as edges: probabilities, these leaving a node must sum to 1


| Math Definition | Text Description |
| --- | --- |
| $$Q = q_1q_2 . . . q_N$$ | a set of N states |
| $$A = a_{11}a_{12} . . . a_{n1} . . . a_{nn}$$ | a transition probability matrix A, each $a_{ij}$ representing the probability of moving from state i to state j, s.t. $\sum_{j=1}^n a_{ij} = 1 \forall i$ |
| $$\pi = \pi_1, \pi_2, ..., \pi_N$$ | an initial probability distribution over states. $\pi_i$ is the probability that the Markov chain will start in state i. Some states j may have $\pi_j = 0$, meaning that they cannot be initial states. Also, $\sum_{i=1}^N \pi_i = 1$ |


#### Example
$π = [0.1, 0.7, 0.2]$ for (a) would mean a probability 0.7 of starting in state 2 (cold), probability 0.1 of starting in state 1 (hot). Tranistion from hot to hot is 0.6. Tranistion from hot to cold is 0.1. Tranistion from cold to hot is 0.1 

(A.2) hot hot hot hot
```math
P(\text{hot hot hot hot}) = P(\text{hot}) * P(\text{hot}|\text{hot}) * P(\text{hot}|\text{hot}) * P(\text{hot}|\text{hot}) = 0.1 * 0.6 * 0.6 * 0.6 = 0.0216
```
(A.3) cold hot cold hot

```math
P(\text{cold hot cold hot}) = P(\text{cold}) * P(\text{hot}|\text{cold}) * P(\text{cold}|\text{hot}) * P(\text{hot}|\text{cold}) = 0.7 * 0.1 * 0.1 * 0.1 = 0.0007
```

This tell us that it is more likely for us to have 4 consecutive hot days than it is to have alternating cold and hot days.

## HMMs

Being interested in __hidden__ events, we need to do a little more than Markov Chains. 

### Hidden Layer
In this model, we assume that there is some underlying process (sequence of hidden states) that generates the observer. The hidden states can only be inferred from the observations we see.

For example speech recongition:

- Goal is to analyze a person's speech pattern.
- Can observe the sounds they make. (acoustic features of the speech signal, such as pitch, intensity, and duration)
- Can't observe the internal mental process that generates those sounds. (units are combined in specific ways to form words and phrases.)

HMM can be used to model the probabilty of . These units and the way they are combined are not directly observable but can be inferred from the observed speech signal.

### HMM Components

We will refer to the observation space, set of possible values for the observations in an HMM, as vocabulary $V$.

 Math Definition | Text Description |
| --- | --- |
| $$Q = q_1q_2 . . . q_N$$ | a set of N states |
| $$A = a_{11}a_{12} . . . a_{n1} . . . a_{nn}$$ | a transition probability matrix A, each $a_{ij}$ representing the probability of moving from state i to state j, s.t. $\sum_{j=1}^n a_{ij} = 1 \forall i$ |
| $$\pi = \pi_1, \pi_2, ..., \pi_N$$ | an initial probability distribution over states. $\pi_i$ is the probability that the Markov chain will start in state i. Some states j may have $\pi_j = 0$, meaning that they cannot be initial states. Also, $\sum_{i=1}^N \pi_i = 1$ |
| $$O = o_1, o_2, . . ., o_T$$ | a sequence of $T$ observation, each $o_t$ is drawn from a vocabulary $V = v_1, v_2, ..., v_V$ |
| $$B = b_i(o_t)$$ | a sequence of **observation likelihoods** aka **emission probabilties**. Represents the probabilty of an observation $o_t$ being generated from a hidden state i. |


#### Vocabulary: 

Think of it like rolling a die. Each time you roll the die, you get a number between 1 and 6. These numbers represent the possible values in the observation space. So, each time you roll the die, you are making an observation that is one of the possible values in the observation space. So $o_1 = v_1 = 1$.


#### Emission Probabilties
Probabilties of observing a specific observation given a specific hidden state. The term “emission probabilities” comes from the idea that the hidden states are emitting the observations. In other words, the observations are being generated by the hidden states. 

The hidden states could be “Hungry” and “Not Hungry”, and the observations could be “Crying” and “Not Crying”. The emission probabilities would represent the probability of observing the baby “Crying” or “Not Crying” given that the baby is “Hungry” or “Not Hungry”. We can not directly observe hunger but we can see crying.

For example, if the baby is “Hungry”, there might be a high probability that the baby will be observed “Crying”. On the other hand, if the baby is “Not Hungry”, there might be a low probability that the baby will be observed “Crying”

### Stages of HMMs
1. Inference: Given an HMM, $\lambda = (A, B)$ (A is *transition probability* matrix and B is *emission probability* matrix), and an observation sequence $O$, we need to determine the likelihood $P(O|\lambda)$
2. Decoding: Given an observation sequence $O$ and an HMM $λ = (A, B)$, discover the best hidden state sequence $Q$.
3. Learning: Given an observation sequence $O$ and the set of states
in the HMM, learn the HMM parameters $A$ and $B$.


#### Bishop
HMM $\lambda = (A, B)$ is also $\theta = {A, \pi, \phi}$ and $X = O$ for the observations is according to Bishop. $Z = Q$ for the hidden states, $B = \phi$.

1. Inference: $p(X|\theta)$ - find likelihood of a sequence
2. Decoding: $argsmax_zp(Z|X, \theta)$ - find most likely hidden states
3. Learning: - $argmax_{\theta}P(X|\theta)$ - find params w/max likelihood


## Likelihood Problem (Inference): The Forward Algorithm
*What is the probability of the sequence ...?*

For this task, we are interested in the **computing the likelihood** of a particular sequence.


- Example: We want to determine the probability of an ice-cream observation sequence like *3 1 3*, but we don’t know what the hidden state sequence is! Computing the probability of an observation sequence without knowing the hidden state sequence (the weather).
* This means that we need to consider all possible hidden state sequences and compute the probability of observing the ice-cream sequence 3 1 3 for each of them. 

- Simplier Example: Okay, assume we know where we know the weather (hidden state sequence ) like *hot hot cold* and we want the probability of an ice-cream observation sequence like *3 1 3*. Computing the output likelihood of an observation sequence given a known hidden state sequence.
* This means that we only need to consider a single hidden state sequence (e.g., *hot hot cold*) and compute the output likelihood of observing the ice-cream sequence *3 1 3* given this hidden state sequence.
    - Each hidden state only produces 1 observation -> Meaning hidden and observation state have same length
    - Given this 1:1 mappiing and Markov Assumption, likelihood sequence is:$P(O|Q) = Π^{T}_{i=1}P(o_i|q_i)$
    - $P(3, 1, 3| \text{hot} \text{hot} \text{cold}) = P(3|\text{hot}) \cdot P(1|\text{hot}) \cdot P(3|\text{cold})$

The simplier example is nice, but of course we aren't going to actually know the hidden state sequence. So are going to need to: 1. Consider all the hidden sequences, 2. Compute the probability of observing an observation sequence for each hidden sequence. For our example, we need to compute the probabilty of the ice-cream (observation) events $3 1 3$ instead by summing over all possible weather (hidden) sequences, weighted by their probabilty.

1. We compute the joint probabilty of being in a particular weather (hidden) sequence $Q$ and generating a particular ice-cream(observation) sequence $O$:

$P(O, Q)=P(O|Q)* P(Q) = Π^{T}_{i=1}P(o_i|q_i) * Π^{T}_{i=1}P(q_i|q_{i-1)$

**NOTE**

<sub>The joint probability P(O, Q) can be computed as the product of two terms: the conditional probability of observing the observation sequence O given the hidden state sequence Q, denoted by P(O|Q), and the prior probability of the hidden state sequence Q, denoted by P(Q).<sub>

<sub>The conditional probability P(O|Q) can be computed as the product of the individual observation probabilities P(o_i|q_i) for each time step i. This represents the probability of observing the ice-cream event o_i at time step i given that the weather is q_i at time step i.<sub>

<sub>The prior probability P(Q) can be computed as the product of the individual state transition probabilities P(q_i|q_{i-1}) for each time step i. This represents the probability of transitioning from weather q_{i-1} at time step i-1 to weather q_i at time step i.<sub>

<sub>By multiplying these two terms together, we obtain the joint probability of being in a particular hidden state sequence Q and generating a particular observation sequence O.<sub>







## References
- https://criss-wang.github.io/post/blogs/hidden-markov-models/
- https://web.stanford.edu/~jurafsky/slp3/A.pdf