# Iterative LLM-Assisted Development Process Guide
**Version 1.0 - dsr-dev-proc**

This document outlines a comprehensive, iterative approach to software development that leverages Large Language Models (LLMs) at each stage of the process. The dsr-dev-proc methodology emphasizes thorough documentation, visual modeling, and continuous refinement to build high-quality software systems.

> **Key Ideas at a Glance:**
> 
> - **UI-First Approach**: Start with sketches and wireframes to drive requirements
> - **LLM at the Center**: Use Claude for both requirements exploration and code generation
> - **Modular Organization**: Structure work by functional domains for clarity
> - **Visual Documentation**: Leverage diagrams and prototypes to enhance understanding
> - **Iterative Refinement**: Build, learn, refine in continuous cycles
> - **Temporary Sessions**: Save outputs from LLM sessions to permanent storage

## 1. Requirements Discovery Phase

**Input**: Initial user story or use case description  
**Output**: Comprehensive specification document with diagrams

> **Phase Summary**: Explore requirements through UI sketches, organize by functional modules, leverage Claude for ideation, create visual representations, validate with different models, and produce detailed specifications.

### Process Steps:

> **Note on Flexibility**: While these steps are presented sequentially, in practice they often happen concurrently and iteratively. The goal is to organize thinking, not enforce a rigid process. During requirements discovery, conversations naturally flow between modules and levels of detail. The framework below helps organize these insights rather than constraining the discovery process.

1. **Concurrent Functional Decomposition and Analysis**
   - Identify functional domains or modules while analyzing use cases
   - Examples of modules: User Management, Content Management, Reporting, Payment Processing
   - Use modules as organizational units, not strict boundaries
   - Create a simple module relationship map to visualize connections
   
   **Example Module Relationship Map (Text Version)**:
   ```
   User Management Module
   ├── Handles: authentication, profiles, permissions
   ├── Provides data to → Reporting Module
   ├── Provides authentication to → ALL other modules
   └── Consumes payment status from → Payment Module
   
   Content Management Module
   ├── Handles: creating/editing content, categorization, publishing
   ├── Provides content to → Public Portal Module  
   ├── Sends usage data to → Reporting Module
   └── Receives user data from → User Management Module
   
   Payment Processing Module
   ├── Handles: payment methods, transactions, invoicing
   ├── Updates user accounts in → User Management Module
   ├── Provides transaction data to → Reporting Module
   └── Triggers content access in → Content Management Module
   ```

2. **Flexible Module-Based Requirements Organization**
   - Organize requirements by module for clarity and focus
   - Allow natural transitions between modules during discovery sessions
   - It's acceptable to sketch high-level functionality across multiple modules in one session
   - Circle back to add detail to priority modules as needed
   - Use standardized requirement ID format: `[module]-[role]-[number]-[action]`
     - Examples: `marketing-admin-123-process-refund`, `customer-user-013-book-session`
     - Module prefix ensures requirements are organized by functional domain
     - This naming convention applies universally across user stories, requirements, and features
     - Improves traceability and makes referencing specific requirements easier

3. **Collaborative Requirements Exploration with Claude**
   - Use Claude as the central tool for requirements ideation and exploration
   - Begin with UI sketches to focus minds on functionality and flesh out use cases:
     - Start with pencil sketches as input to the LLM
     - Create simple wireframes using tools like Balsamiq or Figma
     - Use these visual elements to drive concrete discussions about functionality
   - When a conversation begins to cover too many areas, use prompts to refocus:
     - "Let's park the payment processing ideas for now and focus on completing the user management requirements."
     - "I notice we're discussing several modules. Let's document these cross-cutting concerns and then return to our focus module."
   - Explore for each module:
     - Functional requirements
     - Core user flows and journeys
     - Entity relationships and data needs
     - Technical constraints and considerations
     - Non-functional requirements (performance, security, etc.)
   - Use LLM prompting for creative brainstorming:
     - Generate alternative approaches to solving problems
     - Anticipate user needs and edge cases
     - Explore different technical implementation strategies
     - Compare pros and cons of various solutions
   - **Important**: Treat LLM sessions as temporary workspaces
     - Save important outputs before ending sessions
     - Extract key insights, requirements, and designs to permanent storage
     - Don't rely on file stores or project repositories provided by LLM tools for long-term retention

