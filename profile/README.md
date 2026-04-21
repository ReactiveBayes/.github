# Reactive Bayes

Open source software for reactive, efficient and scalable Bayesian inference.

Welcome to the Reactive Bayes organization! We develop and maintain a suite of Julia packages for probabilistic programming and Bayesian inference with a focus on reactive and message-passing based inference algorithms.

```mermaid 
graph TD
    %% Node definitions
    RxInfer["RxInfer.jl"]
    RxInferExamples["RxInferExamples.jl"]
    GraphPPL["GraphPPL.jl"]
    ReactiveMP["ReactiveMP.jl"]
    Rocket["Rocket.jl"]
    RxEnvironments["RxEnvironments.jl"]
    ExponentialFamily["ExponentialFamily.jl"]
    ExponentialFamilyProjection["ExponentialFamilyProjection.jl"]
    ExponentialFamilyManifolds["ExponentialFamilyManifolds.jl"]
    BayesBase["BayesBase.jl"]
    RxGP["RxGP.jl"]

    %% Connections
    RxInfer --> GraphPPL
    RxInfer --> ReactiveMP
    RxInfer --> Rocket

    RxEnvironments --> Rocket

    RxInferExamples --> RxInfer
    RxGP --> RxInfer
    
    ReactiveMP --> ExponentialFamily
    ReactiveMP --> ExponentialFamilyProjection
    ReactiveMP --> Rocket
    
    ExponentialFamilyProjection --> ExponentialFamilyManifolds
    ExponentialFamilyProjection --> ExponentialFamily
    ExponentialFamilyManifolds --> ExponentialFamily
    
    ReactiveMP --> ExponentialFamily
    
    ExponentialFamily --> BayesBase
    ExponentialFamilyManifolds --> BayesBase
    ExponentialFamilyProjection --> BayesBase

    %% Node styling
    classDef default fill:#f0f4f8,stroke:#a0aec0,stroke-width:2px,rx:5px,text-decoration:none,color:#000;
    classDef rxi fill:#e6f0ff,stroke:#4a90e2,stroke-width:2px,rx:5px,text-decoration:none,color:#000;
    classDef core fill:#e3f2fd,stroke:#2196f3,stroke-width:2px,rx:5px,text-decoration:none,color:#000;
    
    %% Apply core styling to main packages
    class ReactiveMP,GraphPPL,Rocket,ExponentialFamily core;
    class RxInfer rxi;
```

## Key Packages

- **[RxInfer](https://github.com/ReactiveBayes/RxInfer.jl)**
The central high-level probabilistic programming framework that enables reactive Bayesian inference on factor graphs through reactive message passing. It integrates tools including [probabilistic graphical model definition](https://github.com/ReactiveBayes/GraphPPL.jl) and [reactive message-based Bayesian inference](https://github.com/ReactiveBayes/ReactiveMP.jl).
- **[ReactiveMP](https://github.com/ReactiveBayes/ReactiveMP.jl)**
An efficient message passing-based Bayesian inference engine that implements the core algorithms and rules for performing high-performance, reactive message passing on factor graphs.
- **[GraphPPL](https://github.com/ReactiveBayes/GraphPPL.jl)**
A probabilistic programming language for specifying probabilistic graphical models as factor graphs. It provides a high-level domain-specific language for model creation and works seamlessly with RxInfer for inference.
- **[ExponentialFamily](https://github.com/ReactiveBayes/ExponentialFamily.jl)**
Extends [Distributions.jl](https://github.com/JuliaStats/Distributions.jl) with comprehensive implementations of a collection of exponential family distributions.
- **[Rocket](https://github.com/ReactiveBayes/Rocket.jl)**
A reactive programming framework providing core primitives for event handling and streaming for Julia, inspired by [RxJS](https://github.com/ReactiveX/rxjs). It forms the backbone for reactive computations in the ecosystem.

## Supporting Packages

- **[ExponentialFamilyManifolds](https://github.com/ReactiveBayes/ExponentialFamilyManifolds.jl)**
Provides manifold representations of exponential family distributions, enabling advanced optimization workflows with [Manopt.jl](https://github.com/JuliaManifolds/Manopt.jl). It facilitates efficient parameter tuning in natural parameter spaces.

- **[ExponentialFamilyProjection](https://github.com/ReactiveBayes/ExponentialFamilyProjection.jl)**
Enables projection of (un-normalized) log probability density functions onto exponential family distributions. It uses optimization techniques from [Manopt.jl](https://github.com/JuliaManifolds/Manopt.jl) and leverages [ExponentialFamilyManifolds.jl](https://github.com/ReactiveBayes/ExponentialFamilyManifolds.jl).

- **[BayesBase](https://github.com/ReactiveBayes/BayesBase.jl)**
Defines and re-exports core methods and utilities for Bayesian computation. It provides a shared foundation for the Reactive Bayes ecosystem.

## Application specific packages

- **[RxInferExamples](https://github.com/ReactiveBayes/RxInferExamples.jl)**
Contains example applications using RxInfer.
- **[RxEnvironments](https://github.com/ReactiveBayes/RxEnvironments.jl)**
Provides reactive environments for agents.
- **[RxGP](https://github.com/ReactiveBayes/RxGP.jl)**
Sparse Gaussian process factor nodes and variational message passing update rules for Sparse Variational Gaussian Process (VSGP) models within the RxInfer ecosystem. It enables embedding sparse GP computations directly into Forney-style factor graphs, with automatic inference over inducing variables, noise precisions, hyperparameters, and uncertain inputs.

Our packages are designed to work together seamlessly to provide:

- **Reactive Inference**: Real-time updates as new data arrives
- **Message Passing**: Efficient inference through local computations
- **Scalability**: Handle large models and datasets
- **Flexibility**: Mix and match components for your specific needs

We welcome contributions from the community! Check out our individual package repositories for more details on how to get involved.

## Using RxInfer from Python

> **Third-party, unmaintained.** `RxInferServer.jl` and the `RxInferClient.py` Python SDK are developed by [Lazy Dynamics](https://lazydynamics.com) — an external organisation that is separate from the core RxInfer team. These projects are distributed under a different license than `RxInfer.jl` and are **not actively maintained** by the ReactiveBayes / RxInfer core team. The links on this page are provided for reference only; some of them may be outdated or unavailable. Please direct support requests to the respective upstream repositories rather than to the RxInfer issue tracker.

RxInfer can be used from Python through the `RxInferServer.jl` RESTful API and the `RxInferClient.py` Python SDK.

For detailed documentation on how to use RxInfer from Python, please refer to:

- [RxInferServer Repository](https://github.com/lazydynamics/RxInferServer) — Source code and examples for the server
- [Python SDK Repository](https://github.com/lazydynamics/RxInferClient.py) — Source code and examples for the Python client

For support and issues, please use:

- [RxInferServer Issues](https://github.com/lazydynamics/RxInferServer/issues)
- [Python SDK Issues](https://github.com/lazydynamics/RxInferClient.py/issues)
- [Community Discussions](https://github.com/ReactiveBayes/RxInfer.jl/discussions)
