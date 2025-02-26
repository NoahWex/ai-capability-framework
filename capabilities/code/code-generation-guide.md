# Code Generation Framework

*Created: 2025-02-26T05:55:00Z*  
*Last Modified: 2025-02-26T05:55:00Z*  
*Version: 1.0*

## Overview

The Code Generation Framework provides standardized patterns and practices for creating high-quality, maintainable code across multiple programming languages. This guide establishes consistent approaches to code structure, documentation, error handling, and integration with other capabilities.

## Core Principles

### 1. Clarity Over Cleverness

Code should prioritize clarity and readability over clever or terse implementations. This means:

- Using descriptive variable and function names
- Breaking complex operations into well-named helper functions
- Adding appropriate comments for non-obvious logic
- Using standard language idioms rather than obscure features

### 2. Context-Appropriate Solutions

Code solutions should be tailored to the specific context in which they will be used:

- Consider the user's experience level and adjust complexity accordingly
- Match the style of existing codebase when extending or modifying code
- Select appropriate libraries and frameworks based on project requirements
- Adjust verbosity of comments and documentation to match user needs

### 3. Robust Error Handling

All code should include appropriate error handling:

- Use language-specific exception handling mechanisms
- Provide meaningful error messages that guide toward resolution
- Validate inputs before processing
- Fail gracefully when unexpected conditions occur

### 4. Testability and Maintainability

Code should be structured to facilitate testing and future maintenance:

- Keep functions focused on single responsibilities
- Minimize dependencies between components
- Use dependency injection or similar patterns to increase testability
- Include examples of unit tests when appropriate

## Language-Specific Guidelines

### Python

#### Style and Formatting