4. **Create Visual Representations**
   - Develop diagrams using Mermaid specifically for the current module:
     - Use case diagrams (actor interactions)
     - Entity relationship diagrams (data model)
     - Sequence diagrams (key workflows)
     - Component diagrams (system architecture)
   - Focus on clarity over comprehensiveness in early iterations
   - Create UI mockups and wireframes to visualize the module's user experience:
     - Use Tailwind CSS for rapid prototyping
     - Build simple interactive prototypes
     - Include multiple design iterations to explore alternatives
     - Store and organize mockups in a prototype catalog by module (see Web Development Catalog below)
   - Document interfaces between the current module and other modules

5. **Cross-validate with Another Model**
   - Ask a different LLM (e.g., GPT-4) to review module-specific requirements
   - Look for gaps, inconsistencies, or alternative perspectives
   - Ask specifically: "What important considerations are missing from this module?"
   - Have the second model summarize key points to ensure clarity
   - Validate module boundaries and interfaces with other modules

6. **Create Module-Specific Specification**
   - Develop a structured markdown document for each module containing:
     - User stories and detailed use cases with standardized IDs
     - Visual data model with field definitions
     - API specifications (endpoints, parameters, responses)
     - Business rules and constraints catalog
     - Non-functional requirements
     - Technical stack recommendations
     - UI mockups and design iterations
   - Clearly document dependencies and interfaces with other modules

### Recommended Tools:

