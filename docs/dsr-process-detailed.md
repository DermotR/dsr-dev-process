# Iterative LLM-Assisted Development Process Guide
**Version 1.0 - DSRFlow**

This document outlines a comprehensive, iterative approach to software development that leverages Large Language Models (LLMs) at each stage of the process. The DSRFlow methodology emphasizes thorough documentation, visual modeling, and continuous refinement to build high-quality software systems.

## 1. Requirements Discovery Phase

**Input**: Initial user story or use case description  
**Output**: Comprehensive specification document with diagrams

### Process Steps:

1. **Define Core Use Case**
   - Start with a clear, specific user story or use case
   - Format as: "As a [role], I want to [action], so that [benefit]"
   - Ensure the use case represents a key value proposition

2. **Brainstorm Requirements with Claude**
   - Conduct structured conversations with Claude to explore:
     - Functional requirements
     - Core user flows and journeys
     - Entity relationships and data needs
     - Technical constraints and considerations
     - Non-functional requirements (performance, security, etc.)
   - Use probing questions: "What else might users need?" or "What edge cases should we handle?"

3. **Create Visual Representations**
   - Develop diagrams using Mermaid for:
     - Use case diagrams (actor interactions)
     - Entity relationship diagrams (data model)
     - Sequence diagrams (key workflows)
     - Component diagrams (system architecture)
   - Focus on clarity over comprehensiveness in early iterations

4. **Cross-validate with Another Model**
   - Ask a different LLM (e.g., GPT-4) to review requirements
   - Look for gaps, inconsistencies, or alternative perspectives
   - Ask specifically: "What important considerations are missing?"
   - Have the second model summarize key points to ensure clarity

5. **Create Comprehensive Specification**
   - Develop a structured markdown document containing:
     - User stories and detailed use cases
     - Visual data model with field definitions
     - API specifications (endpoints, parameters, responses)
     - Business rules and constraints catalog
     - Non-functional requirements
     - Technical stack recommendations

### Recommended Tools:

- **Documentation & Diagrams**:
  - Visual Studio Code with extensions:
    - [Markdown All in One](https://marketplace.visualstudio.com/items?itemName=yzhang.markdown-all-in-one)
    - [Mermaid Markdown Syntax Highlighting](https://marketplace.visualstudio.com/items?itemName=bpruitt-goddard.mermaid-markdown-syntax-highlighting)
    - [Markdown Preview Mermaid Support](https://marketplace.visualstudio.com/items?itemName=bierner.markdown-mermaid)
  - [Mermaid Live Editor](https://mermaid.live/) - Browser-based diagram creation
  - [Notion](https://notion.so) - Collaborative documentation with Mermaid support
  - [Obsidian](https://obsidian.md/) - Knowledge management with Mermaid support

- **LLM Interaction**:
  - Claude (web interface or API) - Primary model for requirements gathering
  - Another LLM model (for cross-validation)
  - Claude Code - For implementation patterns and architecture guidance

### Mermaid UML Resources:

- [Official Mermaid UML Diagrams Guide](https://mermaid.js.org/syntax/classDiagram.html)
- [Mermaid Entity Relationship Diagrams](https://mermaid.js.org/syntax/entityRelationshipDiagram.html)
- [Mermaid Sequence Diagrams](https://mermaid.js.org/syntax/sequenceDiagram.html)
- [GitHub's Mermaid Documentation](https://github.blog/2022-02-14-include-diagrams-markdown-files-mermaid/)

## 2. Architecture & Development Phase

**Input**: Comprehensive specification document  
**Output**: Project structure and boilerplate code

### Process Steps:

1. **Define Project Architecture**
   - Use Claude Code to outline overall system architecture
   - Identify key components and their interactions
   - Determine appropriate design patterns
   - Choose technology stack based on requirements

2. **Create Folder Structure & Boilerplate**
   - Generate an organized folder structure for the project
   - Create initial project configuration files
   - Set up basic application scaffolding
   - Implement foundational components

3. **Define Database Schema**
   - Create schema definitions based on data model
   - Include indexes, constraints, and relationships
   - Generate migration scripts if applicable
   - Set up seed data for development

4. **Create DevOps Assets**
   - Generate CI/CD workflow configurations
   - Create Docker files or containerization scripts
   - Set up testing frameworks and initial tests
   - Establish deployment configurations

5. **Update Documentation**
   - Enhance the specification with implementation details
   - Document architectural decisions and rationales
   - Create technical documentation for the codebase
   - Update diagrams to reflect actual implementation

### Recommended Tools:

- **LLM Tools**:
  - **Claude Code** - Critical for architectural and design code implementation
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

**Input**: Basic application with core use cases implemented  
**Output**: Refined and optimized application

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

The DSRFlow process is inherently iterative. After completing the Refinement Phase, the team should cycle through the following steps, deepening understanding and improving implementation with each iteration:

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

Each iteration increases the resolution of understanding and improves the quality of the implementation. Documentation should evolve alongside the code to maintain a comprehensive and accurate representation of the system. The most valuable iterations often come from real-world usage insights, making early user feedback essential to the DSRFlow process.

### Iteration Tracking Tools:

- [Jira](https://www.atlassian.com/software/jira) - Agile project management
- [GitHub Projects](https://github.com/features/issues) - Issue and project tracking
- [Trello](https://trello.com/) - Kanban-style project boards
- [Notion](https://www.notion.so/) - All-in-one workspace for notes and projects

## Best Practices

1. **Maintain Documentation Currency**
   - Update documentation immediately after code changes
   - Use documentation-as-code approaches when possible
   - Automate documentation generation where appropriate

2. **Leverage LLM Strengths**
   - Use Claude for creative ideation and requirement expansion
   - Use Claude Code for structured code generation
   - Use Cursor for targeted refinements and improvements

3. **Establish Clear Checkpoints**
   - Define clear criteria for moving between phases
   - Ensure documentation meets quality standards before proceeding
   - Validate with stakeholders at key milestones

4. **Embrace Incremental Improvement**
   - Recognize that perfect understanding evolves over time
   - Focus on continuous improvement rather than perfection
   - Document known limitations and future enhancement opportunities

5. **Cross-Validate Critical Decisions**
   - Use multiple LLMs for important architectural decisions
   - Seek diverse perspectives on complex problems
   - Document alternative approaches considered

By following the DSRFlow process and adhering to these best practices, teams can leverage the power of LLMs to create well-documented, thoughtfully designed software systems that evolve through iterative refinement.