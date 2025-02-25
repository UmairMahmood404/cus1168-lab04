# Lab 4: Building a Recursive Descent Parser

### Learning Objectives

By completing this lab, students will:

- Understand the principles of recursive descent parsing
- Implement a basic arithmetic expression evaluator
- Learn about operator precedence and grammar rules
- Practice handling string input and error cases

### Background

Recursive descent parsing is a fundamental technique in compiler design. In this lab, we'll build a parser that can
evaluate arithmetic expressions following these grammar rules:

```text
expr   → expr + term   | term
term   → term * factor | factor
factor → ( expr )      | number
```

### Prerequisites

- Basic understanding of Java programming
- Familiarity with recursion
- Understanding of basic arithmetic operator precedence

### Task Description

In this lab, you will implement a recursive descent parser that evaluates arithmetic expressions. The parser will
process expressions like "2 + 3 * (4 + 5)" and compute their results following standard mathematical precedence rules.
You'll work through a series of tasks that build upon each other:

1. **Task 1: Basic Expression Parsing**
   - Implement the `parseExpression()` method to handle addition
   - Process expressions left to right
   - Return the sum of terms
   - Example: "2 + 3" should return 5.0
2. **Task 2: Term Parsing**
   - Implement the `parseTerm()` method to handle multiplication
   - Ensure multiplication has higher precedence than addition
   - Return the product of factors
   - Example: "2 * 3" should return 6.0
3. **Task 3: Factor Parsing**
   - Implement the `parseFactor()` method to handle parentheses
   - Process expressions within parentheses recursively
   - Handle both parenthesized expressions and numbers
   - Example: "(2 + 3)" should return 5.0
4. **Task 4: Number Parsing**
   - Implement the `parseNumber()` method
   - Handle multi-digit numbers
   - Support decimal points
   - Example: "123.45" should return 123.45

### Functional Requirements

- Expression Parsing
    - Must handle basic arithmetic expressions
    - Support addition (+) and multiplication (*)
    - Handle parentheses for grouping
    - Process numeric values (integers and decimals)
- Input Processing
    - Remove all whitespace from input expressions
    - Support decimal numbers (e.g., 3.14)
    - Handle multi-digit numbers correctly
    - Support nested parentheses
- Operator Precedence
    - Multiplication (*) must have higher precedence than addition (+)
    - Expressions in parentheses must be evaluated before operations outside
    - Left-to-right evaluation for operators of the same precedence
- Error Handling
    - Detect and report mismatched parentheses
    - Handle invalid characters in input
    - Provide meaningful error messages with position information

### Technical Requirements

**Method Specifications**

- `parseExpression()`
    - Input: None (uses class instance variables)
    - Output: `double`
    - Purpose: Parse and evaluate addition operations
- `parseTerm()`
    - Input: None (uses class instance variables)
    - Output: `double`
    - Purpose: Parse and evaluate multiplication operations
- `parseFactor()`
    - Input: None (uses class instance variables)
    - Output: `double`
    - Purpose: Parse parentheses and numbers
- `parseNumber()`
    - Input: None (uses class instance variables)
    - Output: `double`
    - Purpose: Parse numeric values
- Instance Variables
    - `input`: Stores the input string
    - `position`: Tracks current parsing position

### Project Setup

- Open the project in your IDE
- Locate the starter code at: `src/main/java/academy/javapro/ExpressionParser.java`
- Do not modify the package structure or class name
- Implement the required functionality in the TODOs provided

### Starter Code

```java
package academy.javapro;

class ExpressionParser {
    private final String input;
    private int position;

    public ExpressionParser(String input) {
        this.input = input;
        this.position = 0;
    }

    // expr → expr + term
    public double parseExpression() {
        // TODO: Get the leftmost term value by calling parseTerm()
        // TODO: While we haven't reached the end of input and current char is '+'
        // TODO: Increment position to skip the '+' operator
        // TODO: Get the next term on the right
        // TODO: Add the right term to our running total
        // TODO: Return the final value
        throw new UnsupportedOperationException("Implement parseExpression");
    }

    // term → term * factor
    private double parseTerm() {
        // TODO: Get the leftmost factor value by calling parseFactor()
        // TODO: While we haven't reached the end of input and current char is '*'
        // TODO: Increment position to skip the '*' operator
        // TODO: Get the next factor on the right
        // TODO: Multiply the right factor with our running total
        // TODO: Return the final value
        throw new UnsupportedOperationException("Implement parseTerm");
    }

    // factor → ( expr )
    private double parseFactor() {
        // TODO: Check if we have an opening parenthesis and haven't reached end of input
        // TODO: Increment position to skip the opening parenthesis
        // TODO: Parse the expression inside the parentheses
        // TODO: Increment position to skip the closing parenthesis
        // TODO: Return the result of the parenthesized expression
        // TODO: If no parentheses, parse and return a number
        throw new UnsupportedOperationException("Implement parseFactor");
    }

    // Parse a numeric value
    private double parseNumber() {
        // TODO: Create a StringBuilder to collect digits
        // TODO: While we haven't reached the end and current char is digit or decimal point
        // TODO: Append the current digit to our number string
        // TODO: Move to next character
        // TODO: Convert the string of digits to a double and return it
        throw new UnsupportedOperationException("Implement parseNumber");
    }

    public static void main(String[] args) {
        // Test cases
        String[] testCases = {
                "2 + 3 * (4 + 5)",    // Complex expression with parentheses
                "2 + 3 * 4",          // Basic arithmetic with precedence
                "(2 + 3) * 4",        // Parentheses changing precedence
                "2 * (3 + 4) * (5 + 6)", // Multiple parentheses
                "1.5 + 2.5 * 3"       // Decimal numbers
        };

        // Process each test case
        for (String expression : testCases) {
            System.out.println("\nTest Case: " + expression);
            try {
                ExpressionParser parser = new ExpressionParser(expression.replaceAll("\\s+", "")); // Remove spaces
                double result = parser.parseExpression();
                System.out.println("Result: " + result);
            } catch (Exception e) {
                System.out.println("Error: " + e.getMessage());
            }
        }
    }
}
```

### Testing Your Implementation

```text
Test Case: 2 + 3 * (4 + 5)
Result: 29.0

Test Case: 2 + 3 * 4
Result: 14.0

Test Case: (2 + 3) * 4
Result: 20.0

Test Case: 2 * (3 + 4) * (5 + 6)
Result: 154.0

Test Case: 1.5 + 2.5 * 3
Result: 9.0
```