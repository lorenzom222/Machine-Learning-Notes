## EM Algorithm

Expectation: Q($\theta$, $\theta^{old}$) = sum for all **Z** of the product of p(**Z**, **X**, $\theta^{old}$) and the natrual log of p(**Z**, **X**, $\theta$)

- p(**Z**, **X**, $\theta$): Joint distribution 
- **X**: Observed variables
- **Z**: Latent variable
- $\theta$: Governing variable

Goal: *Maximize p(__X__, $\theta$) wrt $\theta$*


1. init: Choose an initial setting for the param $\theta^{old}$
2. E-step: Evaluate p(**Z**, **X**, $\theta$)
3. M-step: Evaluate $\theta^{new}$ 
	- Given by:  $\theta^{new}$ argmax$Q(\theta,  \theta^{old})$
	- where Q is the expectation as stated before

- repeat 2 & 3


## Exam 2:
Understand Metal-Level EM:

- Convergence
- GMMs & HMMs

- HMMS: Know the general model
	- init: Transition Emission
	- Foward/Backwards (aka D-Step)
	- EM
