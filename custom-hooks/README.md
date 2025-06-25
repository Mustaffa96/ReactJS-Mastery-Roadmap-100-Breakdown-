Alright, let’s break down ReactJS Custom Hooks in a way that feels like we’re chatting in the kampung, sipping teh tarik under a big shady tree. I’ll keep it simple, like explaining to your cousin who’s just getting into coding.

# What Are Custom Hooks?
Imagine you’re in the kampung, and you’ve got a special recipe for nasi lemak that you love to cook. Every time you want to make it, you don’t start from scratch—you’ve got a handy notebook with all the steps (like how to cook the rice, make the sambal, and fry the ikan bilis). This notebook saves you time and effort because you can reuse it whenever you want to whip up nasi lemak, or even share it with your neighbor so they can make it too.

In ReactJS, **Custom Hooks** are like that notebook. They let you bundle up reusable logic (the steps for your recipe) so you can use it in multiple parts of your app without repeating yourself. It’s a way to make your code cleaner, more organized, and easier to share, just like passing your recipe to someone else in the kampung.

# How Do Custom Hooks Work?
In React, a hook is a special function that lets you “hook into” React features like state or lifecycle methods. You’ve probably heard of built-in hooks like useState (for managing data) or useEffect (for handling side effects like fetching data). Custom Hooks are just hooks you create yourself to package up logic that you use over and over again.
Think of it like this: in the kampung, you notice everyone is making their own sambal for nasi lemak, but they’re all doing the same steps—grind the chilies, fry the onions, add some tamarind. So, you decide to make a “Sambal Master Kit” (your custom hook). Anyone can grab your kit, follow the steps, and get perfect sambal without figuring it out themselves.

A Custom Hook is a JavaScript function that:
* Starts with the word `use` (like `useSambalMaker`—this is a React rule).
* Can use other React hooks (like `useState` or `useEffect`) inside it.
* Packages up logic that you can reuse in different components.

# Why Use Custom Hooks?
Let’s say you’re building a small app for the kampung’s pasar malam (night market). You have a few components:
* One shows a list of stalls with their names.
* Another shows which stalls are open based on the time.
* Another lets users save their favorite stalls.
In each of these components, you need to fetch data from an API, handle loading states, and deal with errors. Without Custom Hooks, you’d write the same fetch logic, loading spinner, and error messages in every component. That’s like every auntie in the kampung grinding her own chilies for sambal from scratch—tiring and messy!

With a Custom Hook, you can write the logic once in a reusable function (like `useFetchStallData`) and share it across all your components. It’s like giving every auntie your “Sambal Master Kit” so they can make sambal quickly and consistently.

# Example: A Custom Hook in Kampung Terms
Let’s create a Custom Hook called `useFetchStallData` to fetch stall info for the pasar malam app. This is like your notebook for making sambal, but for fetching data.
```javascript
import { useState, useEffect } from 'react';

// Our Custom Hook
function useFetchStallData(stallUrl) {
  // State to keep track of data, loading, and errors
  const [data, setData] = useState(null); // The stall info
  const [isLoading, setIsLoading] = useState(true); // Is the data still cooking?
  const [error, setError] = useState(null); // Any problems?

  // Fetch the data when the component loads
  useEffect(() => {
    async function fetchStall() {
      try {
        setIsLoading(true); // Start cooking
        const response = await fetch(stallUrl); // Get data from the API
        const result = await response.json(); // Turn it into usable info
        setData(result); // Save the stall info
      } catch (error) {
        setError("Oi, something went wrong lah!"); // Handle errors
      } finally {
        setIsLoading(false); // Done cooking
      }
    }
    fetchStall();
  }, [stallUrl]); // Run again if the URL changes

  // Return the stuff we need
  return { data, isLoading, error };
}
```

Now, imagine you’re using this hook in your app, like how you’d use the sambal kit in the kitchen:
```javascript
import React from 'react';
import useFetchStallData from './useFetchStallData';

function StallList() {
  // Use the Custom Hook to get stall data
  const { data, isLoading, error } = useFetchStallData('https://pasar-malam-api.com/stalls');

  if (isLoading) return <p>Loading stalls, tunggu sikit...</p>;
  if (error) return <p>{error}</p>;

  return (
    <div>
      <h2>Pasar Malam Stalls</h2>
      <ul>
        {data.map(stall => (
          <li key={stall.id}>{stall.name} - {stall.foodType}</li>
        ))}
      </ul>
    </div>
  );
}
```
In this example:
* The `useFetchStallData` hook is like your “Sambal Master Kit.” It handles all the hard work of fetching data, managing loading states, and catching errors.
* You can use it in any component that needs to fetch stall data, like one for showing open stalls or another for saving favorites. No need to rewrite the fetch logic every time.
* If you need to fetch different data (say, customer reviews), you just pass a different URL to the hook, like tweaking the sambal recipe for a spicier version.

# Benefits of Custom Hooks (Kampung Style)
* **Saves Time:** Instead of rewriting the same logic (like fetching data or handling forms) in every component, you write it once in a Custom Hook and reuse it. It’s like sharing your sambal recipe instead of everyone starting from zero.
* **Keeps Things Tidy:** Your components stay clean and focused on what they display, not on the messy logic. It’s like keeping your kitchen neat while the sambal kit does the heavy lifting.
* **Easy to Share**: You can share your Custom Hook with other developers in the kampung (or your team) so everyone can use the same logic without duplicating effort.
* **Flexible:** You can tweak the hook for different situations. For example, `useFetchStallData` can fetch any data by changing the URL, just like adding more chili to your sambal for a different flavor.

# Another Example: A Toggle Hook
Let’s say you’re building a feature for the pasar malam app where users can toggle between “light” and “dark” mode for the app’s look. You could write a Custom Hook called useToggle to handle this logic:

```javascript
import { useState } from 'react';

function useToggle(initialValue = false) {
  const [value, setValue] = useState(initialValue);

  const toggle = () => {
    setValue(!value);
  };

  return [value, toggle];
}
```

Use it in a component:
```javascript
import React from 'react';
import useToggle from './useToggle';

function AppTheme() {
  const [isDarkMode, toggleDarkMode] = useToggle(false);

  return (
    <div style={{ background: isDarkMode ? 'black' : 'white', color: isDarkMode ? 'white' : 'black' }}>
      <h2>Pasar Malam App</h2>
      <button onClick={toggleDarkMode}>
        Switch to {isDarkMode ? 'Light' : 'Dark'} Mode
      </button>
    </div>
  );
}
```
This `useToggle` hook is like a simple kampung light switch. You can use it anywhere you need to toggle something on or off (like showing/hiding a menu or enabling/disabling a feature). It’s small but super reusable.

# Tips for Making Good Custom Hooks
* **Name It Right:** Always start the name with `use` (e.g., `useFetchStallData`, `useToggle`). This tells React it’s a hook and follows the rules.
* **Keep It Focused:** A good hook does one thing well, like fetching data or toggling a value. Don’t make it a big, messy “everything” hook.
* **Make It Reusable:** Design it so it can work in different situations. For example, `useFetchStallData` works with any URL, not just one specific API.
* **Test It:** Just like you’d taste your sambal before serving it, test your hook to make sure it works in different components.

### Wrapping Up
Custom Hooks in React are like your trusty kampung recipe book. They let you package up logic (like fetching data, toggling states, or handling forms) so you can reuse it across your app without repeating yourself. It’s like sharing your best sambal recipe with the whole kampung—everyone gets to enjoy it, and you save time and effort.
