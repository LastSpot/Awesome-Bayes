# Awesome-Bayes

A Python implementation of Bayesian Network sampling and inference algorithms. This project provides tools for probabilistic reasoning using various sampling methods in Bayesian networks.

## Overview

This project implements three different sampling approaches for Bayesian networks:
1. Simple Sampling
2. Rejection Sampling
3. Likelihood Weighting Sampling

Each method provides different ways to estimate probabilities in Bayesian networks, with varying levels of efficiency and accuracy when dealing with evidence.

## Components

### BooleanVariableNode
- Represents a node in a Bayesian network
- Handles boolean variables with conditional probability tables (CPTs)
- Manages parent-child relationships between nodes

### Sampling Classes

1. **SimpleSampler**
   - Basic sampling without evidence
   - Generates unconditional samples from the network
   - Useful for calculating joint probabilities

2. **RejectionSampler**
   - Extends SimpleSampler
   - Handles evidence through rejection sampling
   - More efficient than simple sampling when evidence is present
   - May discard many samples when evidence is unlikely

3. **LikelihoodWeightingSampler**
   - Implements likelihood weighting
   - Most efficient when dealing with evidence
   - Generates weighted samples that always conform to evidence

### Utility Functions

- `compare_estimates`: Compare probability estimates from different samplers
- `bayes_sample_size_plot`: Generate plots comparing sampler performance
- Visualization tools for analyzing sampling convergence

## Usage

```python
# Example usage (basic sampling)
nodes = [node1, node2, ...]  # Define your Bayesian network nodes
sampler = SimpleSampler(nodes)
prob = sampler.get_prob(query_vals={}, num_samples=1000)

# With evidence (using rejection sampling)
rejection_sampler = RejectionSampler(nodes)
prob = rejection_sampler.get_prob(
    query_vals={'A': True}, 
    evidence_vals={'B': False}, 
    num_samples=1000
)

# Using likelihood weighting
lw_sampler = LikelihoodWeightingSampler(nodes)
prob = lw_sampler.get_prob(
    query_vals={'A': True}, 
    evidence_vals={'B': False}, 
    num_samples=1000
)
```

## Requirements

- Python 3.x
- matplotlib (for visualization)
- random (standard library)

## Features

- Implementation of three different sampling methods
- Support for boolean variables in Bayesian networks
- Conditional probability estimation
- Performance comparison tools
- Visualization of sampling convergence

## Technical Details

The implementation uses object-oriented programming principles to create a modular and extensible framework for Bayesian network sampling. Each sampling method is implemented as a separate class, allowing for easy comparison and extension.

The `BooleanVariableNode` class provides the foundation for representing network structure and conditional probabilities, while the sampling classes implement different strategies for generating samples and estimating probabilities.

## Performance Considerations

- Simple Sampling: Fast but cannot handle evidence
- Rejection Sampling: Can be inefficient with unlikely evidence
- Likelihood Weighting: Generally most efficient with evidence, but may require more samples for accurate results

## Contributing

Feel free to submit issues and enhancement requests! 