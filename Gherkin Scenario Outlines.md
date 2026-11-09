# Gherkin Scenario Outlines

A **Scenario Outline** is a powerful Gherkin feature used to run the same test scenario multiple times with different sets of data. It acts as a template, reducing duplication and keeping your feature files DRY (Don't Repeat Yourself).

## Core Components

1. **Scenario Outline:** Replaces the standard `Scenario` keyword to signal that this test uses a data table.
2. **Placeholders (`<parameter>`):** Variables enclosed in angle brackets within the test steps.
3. **Examples:** A data table placed at the end of the scenario. The first row defines the parameter names, and subsequent rows provide the test values.

## How It Works
The testing framework (like Cucumber or SpecFlow) loops through each row of the **Examples** table, substitutes the placeholders with the row's values, and executes the scenario steps.

## Example

```gherkin
Feature: User Authentication

  Scenario Outline: Successful and unsuccessful login attempts
    Given I am on the login page
    When I enter "<username>" and "<password>"
    Then I should see "<message>"

    Examples:
      | username | password | message               |
      | user1    | pass1    | Welcome user1         |
      | user2    | pass2    | Welcome user2         |
      | locked   | wrongpwd | Error: Invalid login  |
```

## Benefits
- **Reduces Duplication:** No need to copy-paste the same steps for different test cases.
- **Improves Readability:** Data is separated cleanly from the test logic.
- **Easy Maintenance:** Adding a new test condition only requires adding a new row to the table.
