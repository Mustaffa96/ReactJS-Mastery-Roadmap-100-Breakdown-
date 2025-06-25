Alright, let’s break down Memoization in ReactJS with React.memo, useMemo, and useCallback in a way that feels like we’re chatting in a kampung (village) setting—simple, relatable, and straight from the heart. Imagine we’re sitting under a big tree, sipping teh tarik, and I’m explaining this like I’m talking to a neighbor who’s curious about coding.

# What’s Memoization, Lah?
Memoization is like keeping your favorite kuih recipe in a special notebook so you don’t have to figure it out every time you want to make kuih. In React, it’s about saving the results of expensive calculations or functions so you don’t waste time redoing them if nothing has changed. It’s all about making your app run faster, like making sure your motorbike doesn’t burn extra petrol for no reason.

React gives us three tools for this: React.memo, useMemo, and useCallback. Let’s explain each one with kampung-style analogies.

# 1. React.memo: The Smart Kuih Maker
Imagine you’re a kuih seller in the kampung. Every morning, you make a big batch of kuih pisang. If the recipe (your ingredients and steps) hasn’t changed, you don’t remake the kuih from scratch—you just use the ones you already prepared. React.memo is like that for React components.
* **What it does:** It “remembers” a component’s output. If the props (the “ingredients” you pass to the component) are the same, React skips re-rendering it and uses the saved version.
* **When to use it:** For components that don’t need to update often, especially if they’re “heavy” (like a big kuih pisang with lots of bananas and sugar) and rendering them takes time.
* **Kampung example:** Your neighbor asks for kuih pisang every day. If they ask for the same amount and flavor, you just hand them the kuih from your pre-made batch instead of cooking a new one.
Code example:
```jsx
const KuihPisang = React.memo(({ flavor, amount }) => {
  console.log("Making kuih pisang..."); // Only logs if props change
  return <div>{flavor} kuih, {amount} pieces!</div>;
});
```
If the `flavor` and `amount` props don’t change, React.memo says, “Eh, no need to remake the kuih, just use the one from yesterday!” This saves time and keeps your app smooth.

# 2. useMemo: The Recipe Shortcut
Now, imagine you’re making a complicated sambal for your nasi lemak. Calculating the perfect mix of chili, belacan, and onions takes effort. If the ingredients are the same, you don’t want to keep mixing a new batch every time someone orders nasi lemak. useMemo is like writing down the sambal recipe’s result so you can reuse it.
* **What it does:** It “remembers” the result of a calculation or value. It only recalculates if the inputs (dependencies) change.
* **When to use it:** For expensive calculations, like filtering a big list or doing math that doesn’t need to happen every render.
* **Kampung example:** You’ve got a list of 100 kampung kids’ names for a party. You only sort the list again if new kids are added. Otherwise, you reuse the sorted list from your notebook.
**Code example:**
```jsx
const sortedKids = useMemo(() => {
  console.log("Sorting kids list..."); // Only logs if kidsList changes
  return kidsList.sort();
}, [kidsList]); // Only re-sorts if kidsList changes
```
Here, `useMemo` saves the sorted list. If `kidsList` doesn’t change, it skips the sorting and uses the saved result, saving time like reusing your sambal mix.

# 3. useCallback: The Reusable Cooking Instructions
Let’s say you’re teaching your cousin how to fry mee goreng. You write down the steps (like “heat oil, add garlic, toss noodles”). If the recipe doesn’t change, you don’t rewrite the instructions every time—they’re the same! useCallback is like keeping those instructions saved so you don’t create a new copy unnecessarily.
* **What it does:** It “remembers” a function and only creates a new one if its dependencies change. This is important because React components re-render often, and new functions get created each time, which can cause problems for child components.
* **When to use it:** When you pass functions to child components or use them in `useEffect`, and you want to avoid unnecessary re-renders.
* **Kampung example:** You give your cousin the same mee goreng recipe every day. If the recipe hasn’t changed, you don’t rewrite it—you just point to the same piece of paper.
**Code example:**
```jsx
const fryMeeGoreng = useCallback(() => {
  console.log("Frying mee goreng with", ingredients);
  return `Mee goreng with ${ingredients}!`;
```
}, [ingredients]); // Only creates a new function if ingredients change
If `ingredients` stays the same, `useCallback` gives you the same function (like the same recipe paper). This prevents child components from thinking, “Eh, new recipe? Better re-render!” when nothing has changed.

### How They Work Together in the Kampung
Imagine you’re running a kampung food stall:
* **React.memo** makes sure your kuih pisang component doesn’t re-render unless the customer asks for a different flavor or amount.
* **useMemo** saves the sorted list of customers so you don’t keep sorting it every time someone orders.
* **useCallback** keeps your mee goreng frying instructions the same, so your helper (a child component) doesn’t get confused by new instructions every time.

**When to use them:**
* Use **React.memo** for components that render the same output with the same props.
* Use **useMemo** for heavy calculations or values you don’t want to redo unnecessarily.
* Use **useCallback** for functions you pass around, especially to child components or useEffect.

**Warning:** Don’t overuse these tools, lah. It’s like adding too much sugar to your kuih—too much memoization can make your code complicated and slow down your app instead. Only use them when you notice performance issues, like when your app is lagging like a slow motorbike on a bumpy kampung road.

### Quick Kampung Recap
* **React.memo:** “Same kuih order? Just give the pre-made one.”
* **useMemo:** “Same sambal ingredients? Use the mix I already made.”
* **useCallback:** “Same mee goreng recipe? Don’t rewrite the instructions.”
