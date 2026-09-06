# Ex.No.7 – Develop a Prompt-Based Application Tailored to Personal Needs

### Date: 4-09-2026
### Name: Vishnu K M
### Register No.: 212223240185

---

# Aim

To develop a prompt-based application using ChatGPT that demonstrates how Large Language Models can be used to assist with practical software development tasks, with prompts progressing from simple to advanced designs and producing increasingly useful outputs.

---

# AI Tools Required

* ChatGPT
* Python
* Java
* Spring Boot
* React.js
* Large Language Model (LLM)
* Web Browser
* Visual Studio Code / IntelliJ IDEA

---

# Project Used

## REVIORA – AI-Powered Cloud Code Intelligence Platform

REVIORA is an AI-based code analysis and review platform designed to help developers analyze their source code, identify programming issues, understand algorithmic complexity and receive optimization suggestions.

The prompt-based application developed for this experiment acts as an **AI Programming Assistant** for REVIORA.

---

# Explanation

A prompt-based application uses carefully designed natural-language instructions to communicate with a Large Language Model.

In REVIORA, the application can use prompts to perform tasks such as:

* Analyze source code
* Detect bugs
* Explain programming errors
* Suggest optimized solutions
* Identify time and space complexity
* Generate test cases
* Provide code improvement suggestions
* Explain code in simple language
* Review code according to programming best practices

The experiment demonstrates how the quality of the AI response changes when the prompt is progressively improved.

---

# Problem Statement

Develop a prompt-based AI programming assistant for the REVIORA project that accepts source code from a developer and generates useful code analysis, including error identification, explanation, optimization suggestions and complexity analysis.

The assistant should understand the user's natural-language request and generate an appropriate response using a Large Language Model.

---

# Prompt-Based Application

The application is designed as an **AI Code Review Assistant**.

### Input

The user provides:

* Programming language
* Source code
* Specific question or requirement

### Processing

```text
User Input
    ↓
Prompt Construction
    ↓
Large Language Model
    ↓
AI Code Analysis
    ↓
Review / Suggestions
    ↓
User
```

### Output

The application generates:

* Code issues
* Error explanations
* Optimization suggestions
* Complexity analysis
* Corrected code
* Best-practice recommendations

---

# Procedure

1. Identify a practical requirement from the REVIORA project.
2. Define the input source code and expected output.
3. Create a simple prompt for the task.
4. Execute the prompt using ChatGPT.
5. Observe and record the generated response.
6. Improve the prompt by adding context and instructions.
7. Execute the improved prompt.
8. Compare the outputs obtained from different prompts.
9. Develop a final refined prompt suitable for the application.
10. Evaluate the usefulness of the final AI-generated response.

---

# Selected Engineering Scenario

The selected scenario is **AI-based code review**.

The following Python program is provided to the AI assistant:

```python
def calculate_average(numbers):
    total = 0

    for i in range(len(numbers)):
        total = total + numbers[i]

    average = total / len(numbers)

    return average


numbers = []
print("Average:", calculate_average(numbers))
```

The program attempts to calculate the average of a list of numbers.

However, when an empty list is provided, the program attempts to divide by zero.

---

# Prompt 1 – Simple Prompt

## Prompt

> Review this code and find the error:
>
> ```python
> def calculate_average(numbers):
>     total = 0
>
>     for i in range(len(numbers)):
>         total = total + numbers[i]
>
>     average = total / len(numbers)
>
>     return average
>
> numbers = []
> print("Average:", calculate_average(numbers))
> ```

## Output

The code contains a **ZeroDivisionError** because the list is empty.

When:

```python
numbers = []
```

the value of:

```python
len(numbers)
```

is `0`.

Therefore:

```python
average = total / len(numbers)
```

becomes division by zero.

### Suggested Fix

```python
def calculate_average(numbers):
    if not numbers:
        return 0

    return sum(numbers) / len(numbers)
```

