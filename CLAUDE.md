# Stock Analyzer - AI Assistant Guidelines

## Project Overview
This is an Angular TypeScript application for analyzing stock market data with interactive charts. The project follows Domain-Driven Design (DDD) and SOLID principles with a clean architecture pattern.

## Architecture & Structure

### Domain-Driven Design (DDD)
- **Domain Layer**: Core business logic and entities (`src/app/core/domain/`)
- **Application Layer**: Use cases and business workflows (`src/app/core/application/`)
- **Infrastructure Layer**: External services and repository implementations (`src/app/infrastructure/`)
- **Presentation Layer**: UI components and pages (`src/app/presentation/`)
- **Shared Layer**: Common utilities and interfaces (`src/app/shared/`)

### Project Structure
```
src/app/
├── core/
│   ├── domain/
│   │   ├── entities/          # Domain entities (Stock, StockPrice)
│   │   └── repositories/      # Repository abstractions
│   └── application/
│       └── use-cases/         # Business use cases
├── infrastructure/
│   ├── repositories/          # Repository implementations
│   └── services/              # External API services
├── presentation/
│   └── pages/                 # Page components
└── shared/
    ├── common/components/     # Reusable components
    └── interfaces/            # Shared interfaces
```

## Development Rules

### Code Quality Standards
1. **File Size**: Keep files under 500 lines for maintainability
2. **TypeScript**: Use strict TypeScript with proper type definitions
3. **Naming**: Use PascalCase for classes, camelCase for methods/properties
4. **Documentation**: Include JSDoc comments for public APIs
5. **Error Handling**: Implement proper error handling with custom error types

### Angular Best Practices
1. **Components**: Use OnPush change detection strategy when possible
2. **Services**: Mark services as `@Injectable({ providedIn: 'root' })` for tree-shaking
3. **Reactive Forms**: Use reactive forms over template-driven forms
4. **RxJS**: Use operators like `map`, `filter`, `switchMap` appropriately
5. **Lazy Loading**: Implement lazy loading for feature modules

### SOLID Principles Implementation
1. **Single Responsibility**: Each class/service has one reason to change
2. **Open/Closed**: Extend functionality through abstractions, not modifications
3. **Liskov Substitution**: Derived classes must be substitutable for base classes
4. **Interface Segregation**: Create specific interfaces rather than large ones
5. **Dependency Inversion**: Depend on abstractions, not concretions

### Testing Guidelines
1. **Unit Tests**: Use Jasmine/Karma for component and service testing
2. **Test Coverage**: Aim for 80%+ code coverage
3. **Test Structure**: Follow Arrange-Act-Assert pattern
4. **Mocking**: Use Angular testing utilities and jasmine spies
5. **Integration Tests**: Test component interactions and data flow

## API Integration
- **Financial Modeling Prep API**: External service for stock data
- **Environment Variables**: Store API keys in environment files
- **HTTP Interceptors**: Handle authentication and error responses
- **Repository Pattern**: Abstract API calls behind repository interfaces

## Commands & Scripts
- `ng serve`: Development server
- `ng build`: Production build
- `ng test`: Run unit tests
- `ng lint`: Run linting
- `ng e2e`: Run end-to-end tests

## AI Assistant Instructions

### When Making Changes
1. **Understand Context**: Always read existing code to understand patterns and conventions
2. **Follow Architecture**: Respect the DDD layers and don't create circular dependencies
3. **Maintain Consistency**: Use existing naming conventions and code style
4. **Update Tests**: Modify or create tests when changing functionality
5. **Document Changes**: Update relevant documentation and comments

### Code Generation Rules
1. **Use Existing Patterns**: Look at similar components/services before creating new ones
2. **Import Management**: Use barrel exports and proper import paths
3. **Type Safety**: Always provide proper TypeScript types
4. **Dependency Injection**: Use Angular's DI system correctly
5. **Error Handling**: Implement proper error handling with user-friendly messages

### Validation Steps
1. **Compile Check**: Ensure TypeScript compilation succeeds
2. **Lint Check**: Run linting to maintain code quality
3. **Test Check**: Verify all tests pass after changes
4. **Build Check**: Ensure production build works
5. **Manual Testing**: Test functionality in development server

### Don't Do
- Don't create circular dependencies between layers
- Don't put business logic in components
- Don't ignore TypeScript errors or use `any` type
- Don't create large monolithic files
- Don't skip error handling
- Don't modify core Angular files without good reason

### Communication
- Ask for clarification when requirements are unclear
- Explain architectural decisions when making significant changes
- Provide context for why certain patterns are used
- Suggest improvements when you notice anti-patterns

## External Dependencies
- **Angular**: v18+ with standalone components
- **Chart.js**: For interactive charts
- **RxJS**: For reactive programming
- **Financial Modeling Prep API**: Stock data source

## Environment Setup
1. Node.js v18+
2. Angular CLI
3. Financial Modeling Prep API key
4. Configure environment variables in `src/environments/`

Remember: This is a learning project focusing on clean architecture, so prioritize code quality and maintainability over quick fixes.