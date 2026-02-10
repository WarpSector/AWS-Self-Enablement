# Domain 1: Fundamentals of Machine Learning (ML) and Artificial Intelligence (AI)
# (1E: Machine Learning: Lifecycle, Sourcing Models, Deploying Models, and Operations)

# High-Level Overview


# Deep Dive

## Machine Learning Lifecycle                                            
```mermaid
graph TD
    %% Nodes outside the process box
    Goal[1. Identify Business Goal] --> Frame[2. Frame ML Problem]
    
    %% Explicitly connect Frame to the start of the subgraph
    Frame --> Collect

    %% Subgraph for Data Processing Callout (Strictly 3-5)
    subgraph Process_Data ["Process Data Phase"]
        direction TB
        Collect[3. Collect Data] --> Pre[4. Pre-Process Data]
        Pre --> Eng[5. Engineer Features]
    end

    %% Connect out of the subgraph
    Eng --> Train[6. Train, Tune, Evaluate]
    Train --> Deploy[7. Deploy]
    Deploy --> Monitor[8. Monitor]

    %% Feedback Loop
    Monitor -.-> |Insights for Improvement| Goal

    %% Node Styling
    style Goal fill:#f9f,stroke:#333,stroke-width:2px,color:#000
    style Train fill:#f96,stroke:#333,stroke-width:2px,color:#000
    style Deploy fill:#f96,stroke:#333,stroke-width:2px,color:#000
    style Monitor fill:#bbf,stroke:#333,stroke-width:2px,color:#000
    style Frame fill:#eee,stroke:#333,color:#000
    style Collect fill:#eee,stroke:#333,color:#000
    style Pre fill:#eee,stroke:#333,color:#000
    style Eng fill:#eee,stroke:#333,color:#000

    %% Subgraph Callout Styling
    style Process_Data fill:#e6f7ff,stroke:#1890ff,stroke-width:2px,stroke-dasharray: 5 5,color:#000
```
