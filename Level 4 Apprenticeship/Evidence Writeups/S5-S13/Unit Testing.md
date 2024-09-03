### Unit Testing A Business Layer Method

#### Arthur Clarkson
**3rd September 2024**

The holiday management system on the intranet allows users to book a range of dates which they want to take holiday for. I was assigned the task of adding some quality-of-life features to this such as: better UI/UX, the ability to book off mornings/afternoons, and updating the text shown on our calendar module.

The final feature had the following spec:

- If the range of dates was only for 1 day, the text should just be: “{username} HOL}”
- If the range of dates spanned multiple days within the same week, the text should be for example: “{username} HOL Mon - Wed”.
- If the range of dates has been set to morning/afternoon, the text should be:   “{username} HOL AM”
- If the range spanned across weeks the text should be: “{username} HOL 15 Jul - 22 Jul”

After reading this spec I came up with this method:

![[clip_image002.png]]

With there being many permutations with this method, I decided to unit test it.

Using C#’s NUnit testing framework I came up with the following test data:

![[clip_image004.png]]

After running the test, I get failure on the following cases:  

![[clip_image006 1.png]]

It looked like it was trying to add null/empty parameters to the description text, adding a random space to the string, due to this code:

![](file:///C:/Users/ACLARK~1/AppData/Local/Temp/msohtmlclip1/01/clip_image008.png)

I decided to add the following null check:

![[clip_image010.png]]

After running the test again, it managed to pass all cases.