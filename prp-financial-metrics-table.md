# Product Requirements Prompt: Financial Metrics Table Implementation

## Feature Request
Add a comprehensive financial metrics table to the stock analysis page displaying essential financial parameters including valuation ratios, profitability metrics, balance sheet strength indicators, and growth metrics using the Financial Modeling Prep API.

## Feature Analysis

### Clear Description
Implement a financial metrics table component that displays critical financial parameters for stock analysis, including:
- **Valuation Ratios**: P/E, P/B, PEG, EV/EBITDA
- **Profitability Metrics**: ROE, ROA, Gross/Operating/Net Margins
- **Balance Sheet Strength**: Current Ratio, Quick Ratio, Debt-to-Equity
- **Growth Metrics**: Revenue Growth, Earnings Growth, Sustainable Growth Rate
- **Cash Flow Analysis**: Operating Cash Flow, Free Cash Flow, Cash Conversion Cycle

### Business Value and User Impact
- **Enhanced Analysis**: Users can perform comprehensive fundamental analysis beyond just price charts
- **Investment Screening**: Provides systematic framework for identifying quality companies with ROE >15%, debt-to-equity <1.0, and consistent growth
- **Risk Assessment**: Balance sheet metrics help identify financially healthy companies and avoid value traps
- **Industry Comparison**: Standardized metrics enable comparison across companies and sectors

### Technical Requirements and Constraints
- Must integrate with existing Financial Modeling Prep API
- Follow DDD architecture principles and maintain clean separation of concerns
- Display real-time financial data with proper error handling
- Responsive design for mobile and desktop viewing
- Maintain performance with lazy loading and caching strategies

## Architecture Review

### DDD Layer Impact Analysis

#### Domain Layer (`/core/domain/`)
**New Entities Required:**
- `FinancialMetrics`: Core financial ratios and metrics
- `FinancialStatements`: Income statement, balance sheet, cash flow data
- `KeyMetrics`: TTM (trailing twelve months) metrics
- `CompanyFundamentals`: Aggregate financial health indicators

**Repository Extensions:**
- Extend `StockDataRepository` with financial metrics retrieval methods
- Add proper error handling and data validation contracts

#### Application Layer (`/core/application/`)
**New Use Cases:**
- `GetFinancialMetricsUseCase`: Retrieve comprehensive financial metrics
- `GetCompanyFundamentalsUseCase`: Aggregate financial statements and ratios
- `AnalyzeFinancialHealthUseCase`: Business logic for financial health scoring

#### Infrastructure Layer (`/infrastructure/`)
**Service Extensions:**
- Enhance `FinancialModelingPrepService` with financial metrics endpoints
- Add data transformation and mapping for complex financial data
- Implement caching strategy for financial data

**Repository Implementations:**
- Update `StockDataRepositoryImpl` with financial metrics methods
- Add proper error handling for API failures

#### Presentation Layer (`/presentation/`)
**New Components:**
- `FinancialMetricsTableComponent`: Display financial metrics in tabular format
- `DataTableComponent`: Generic reusable table component
- `MetricCardComponent`: Individual metric display component

## Implementation Plan

### Phase 1: Domain Layer Foundation
1. **Create Financial Metrics Entities** (2-3 hours)
   - Define `FinancialMetrics` interface with all required metrics
   - Create `FinancialStatements` interfaces for income statement, balance sheet, cash flow
   - Add `KeyMetrics` interface for TTM data
   - Create `CompanyFundamentals` aggregate entity

2. **Extend Repository Contracts** (1 hour)
   - Add financial metrics methods to `StockDataRepository`
   - Define proper return types and error handling

### Phase 2: Infrastructure Layer Implementation
1. **Enhance API Service** (4-5 hours)
   - Add Financial Modeling Prep endpoints for:
     - `/key-metrics-ttm/{symbol}`
     - `/ratios/{symbol}`
     - `/income-statement/{symbol}`
     - `/balance-sheet/{symbol}`
     - `/cash-flow-statement/{symbol}`
   - Implement data transformation and mapping
   - Add comprehensive error handling

2. **Update Repository Implementation** (2 hours)
   - Implement financial metrics methods in `StockDataRepositoryImpl`
   - Add data aggregation and processing logic

