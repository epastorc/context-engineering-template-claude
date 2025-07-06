# Context Engineering Template

This repository demonstrates an Angular project following Domain-Driven Design (DDD) and SOLID principles, using context engineering to generate high-quality code with AI assistance. It serves as a practical example of how structured context and clear guidelines can improve AI-assisted development workflows.

## Quick Start

1. Clone this repository
2. Try the context engineering workflow:
   ```bash
   # Generate a new PRP (Product Requirements Prompt)
   generate-prp "Add user authentication feature with JWT tokens"
   
   # Execute the generated PRP
   execute-prp prp-user-authentication.md
   ```

## Table of Contents

- [What is Context Engineering](#what-is-context-engineering)
- [Template Structure](#template-structure)
- [Step-by-Step Guide](#step-by-step-guide)
- [Commands](#commands)
- [Best Practices](#best-practices)
- [Resources](#resources)

## What is Context Engineering

Context engineering is the practice of providing AI assistants with structured context and instructions to improve their performance on specific tasks. It involves crafting clear, comprehensive instructions that guide AI behavior and decision-making within a particular domain or project.

### Context Engineering vs Prompt Engineering

- **Prompt Engineering**: Crafting individual prompts for specific tasks
- **Context Engineering**: Creating comprehensive, persistent context that guides AI behavior across entire projects

### Why Context Engineering Matters

Context engineering is 10x better than prompt engineering and 100x better than "vibe coding" because it:

- Provides consistent behavior across development sessions
- Reduces the need for repetitive explanations
- Ensures adherence to architectural patterns and best practices
- Maintains code quality and project standards automatically

## Template Structure

This template demonstrates context engineering through:

```
├── CLAUDE.md                 # Main context engineering file
├── example-prp/             # Example of PRP generation
│   └── prp-financial-metrics-table.md  # Sample PRP for financial metrics feature
├── src/app/
│   ├── core/
│   │   ├── domain/          # Domain entities and repositories
│   │   └── application/     # Use cases and business logic
│   ├── infrastructure/      # External services and implementations
│   ├── presentation/        # UI components and pages
│   └── shared/             # Common utilities and interfaces
└── README.md               # This file
```


## Step-by-Step Guide

### 1. Set Up Global Rules

The `CLAUDE.md` file contains:
- Project overview and architecture guidelines
- Development rules and code quality standards
- Angular best practices and SOLID principles
- Testing guidelines and validation steps

### 2. Create Initial Feature Request

Define what you want to build with clear requirements and acceptance criteria.

### 3. Generate PRP 

Use the `generate-prp "description of the task"` command to create a detailed proposal for your feature implementation.

### 4. Execute PRP

Use the `execute-prp prp-file-name` command to implement the proposed changes following the established patterns.

## Commands

This template includes custom commands for context engineering workflows:

- `execute-prp prp-file-name` - Execute a Product Requirements Prompt following established patterns
- `generate-prp "description"` - Generate a Product Requirements Prompt with detailed implementation plan
- `refactor` - Refactor existing code following DDD and SOLID principles
- `validate` - Validate code against project standards and run tests

## Best Practices

1. **Clear Instructions**: Provide explicit guidelines on what to do and what not to do
2. **Domain-Specific Knowledge**: Include relevant information about the project architecture
3. **Structured Context**: Organize information in logical, hierarchical manner
4. **Behavioral Guidelines**: Define how the AI should interact and respond
5. **Validation Steps**: Always include steps to verify code quality and functionality

## Resources

### Context Engineering Resources

- **Original Context Engineering Guide**: [Context Engineering Introduction](https://github.com/coleam00/context-engineering-intro)
- **LangChain - Context Engineering for Agents**: [Context Engineering Strategies](https://blog.langchain.com/context-engineering-for-agents/)
- **LangChain - The Rise of Context Engineering**: [Context Engineering Evolution](https://blog.langchain.com/the-rise-of-context-engineering/)

### Development Resources

- **Angular Documentation**: [Angular.io](https://angular.io)
- **Domain-Driven Design**: Principles and patterns for complex applications
- **SOLID Principles**: Object-oriented design principles for maintainable code

---