- **Documentation & Diagrams**:
  - Visual Studio Code with extensions:
    - [Markdown All in One](https://marketplace.visualstudio.com/items?itemName=yzhang.markdown-all-in-one)
    - [Mermaid Markdown Syntax Highlighting](https://marketplace.visualstudio.com/items?itemName=bpruitt-goddard.mermaid-markdown-syntax-highlighting)
    - [Markdown Preview Mermaid Support](https://marketplace.visualstudio.com/items?itemName=bierner.markdown-mermaid)
  - [Mermaid Live Editor](https://mermaid.live/) - Browser-based diagram creation
  - [Notion](https://notion.so) - Collaborative documentation with Mermaid support
  - [Obsidian](https://obsidian.md/) - Knowledge management with Mermaid support

- **UI Design & Prototyping**:
  - [Pencil & Paper] - For initial sketches to drive requirements discussions
  - [Balsamiq](https://balsamiq.com/) - Simple wireframing tool for early concepts
  - [Tailwind CSS](https://tailwindcss.com/) - Utility-first CSS framework for rapid UI development
  - [React](https://reactjs.org/) - Component-based UI library
  - [Vite](https://vitejs.dev/) - Fast build tool for modern web projects
  - [Figma](https://www.figma.com/) - Collaborative interface design tool
  - Web Development Catalog (see section below) - For organizing and referencing UI mockups

- **LLM Interaction**:
  - Claude (web interface or API) - Primary model for requirements gathering and brainstorming
  - Another LLM model (for cross-validation)
  - Claude Code - For implementation patterns and architecture guidance

### Web Development Catalog

A simple React + Tailwind CSS project is recommended to help catalog design iterations and UI prototypes, organized by functional module:

- **Purpose**: Create a living documentation of UI components, mockups, and design iterations
- **Benefits**:
  - Centralizes all design artifacts in one browsable interface
  - Allows team members to see the evolution of designs
  - Provides a reference library of components for reuse
  - Makes it easy to showcase alternatives and get feedback
  - Supplements written documentation with visual examples
  - Maintains organization while allowing flexible development

- **Module-Based Organization**:
  - Primary navigation based on functional modules (e.g., User Management, Content, Payments)
  - Secondary navigation by requirement ID within each module
  - Special section for module interfaces and integration points
  - Helps maintain focus by separating concerns into distinct modules
  - Prevents scope creep by making module boundaries visible

- **Implementation**:
  - Simple React + Tailwind CSS app with minimal dependencies
  - Static site with no backend requirements
  - Folder structure mirrors module organization (e.g., `/src/modules/moduleA/`)
  - Organized by module and feature ID using the standard naming convention
  - Each mockup includes metadata (date, purpose, feedback, module)
  - Can be deployed as static site or run locally

- **Example UI Prototype Catalog Structure for Non-Technical Readers**:

```
UI Prototype Catalog
│
├── Modules
│   │
│   ├── User Management
│   │   ├── Login Screen [user-001-login]
│   │   │   ├── Version 1 - Basic login form
│   │   │   ├── Version 2 - With social login options
│   │   │   └── Version 3 - Final design with password recovery
│   │   │
│   │   └── User Profile [user-002-view-profile]
│   │       ├── Version 1 - Simple profile view
│   │       └── Version 2 - With editing capabilities
│   │
│   ├── Content Management
│   │   ├── Article Editor [content-001-create-article]
│   │   └── Media Gallery [content-002-manage-media]
│   │
│   └── Payment Processing
│       ├── Checkout Flow [payment-001-checkout]
│       └── Invoice History [payment-002-view-invoices]
│
├── Cross-Module Interfaces
│   ├── User → Content (Content permissions)
│   ├── Content → Payment (Premium content access)
│   └── Payment → User (Subscription status)
│
└── Design System
    ├── Color Palette
    ├── Typography
    ├── Common Components
    └── Responsive Breakpoints
```

This organization allows stakeholders to easily navigate between different functional areas while seeing relationships between modules. While organized by module, the prototype catalog doesn't restrict when or how mockups are created - early discovery sessions might populate several modules at once with basic mockups, which are then refined iteratively.

### Mermaid UML Resources:

- [Official Mermaid UML Diagrams Guide](https://mermaid.js.org/syntax/classDiagram.html)
- [Mermaid Entity Relationship Diagrams](https://mermaid.js.org/syntax/entityRelationshipDiagram.html)
- [Mermaid Sequence Diagrams](https://mermaid.js.org/syntax/sequenceDiagram.html)
- [GitHub's Mermaid Documentation](https://github.blog/2022-02-14-include-diagrams-markdown-files-mermaid/)

## 2. Core Implementation Phase

**Input**: Comprehensive specification document  
**Output**: Working implementation of core use cases with project structure, architecture, and supporting assets

> **Phase Summary**: Implement essential features, define architecture with Claude Code, establish project structure, create database schema, set up DevOps assets, and document implementation details. Generate working React code directly from UI mockups.

### Process Steps:

1. **Implement Core Use Cases**
   - Build initial working implementation of all essential features
   - Focus on functionality over optimization at this stage
   - Ensure all primary user journeys are implemented
   - Create minimal viable implementation of each core requirement

2. **Define Project Architecture**
   - Use Claude Code or similar agentic Coding Assistant as the primary tool
   - Define overall system architecture based on requirements
   - Identify key components and their interactions
   - Determine appropriate design patterns
   - Choose technology stack based on requirements
   - Leverage LLMs to generate working React code:
     - Use UI mockups from requirements phase as visual references
     - Generate code that can be directly integrated into the catalog site
     - Refine generated code through iterative prompting

3. **Create Folder Structure & Boilerplate**
   - Use Claude Code to generate an organized folder structure
   - Create initial project configuration files
   - Set up basic application scaffolding
   - Implement foundational components

4. **Define Database Schema**
   - Use Claude Code to create schema definitions based on data model
   - Include indexes, constraints, and relationships
   - Generate migration scripts if applicable
   - Set up seed data for development

5. **Create DevOps Assets**
   - Use Claude Code to generate CI/CD workflow configurations
   - Create Docker files or containerization scripts
   - Set up testing frameworks and initial tests
   - Establish deployment configurations

6. **Update Documentation**
   - Enhance the specification with implementation details
   - Document architectural decisions and rationales
   - Create technical documentation for the codebase
   - Update diagrams to reflect actual implementation

### Recommended Tools:

- **LLM Tools**:
  - **Claude Code or similar agentic Coding Assistant** - Core tool for Phase 2 implementation, handling file/folder creation, boilerplate code, schema definition, and implementation of all core use cases
  - **Cursor in Agent mode using Claude 3.7** - For targeted refinement at the individual component level (never across the entire codebase)
  - **Claude** (web interface or API) - For requirements gathering and documentation

- **Project Stack & Scaffolding**:
  - [Vite](https://vitejs.dev/) - Fast frontend tooling for React
  - [React](https://reactjs.org/) - Default UI library for client applications
  - [Tailwind CSS](https://tailwindcss.com/) or [Material UI](https://mui.com/) - Preferred styling frameworks
  - [Visual Studio Code](https://code.visualstudio.com/) with appropriate language extensions

- **Database & ORM**:
  - [PostgreSQL](https://www.postgresql.org/) - Primary database system
  - [Prisma](https://www.prisma.io/) - ORM with type safety and schema management

- **DevOps Tooling**:
  - [GitHub Actions](https://github.com/features/actions) - CI/CD integration
  - [Docker](https://www.docker.com/) - Containerization

## 3. Refinement Phase

**Input**: Working implementation of core use cases from Phase 2  
**Output**: Refined and optimized application with improved quality and performance

> **Phase Summary**: Focus on component-level refinement using Cursor Agent, refactor code for quality and performance, keep documentation updated, and gather feedback for the next iteration cycle.

### Process Steps:

1. **Component-Level Refinement**
   - Use Cursor Agent to focus on specific components
   - Improve code quality and performance
   - Add edge case handling and error recovery
   - Enhance component documentation

2. **Code Refactoring**
   - Identify areas for improvement
   - Apply appropriate design patterns
   - Reduce duplication and improve maintainability
   - Optimize for performance where needed

3. **Documentation Updates**
   - Keep documentation in sync with code changes
   - Document refactoring decisions and rationales
   - Update diagrams to reflect current implementation
   - Create or update API documentation

4. **Iterative Feedback**
   - Gather feedback on current implementation
   - Identify areas for further improvement
   - Revisit requirements as needed
   - Plan next iteration cycle

### Recommended Tools:

- **Code Refinement**:
  - [Cursor in Agent mode with Claude 3.7](https://cursor.sh/) - For targeted component-level refinements (never across the entire codebase)
  - [ESLint](https://eslint.org/) - Code linting and static analysis

- **Documentation**:
  - [JSDoc](https://jsdoc.app/) / [PyDoc](https://docs.python.org/3/library/pydoc.html) - Code documentation
  - [Swagger](https://swagger.io/) / [OpenAPI](https://www.openapis.org/) - API documentation
  - [Docusaurus](https://docusaurus.io/) - Documentation websites

- **Testing**:
  - [Jest](https://jestjs.io/) / [PyTest](https://pytest.org/) - Testing frameworks
  - [Cypress](https://www.cypress.io/) - End-to-end testing
  - [k6](https://k6.io/) - Load testing

## 4. Continuous Iteration

> **Phase Summary**: Evaluate implementation against requirements, identify areas of deepened understanding, return to requirements with enhanced knowledge, update documentation, implement refinements, and continue the cycle until quality targets are met.

The dsr-dev-proc process is inherently iterative. After completing the Refinement Phase, the team should cycle through the following steps, deepening understanding and improving implementation with each iteration:

### 1. Evaluate Current Implementation Against Original Requirements

**Key Questions to Address:**
- Does the implementation satisfy the core user stories and use cases?
- Are there gaps between what was specified and what was delivered?
- Have we discovered requirements that weren't apparent in earlier phases?
- Are there performance or usability issues that weren't anticipated?

**Potential Updates:**
- Revised success criteria for user stories
- Updated acceptance tests to reflect actual usage patterns
- Enhanced performance metrics based on real-world testing

### 2. Identify Areas Where Understanding Has Deepened

**Key Questions to Address:**
- What did we learn about the domain that we didn't know before?
- How has our understanding of user needs evolved?
- What technical constraints or opportunities have we discovered?
- What assumptions were validated or invalidated during implementation?

**Potential Updates:**
- More nuanced user persona definitions
- Expanded domain glossary with refined terminology
- Revised system boundaries based on technical discoveries
- Documented assumptions with validation status

### 3. Return to Requirements Discovery with Enhanced Knowledge

**Key Questions to Address:**
- How should our requirements evolve based on new insights?
- What additional use cases should we consider?
- Do we need to revise our understanding of the data model?
- Are there workflow optimizations we can now envision?

**Potential Updates:**
- **Data Model Refinements:**
  - Additional entities discovered during implementation
  - Modified relationships between entities
  - New attributes needed for reporting or analytics
  - Optimized structures for performance or scalability
- **Process Flow Improvements:**
  - Streamlined user journeys based on feedback
  - Additional error handling paths
  - Automated steps that were initially manual
  - Integration points with other systems

### 4. Update Specifications, Diagrams, and Documentation

**Key Questions to Address:**
- How do our diagrams need to change to reflect our current understanding?
- What documentation is missing or outdated?
- Are there new architectural decisions that need to be documented?
- How have our API definitions evolved?

**Potential Updates:**
- Revised ERD diagrams with new entities and relationships
- Updated sequence diagrams showing optimized flows
- Enhanced API specifications with additional endpoints or parameters
- Architecture decision records (ADRs) for significant changes
- Updated non-functional requirements based on performance testing

### 5. Implement New Features or Refinements

**Key Questions to Address:**
- What is the priority order for new features or refinements?
- Which improvements will deliver the most value?
- What technical debt should we address before proceeding?
- How can we implement changes while maintaining system stability?

**Potential Updates:**
- Revised development roadmap
- Refactored components based on new understanding
- Additional automated tests for edge cases
- Enhanced error handling and resilience patterns

### 6. Continue the Cycle Until Quality and Feature Targets Are Met

**Key Questions to Address:**
- How do we know when we've reached sufficient quality?
- What metrics indicate we've met our feature targets?
- How do we balance further refinement against diminishing returns?
- When is the product ready for wider release or next phase?

**Potential Updates:**
- Defined quality gates with measurable criteria
- Feature completion checklist with stakeholder sign-off
- Performance benchmark results compared to targets
- User feedback summary from testing or limited release

Each iteration increases the resolution of understanding and improves the quality of the implementation. Documentation should evolve alongside the code to maintain a comprehensive and accurate representation of the system. The most valuable iterations often come from real-world usage insights, making early user feedback essential to the dsr-dev-proc process.

### Iteration Tracking Tools:

- [Jira](https://www.atlassian.com/software/jira) - Agile project management
- [GitHub Projects](https://github.com/features/issues) - Issue and project tracking
- [Trello](https://trello.com/) - Kanban-style project boards
- [Notion](https://www.notion.so/) - All-in-one workspace for notes and projects

## Best Practices

> **Summary**: Keep documentation current, leverage appropriate LLM tools for specific tasks, establish phase checkpoints, embrace incremental improvement, and validate critical decisions with multiple perspectives.

### 1. **Maintain Documentation Currency**
- Update documentation immediately after code changes
- Use documentation-as-code approaches when possible
- Automate documentation generation where appropriate

### 2. **Leverage LLM Strengths**
- Use Claude for creative ideation and requirement expansion
- Use Claude Code for structured code generation and React components
- Use Cursor for targeted refinements and improvements
- Save important outputs before ending LLM sessions

### 3. **Start with UI**
- Begin with pencil sketches to drive requirements discussions
- Use simple wireframes to focus on functionality and user experience
- Generate working React code from UI mockups

### 4. **Establish Clear Checkpoints**
- Define clear criteria for moving between phases
- Ensure documentation meets quality standards before proceeding
- Validate with stakeholders at key milestones

### 5. **Embrace Incremental Improvement**
- Recognize that perfect understanding evolves over time
- Focus on continuous improvement rather than perfection
- Document known limitations and future enhancement opportunities

### 6. **Cross-Validate Critical Decisions**
- Use multiple LLMs for important architectural decisions
- Seek diverse perspectives on complex problems
- Document alternative approaches considered

By following the dsr-dev-proc process and adhering to these best practices, teams can leverage the power of LLMs to create well-documented, thoughtfully designed software systems that evolve through iterative refinement.