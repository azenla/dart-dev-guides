# Commits

Dart doesn't really have any specific commit guidelines. However, I am going to lay out some best practices.

## Link Related Bug

```
Fixed typo in pub help command

BUG: http://dartbug.com/ISSUE_NUMBER
```

## Be Descriptive

Let's say you make a change that breaks an API (which you probably wont do). Make sure to include that in your commit message.

```
BREAKING: Refactor `int.parse` to `new int.fromString` constructor.

- Provides Readability
- Makes use of named constructors

BUG: http://dartbug.com/ISSUE_NUMBER
```
