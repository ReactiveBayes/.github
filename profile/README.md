# Reactive Bayes

Open source software for reactive, efficient and scalable Bayesian inference.

Welcome to the Reactive Bayes organization! We develop and maintain a suite of Julia packages for probabilistic programming and Bayesian inference with a focus on reactive and message-passing based inference algorithms.

```mermaid 
graph TD
    %% Node definitions with links
    RxInfer[RxInfer.jl]
    click RxInfer href "https://github.com/ReactiveBayes/RxInfer.jl" _blank
    GraphPPL[GraphPPL.jl]
    click GraphPPL href "https://github.com/ReactiveBayes/GraphPPL.jl" _blank
    ReactiveMP[ReactiveMP.jl]
    click ReactiveMP href "https://github.com/ReactiveBayes/ReactiveMP.jl" _blank
    Rocket[Rocket.jl]
    click Rocket href "https://github.com/ReactiveBayes/Rocket.jl" _blank
    RxEnvironments[RxEnvironments.jl]
    click RxEnvironments href "https://github.com/ReactiveBayes/RxEnvironments.jl" _blank
    ExponentialFamily[ExponentialFamily.jl]
    click ExponentialFamily href "https://github.com/ReactiveBayes/ExponentialFamily.jl" _blank
    ExponentialFamilyProjection[ExponentialFamilyProjection.jl]
    click ExponentialFamilyProjection href "https://github.com/ReactiveBayes/ExponentialFamilyProjection.jl" _blank
    ExponentialFamilyManifolds[ExponentialFamilyManifolds.jl]
    click ExponentialFamilyManifolds href "https://github.com/ReactiveBayes/ExponentialFamilyManifolds.jl" _blank
    BayesBase[BayesBase.jl]
    click BayesBase href "https://github.com/ReactiveBayes/BayesBase.jl" _blank
    RxInferExamples[RxInferExamples.jl]
    click RxInferExamples href "https://github.com/ReactiveBayes/RxInferExamples.jl" _blank

    %% Connections
    RxInfer --> GraphPPL
    RxInfer --> ReactiveMP
    RxInfer --> Rocket

    RxEnvironments --- RxInfer
    RxEnvironments --- Rocket

    RxInferExamples --- RxInfer
    
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
    classDef default fill:#f0f4f8,stroke:#a0aec0,stroke-width:2px,rx:5px;
    classDef rxi fill:#e6f0ff,stroke:#4a90e2,stroke-width:2px,rx:5px;
    classDef core fill:#e3f2fd,stroke:#2196f3,stroke-width:2px,rx:5px;
    
    %% Apply core styling to main packages
    class ReactiveMP,GraphPPL,Rocket,ExponentialFamily core;
    class RxInfer rxi;

    %% Remove background from main graph
    subgraph "ReactiveBayes Ecosystem"
        RxInfer["RxInfer.jl<br/><small>High-level probabilistic<br/>programming framework</small>"]
        RxInferExamples["RxInferExamples.jl<br/><small>Example applications<br/>using RxInfer</small>"]
        GraphPPL["GraphPPL.jl<br/><small>Probabilistic model<br/>specification language</small>"]
        ReactiveMP["ReactiveMP.jl<br/><small>Message passing-based<br/>inference engine</small>"]
        Rocket["Rocket.jl<br/><small>Reactive programming<br/>primitives</small>"]
        RxEnvironments["RxEnvironments.jl<br/><small>Reactive environments<br/>for RL</small>"]
        ExponentialFamily["ExponentialFamily.jl<br/><small>Extended probability<br/>distributions</small>"]
        ExponentialFamilyProjection["ExponentialFamilyProjection.jl<br/><small>Density projection<br/>utilities</small>"]
        ExponentialFamilyManifolds["ExponentialFamilyManifolds.jl<br/><small>Distribution manifold<br/>representations</small>"]
        BayesBase["BayesBase.jl<br/><small>Core Bayesian<br/>utilities</small>"]
    end

    %% Style settings
    %%{ init: { 'theme': 'base', 'themeVariables': { 'fontSize': '32px' } } }%%
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

Our packages are designed to work together seamlessly to provide:

- **Reactive Inference**: Real-time updates as new data arrives
- **Message Passing**: Efficient inference through local computations
- **Scalability**: Handle large models and datasets
- **Flexibility**: Mix and match components for your specific needs

We welcome contributions from the community! Check out our individual package repositories for more details on how to get involved.