### Observation

The simple prompt successfully identifies the main error but provides only basic analysis.

---

# Prompt 2 – Context-Based Prompt

## Prompt

> You are assisting the REVIORA AI Code Review Platform. Review the following Python code and identify bugs, edge cases and code-quality problems. Explain the problems and provide corrected code.
>
> ```python
> def calculate_average(numbers):
>     total = 0
>
>     for i in range(len(numbers)):
>         total = total + numbers[i]
>
>     average = total / len(numbers)
>
>     return average
>
> numbers = []
> print("Average:", calculate_average(numbers))
> ```

## Output

### Bug Identified

The function produces a `ZeroDivisionError` when an empty list is passed.

### Edge Case

The empty-list input is not handled.

### Code Quality Issue

The manual loop can be replaced with Python's built-in `sum()` function.

### Improved Code

```python
def calculate_average(numbers):
    if not numbers:
        return 0

    return sum(numbers) / len(numbers)
```

### Observation

Adding project context resulted in a more detailed and professional code review.

---

# Prompt 3 – Role-Based Prompt

## Prompt

> Act as a senior software engineer working as an AI code reviewer for REVIORA. Analyze the following Python code.
>
> Identify:
>
> 1. Runtime errors
> 2. Logical errors
> 3. Edge cases
> 4. Code-quality problems
> 5. Optimization opportunities
>
> Explain each issue clearly, assign a severity level and provide corrected code.
>
> ```python
> def calculate_average(numbers):
>     total = 0
>
>     for i in range(len(numbers)):
>         total = total + numbers[i]
>
>     average = total / len(numbers)
>
>     return average
>
> numbers = []
> print("Average:", calculate_average(numbers))
> ```

## Output

### Issue 1 – Division by Zero

**Severity:** High

The function attempts to divide by `len(numbers)`. If the list is empty, its length is zero, resulting in a `ZeroDivisionError`.

### Issue 2 – Empty Input

**Severity:** Medium

The function does not handle an empty list.

### Issue 3 – Unnecessary Manual Loop

**Severity:** Low

The sum can be calculated more simply using Python's built-in `sum()` function.

### Corrected Code

```python
def calculate_average(numbers):
    if not numbers:
        return 0

    return sum(numbers) / len(numbers)
```

### Observation

The role-based prompt generated a professional code review with severity classification and multiple categories of analysis.

---

# Prompt 4 – Advanced Structured Prompt

## Prompt

> You are the AI Code Review Engine of REVIORA, an AI-powered cloud code intelligence platform.
>
> Analyze the following Python code systematically.
>
> **Step 1:** Understand the intended functionality.
>
> **Step 2:** Identify runtime and logical errors.
>
> **Step 3:** Check important edge cases.
>
> **Step 4:** Identify code-quality and efficiency issues.
>
> **Step 5:** Suggest improvements without changing the intended functionality.
>
> **Step 6:** Provide corrected code.
>
> **Step 7:** Provide time and space complexity.
>
> **Step 8:** Generate two test cases to validate the corrected implementation.
>
> Use the following output format:
>
> **Summary**
>
> **Issues**
>
> **Severity**
>
> **Explanation**
>
> **Recommendation**
>
> **Corrected Code**
>
> **Complexity**
>
> **Test Cases**
>
> Source Code:
>
> ```python
> def calculate_average(numbers):
>     total = 0
>
>     for i in range(len(numbers)):
>         total = total + numbers[i]
>
>     average = total / len(numbers)
>
>     return average
>
> numbers = []
> print("Average:", calculate_average(numbers))
> ```

---

# Advanced Prompt Output

## Summary

The function calculates the average of a list of numbers but fails when an empty list is provided.

## Issues

### Issue 1 – Division by Zero

**Severity:** High

When the input list is empty:

```python
len(numbers) = 0
```

The program performs:

```python
0 / 0
```

which produces:

```text
ZeroDivisionError
```

