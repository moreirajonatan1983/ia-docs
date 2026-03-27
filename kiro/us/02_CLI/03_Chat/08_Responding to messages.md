# Responding to Messages

> **Source:** [kiro.dev/docs/cli/chat/responding/](https://kiro.dev/docs/cli/chat/responding/)

---

The `/reply` command opens your editor pre-populated with Kiro's most recent response, quoted for reference. You can then add your responses inline and submit.

---

## How It Works

1. **Retrieves last response** — Finds the most recent assistant message
2. **Formats with quotes** — Each line is prefixed with `>` for clear attribution
3. **Opens editor** — Your default editor opens with the quoted content
4. **Edit and respond** — Add your responses below or interspersed with the quoted text
5. **Submit** — When you save and close the editor, your response is submitted

---

## Editor Behavior

- **Pre-populated content** — Editor opens with Kiro's response already quoted
- **Quote format** — Each line prefixed with `>` for visual distinction
- **Flexible editing** — Add content anywhere: below quotes, between lines, or interspersed
- **Auto-submission** — Content is submitted automatically when editor closes successfully

---

## Use Cases

### Responding to Multiple Questions

When Kiro asks several clarifying questions:

```
> What programming language are you using?
Python
> What framework are you working with?
Django
> What specific error are you encountering?
I'm getting a 404 error when trying to access my API endpoints.
```

### Addressing Specific Points

Respond to specific parts of a detailed explanation:

```
> Here are three approaches you could take:
> 1. Use a database migration
> 2. Update the model directly
> 3. Create a custom management command
I'd like to go with option 1. Can you show me how to create the migration?
> Make sure to backup your data first.
Already done - I have a full backup from this morning.
```

### Providing Structured Feedback

Organize responses to multiple suggestions:

```
> I recommend these improvements:
> - Add error handling for network requests
> - Implement input validation
> - Add logging for debugging
Agreed on all points.
For the error handling: - Should I use try/catch blocks or a decorator pattern?
For logging: - What level of detail do you recommend?
```

---

## Status Messages

| Status | Message |
|---|---|
| Success | "Content loaded from editor. Submitting prompt..." |
| No changes | "No changes made in editor, not submitting." |
| No message | "No assistant message found to reply to." |
| Editor error | "Error opening editor: [specific error details]" |