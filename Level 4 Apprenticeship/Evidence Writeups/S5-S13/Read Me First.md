#### Arthur Clarkson
**4th September 2024**

The holiday management system on the intranet allows users to book a range of dates which they want to take holiday for. I was assigned the task of adding some quality-of-life features to this such as: better UI/UX, the ability to book off mornings/afternoons, and updating the text shown on our calendar module.

In order to find errors, gaps, or missing requirements I decided to do Non-functional, Unit, Integration, Performance, Security, System, and User Acceptance tests during development.

The technical specification looked something like:

```

When you add a holiday, it should: add the timesheet hours for each selected days within given range, and then add a calendar event that lasts for the date range - with the following text:

- If the range of dates was only for 1 day, the text should just be: “{username} HOL}”
- If the range of dates spanned multiple days within the same week, the text should be for example: “{username} HOL Mon - Wed”.
- If the range of dates has been set to morning/afternoon, the text should be:   “{username} HOL AM”
- If the range spanned across weeks the text should be: “{username} HOL 15 Jul - 22 Jul”

```
 