### Phase 3: Application Layer Use Cases
1. **Create Use Cases** (3-4 hours)
   - Implement `GetFinancialMetricsUseCase`
   - Create `GetCompanyFundamentalsUseCase` with data aggregation
   - Add `AnalyzeFinancialHealthUseCase` for business rules

### Phase 4: Presentation Layer Components
1. **Create Shared Table Component** (4-5 hours)
   - Implement generic `DataTableComponent` with sorting and filtering
   - Add responsive design and accessibility features
   - Include loading states and error handling

2. **Financial Metrics Table Component** (3-4 hours)
   - Create `FinancialMetricsTableComponent`
   - Implement metric categorization and display
   - Add tooltips and explanations for complex metrics

3. **Enhanced Stock Analyzer Integration** (2-3 hours)
   - Add financial metrics tab to existing `StockAnalyzerComponent`
   - Implement data loading and state management
   - Add metric refresh and caching logic

### Phase 5: Testing and Validation
1. **Unit Tests** (4-5 hours)
   - Test all new use cases and services
   - Mock API responses and test error scenarios
   - Validate data transformation logic

2. **Component Tests** (3-4 hours)
   - Test financial metrics table component
   - Verify responsive design and accessibility
   - Test user interactions and state management

3. **Integration Tests** (2-3 hours)
   - Test complete data flow from API to UI
   - Verify error handling and loading states

## Technical Specifications

### TypeScript Interfaces

```typescript
// Core Financial Metrics Interface
export interface FinancialMetrics {
  symbol: string;
  companyName: string;
  marketCap: number;
  
  // Valuation Ratios
  peRatio: number;
  pegRatio: number;
  priceToBook: number;
  priceToSales: number;
  enterpriseValue: number;
  evToRevenue: number;
  evToEbitda: number;
  
  // Profitability Metrics
  profitMargin: number;
  operatingMargin: number;
  grossMargin: number;
  returnOnAssets: number;
  returnOnEquity: number;
  returnOnCapital: number;
  
  // Balance Sheet Strength
  currentRatio: number;
  quickRatio: number;
  debtToEquity: number;
  debtToAssets: number;
  interestCoverage: number;
  
  // Growth Metrics
  revenueGrowth: number;
  earningsGrowth: number;
  bookValueGrowth: number;
  sustainableGrowthRate: number;
  
  // Cash Flow Analysis
  operatingCashFlow: number;
  freeCashFlow: number;
  freeCashFlowMargin: number;
  cashConversionCycle: number;
  
  // Additional Metrics
  dividendYield: number;
  payoutRatio: number;
  beta: number;
  eps: number;
  
  lastUpdated: Date;
}

// Financial Statements Interfaces
export interface IncomeStatement {
  symbol: string;
  date: Date;
  revenue: number;
  costOfRevenue: number;
  grossProfit: number;
  operatingExpenses: number;
  operatingIncome: number;
  netIncome: number;
  eps: number;
  shares: number;
}

export interface BalanceSheet {
  symbol: string;
  date: Date;
  totalAssets: number;
  currentAssets: number;
  totalLiabilities: number;
  currentLiabilities: number;
  totalEquity: number;
  totalDebt: number;
  cash: number;
  inventory: number;
}

export interface CashFlowStatement {
  symbol: string;
  date: Date;
  operatingCashFlow: number;
  investingCashFlow: number;
  financingCashFlow: number;
  freeCashFlow: number;
  capitalExpenditures: number;
}
```

### Angular Component Structure

```typescript
// Financial Metrics Table Component
@Component({
  selector: 'app-financial-metrics-table',
  standalone: true,
  imports: [CommonModule, DataTableComponent],
  templateUrl: './financial-metrics-table.component.html',
  styleUrls: ['./financial-metrics-table.component.scss'],
  changeDetection: ChangeDetectionStrategy.OnPush
})
export class FinancialMetricsTableComponent {
  @Input() metrics: FinancialMetrics | null = null;
  @Input() loading: boolean = false;
  @Input() error: string | null = null;
  
  readonly metricCategories = [
    {
      name: 'Valuation Ratios',
      metrics: ['peRatio', 'pegRatio', 'priceToBook', 'evToEbitda']
    },
    {
      name: 'Profitability',
      metrics: ['returnOnEquity', 'returnOnAssets', 'profitMargin', 'operatingMargin']
    },
    {
      name: 'Balance Sheet',
      metrics: ['currentRatio', 'quickRatio', 'debtToEquity', 'interestCoverage']
    },
    {
      name: 'Growth',
      metrics: ['revenueGrowth', 'earningsGrowth', 'sustainableGrowthRate']
    }
  ];
}
```

