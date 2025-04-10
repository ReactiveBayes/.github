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
    RxInferServer["RxInferServer"]
    RxInferClient["RxInferClient.py"]

    %% Connections
    RxInfer --> GraphPPL
    RxInfer --> ReactiveMP
    RxInfer --> Rocket

    RxInferServer --> RxInfer
    RxInferClient --> RxInferServer
    RxEnvironments --> Rocket

    RxInferExamples --> RxInfer
    
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

## Deployment and Integration

- **[RxInferServer](https://github.com/lazydynamics/RxInferServer)**
A RESTful HTTP server that enables deploying RxInfer models as web services. It provides endpoints for model management, inference, and learning operations. The server is available at [server.rxinfer.com](https://server.rxinfer.com/).

- **[RxInferClient.py](https://github.com/lazydynamics/RxInferClient.py)**
A Python client library for interacting with RxInferServer. It provides a simple and intuitive interface to work with RxInfer models from Python, including model management, inference, and result processing. Documentation is available at [lazydynamics.github.io/RxInferClient.py](https://lazydynamics.github.io/RxInferClient.py/).

Our packages are designed to work together seamlessly to provide:

- **Reactive Inference**: Real-time updates as new data arrives
- **Message Passing**: Efficient inference through local computations
- **Scalability**: Handle large models and datasets
- **Flexibility**: Mix and match components for your specific needs
- **Deployment**: Easy deployment of models as web services
- **Integration**: Seamless integration with other programming languages

We welcome contributions from the community! Check out our individual package repositories for more details on how to get involved.
