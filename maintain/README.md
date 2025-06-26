# What is Maintainable and Reusable Code?
* **Maintainable code** is like a well-built village house. It’s easy to repair, clean, or add new parts without tearing everything down. If something breaks (like a bug), you can fix it without causing a mess.

* **Reusable code** is like crafting reusable tools or furniture in the village. Instead of building a new chair every time someone needs to sit, you make one good chair design that can be used in many houses.

In ReactJS, these ideas help you write code that’s clean, easy to update, and can be reused across different parts of your app.
# Explaining in Kampung Terms
Imagine you’re building a village community app using ReactJS, like a digital balai raya (community hall) where people share info, plan events, or sell stuff. Here’s how you make your code maintainable and reusable:
### 1. Build Small, Modular Parts (Components)
* **Kampung analogy:** Think of your app like a village house made of smaller parts—doors, windows, and walls. Each part has one job and can be reused in other houses.

* **ReactJS:** Break your app into small components. For example, create a Button component for all buttons in your app instead of writing button code every time.
  * Example: A SubmitButton component can be used for login, signup, or posting messages.

```jsx

function SubmitButton({ label }) {
  return <button className="submit-btn">{label}</button>;
}
```
Now, you can reuse it like <SubmitButton label="Login" /> or <SubmitButton label="Post" />.

* **Why it’s maintainable:** If you need to change the button’s style or behavior, you update one component, not every button in the app.

* **Why it’s reusable:** The same button works everywhere—login page, profile page, or event page.

### 2. Keep Things Organized (Folder Structure)
* **Kampung analogy:** In a village, you don’t throw tools, food, and clothes in one pile. You store them neatly in separate places (like a shed for tools, kitchen for food). This makes it easy to find and fix things.

* **ReactJS:** Organize your code in a clear folder structure. For example:
```
src/
  components/  <- Reusable parts like Button, Header, Footer
  pages/       <- Specific app sections like HomePage, ProfilePage
  styles/      <- CSS files for styling
  utils/       <- Helper functions, like formatting dates
```
* **Why it’s maintainable:** If someone new joins the village (a new developer), they can quickly find what they need.

* **Why it’s reusable:** Components in the components/ folder can be imported and used across different pages.

### 3. Write Simple, Clear Code (Don’t Overcomplicate)
* **Kampung analogy:** When building a house, don’t use fancy, fragile materials that nobody understands how to fix. Use simple, sturdy wood or bamboo that everyone in the village knows how to work with.

* **ReactJS:** Write code that’s easy to read and understand. Avoid complex logic in one place.
  * Bad example (messy):
```jsx

function Profile() {
  return (
    <div>
      <h1 style={{ color: 'blue', fontSize: '24px' }}>Welcome, Ali!</h1>
      <button onClick={() => alert('You clicked me!')}>Click me</button>
    </div>
  );
}
```
  * Good example (clear and reusable):
```jsx

function Profile() {
  return (
    <div>
      <Title text="Welcome, Ali!" />
      <SubmitButton label="Click me" onClick={() => alert('You clicked me!')} />
    </div>
  );
}

function Title({ text }) {
  return <h1 className="title">{text}</h1>;
}
```
* **Why it’s maintainable:** Simple code is easier to debug or update. If Ali’s name changes, you just update the text prop.

* **Why it’s reusable:** The Title component can be used for any heading, not just the profile page.

### 4. Use Props and State Wisely (Pass Tools Around)
* **Kampung analogy:** Imagine you’re sharing a hammer between houses. You don’t need a new hammer for every house—just pass the same one where it’s needed.

* **ReactJS:** Use props to pass data or functions to components, and state to manage data that changes.
  * Example: A TodoList component that displays tasks.
```jsx

function TodoList({ tasks }) {
  return (
    <ul>
      {tasks.map((task) => (
        <li key={task.id}>{task.name}</li>
      ))}
    </ul>
  );
}
```
You can reuse `TodoList` for shopping lists, event tasks, or anything else by passing different tasks props.

* **Why it’s maintainable:** If you need to change how tasks are displayed, you edit one component, not every list in the app.

* **Why it’s reusable:** The same TodoList works for any list of items.

### 5. Avoid Repeating Yourself (DRY - Don’t Repeat Yourself)
* **Kampung analogy:** If every house in the village builds its own well, you waste time and effort. Instead, dig one good well that everyone can use.

* **ReactJS:** Don’t repeat code. If you’re writing the same logic or UI multiple times, turn it into a reusable component or function.
  * Example: Instead of repeating a date formatter in every component, create a utility function:
jsx

// utils/formatDate.js
export function formatDate(date) {
  return new Date(date).toLocaleDateString();
}

// In a component
import { formatDate } from './utils/formatDate';
function EventCard({ eventDate }) {
  return <p>Event on: {formatDate(eventDate)}</p>;
}
```
* **Why it’s maintainable:** If the date format changes, you update one function, not every component.

* **Why it’s reusable:** Any component can import and use formatDate.

### 6. Add Comments and Documentation (Leave Instructions)
Kampung analogy: If you build a water pump, leave a note explaining how to use and fix it, so others in the village don’t struggle.

ReactJS: Add comments to explain tricky code and document components (e.g., using PropTypes or JSDoc).
```jsx

// Button component that displays a clickable button
function SubmitButton({ label, onClick }) {
  return <button onClick={onClick}>{label}</button>;
}
```
* **Why it’s maintainable:** Comments help new developers (or future you) understand the code quickly.

* **Why it’s reusable:** Clear documentation tells others how to use your component correctly.

### 7. Test Your Code (Check the House Before Moving In)
* **Kampung analogy:** Before letting people live in a new house, you check if the roof leaks or the doors work. This prevents problems later.

* **ReactJS:** Write tests for your components using tools like Jest or React Testing Library.
Example: Test if the SubmitButton renders correctly.
```jsx

import { render, screen } from '@testing-library/react';
test('renders button with correct label', () => {
  render(<SubmitButton label="Click me" />);
  expect(screen.getByText('Click me')).toBeInTheDocument();
});
```
* **Why it’s maintainable:** Tests catch bugs early, so changes don’t break the app.

* **Why it’s reusable:** Tests ensure components work as expected when reused in new places.

# Key Tips in Kampung Style
* **Think like a village builder**: Build small, strong parts (components) that can be reused, like bricks for many houses.

* **Keep the village tidy:** Organize code like you’d organize tools in a shed—easy to find and use.

* **Share tools, don’t hoard:** Pass data (props) and logic (functions) instead of rewriting them.

* **Test the foundation:** Check your code (with tests) to make sure it won’t collapse later.

* **Leave a guidebook:** Comment your code so others in the village can understand and maintain it.

# Why This Matters
Writing maintainable and reusable code in ReactJS is like building a village that lasts. It saves time (no need to rebuild everything), makes teamwork easier (new developers can jump in), and keeps the app running smoothly (fewer bugs, easier updates). Your digital balai raya will be a place everyone loves to use!

