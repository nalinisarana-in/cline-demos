You have access to the `gh` terminal command. I already authenticated it for you. Please review it to use the PR that I asked you to review. You're already in the `cline` repo.

<detailed_sequence_of_steps>

# GitHub PR Review Process - Detailed Sequence of Steps

## 1. Gather PR Information

1. Get the PR title, description, and comments:

    ```bash
    gh pr view <PR-number> --json title,body,comments
    ```

2. Get the full diff of the PR:
    ```bash
    gh pr diff <PR-number>
    ```

## 2. Understand the Context

1. Identify which files were modified in the PR:

    ```bash
    gh pr view <PR-number> --json files
    ```

2. Examine the original files in the main branch to understand the context:

    ```xml
    <read_file>
    <path>src/main/java</path>
    </read_file>
    ```

3. For specific sections of a file, you can use search_files:
    ```xml
    <search_files>
    <path>src/main/java/com/example</path>
    <regex>search term</regex>
    <file_pattern>*.java</file_pattern>
    </search_files>
    ```

## 3. Analyze the Changes

1. For each modified file, understand:

    - What was changed
    - Why it was changed (based on PR description)
    - How it affects the codebase
    - Potential side effects

2. Look for:
    - Code quality issues
    - Potential bugs
    - Performance implications
    - Security concerns
    - Test coverage

## 4. Ask for User Confirmation

1. Before making a decision, ask the user if you should approve the PR, providing your assessment and justification:

    ```xml
    <ask_followup_question>
    <question>Based on my review of PR #<PR-number>, I recommend [approving/requesting changes]. Here's my justification:

    [Detailed justification with key points about the PR quality, implementation, and any concerns]

    Would you like me to proceed with this recommendation?</question>
    <options>["Yes, approve the PR", "Yes, request changes", "No, I'd like to discuss further"]</options>
    </ask_followup_question>
    ```

## 5. Ask if User Wants a Comment Drafted

1. After the user decides on approval/rejection, ask if they would like a comment drafted:

    ```xml
    <ask_followup_question>
    <question>Would you like me to draft a comment for this PR that you can copy and paste?</question>
    <options>["Yes, please draft a comment", "No, I'll handle the comment myself"]</options>
    </ask_followup_question>
    ```

2. If the user wants a comment drafted, provide a well-structured comment they can copy:

    ```
    Thank you for this PR! Here's my assessment:

    [Detailed assessment with key points about the PR quality, implementation, and any suggestions]

    [Include specific feedback on code quality, functionality, and testing]
    ```