- Follow [PEP 8](https://www.python.org/dev/peps/pep-0008/) conventions
- Use 4 spaces for indentation (not tabs)
- Limit line length to 79-88 characters
- Use snake_case for variables and function names
- Use PascalCase for class names
- Group imports in the standard order: standard library, third-party, local application

#### Documentation

- Use Google-style docstrings:

```python
def example_function(param1, param2):
    """Summary of function purpose.
    
    More detailed description that explains what the function
    does, any algorithms used, and its general purpose.
    
    Args:
        param1 (type): Description of param1
        param2 (type): Description of param2
        
    Returns:
        return_type: Description of return value
        
    Raises:
        ExceptionType: When and why this exception may be raised
    """
    # Function implementation
```

- Include type hints for function parameters and return values:

```python
def calculate_total(prices: list[float], discount: float = 0.0) -> float:
    """Calculate total price after applying discount.
    
    Args:
        prices: List of individual prices
        discount: Discount as a decimal percentage (default: 0.0)
        
    Returns:
        Total price after discount
    """
    subtotal = sum(prices)
    return subtotal * (1 - discount)
```

#### Best Practices

- Use list/dict/set comprehensions for simple transformations
- Prefer composition over inheritance for most cases
- Use context managers (`with` statements) for resource management
- Use dataclasses or named tuples for data containers
- Leverage Python's built-in functions and standard library

#### Error Handling

```python
def process_data(filename):
    """Process data from a file.
    
    Args:
        filename: Path to the file to process
        
    Returns:
        Processed data as a dictionary
        
    Raises:
        FileNotFoundError: If the file doesn't exist
        ValueError: If the file has invalid format
    """
    try:
        with open(filename, 'r') as file:
            data = file.read()
    except FileNotFoundError:
        raise FileNotFoundError(f"File not found: {filename}")
    
    try:
        return parse_data(data)
    except Exception as e:
        raise ValueError(f"Invalid data format in {filename}: {str(e)}")
```

### JavaScript/TypeScript

#### Style and Formatting

- Follow [Airbnb JavaScript Style Guide](https://github.com/airbnb/javascript)
- Use 2 spaces for indentation
- Use semicolons after statements
- Use camelCase for variables and functions
- Use PascalCase for classes and React components
- Use UPPERCASE_SNAKE_CASE for constants

#### Documentation

- Use JSDoc for documentation:

```javascript
/**
 * Calculate total price after applying discount
 * 
 * @param {number[]} prices - List of individual prices
 * @param {number} [discount=0] - Discount as a decimal percentage
 * @returns {number} Total price after discount
 */
function calculateTotal(prices, discount = 0) {
  const subtotal = prices.reduce((sum, price) => sum + price, 0);
  return subtotal * (1 - discount);
}
```

- For TypeScript, use proper type annotations:

```typescript
/**
 * Calculate total price after applying discount
 * 
 * @param prices - List of individual prices
 * @param discount - Discount as a decimal percentage
 * @returns Total price after discount
 */
function calculateTotal(prices: number[], discount: number = 0): number {
  const subtotal = prices.reduce((sum, price) => sum + price, 0);
  return subtotal * (1 - discount);
}
```

#### Best Practices

- Use ES6+ features (arrow functions, destructuring, spread/rest operators)
- Prefer `const` over `let`, avoid `var`
- Use async/await for asynchronous operations
- Use functional programming patterns for data transformations
- Implement proper error handling with try/catch

#### Error Handling

```javascript
/**
 * Fetch and process user data
 * 
 * @param {string} userId - ID of the user to fetch
 * @returns {Promise<Object>} Processed user data
 * @throws {Error} If user cannot be found or data is invalid
 */
async function fetchUserData(userId) {
  try {
    const response = await fetch(`/api/users/${userId}`);
    
    if (!response.ok) {
      throw new Error(`HTTP error! status: ${response.status}`);
    }
    
    const data = await response.json();
    return processUserData(data);
  } catch (error) {
    console.error(`Error fetching user ${userId}:`, error);
    throw new Error(`Failed to fetch user data: ${error.message}`);
  }
}
```

### SQL

#### Style and Formatting

- Use uppercase for SQL keywords (SELECT, FROM, WHERE)
- Use lowercase for table and column names
- Use underscores for table and column names (snake_case)
- Indent subqueries and separate logical parts
- Use meaningful table aliases

#### Documentation

- Include a header comment explaining the query's purpose
- Document complex join conditions or filtering logic
- Explain the expected result set

```sql
-- Find active customers who haven't placed an order in the last 90 days
-- Returns: customer_id, name, email, days_since_last_order
SELECT 
  c.customer_id,
  c.name,
  c.email,
  DATEDIFF(CURRENT_DATE, MAX(o.order_date)) AS days_since_last_order
FROM 
  customers c
  -- Only include customers with at least one order
  LEFT JOIN orders o ON c.customer_id = o.customer_id
WHERE 
  c.status = 'active'
GROUP BY 
  c.customer_id, c.name, c.email
HAVING 
  -- No orders or last order was more than 90 days ago
  MAX(o.order_date) IS NULL OR DATEDIFF(CURRENT_DATE, MAX(o.order_date)) > 90
ORDER BY 
  days_since_last_order DESC;
```

#### Best Practices

- Use parameterized queries to prevent SQL injection
- Include appropriate indexes for performance
- Use CTEs (Common Table Expressions) for readability
- Limit result sets for performance
- Use appropriate join types (INNER, LEFT, RIGHT)

#### Performance Considerations

```sql
-- Using a CTE for readability and maintainability
WITH recent_orders AS (
  SELECT 
    customer_id,
    MAX(order_date) AS last_order_date
  FROM 
    orders
  WHERE 
    order_date > DATE_SUB(CURRENT_DATE, INTERVAL 1 YEAR)
  GROUP BY 
    customer_id
),
customer_spend AS (
  SELECT
    customer_id,
    SUM(total_amount) AS total_spent
  FROM
    orders
  WHERE
    order_date > DATE_SUB(CURRENT_DATE, INTERVAL 1 YEAR)
  GROUP BY
    customer_id
)
SELECT
  c.customer_id,
  c.name,
  c.email,
  ro.last_order_date,
  COALESCE(cs.total_spent, 0) AS yearly_spend
FROM
  customers c
  LEFT JOIN recent_orders ro ON c.customer_id = ro.customer_id
  LEFT JOIN customer_spend cs ON c.customer_id = cs.customer_id
WHERE
  c.status = 'active'
ORDER BY
  yearly_spend DESC
LIMIT 100;
```

### R

#### Style and Formatting

- Follow [tidyverse style guide](https://style.tidyverse.org/)
- Use 2 spaces for indentation
- Limit line length to 80 characters
- Use snake_case for variables and functions
- Use `<-` for assignment, not `=`

#### Documentation

- Use roxygen2 style documentation:

```r
#' Calculate total price after applying discount
#'
#' @param prices A numeric vector of individual prices
#' @param discount Discount as a decimal percentage (default: 0)
#'
#' @return The total price after discount
#' @export
#'
#' @examples
#' calculate_total(c(10.50, 20.75, 30.00), 0.1)
calculate_total <- function(prices, discount = 0) {
  subtotal <- sum(prices)
  return(subtotal * (1 - discount))
}
```

#### Best Practices

- Use tidyverse packages for data manipulation and visualization
- Use piping (`%>%` or `|>`) for readable data transformations
- Use tibbles instead of data frames when practical
- Use vectorized operations rather than loops
- Properly handle missing values (NA)

#### Data Analysis Example

```r
library(tidyverse)

#' Analyze customer order patterns
#'
#' @param order_data Tibble containing order information
#' @param min_orders Minimum number of orders to include customer
#'
#' @return Tibble with customer order statistics
analyze_customer_orders <- function(order_data, min_orders = 5) {
  # Input validation
  if (!is.data.frame(order_data)) {
    stop("order_data must be a data frame or tibble")
  }
  
  required_cols <- c("customer_id", "order_date", "order_total")
  missing_cols <- setdiff(required_cols, names(order_data))
  if (length(missing_cols) > 0) {
    stop(paste("Missing required columns:", paste(missing_cols, collapse = ", ")))
  }
  
  # Analysis with tidyverse pipeline
  result <- order_data %>%
    group_by(customer_id) %>%
    summarize(
      order_count = n(),
      first_order = min(order_date),
      last_order = max(order_date),
      total_spent = sum(order_total),
      avg_order_value = mean(order_total),
      days_between_orders = if_else(
        order_count > 1,
        as.numeric(difftime(max(order_date), min(order_date), units = "days")) / (order_count - 1),
        NA_real_
      )
    ) %>%
    filter(order_count >= min_orders) %>%
    arrange(desc(total_spent))
  
  return(result)
}
```

## Code Integration with Other Capabilities

### Sequential Thinking + Code Generation

Combine sequential thinking for algorithm design with code implementation:

1. **Thought Process**:
   ```
   1. First, understand the problem requirements
   2. Break down the algorithm into logical steps
   3. Consider edge cases and input validation
   4. Design the data structures and functions
   5. Implement the solution with appropriate error handling
   ```

2. **Code Implementation**:
   ```python
   def find_longest_palindrome(text: str) -> str:
       """Find the longest palindromic substring in the given text.
       
       Args:
           text: Input string to search for palindromes
           
       Returns:
           The longest palindromic substring
       """
       # Input validation
       if not text:
           return ""
       
       # Initialize variables to track longest palindrome
       longest = ""
       max_length = 0
       
       # Helper function to expand around center
       def expand_around_center(left: int, right: int) -> str:
           # Expand while within bounds and characters match
           while left >= 0 and right < len(text) and text[left] == text[right]:
               left -= 1
               right += 1
           # Return the palindromic substring
           return text[left + 1:right]
       
       # Check each possible center position
       for i in range(len(text)):
           # Check odd-length palindromes (centered on a character)
           odd_palindrome = expand_around_center(i, i)
           if len(odd_palindrome) > max_length:
               longest = odd_palindrome
               max_length = len(odd_palindrome)
               
           # Check even-length palindromes (centered between characters)
           even_palindrome = expand_around_center(i, i + 1)
           if len(even_palindrome) > max_length:
               longest = even_palindrome
               max_length = len(even_palindrome)
       
       return longest
   ```

### Knowledge Graph + Code Generation

Use knowledge graph to store and retrieve code patterns:

1. **Knowledge Representation**:
   ```
   Entity: "PalindromeAlgorithm"
   Type: "Algorithm"
   Observations:
     - "Time complexity: O(n²)"
     - "Space complexity: O(1)"
     - "Approach: Expand around center"
     - "Alternative approach: Dynamic programming"
   ```

2. **Code Implementation with Knowledge**:
   ```python
   def find_longest_palindrome(text: str) -> str:
       """Find the longest palindromic substring using center expansion approach.
       
       This implementation uses the "expand around center" approach with O(n²) time 
       complexity and O(1) space complexity as documented in the knowledge graph
       entity "PalindromeAlgorithm".
       
       Args:
           text: Input string to search for palindromes
           
       Returns:
           The longest palindromic substring
       """
       # Implementation follows...
   ```

### Search + Code Generation

Leverage search to find optimal implementations:

1. **Search Query**:
   ```
   search_query = "efficient algorithms for finding longest palindromic substring"
   ```

2. **Integration with Code**:
   ```python
   # Implementation based on Manacher's algorithm found through search
   # This improves time complexity to O(n) compared to the O(n²) naive approach
   def find_longest_palindrome_optimized(text: str) -> str:
       """Find the longest palindromic substring using Manacher's algorithm.
       
       This implementation has O(n) time complexity, an improvement over the
       standard expansion approach based on search results for efficient
       palindrome algorithms.
       
       Args:
           text: Input string to search for palindromes
           
       Returns:
           The longest palindromic substring
       """
       # Preprocess the string
       modified = '#' + '#'.join(text) + '#'
       n = len(modified)
       
       # Initialize array to store palindrome lengths
       p = [0] * n
       
       # Variables to track center and right boundary
       center = right = 0
       
       # Manacher's algorithm
       for i in range(n):
           # Mirror index
           mirror = 2 * center - i
           
           # If within right boundary, use mirror value
           if right > i:
               p[i] = min(right - i, p[mirror])
           
           # Expand around center
           while (i + 1 + p[i] < n and i - 1 - p[i] >= 0 and 
                 modified[i + 1 + p[i]] == modified[i - 1 - p[i]]):
               p[i] += 1
           
           # Update center and right boundary if needed
           if i + p[i] > right:
               center = i
               right = i + p[i]
       
       # Find the maximum palindrome length
       max_len = max(p)
       center_index = p.index(max_len)
       
       # Extract the palindrome from the original string
       start = (center_index - max_len) // 2
       return text[start:start + max_len]
   ```

### GitHub Integration + Code Generation

Use GitHub to find and adapt existing implementations:

1. **Repository Search**:
   ```
   repositories = search_repositories({
       "query": "algorithm palindrome implementation language:python stars:>100"
   })
   ```

2. **Code Search**:
   ```
   code_examples = search_code({
       "q": "function find_longest_palindrome language:python"
   })
   ```

3. **Adapted Implementation**:
   ```python
   # Adapted from highly-starred implementation found on GitHub
   # Original source: github.com/algorithms/python-algorithms (MIT License)
   
   def find_longest_palindrome(text: str) -> str:
       """Find the longest palindromic substring in the given text.
       
       This implementation is adapted from a well-tested, popular 
       GitHub repository with appropriate optimizations.
       
       Args:
           text: Input string to search for palindromes
           
       Returns:
           The longest palindromic substring
       """
       # Implementation follows...
   ```

## Common Code Patterns

### Data Processing Pipeline

```python
def process_data_pipeline(input_data, config=None):
    """Process data through a multi-stage pipeline.
    
    Args:
        input_data: The raw input data to process
        config: Optional configuration dictionary
    
    Returns:
        Processed data ready for analysis
    """
    # Set default configuration
    if config is None:
        config = {
            'clean_nulls': True,
            'normalize_fields': True,
            'aggregate_level': 'daily'
        }
    
    # Stage 1: Validation
    validated_data = validate_input(input_data)
    
    # Stage 2: Cleaning
    if config['clean_nulls']:
        cleaned_data = clean_null_values(validated_data)
    else:
        cleaned_data = validated_data
    
    # Stage 3: Transformation
    if config['normalize_fields']:
        transformed_data = normalize_field_names(cleaned_data)
    else:
        transformed_data = cleaned_data
    
    # Stage 4: Aggregation
    aggregated_data = aggregate_by_level(
        transformed_data, 
        level=config['aggregate_level']
    )
    
    # Stage 5: Final formatting
    result = format_for_output(aggregated_data)
    
    return result
```

### API Client Pattern

```python
class APIClient:
    """Client for interacting with a REST API."""
    
    def __init__(self, base_url, api_key=None, timeout=30):
        """Initialize the API client.
        
        Args:
            base_url: Base URL for the API
            api_key: Optional API key for authentication
            timeout: Request timeout in seconds
        """
        self.base_url = base_url.rstrip('/')
        self.api_key = api_key
        self.timeout = timeout
        self.session = self._create_session()
    
    def _create_session(self):
        """Create a requests session with appropriate headers."""
        session = requests.Session()
        headers = {
            'User-Agent': 'APIClient/1.0',
            'Accept': 'application/json',
        }
        
        if self.api_key:
            headers['Authorization'] = f'Bearer {self.api_key}'
            
        session.headers.update(headers)
        return session
    
    def _handle_response(self, response):
        """Handle API response and errors.
        
        Args:
            response: Response object from requests
            
        Returns:
            Parsed JSON response
            
        Raises:
            APIError: If the API returns an error
        """
        try:
            response.raise_for_status()
            return response.json()
        except requests.exceptions.HTTPError as error:
            # Try to get error details from response
            error_detail = None
            try:
                error_detail = response.json()
            except ValueError:
                error_detail = response.text
                
            raise APIError(f"HTTP Error: {error}", response.status_code, error_detail)
        except ValueError:
            raise APIError("Invalid JSON in response", response.status_code, response.text)
    
    def get(self, endpoint, params=None):
        """Make a GET request to the API.
        
        Args:
            endpoint: API endpoint path
            params: Optional query parameters
            
        Returns:
            Parsed JSON response
        """
        url = f"{self.base_url}/{endpoint.lstrip('/')}"
        
        try:
            response = self.session.get(
                url,
                params=params,
                timeout=self.timeout
            )
            return self._handle_response(response)
        except requests.exceptions.RequestException as error:
            raise APIError(f"Request failed: {error}", None, None)
    
    # Additional methods for POST, PUT, DELETE, etc.
    # ...


class APIError(Exception):
    """Exception raised for API request errors."""
    
    def __init__(self, message, status_code=None, error_detail=None):
        """Initialize the exception.
        
        Args:
            message: Error message
            status_code: HTTP status code, if applicable
            error_detail: Additional error details from the API
        """
        self.status_code = status_code
        self.error_detail = error_detail
        super().__init__(message)
```

### Data Analysis Workflow (R)

```r
#' Complete data analysis workflow
#'
#' @param data_file Path to input data file
#' @param output_dir Directory for output files
#' @param parameters List of analysis parameters
#'
#' @return List containing analysis results and paths to generated outputs
#' @export
analyze_workflow <- function(data_file, output_dir, parameters = list()) {
  # Setup -------------------------------------------------------------------
  library(tidyverse)
  library(lubridate)
  
  # Create output directory if it doesn't exist
  if (!dir.exists(output_dir)) {
    dir.create(output_dir, recursive = TRUE)
  }
  
  # Set default parameters if not provided
  if (is.null(parameters$date_column)) parameters$date_column <- "date"
  if (is.null(parameters$value_column)) parameters$value_column <- "value"
  if (is.null(parameters$group_column)) parameters$group_column <- "group"
  
  # Data loading and validation ---------------------------------------------
  tryCatch({
    # Detect file format and read accordingly
    if (grepl("\\.csv$", data_file)) {
      raw_data <- read_csv(data_file)
    } else if (grepl("\\.rds$", data_file)) {
      raw_data <- readRDS(data_file)
    } else {
      stop("Unsupported file format. Use CSV or RDS.")
    }
    
    # Validate required columns
    required_cols <- c(parameters$date_column, parameters$value_column)
    missing_cols <- setdiff(required_cols, names(raw_data))
    if (length(missing_cols) > 0) {
      stop(paste("Missing required columns:", paste(missing_cols, collapse = ", ")))
    }
  }, error = function(e) {
    stop(paste("Error loading data:", e$message))
  })
  
  # Data cleaning and preparation -------------------------------------------
  clean_data <- raw_data %>%
    # Convert date column to proper date type
    mutate(date = as_date(!!sym(parameters$date_column))) %>%
    # Remove rows with missing values in key columns
    drop_na(!!sym(parameters$value_column)) %>%
    # Sort by date
    arrange(date)
  
  # Save cleaned data
  clean_data_path <- file.path(output_dir, "clean_data.rds")
  saveRDS(clean_data, clean_data_path)
  
  # Exploratory analysis ----------------------------------------------------
  # Summary statistics
  summary_stats <- clean_data %>%
    group_by(!!sym(parameters$group_column)) %>%
    summarize(
      count = n(),
      mean_value = mean(!!sym(parameters$value_column)),
      median_value = median(!!sym(parameters$value_column)),
      min_value = min(!!sym(parameters$value_column)),
      max_value = max(!!sym(parameters$value_column)),
      sd_value = sd(!!sym(parameters$value_column))
    )
  
  # Time series plot
  time_plot <- ggplot(clean_data, aes(x = date, y = !!sym(parameters$value_column), 
                                      color = !!sym(parameters$group_column))) +
    geom_line() +
    labs(
      title = "Time Series Analysis",
      x = "Date",
      y = parameters$value_column,
      color = parameters$group_column
    ) +
    theme_minimal()
  
  # Save plot
  time_plot_path <- file.path(output_dir, "time_series_plot.pdf")
  ggsave(time_plot_path, plot = time_plot, width = 10, height = 6)
  
  # Distribution plot
  dist_plot <- ggplot(clean_data, aes(x = !!sym(parameters$value_column), 
                                     fill = !!sym(parameters$group_column))) +
    geom_histogram(alpha = 0.7, position = "identity", bins = 30) +
    labs(
      title = "Value Distribution",
      x = parameters$value_column,
      y = "Count",
      fill = parameters$group_column
    ) +
    theme_minimal()
  
  # Save plot
  dist_plot_path <- file.path(output_dir, "distribution_plot.pdf")
  ggsave(dist_plot_path, plot = dist_plot, width = 10, height = 6)
  
  # Advanced analysis -------------------------------------------------------
  # Trend analysis by group
  trend_analysis <- clean_data %>%
    group_by(!!sym(parameters$group_column)) %>%
    do(model = lm(formula = paste(parameters$value_column, "~ date"), data = .)) %>%
    mutate(
      slope = coef(model)[2],
      p_value = summary(model)$coefficients[2, 4],
      significant = p_value < 0.05
    ) %>%
    select(-model)
  
  # Seasonal decomposition if applicable
  seasonal_results <- list()
  if (parameters$seasonal_analysis && length(unique(clean_data$date)) > 24) {
    clean_data %>%
      group_by(!!sym(parameters$group_column)) %>%
      do({
        # Convert to time series object
        ts_data <- ts(
          .$value, 
          frequency = parameters$seasonal_frequency
        )
        
        # Decompose
        decomp <- decompose(ts_data)
        
        # Return components
        tibble(
          date = .$date,
          observed = as.numeric(decomp$x),
          trend = as.numeric(decomp$trend),
          seasonal = as.numeric(decomp$seasonal),
          remainder = as.numeric(decomp$random)
        )
      }) -> seasonal_data
    
    seasonal_results$data <- seasonal_data
    
    # Create decomposition plot
    seasonal_plot <- seasonal_data %>%
      pivot_longer(cols = c(observed, trend, seasonal, remainder),
                  names_to = "component", values_to = "value") %>%
      ggplot(aes(x = date, y = value)) +
      geom_line() +
      facet_grid(component ~ !!sym(parameters$group_column), scales = "free_y") +
      labs(title = "Seasonal Decomposition") +
      theme_minimal()
    
    # Save plot
    seasonal_plot_path <- file.path(output_dir, "seasonal_decomposition.pdf")
    ggsave(seasonal_plot_path, plot = seasonal_plot, width = 12, height = 8)
    seasonal_results$plot_path <- seasonal_plot_path
  }
  
  # Return results ----------------------------------------------------------
  results <- list(
    summary_statistics = summary_stats,
    trend_analysis = trend_analysis,
    seasonal_analysis = seasonal_results,
    file_paths = list(
      clean_data = clean_data_path,
      time_series_plot = time_plot_path,
      distribution_plot = dist_plot_path
    )
  )
  
  # Save full results
  results_path <- file.path(output_dir, "analysis_results.rds")
  saveRDS(results, results_path)
  
  # Generate report
  if (parameters$generate_report) {
    report_path <- generate_analysis_report(
      results, 
      output_file = file.path(output_dir, "analysis_report.html"),
      title = parameters$report_title
    )
    results$file_paths$report <- report_path
  }
  
  return(results)
}
```

## Automated Testing Patterns

### Python Unit Testing

```python
import unittest
from mymodule import calculate_total

class TestCalculateTotal(unittest.TestCase):
    """Unit tests for the calculate_total function."""
    
    def test_basic_calculation(self):
        """Test basic calculation without discount."""
        prices = [10.0, 20.0, 30.0]
        expected = 60.0
        result = calculate_total(prices)
        self.assertEqual(result, expected)
    
    def test_with_discount(self):
        """Test calculation with discount."""
        prices = [10.0, 20.0, 30.0]
        discount = 0.1  # 10% discount
        expected = 54.0  # 60 - (60 * 0.1)
        result = calculate_total(prices, discount)
        self.assertEqual(result, expected)
    
    def test_empty_price_list(self):
        """Test with empty price list."""
        prices = []
        expected = 0.0
        result = calculate_total(prices)
        self.assertEqual(result, expected)
    
    def test_negative_prices(self):
        """Test with negative prices."""
        prices = [10.0, -5.0, 30.0]
        expected = 35.0
        result = calculate_total(prices)
        self.assertEqual(result, expected)
    
    def test_invalid_discount(self):
        """Test with invalid discount (>1)."""
        prices = [10.0, 20.0, 30.0]
        discount = 1.5  # 150% discount - invalid
        with self.assertRaises(ValueError):
            calculate_total(prices, discount)
    
    def test_negative_discount(self):
        """Test with negative discount (price increase)."""
        prices = [10.0, 20.0, 30.0]
        discount = -0.1  # -10% discount (10% increase)
        expected = 66.0  # 60 + (60 * 0.1)
        result = calculate_total(prices, discount)
        self.assertEqual(result, expected)

if __name__ == '__main__':
    unittest.main()
```

### JavaScript Testing with Jest

```javascript
// calculator.test.js
const { calculateTotal } = require('./calculator');

describe('calculateTotal function', () => {
  test('basic calculation without discount', () => {
    const prices = [10, 20, 30];
    const expected = 60;
    expect(calculateTotal(prices)).toEqual(expected);
  });
  
  test('calculation with discount', () => {
    const prices = [10, 20, 30];
    const discount = 0.1; // 10% discount
    const expected = 54; // 60 - (60 * 0.1)
    expect(calculateTotal(prices, discount)).toEqual(expected);
  });
  
  test('empty price list', () => {
    const prices = [];
    const expected = 0;
    expect(calculateTotal(prices)).toEqual(expected);
  });
  
  test('negative prices', () => {
    const prices = [10, -5, 30];
    const expected = 35;
    expect(calculateTotal(prices)).toEqual(expected);
  });
  
  test('invalid discount (>1)', () => {
    const prices = [10, 20, 30];
    const discount = 1.5; // 150% discount - invalid
    expect(() => calculateTotal(prices, discount)).toThrow(/discount/i);
  });
  
  test('negative discount (price increase)', () => {
    const prices = [10, 20, 30];
    const discount = -0.1; // -10% discount (10% increase)
    const expected = 66; // 60 + (60 * 0.1)
    expect(calculateTotal(prices, discount)).toEqual(expected);
  });
});
```

## Documentation Patterns

### README Template

```markdown
# Project Name

Brief description of what the project does.

## Features

- Feature 1: Description
- Feature 2: Description
- Feature 3: Description

## Installation

```bash
pip install project-name
```

## Quick Start

```python
from project_name import main_function

# Example usage
result = main_function(input_data)
print(result)
```

## API Documentation

### `main_function(input_data, option=default)`

Description of what the function does.

**Parameters:**
- `input_data` (type): Description of parameter
- `option` (type, optional): Description of parameter. Default: `default`

**Returns:**
- (return_type): Description of return value

**Raises:**
- `ExceptionType`: When and why this exception might be raised

## Examples

### Basic Example

```python
from project_name import main_function

# Example code
```

### Advanced Example

```python
from project_name import main_function, helper_function

# More complex example
```

## Development

### Prerequisites

- Requirement 1
- Requirement 2

### Setup

```bash
git clone https://github.com/username/project-name.git
cd project-name
pip install -e ".[dev]"
```

### Testing

```bash
pytest
```

## License

This project is licensed under the MIT License - see the LICENSE file for details.
```

## Best Practices Checklist

Before finalizing any code generation, verify:

- [ ] Code follows language-specific style guidelines
- [ ] Documentation is complete and follows appropriate format
- [ ] Error handling covers expected failure modes
- [ ] Input validation is thorough and clear
- [ ] Function and variable names are descriptive and consistent
- [ ] Complex logic includes explanatory comments
- [ ] Code structure supports maintainability and testability
- [ ] Performance considerations are addressed
- [ ] Security best practices are followed
- [ ] Testing examples or patterns are included
- [ ] Temporal information is included (creation date, version)

## Version History

| Version | Date | Changes |
|---------|------|---------|
| 1.0 | 2025-02-26 | Initial framework specification |