### Issue 2 – Empty Input Not Handled

The function should explicitly handle an empty list.

### Issue 3 – Manual Summation

The loop can be simplified using Python's `sum()` function.

## Recommendation

Validate the input before calculating the average and use the built-in `sum()` function.

## Corrected Code

```python
def calculate_average(numbers):
    if not numbers:
        return 0

    return sum(numbers) / len(numbers)


numbers = []
print("Average:", calculate_average(numbers))
```

## Complexity

**Time Complexity:** O(n)

**Space Complexity:** O(1)

## Test Cases

### Test Case 1

```python
Input: [10, 20, 30]
Expected Output: 20.0
```

### Test Case 2

```python
Input: []
Expected Output: 0
```

## Observation

The advanced prompt generated the most comprehensive response. It included error detection, severity, explanation, correction, complexity analysis and test cases.

---

# Comparison of Prompt Outputs

| Feature            | Simple Prompt | Context-Based | Role-Based | Advanced Structured |
| ------------------ | ------------- | ------------- | ---------- | ------------------- |
| Error Detection    | Yes           | Yes           | Yes        | Yes                 |
| Error Explanation  | Basic         | Good          | Detailed   | Detailed            |
| Edge Cases         | No            | Yes           | Yes        | Yes                 |
| Code Quality       | No            | Yes           | Yes        | Yes                 |
| Severity           | No            | No            | Yes        | Yes                 |
| Corrected Code     | Yes           | Yes           | Yes        | Yes                 |
| Complexity         | No            | No            | No         | Yes                 |
| Test Cases         | No            | No            | No         | Yes                 |
| Output Structure   | Basic         | Good          | Very Good  | Excellent           |
| Overall Usefulness | Good          | Very Good     | Very Good  | Excellent           |

---

# Analysis

The experiment shows that prompt quality has a direct impact on the quality of AI-generated code reviews.

The **simple prompt** was sufficient to detect the primary error but did not request additional analysis.

The **context-based prompt** provided better results because the AI understood that the task was part of the REVIORA code review system.

The **role-based prompt** generated a more professional response by assigning the AI the role of a senior software engineer.

The **advanced structured prompt** produced the most useful output because it provided detailed instructions, a defined analysis process and a specific output format.

The final prompt is therefore more suitable for integration into the REVIORA AI code review module.

---

# Final Refined Prompt

> You are the AI Code Review Engine of **REVIORA – AI-Powered Cloud Code Intelligence Platform**.
>
> Analyze the submitted source code as a senior software engineer.
>
> Perform the following analysis:
>
> 1. Identify syntax, runtime and logical errors.
> 2. Identify unhandled edge cases.
> 3. Detect inefficient or unnecessarily complex code.
> 4. Identify code-quality and maintainability issues.
> 5. Assign a severity level to each issue.
> 6. Explain the cause of each issue.
> 7. Provide an actionable recommendation.
> 8. Generate corrected code while preserving the intended functionality.
> 9. Provide time and space complexity where applicable.
> 10. Generate relevant test cases.
>
> Return the result using this structure:
>
> ```text
> Code Review Summary
>
> Issues Detected
> - Issue
> - Severity
> - Explanation
> - Recommendation
>
> Corrected Code
>
> Complexity Analysis
>
> Test Cases
>
> Overall Recommendations
> ```
>
> Do not invent errors that are not present in the code. Keep the review technically accurate, concise and actionable.

---

# Result

The prompt-based AI Code Review application for the **REVIORA project** was successfully developed and demonstrated using ChatGPT.

The experiment showed that progressively improving the prompt from a simple instruction to a structured engineering prompt resulted in better **error detection, explanation, code-quality analysis, complexity analysis and test-case generation**.

The final refined prompt provides a suitable foundation for the AI code review functionality of REVIORA and demonstrates how Large Language Models can be effectively leveraged for practical software engineering problem-solving.
