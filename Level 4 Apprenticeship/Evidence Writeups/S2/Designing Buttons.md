#### Arthur Clarkson
**7th January 2025**

## About buttons

Buttons are often considered the gold standard among clickable UI elements because they build on a universally recognized and intuitive metaphor—pressing a button executes an action. Users trust the predictability of buttons: a labelled button clearly denotes what will happen when clicked, and visual conventions (like a rectangular shape with contrasting colour) immediately convey interactivity. In contrast, links typically steer users toward new pages, icons without text can be ambiguous, and toggles handle on/off states better than single, discrete tasks. By leveraging these advantages, buttons effectively adhere to usability heuristics: they provide immediate feedback (e.g., hover or click states), match real-world expectations of “pushing to do something,” and maintain strong user control without the confusion or clutter that can come with less conventional interactive elements.

Beyond their familiarity, buttons promote clarity through concise labels and deliberate placement, reducing cognitive load and avoiding mis clicks. While icons might save space, a single icon can lack enough context and risk ambiguity, particularly for users unfamiliar with that symbol. Meanwhile, toggles are useful for persistent settings but can be confusing or inconsistent for one-time actions like form submission. Buttons address these concerns by striking a balance between directness and flexibility—users understand at a glance how to complete their desired task, and design features like disabled or loading states maintain visibility of system status while preventing errors.

In practice, implementing buttons consistently (using uniform shapes, colours, and hover effects) creates a coherent visual hierarchy, making key actions easy to find and inviting to click. Concise text labels ensure users know exactly what the button does, and proper accessibility features (such as `aria-labels` and sufficient contrast) open the way for inclusive design. Whether it’s a primary call-to-action or a simple “Cancel” step, buttons serve as reliable signposts that guide users down the right path. By adhering to these principles, buttons stand out as superior clickable elements, delivering clarity and confidence in virtually every user journey.

## Designing the perfect button

I have taken the concept of a standard button and refined each detail to ensure it aligns seamlessly with established UI heuristics. First, I made sure the button is immediately recognizable as clickable by giving it a clearly defined shape, balanced padding, and a colour that contrasts effectively with the background. This visual hierarchy ensures users can’t miss it, addressing the need for “Visibility of System Status” and conforming to the “Match Between System and the Real World”—people know buttons mean action. I also kept the label short yet descriptive, so the user always knows precisely what will happen when they click, maintaining clarity under “User Control and Freedom.”

Here is an example designed in figma:

![[Pasted image 20250107102806.png]]

Here is the button in real use on our website with a short label of "Send message":

![[Pasted image 20250107102956.png]]

In keeping with “Consistency and Standards,” this button style remains uniform across the entire product—its position, size, and hover animations never deviate. This consistency helps users form a mental model, reducing the likelihood of accidental clicks or confusion about functionality. For example, a hover state might slightly darken the button or display a subtle border, reinforcing that the button is clickable. Once pressed, the button shifts into a loading or disabled state to confirm the system is processing the request, thus maintaining “Visibility of System Status” and preventing premature repeated clicks.

Finally, accessibility sits at the heart of my design. I’ve ensured the button meets at least WCAG AA contrast standards, making it legible for users with low vision. Users can also tab through and see a distinct focus outline around the button, satisfying “Error Prevention and Recognition” by guiding keyboard-only users. By weaving these heuristics into each facet—labelling, consistency, visual feedback, and accessibility—I’ve designed what I believe to be the perfect button: intuitive, inclusive, and entirely ready for prime time.

The button tabbed onto and outlined:
![[Pasted image 20250107103118.png]]