### API Integration Requirements

```typescript
// Enhanced Financial Modeling Prep Service
@Injectable({
  providedIn: 'root'
})
export class FinancialModelingPrepService {
  private readonly baseUrl = 'https://financialmodelingprep.com/api/v3';
  
  // New Methods for Financial Metrics
  getKeyMetrics(symbol: string): Observable<KeyMetrics> {
    return this.http.get<KeyMetrics[]>(`${this.baseUrl}/key-metrics-ttm/${symbol}`)
      .pipe(
        map(data => data[0]),
        catchError(this.handleError)
      );
  }
  
  getFinancialRatios(symbol: string): Observable<FinancialRatios> {
    return this.http.get<FinancialRatios[]>(`${this.baseUrl}/ratios/${symbol}`)
      .pipe(
        map(data => data[0]),
        catchError(this.handleError)
      );
  }
  
  getIncomeStatement(symbol: string): Observable<IncomeStatement[]> {
    return this.http.get<IncomeStatement[]>(`${this.baseUrl}/income-statement/${symbol}`)
      .pipe(
        map(data => data.slice(0, 5)), // Last 5 years
        catchError(this.handleError)
      );
  }
  
  getBalanceSheet(symbol: string): Observable<BalanceSheet[]> {
    return this.http.get<BalanceSheet[]>(`${this.baseUrl}/balance-sheet-statement/${symbol}`)
      .pipe(
        map(data => data.slice(0, 5)), // Last 5 years
        catchError(this.handleError)
      );
  }
  
  // Aggregate method for comprehensive financial metrics
  getFinancialMetrics(symbol: string): Observable<FinancialMetrics> {
    return forkJoin({
      keyMetrics: this.getKeyMetrics(symbol),
      ratios: this.getFinancialRatios(symbol),
      incomeStatement: this.getIncomeStatement(symbol),
      balanceSheet: this.getBalanceSheet(symbol)
    }).pipe(
      map(data => this.aggregateFinancialMetrics(symbol, data)),
      catchError(this.handleError)
    );
  }
  
  private aggregateFinancialMetrics(symbol: string, data: any): FinancialMetrics {
    // Complex aggregation logic to combine multiple API responses
    // into a single FinancialMetrics object
  }
}
```

### State Management Approach

```typescript
// Enhanced Stock Analyzer Component
export class StockAnalyzerComponent implements OnInit, OnDestroy {
  // Existing properties...
  
  // Financial Metrics State
  financialMetrics$ = new BehaviorSubject<FinancialMetrics | null>(null);
  metricsLoading$ = new BehaviorSubject<boolean>(false);
  metricsError$ = new BehaviorSubject<string | null>(null);
  
  // Tab Management
  activeTab$ = new BehaviorSubject<'chart' | 'metrics'>('chart');
  
  constructor(
    private getHistoricalPricesUseCase: GetHistoricalPricesUseCase,
    private getFinancialMetricsUseCase: GetFinancialMetricsUseCase,
    private cdr: ChangeDetectorRef
  ) {}
  
  loadFinancialMetrics(symbol: string): void {
    this.metricsLoading$.next(true);
    this.metricsError$.next(null);
    
    this.getFinancialMetricsUseCase.execute(symbol)
      .pipe(
        takeUntil(this.destroy$),
        finalize(() => this.metricsLoading$.next(false))
      )
      .subscribe({
        next: (metrics) => {
          this.financialMetrics$.next(metrics);
          this.cdr.markForCheck();
        },
        error: (error) => {
          this.metricsError$.next('Failed to load financial metrics');
          this.cdr.markForCheck();
        }
      });
  }
}
```

## Testing Strategy

