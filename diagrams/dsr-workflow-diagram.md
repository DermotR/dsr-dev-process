
```mermaid
flowchart TD
    A[Start: Clear Business Objectives] --> RD[Requirements Discovery & Design]
    
    subgraph RD[Requirements Discovery & Design]
        subgraph Concurrent [Concurrent Activities]
            direction TB
            C1[Functional Decomposition<br/>Identify Modules & Relationships]
            C2[Requirements Gathering<br/>Across Multiple Modules]
            C3[UI Mockups & Prototypes<br/>Using Tailwind CSS]
            C4[Use Case Analysis<br/>with Claude]
        end
        
        Concurrent --> Organization[Module-Based Organization]
        
        subgraph Organization [Organizing by Module]
            direction TB
            O1[Assign Requirements to Modules]
            O2[Document Module Interfaces]
            O3[Prioritize Module Development]
            O4[Standardize Naming Convention<br/>marketing-admin-123-process-refund]
        end
        
        Organization --> Focus[Focused Analysis Phase]
        
        subgraph Focus [Deepening Module Understanding]
            direction TB
            F1[Detailed Requirements Exploration]
            F2[Module-Specific UML/Mermaid Diagrams]
            F3[Module UI/UX Refinement]
            F4[Cross-Validate with Another LLM]
            F5[Create Module Specification]
        end
    end
    
    RD --> IM[Implementation Phase]
    
    subgraph IM[Implementation Phase]
        subgraph Dev [Development Activities]
            D1[Claude Code Architecture Generation]
            D2[Create Module Boundaries]
            D3[Database Schema Implementation]
            D4[CI/CD & DevOps Setup]
        end
        
        Dev --> Iter[Iteration & Refinement]
        
        subgraph Iter [Refinement Cycles]
            I1[Cursor Agent Component Refinements]
            I2[Code Refactoring & Optimization]
            I3[UI Catalog Updates]
            I4[Documentation Updates]
        end
    end
    
    IM -- Add Features to Current Module --> Focus
    IM -- Implement Interface to New Module --> Focus
    IM -- All Priority Modules Complete --> Delivery[Project Delivery]
    
    %% Notes and callouts
    classDef noteClass fill:#ffffcc,stroke:#999,stroke-width:1px;
    class ProcessNote noteClass;
    ProcessNote[Flexible & Iterative Process:<br/>Discovery and implementation can happen simultaneously<br/>across different modules based on project needs<br/>Organization is module-based, but work can flow naturally]
    ProcessNote -.-> RD
    ProcessNote -.-> IM
    
    classDef exampleClass fill:#e6f7ff,stroke:#1890ff,stroke-width:1px;
    class ExampleModule exampleClass;
    ExampleModule[Module Example:<br/>User Management Module<br/>├── Handles: authentication, profiles<br/>├── Provides auth to → other modules<br/>└── Consumes payment status from → Payment]
    ExampleModule -.-> C1