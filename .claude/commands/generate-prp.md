# Generate Stock Analyzer PRP

Generate a comprehensive Product Requirements Prompt for the Stock Analyzer application.

## Feature Request: $ARGUMENTS

## Generation Process

1. **Analyze Request**
   - Understand the feature request thoroughly
   - Read the project's CLAUDE.md file for complete context
   - Review current codebase structure and existing patterns
   - Analyze any existing feature requests or documentation
   - Identify business value and user impact

2. **Architecture Analysis**
   - Determine how the feature fits into the existing DDD structure
   - Identify which layers will be affected (Domain, Application, Infrastructure, Presentation)
   - Consider any new abstractions or patterns needed
   - Ensure alignment with SOLID principles

3. **Generate Comprehensive PRP**
   - Create a detailed Product Requirements Prompt that includes:

### 1. Feature Analysis
- Clear description of the requested feature
- Business value and user impact
- Technical requirements and constraints

### 2. Architecture Review
- How the feature fits into the existing DDD structure
- Which layers will be affected (Domain, Application, Infrastructure, Presentation)
- Any new abstractions or patterns needed

### 3. Implementation Plan
- Step-by-step development approach
- File structure and naming conventions
- Dependencies and third-party integrations

### 4. Technical Specifications
- TypeScript interfaces and types
- Angular components and services structure
- API integration requirements
- State management approach

### 5. Testing Strategy
- Unit tests for each layer
- Integration tests for data flow
- E2E tests for user interactions
- Test data and mock requirements

### 6. Quality Assurance
- Code review checklist
- Performance considerations
- Security requirements
- Accessibility standards

### 7. Documentation
- Update existing documentation
- New documentation requirements
- Code comments and JSDoc

4. **Create Implementation Guidelines**
   - Define execution guidelines for the PRP
   - Include validation steps and success criteria
   - Specify testing requirements and quality standards
   - Document any constraints or considerations

5. **Output PRP File**
   - Generate the complete PRP as a markdown file
   - Include all necessary sections and details
   - Ensure the PRP is ready for execution
   - Save the PRP file for future reference

## PRP Template Structure

The generated PRP should include:
- **Feature Analysis**: Clear description, business value, technical requirements
- **Architecture Review**: DDD layer impacts, new abstractions needed
- **Implementation Plan**: Step-by-step approach, file structure, dependencies
- **Technical Specifications**: TypeScript interfaces, Angular components, API integration
- **Testing Strategy**: Unit tests, integration tests, E2E tests, test data
- **Quality Assurance**: Code review checklist, performance, security, accessibility
- **Documentation**: Updates needed, new documentation, JSDoc comments

## Execution Guidelines for Generated PRP
- Follow existing code patterns and conventions
- Maintain DDD architecture principles
- Ensure type safety throughout
- Include proper error handling
- Consider performance implications
- Write comprehensive tests

## Success Criteria
- Feature works as specified
- All tests pass
- Code follows project standards
- Documentation is updated
- No architectural violations

Generate a comprehensive PRP file that can be executed using the execute-prp command.