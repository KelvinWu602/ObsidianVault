#machine-learning 

```mermaid
flowchart TB
	DNN --> vanishing-gradient
	DNN --> faster-convergence
	DNN --> robust-model

	vanishing-gradient --> better-activation
	vanishing-gradient --> weight-init
	vanishing-gradient --> batch-norm

	faster-convergence --> optimizers

	robust-model --> data-augmentation
	robust-model --> dropout 
	
	better-activation --> ReLU
	better-activation --> leaky-ReLU
	better-activation --> ELU
	
	weight-init --> Havier
	weight-init --> He	
	
	optimizers --> adagrad
	optimizers --> rmsprop
	optimizers --> adam
```

# Vanishing Gradient

## Nonsaturating Activation Functions

Sigmoid, tanh are saturating activation functions, instead, we need functions that slope will not go to zero as input size grow.

