Let’s break down functional programming (FP) concepts like map, filter, reduce, closures, and immutability in a way that feels like a chat in a kampung (village) setting—simple, relatable, and grounded. Imagine we’re sitting under a big tree, sipping teh tarik, and I’m explaining this like I’m telling a story about farming or fishing. Then, I’ll tie it to how these ideas are used in ReactJS, a popular tool for building web apps.

# Functional Programming in Kampung Terms
Functional programming is like following a traditional recipe passed down in the kampung. You don’t mess with the ingredients (data), you follow clear steps (functions), and you always get the same dish (output) if you use the same ingredients. No surprises, no changing the recipe halfway!
Here’s how each concept fits:

### 1. Map - Turning One Thing into Another
Imagine you have a basket of manggis (mangosteens). You want to peel each one to get the juicy fruit inside. Map is like going through the basket, peeling each manggis one by one, and putting the peeled fruit in a new basket. You don’t change the original manggis; you just create something new from each one.
* **How it works:** Map takes a list (like your basket) and a function (like peeling). It applies the function to every item and gives you a new list with the results.
* **Example:** You have `[1, 2, 3]` and want to double each number. Map applies `double` to each, giving `[2, 4, 6`].
* **Kampung analogy** Every manggis becomes peeled fruit, but the original basket stays untouched.

### 2. Filter - Picking Only What You Want
Now, you’re at the market with a pile of durians. Some are ripe, some are not. Filter is like picking only the ripe ones to take home. You check each durian, keep the good ones, and leave the rest behind, without changing the original pile.
* **How it works:** Filter takes a list and a condition (like “is it ripe?”). It returns a new list with only the items that meet the condition.
* **Example:** You have `[1, 2, 3, 4]` and want only even numbers. Filter keeps numbers where number `% 2 === 0`, giving `[2, 4]`.
* **Kampung analogy:** You’re choosing only the best durians for your feast, leaving the unripe ones for someone else.

### 3. Reduce - Combining Everything into One
Picture you’re making cendol for the kampung party. You have ingredients—palm sugar, coconut milk, green jelly—and you mix them all together to get one bowl of cendol. **Reduce is** like taking a bunch of things and combining them into a single result.
* **How it works:** Reduce takes a list and a function that combines two things at a time. It keeps combining until you get one final value.
* **Example:** You have `[1, 2, 3, 4]` and want the sum. Reduce starts with 0, adds 1 (0+1=1), adds 2 (1+2=3), adds 3 (3+3=6), adds 4 (6+4=10), giving `10`.
* **Kampung analogy:** Mixing all your ingredients step-byredients step-by-step to make one perfect cendol.

### 4. Closures - Keeping Secrets in a Pouch
Imagine you’re a kampung fisherman with a special net. You make the net with a special knot that “remembers” how many fish you caught last time. Even if you give the net to someone else, it still keeps that memory inside. Closures are like functions that carry their own little pouch of memory, even when they’re used somewhere else.
* **How it works:** A closure is a function that remembers variables from where it was created, even if it’s called later in a different place.
* **Example:** You create a counter function:
```javascript
function makeCounter() {
  let count = 0;
  return function() {
    return count += 1;
  };
}
const counter = makeCounter();
console.log(counter()); // 1
console.log(counter()); // 2
```
The inner function remembers `count` even after `makeCounter` finishes.
* **Kampung analogy:** Your fishing net keeps track of your catch, no matter who uses it or where.

### 5. Immutability - Don’t Mess with the Original
In the kampung, you have a sacred recipe for rendang written on a wooden board. You never scribble over it or change it. If you want a new version, you copy it onto a new board and tweak that one. Immutability means you don’t change the original data; you make a new copy if you need changes.
* **How it works:** Instead of modifying a list or object, you create a new one with the changes.
* **Example:** You have `const numbers = [1, 2, 3]`. Instead of `numbers.push(4)`, you do `const newNumbers = [...numbers, 4]`, keeping `numbers` unchanged.
* **Kampung analogy:** You respect the original rendang recipe and make a new one for experiments, leaving the sacred board alone.

# Why Functional Programming in the Kampung?
FP is like farming in the kampung with clear rules:
* **Pure functions:** Like a recipe, same ingredients = same dish, no surprises.
* **No side effects:** Don’t mess up the kitchen (or data) while cooking.
* **Predictable:** Everyone knows what to expect from your nasi lemak.
It makes code easier to understand, test, and share, like passing down a foolproof recipe.

