Alright, let’s break down useCallback, useMemo, and useRef in ReactJS using simple, "kampung" (village-style) terms—like we’re chatting over a cup of teh tarik at the warung. These are tools in React to make your app run smoother (like a well-oiled bicycle) and handle things like accessing the DOM (think of it as poking at the nuts and bolts of your webpage). Let’s go one by one.

# 1. useCallback: Keeping Your Functions Steady Like a Reliable Motor
**What is it?**
Imagine you’re a hawker who fries kuey teow every day. You have a trusty spatula you use for flipping. Every time you cook, you don’t grab a new spatula—you use the same one because it works fine. In React, useCallback is like keeping that same spatula (a function) instead of making a new one every time your component redraws. It’s about saving memory and preventing unnecessary work.

**Why use it?**
When your component updates (like when someone changes their order), React might create a new version of your function. If that function is passed to a child component (like handing your spatula to an assistant), the child might think, “Eh, new spatula? I better start over!” This can cause the child to re-render unnecessarily, slowing down your app. useCallback says, “No need new spatula, use the old one unless the recipe changes.”

**How it works (in kampung terms):**
You tell React, “Oi, keep this function the same unless certain things (dependencies) change.” It’s like telling your assistant, “Only get a new spatula if I change the wok or the ingredients.”
**Example:**
```jsx
const MyComponent = () => {
  const [count, setCount] = useState(0);

  // Without useCallback, this function is recreated every render
  const handleClick = useCallback(() => {
    console.log("Button clicked, count is", count);
  }, [count]); // Only make a new function if `count` changes

  return <ChildComponent onClick={handleClick} />;
};
```
**When to use it?**
Use useCallback when you pass a function to a child component that’s wrapped in React.memo (a way to tell the child, “Don’t redraw unless you really need to”). It prevents the child from thinking, “New function? I better redraw!” This saves performance, especially in big apps with many components.

# 2. useMemo: Saving Your Hard Work Like Storing Leftover Nasi Lemak
**What is it?**
Imagine you’re making nasi lemak, and the sambal takes a long time to cook. You don’t want to cook fresh sambal every time someone orders—you store some in a container and reuse it unless the ingredients (like chilies or onions) change. useMemo is like that container—it saves the result of a heavy calculation so React doesn’t redo it every time the component updates.

**Why use it?**
Some calculations in your app (like sorting a big list of customers or doing math on data) are “expensive” (take time and effort). If the component re-renders but the data hasn’t changed, redoing the calculation is like cooking sambal from scratch for no reason. useMemo says, “Eh, just use the sambal from the fridge unless the recipe changes.”

**How it works (in kampung terms):**
You tell React, “Store this calculation result and only redo it if certain things (dependencies) change.” It’s like checking if your onions or chilies are different before making new sambal.
**Example:**
```jsx
const MyComponent = () => {
  const [numbers, setNumbers] = useState([1, 2, 3, 4, 5]);

  // Expensive calculation: sorting a big array
  const sortedNumbers = useMemo(() => {
    console.log("Sorting numbers...");
    return [...numbers].sort((a, b) => b - a);
  }, [numbers]); // Only re-sort if `numbers` changes

  return <div>Sorted: {sortedNumbers.join(", ")}</div>;
};
```
**When to use it?**
Use useMemo when you have heavy computations (like filtering, sorting, or processing big data) that don’t need to run every time the component updates. It’s like saving your energy for when it’s really needed.

# 3. useRef: A Sticky Note for Things You Want to Remember or Poke
**What is it?**
Imagine you have a sticky note where you jot down something important, like the number of customers who visited your warung today. This note doesn’t change just because you serve a new customer—it stays until you update it yourself. useRef is like that sticky note in React—it holds a value that doesn’t get reset when the component re-renders. It’s also handy for “poking” the DOM, like grabbing a specific input field to focus on it.

**Why use it?** 
* **To remember stuff:** Unlike state (which triggers re-renders when it changes), useRef lets you store values (like a counter or a timer ID) without causing the component to redraw. It’s like keeping a tally on your sticky note without repainting the whole warung.
* **To access the DOM:** You can use useRef to point at an HTML element (like an input field) and do things like focus it or check its value, like reaching out to adjust a signboard in your warung.

**How it works (in kampung terms):**
You create a **useRef** sticky note and stick it somewhere. You can write on it, read it, or use it to point at something in your warung (like the cash register). It stays there even if you rearrange the tables (re-render).
**Example:**
```jsx
const MyComponent = () => {
  const inputRef = useRef(null); // Create a sticky note to point at an input
  const countRef = useRef(0); // Create a sticky note for a counter

  const handleClick = () => {
    countRef.current += 1; // Update the counter without re-rendering
    console.log("Clicked", countRef.current, "times");
    inputRef.current.focus(); // Poke the input field to focus it
  };

  return (
    <div>
      <input ref={inputRef} type="text" />
      <button onClick={handleClick}>Click me</button>
    </div>
  );
};
```
**When to use it?** 
* Use **useRef** to store values that don’t need to trigger re-renders (like counters, timers, or previous values).
* Use it to access DOM elements directly, like focusing an input, scrolling to a div, or measuring something on the page.

# How They Help with Performance and DOM Access
* **Performance (useCallback & useMemo):** These two are like telling your warung assistants to reuse tools and ingredients instead of starting from scratch every time. **useCallback** prevents unnecessary function creation, and useMemo avoids redoing heavy calculations. This makes your app faster, especially when you have many components or complex logic.
* **DOM Access (useRef): useRef** is your tool for directly touching the webpage’s nuts and bolts (like focusing an input or measuring a div’s size) without relying on state or causing extra work for React.

### Kampung Analogy Summary
* **useCallback:** Your trusty spatula you reuse unless the recipe changes.
* **useMemo:** Your container of pre-made sambal you pull out unless the ingredients change.
* **useRef:** A sticky note for jotting down numbers or pointing at something in your warung that stays put no matter how busy things get.
