Let’s break down ReactJS components, props, and state in a way that feels like we’re chatting in a kampung (village) setting—simple, relatable, and grounded. Imagine we’re sitting under a big tree, sipping teh tarik, and I’m explaining this like I’m telling a story about building a village house.

# 1. What Are React Components?
Think of a React component as a small, reusable part of your village house. Each part—like the door, window, or roof—has a specific job. Together, these parts make up the whole house (your web app). Components are like these building blocks in React that create the user interface (UI).

There are two types of components: **Functional Components** and **Class Components**. Let’s compare them.

# 2. Functional Components vs. Class Components
Functional Components (The Simple Bamboo Hut)
* **What is it?** A functional component is like a basic bamboo hut in the kampung. It’s simple, lightweight, and does one job well—showing something on the screen.
* **How it works?** It’s just a JavaScript function that returns some JSX (like HTML) to describe what you see on the webpage.
* **Why use it?** It’s easy to build and maintain, like a hut you can quickly put together with bamboo and palm leaves.
* **Example in kampung terms:** Imagine a functional component as a small stall selling nasi lemak. It takes an order (input) and serves the food (output) without keeping track of anything complicated.
**Code Example:**
```jsx
function NasiLemakStall(props) {
  return <h1>Sell {props.quantity} packets of nasi lemak!</h1>;
}
```
* **Here, `NasiLemakStall` is the component. It takes `props` (like the order details) and displays the output (the nasi lemak packets).

### Class Components (The Big Brick House)
* **What is it?** A class component is like a big, solid brick house in the kampung. It’s more complex and can do more things, like keeping track of changes or managing its own "memory."
* **How it works?** It’s a JavaScript class that extends `React.Component`. It has a `render()` method to show the UI and can manage its own state (more on that later).
* **Why use it?** It’s useful when you need a component to "remember" things or handle more complex logic, like a house with rooms for different purposes.
* **Example in kampung terms:** Think of a class component as the village head’s house. It not only serves guests (displays UI) but also keeps track of village events (state) and makes decisions.

**Code Example:**
```jsx
class VillageHeadHouse extends React.Component {
  render() {
    return <h1>Welcome to {this.props.villageName}!</h1>;
  }
}
```
* `VillageHeadHouse` is the component. It uses `this.props` to access input (like the village name) and displays it.

### Functional vs. Class: Which to Use?
* Nowadays, functional components are the kampung favorite because they’re simpler and support modern React features like Hooks (a way to add "memory" to functional components).
* Class components are still used in older projects, but they’re like the old brick houses—solid but harder to maintain.
* **Rule of thumb:** Start with functional components. Only use class components if you’re working on an older project or have a specific need.

# 3. Props (Passing Notes in the Kampung)
* **What are props?** Props are like notes you pass to a component to tell it what to do or show. They’re read-only, meaning the component can’t change the note—it just uses it.
* **In kampung terms:** Imagine you’re sending a note to the nasi lemak stall saying, “Make 5 packets with extra sambal.” The stall uses that note (props) to prepare your order but doesn’t rewrite it.
* **How it works?** Props are passed to a component like arguments to a function. Both functional and class components can use props.
* **Example:**
```jsx
// Functional component using props
function NasiLemakStall(props) {
  return <h1>Sell {props.quantity} packets with {props.sambalLevel} sambal!</h1>;
}

// Using the component
<NasiLemakStall quantity={5} sambalLevel="extra" />
```
* Here, `quantity` and `sambalLevel` are props passed to `NasiLemakStall`. The component uses them to display the message.
* **Key point:** Props are like instructions from the parent component (the one using the component). The child component (like `NasiLemakStall`) can’t change them—it just follows the note.

# 4. State (The Component’s Memory)
* **What is state?** State is like a component’s personal notebook where it keeps track of things that can change over time, like how many nasi lemak packets are left or whether the stall is open.
* **In kampung terms:** Imagine the village head’s house has a whiteboard (state) where they write down the number of visitors today. They can update it (change state) when more people arrive.
* **How it works?**
  * In **class components**, state is an object managed with `this.state` and updated using `this.setState()`.
  * In **functional components**, you use the `useState` Hook to manage state.
* **Why use state?** State lets a component be dynamic, like updating the UI when something changes (e.g., a button click).
**Example (Class Component with State):**
```jsx
class VillageHeadHouse extends React.Component {
  constructor(props) {
    super(props);
    this.state = { visitors: 0 }; // Initial state: 0 visitors
  }

  addVisitor = () => {
    this.setState({ visitors: this.state.visitors + 1 }); // Update state
  };

  render() {
    return (
      <div>
        <h1>Visitors today: {this.state.visitors}</h1>
        <button onClick={this.addVisitor}>Add Visitor</button>
      </div>
    );
  }
}
```
* Here, `visitors` is part of the state. Clicking the button updates the state, and React re-renders the UI to show the new number.

### Example (Functional Component with State):
```jsx
import { useState } from 'react';

function NasiLemakStall() {
  const [packetsLeft, setPacketsLeft] = useState(10); // Initial state: 10 packets

  const sellPacket = () => {
    setPacketsLeft(packetsLeft - 1); // Update state
  };

  return (
    <div>
      <h1>Packets left: {packetsLeft}</h1>
      <button onClick={sellPacket}>Sell Packet</button>
    </div>
  );
}
```
* Here, `useState` creates a state variable (`packetsLeft`) and a function to update it (`setPacketsLeft`). Clicking the button reduces the packets and updates the UI.
* **Key point:** State is private to the component. Only the component can change its own state. If you need to share data with another component, use props or other patterns like context).

### Putting It All Together: A Kampung Analogy
Imagine you’re building a kampung festival webpage:
* **Components** are the stalls, stages, and decorations (functional or class).
* **Props** are the instructions you give each stall, like “Serve 10 packets” or “Play traditional music.”
* **State** is each stall’s own record book, tracking things like “How many customers came?” or “Are we open?”
* **Functional components** are simple stalls that just follow instructions (props) and maybe keep a small notebook (state with Hooks).
* **Class components** are like the big community hall, with more features but harder to set up.

### Quick Tips for the Kampung Coder
* Use **functional components** for new projects—they’re simpler and modern.
* Pass **props** to customize components, like sending notes to your neighbors.
* Use **state** when a component needs to “remember” something that changes, like a counter or form input.
* Keep it simple, like a kampung house: only add complexity (class components or extra state) when you really need it.
