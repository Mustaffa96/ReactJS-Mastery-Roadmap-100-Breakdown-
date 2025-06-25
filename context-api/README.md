Alright, let’s break down the ReactJS Context API with useContext for state management in simple, kampung-style terms, like we’re chatting under a coconut tree with a glass of teh tarik in hand. 😄

# What’s Context API, Bro?
Imagine you’re in a kampung where everyone lives in a big family house with many rooms. Each room is like a React component in your app. Now, let’s say your atok (grandpa) has a big jar of kuih raya (cookies) in the living room, and he wants everyone in the house—kids, uncles, cousins—to be able to grab some kuih without him passing the jar to every single person one by one.

In React, passing data (like the kuih) from one component to another is called props. But if you have to pass the kuih jar from atok to your cousin in the attic through 10 other people, it’s leceh (troublesome), right? This is called prop drilling.

Context API is like atok putting the kuih jar in a central pantry (the Context). Now, anyone in the house (any component) can go straight to the pantry to grab kuih without asking 10 people to pass it. Context API lets you share data (state) across your app without passing props through every level.

# How Does It Work, Lah?
In the kampung house (your React app), you set up the pantry (Context) like this:
* **Create the Pantry (Context):** You tell React, “Oi, I want a central place to store my kuih jar.”
* **Put Kuih in the Pantry (Provider):** You decide what kuih (data or state) goes into the pantry and make it available to everyone.
* **Grab Kuih from the Pantry (Consumer or useContext):** Any room (component) can check the pantry and take the kuih they need.

# Let’s Get Into the Code, Like a Kampung Recipe
Here’s how you’d use Context API with useContext to manage state, explained in kampung terms.

### Step 1: Create the Pantry (Context)
You need to make a pantry to store the kuih jar. In React, you use createContext.
```javascript
import React, { createContext } from 'react';

// Create a pantry called KuihContext
const KuihContext = createContext();
```
This `KuihContext` is like an empty pantry waiting for you to put something inside.

### Step 2: Stock the Pantry with Kuih (Provider)
Now, atok puts the kuih jar in the pantry and decides how many kuih are available. You use a Provider to wrap your app (or part of it) and share the kuih (state).
```javascript
import React, { createContext, useState } from 'react';

// Create the pantry
const KuihContext = createContext();

function App() {
  // Atok has 10 kuih in the jar (state)
  const [kuihCount, setKuihCount] = useState(10);

  // Function to eat kuih (update state)
  const eatKuih = () => {
    if (kuihCount > 0) {
      setKuihCount(kuihCount - 1);
    }
  };

  return (
    // Put the kuih jar in the pantry and share it
    <KuihContext.Provider value={{ kuihCount, eatKuih }}>
      <div>
        <h1>Welcome to Kampung Kuih!</h1>
        <LivingRoom />
        <Attic />
      </div>
    </KuihContext.Provider>
  );
}
```
* **Provider:** The `<KuihContext.Provider>` is like atok saying, “This pantry has kuih, and here’s how you can eat it.” The `value` prop is the kuih jar (state) and the function to eat kuih (state updater).
* `kuihCount`: The number of kuih left (state).
* `eatKuih`: A function to reduce the kuih count when someone eats one.
The Provider wraps the components (`LivingRoom`, `Attic`) that need access to the kuih. Any component inside can now grab kuih from the pantry.

### Step 3: Grab Kuih from the Pantry (useContext)
Now, let’s say your cousin in the Attic (a component) wants to check how many kuih are left and eat one. Instead of asking everyone to pass the jar, he uses useContext to go straight to the pantry.
```javascript
import React, { useContext } from 'react';

// Grab the pantry
import { KuihContext } from './App';

function Attic() {
  // Open the pantry and take the kuih jar
  const { kuihCount, eatKuih } = useContext(KuihContext);

  return (
    <div>
      <h2>In the Attic</h2>
      <p>Kuih left: {kuihCount}</p>
      <button onClick={eatKuih}>Eat one kuih!</button>
    </div>
  );
}
```
* **useContext(KuihContext):** This is like your cousin opening the pantry door and grabbing the kuih jar. It gives him access to `kuihCount` (how many kuih are left) and `eatKuih` (the function to eat one).
* When he clicks the button, `eatKuih` runs, updates the state, and everyone in the house (other components) sees the new kuih count because the pantry is shared.

# Full Kampung Example
Here’s the whole code put together, like a kenduri (feast) where everyone shares the kuih.
```javascript
import React, { createContext, useContext, useState } from 'react';

// Create the pantry
const KuihContext = createContext();

function App() {
  const [kuihCount, setKuihCount] = useState(10);

  const eatKuih = () => {
    if (kuihCount > 0) {
      setKuihCount(kuihCount - 1);
    }
  };

  return (
    <KuihContext.Provider value={{ kuihCount, eatKuih }}>
      <div>
        <h1>Welcome to Kampung Kuih!</h1>
        <LivingRoom />
        <Attic />
      </div>
    </KuihContext.Provider>
  );
}

function LivingRoom() {
  const { kuihCount } = useContext(KuihContext);

  return (
    <div>
      <h2>In the Living Room</h2>
      <p>Kuih left: {kuihCount}</p>
    </div>
  );
}

function Attic() {
  const { kuihCount, eatKuih } = useContext(KuihContext);

  return (
    <div>
      <h2>In the Attic</h2>
      <p>Kuih left: {kuihCount}</p>
      <button onClick={eatKuih}>Eat one kuih!</button>
    </div>
  );
}

export default App;
```

# What Happens When You Run This?
* The app starts with 10 kuih in the pantry (`kuihCount = 10`).
* The **Living Room** shows “Kuih left: 10”.
* The **Attic** shows “Kuih left: 10” and has a button to eat kuih.
* When you click “Eat one kuih!” in the Attic, `eatKuih` runs, updates `kuihCount` to 9, and both the Living Room and Attic update to show “Kuih left: 9”.
* Everyone in the kampung (all components) stays in sync because they’re all checking the same pantry.

### Why Use Context API for State Management?
* **No More *Leceh* Prop Drilling:** Instead of passing kuih through 10 rooms, everyone can access the pantry directly.
* **Centralized State:** The kuih jar (state) lives in one place, making it easy to manage.
* **Scales Well:** If your kampung grows with more rooms (components), they can all access the pantry without extra work.
* **Simple for Small Apps:** For small to medium kampung apps, Context API is lighter than big tools like Redux, like using a bicycle instead of a lorry.

### When *Not* to Use Context API?
* **Too Many Updates:** If the kuih jar changes every second (frequent state updates), Context might make your app slow because every component using the pantry re-renders. For big kampung apps with lots of state, consider tools like Redux or Zustand.
* **Small Apps:** If you only have two rooms (components), just pass props lah, no need for a fancy pantry.

### Kampung Tips for Context API
* **Don’t Overuse:** Only put shared kuih (global state like user info, theme, or settings) in the pantry. Don’t store every little thing there, or it’ll get messy.
* **Split Contexts:** If you have kuih and nasi lemak to share, make separate pantries (Contexts) for each to keep things organized.
* **Use with useReducer:** For complex state (like managing a whole kenduri menu), pair Context with `useReducer` to handle state updates like a pro.

### Final Kampung Thought
Context API with `useContext` is like setting up a shared pantry in your kampung house. It makes sharing kuih (state) easy, keeps everyone happy, and saves you from the leceh of passing props everywhere. Just don’t put too many kuih jars in the pantry, or your app might get pening (dizzy)!
