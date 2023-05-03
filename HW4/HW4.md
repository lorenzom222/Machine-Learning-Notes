## Question 1
1)
  - A: 2 (C, B)
  - B: 2 (C, A)
  - C: 5 (A, B, D, E, F)
  - D: 1 (C)
  - E: 2 (C, F)

2) E: (C, F)

3) $C_1$:{$A,B,C$} , $C_2$:{$C,F,E$} ,$C_3$: {$C,D$}
```
A --- B
 \   /
   C -- F
  / \  /
 D    E
```
4) 

```
       A--(F1)--B
           |
     (F3)--C--(F2)--F 
       |       |
       D       E
```
5)
- F1(A,B,C) = P(A)\*P(B)\*P(C|A,B) = P(A,B,C)
- F2(C,F,E) = P(E|C)\*P(F|C)\*P(C) = P(E,F|C)
- F3(C,D) = P(D|C)

## Question 2

## Question 3

## Question 4
1) $\mu_{E \rightarrow f3} = 1$
2) $\mu_{D \rightarrow f2} = 1$
3) $\mu_{f1 \rightarrow D} = \sum_{A,B}(\psi(A,B,D)) * \mu_{A \rightarrow f1}* \mu_{B \rightarrow f1})=\sum_{A,B}(\psi(A,B,D)$ 

- $\mu_{f1 \rightarrow D=0} = \psi(0,0,0)+\psi(0,1,0)+ \psi(1,0,0)+\psi(1,1,0)=0.62$
- $\mu_{f1 \rightarrow D=1} = \psi(0,0,1)+\psi(0,1,1)+ \psi(1,0,1)+\psi(1,1,1)=0.39$

$\therefore$  $\mu_{f1 \rightarrow D} = [0.62, 0.39]$

4) 
```math
P(D=0) = \Sigma_A \Sigma_B \Sigma_C \Sigma_E \psi_1(A,B,D=0) * \psi_2(C,D=0) *
\psi_3(D=0,E)
```

```math

P(D=1) = \Sigma_A \Sigma_B \Sigma_C \Sigma_E \psi_1(A,B,D=1) * \psi_2(C,D=1) *
\psi_3(D=1,E)
```


Substituting the values from the given tables, we get:

P(D=0) = (0.08+0.08+0.08+0.02) * 0.60 * (0.40+0.60) +
(0.40+0.05+0.06+0.24) * 0.40 * (0.90+0.10) P(D=1) =
(0.08+0.08+0.08+0.02) * 0.10 * (0.40+0.60) +
(0.40+0.05+0.06+0.24) * 0.90 * (0.90+0.10)

After calculating these values, we get:

P(D=0) = 1.056 P(D=1) = 1.584

Since these probabilities must sum to 1, we need to normalize them:

P(D=0) = 1.056 /  (1.056 + 1.584) ≈ 0.400 P(D=1) = 1 / (1 +
(1.056\slash 1.584)) ≈ 0.600

So, P(D=0) ≈ 0.400 and P(D=1) ≈ 0.600.


### Question 5

Directed graphical models, such as Bayesian networks, can be used to study Autism Spectrum Disorder (ASD) by identifying the causal relationships between different symptoms or characteristics of ASD. For example, a directed graphical model could be used to identify the causal relationships between social communication difficulties, repetitive behaviors, sensory sensitivities, and other symptoms of ASD. Consider a directed graphical model with the following variables:
```
PE --> ASD
       / | \
      /  |  \
     /   |   \
  V    V    V
SCD   RB   SS
```

* ASD (Autism Spectrum Disorder): The outcome variable of interest. This variable indicates the presence or absence of ASD.
* SCD (Social Communication Difficulties): This variable measures social communication difficulties, such as difficulties with nonverbal communication or social interactions. SCD is a potential predictor of ASD because individuals with ASD often have difficulties with social communication.
* RB (Repetitive Behaviors): This variable measures repetitive behaviors, such as repetitive movements or rituals. RB is a potential predictor of ASD because individuals with ASD often display repetitive behaviors.
* SS (Sensory Sensitivities): This variable measures sensory sensitivities, such as sensitivity to noise or light. SS is a potential predictor of ASD because individuals with ASD often have sensory sensitivities.
* PE (Pregnancy Environment): This variable measures the pregnancy environment, which could include factors such as exposure to alcohol, drugs, or environmental toxins, as well as genetic predisposition to ASD. PE is a potential predictor of ASD because the pregnancy environment may influence the probability of having ASD.
The conditional probability distributions (or potential functions) for this model can be defined as follows:
* P(ASD | PE): The probability of having ASD given the values of the predictor variable PE.
* P(SCD | ASD): The probability of having social communication difficulties given the presence of ASD.
* P(RB | ASD): The probability of having repetitive behaviors given the presence of ASD.
* P(SS | ASD): The probability of having sensory sensitivities given the presence of ASD.

This model can be used to answer a variety of questions related to ASD and its potential predictors, such as:
* How does the pregnancy environment influence the probability of having ASD?
* Can social communication difficulties, repetitive behaviors, or sensory sensitivities be used as early indicators of ASD?
* How do the different predictors interact to influence the probability of having ASD?
* How can interventions be tailored based on the specific combination of symptoms and predictors in individuals with ASD?

