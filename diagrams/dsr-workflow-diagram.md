
```mermaid
flowchart TD
    A[Start: Clear Use Case/User Story] --> B[Requirements & Design Phase]
    
    subgraph B[Requirements & Design Phase]
        B1[Brainstorm Requirements with Claude]
        B2[Create UML/Mermaid Diagrams]
        B3[Cross-validate with Another Model]
        B4[Create Comprehensive Spec Markdown]
    end
    
    B --> C[Development Architecture Phase]
    
    subgraph C[Development Architecture Phase]
        C1[Use Claude Code to Generate Project Architecture]
        C2[Create Folder Structure & Boilerplate]
        C3[Generate Database Schema]
        C4[Create DevOps Assets]
        C5[Update Documentation with Implementation Details]
    end
    
    C --> D[Refinement Phase]
    
    subgraph D[Refinement Phase]
        D1[Use Cursor Agent for Component Refinements]
        D2[Refactor Code Segments]
        D3[Update Documentation]
    end
    
    D -- Continuous Iteration & Refinement --> B
    D --> E[Project Delivery]
    
    %% Note on iteration
    classDef noteClass fill:#ffffcc,stroke:#999,stroke-width:1px;
    class Note noteClass;
    Note[Iteration is central to the process:<br/>Each cycle increases problem understanding<br/>and solution resolution]
    Note -.-> B
    Note -.-> C
    Note -.-> D