### Unit Tests Coverage
1. **Domain Entities**: Validate interfaces and data models
2. **Use Cases**: Test business logic and data aggregation
3. **Services**: Mock API responses and test error handling
4. **Components**: Test user interactions and state management

### Integration Tests
1. **API Integration**: Test Financial Modeling Prep endpoints
2. **Data Flow**: Verify complete data flow from API to UI
3. **Error Scenarios**: Test network failures and API errors

### E2E Tests
1. **User Workflows**: Test complete user journey from search to metrics display
2. **Cross-browser Testing**: Ensure compatibility across different browsers
3. **Performance Testing**: Verify table rendering performance with large datasets

## Quality Assurance

### Code Review Checklist
- [ ] Follows DDD architecture principles
- [ ] Proper TypeScript typing throughout
- [ ] Comprehensive error handling
- [ ] Responsive design implementation
- [ ] Accessibility standards (WCAG 2.1)
- [ ] Performance optimization
- [ ] Unit test coverage >80%

### Performance Considerations
- Implement virtual scrolling for large datasets
- Use OnPush change detection strategy
- Implement proper caching for financial data
- Optimize API calls with request batching

### Security Requirements
- Validate all API responses
- Sanitize financial data display
- Implement proper error handling without exposing sensitive information
- Use HTTPS for all API communications

### Accessibility Standards
- Proper ARIA labels for financial data
- Keyboard navigation support
- Screen reader compatibility
- Color contrast compliance for financial indicators

## Documentation

### Code Documentation
- JSDoc comments for all public APIs
- Inline comments for complex financial calculations
- Component documentation with usage examples

### User Documentation
- Tooltip explanations for financial metrics
- Help section explaining financial ratios
- Industry benchmark information

### Technical Documentation
- API endpoint documentation
- Data transformation logic
- Error handling procedures

## Execution Guidelines

### Development Standards
- Follow existing code patterns and conventions
- Maintain DDD architecture principles
- Use strict TypeScript with proper type definitions
- Implement comprehensive error handling
- Write unit tests for all new functionality

### Validation Steps
1. Run `ng build` to verify TypeScript compilation
2. Run `ng lint` to check code quality
3. Run `ng test` to verify all tests pass
4. Run `ng serve` to test functionality
5. Verify responsive design on different screen sizes

## Success Criteria

### Functional Requirements
- [ ] Financial metrics table displays all required metrics
- [ ] Data is fetched from Financial Modeling Prep API
- [ ] Proper error handling and loading states
- [ ] Responsive design for mobile and desktop
- [ ] Accessible to users with disabilities

### Technical Requirements
- [ ] Follows DDD architecture principles
- [ ] No circular dependencies
- [ ] TypeScript compilation succeeds
- [ ] All unit tests pass (>80% coverage)
- [ ] Linting passes without errors
- [ ] Production build succeeds

### Performance Requirements
- [ ] Table renders within 2 seconds
- [ ] Smooth scrolling and interactions
- [ ] Efficient memory usage
- [ ] Proper caching implementation

### Quality Requirements
- [ ] Code follows project standards
- [ ] Comprehensive documentation
- [ ] Error scenarios handled gracefully
- [ ] Cross-browser compatibility
- [ ] Accessibility compliance

## Risk Mitigation

### Technical Risks
- **API Rate Limits**: Implement proper caching and request throttling
- **Data Inconsistencies**: Add data validation and error handling
- **Performance Issues**: Use virtual scrolling and lazy loading

### Business Risks
- **User Confusion**: Provide clear explanations and tooltips
- **Data Accuracy**: Clearly indicate data sources and update times
- **Mobile Usability**: Ensure table is usable on small screens

## Implementation Timeline

**Total Estimated Time**: 25-30 hours

- **Phase 1**: Domain Layer (3-4 hours)
- **Phase 2**: Infrastructure Layer (6-7 hours)
- **Phase 3**: Application Layer (3-4 hours)
- **Phase 4**: Presentation Layer (9-10 hours)
- **Phase 5**: Testing and Validation (4-5 hours)

This PRP provides a comprehensive roadmap for implementing a robust financial metrics table that enhances the Stock Analyzer application while maintaining architectural integrity and code quality standards.