# Uses in ReactJS
ReactJS is like building a kampung community website where houses (components) update automatically when something changes (like a new event). Functional programming fits perfectly because React loves predictable, reusable code. Here’s how the concepts above are used in React:

### 1. Map in ReactJS
You’re displaying a list of kampung events on your website, like kenduri or gotong-royong. Each event needs its own card on the page. You use map to take an array of events and create a list of React components.
**Example:**
```javascript
const events = ["Kenduri", "Gotong-Royong", "Fishing Trip"];
return (
  <ul>
    {events.map((event, index) => (
      <li key={index}>{event}</li>
    ))}
  </ul>
);
```
* **Why it’s FP:** Map creates a new array of components without changing the `events` array. It’s pure and predictable.
* **Use case:** Rendering lists of posts, comments, or products in a React app.

### 2. Filter in ReactJS
You want to show only upcoming events, not past ones. You use filter to pick events based on a condition, like `date > today`.
**Example:**
```javascript
const allEvents = [
  { name: "Kenduri", date: "2025-06-20" },
  { name: "Fishing Trip", date: "2025-06-25" },
];
const today = "2025-06-23";
const upcomingEvents = allEvents.filter(event => event.date > today);
return (
  <ul>
    {upcomingEvents.map((event, index) => (
      <li key={index}>{event.name}</li>
    ))}
  </ul>
);
```
* **Why it’s FP:** Filter returns a new array, leaving `allEvents` untouched (immutability).
* **Use case:** Filtering search results, to-do lists, or user posts.

### 3. Reduce in ReactJS
You’re building a feature to count total attendees across all events. **Reduce*** combines the attendee counts into one number.
**Example:**
```javascript
const events = [
  { name: "Kenduri", attendees: 50 },
  { name: "Fishing Trip", attendees: 20 },
];
const totalAttendees = events.reduce((sum, event) => sum + event.attendees, 0);
return <p>Total Attendees: {totalAttendees}</p>;
```
* **Why it’s FP:** Reduce is pure—it doesn’t change the `events` array and always gives the same result for the same input.
* **Use case:** Calculating totals, like cart prices in an e-commerce app.

### 4. Closures in ReactJS
React uses closures in hooks like `useState` or `useEffect`. Imagine a button that counts how many times it’s clicked, like tracking how many kampung kids joined a game. The counter remembers its value between clicks.
**Example:**
```javascript
import React, { useState } from "react";
function Counter() {
  const [count, setCount] = useState(0);
  return (
    <button onClick={() => setCount(count + 1)}>
      Clicked {count} times
    </button>
  );
}
```
* **Why it’s FP:** The `setCount` function “closes over” the `count` variable, keeping it alive between renders. It’s predictable and encapsulated.
* **Use case:** Managing state in forms, counters, or toggles.

### 5. Immutability in ReactJS
React relies on immutability to detect changes and update the UI efficiently. When you update state, you create a new copy instead of modifying the old one, like copying the rendang recipe.
* **Example:**
```javascript
import React, { useState } from "react";
function EventList() {
  const [events, setEvents] = useState(["Kenduri"]);
  const addEvent = () => {
    setEvents([...events, "Fishing Trip"]); // New array, not events.push
  };
  return (
    <div>
      <ul>
        {events.map((event, index) => (
          <li key={index}>{event}</li>
        ))}
      </ul>
      <button onClick={addEvent}>Add Event</button>
    </div>
  );
}
```
* **Why it’s FP:** Using `[...events, "Fishing Trip"]` creates a new array, preserving immutability. React compares the new state to the old one to decide what to re-render.
* **Use case:** Updating lists, objects, or form inputs in React apps.

### Why FP in ReactJS?
React loves functional programming because:
* **Predictability:** Pure functions (like map, filter) make components easier to test and debug.
* **Reusability:** Functions like map create reusable patterns for rendering lists.
* **Immutability:** Helps React optimize updates by comparing old and new data.
* **State management:** Hooks like `useState` use closures to manage state cleanly.
In the kampung website, FP ensures your event list doesn’t suddenly show durian parties when you meant kenduri. It keeps things organized, like a well-run village.

### Wrapping Up
Functional programming is like running a kampung with clear, repeatable tasks:
* **Map** peels every manggis into a new basket of fruit.
* **Filter** picks only the ripe durians.
* **Reduce** mixes ingredients into one cendol.
* **Closures** are nets that remember your fish count.
* **Immutability** keeps your rendang recipe sacred.
