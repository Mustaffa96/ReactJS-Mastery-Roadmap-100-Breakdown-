# ESLint: The Village Elder Who Checks Your Work
Imagine you’re building a wooden bench in the kampung. You’ve got your tools and skills, but sometimes you make small mistakes—like forgetting to sand the edges or using the wrong nails. The village elder, Pakcik Linter, comes by with his sharp eyes and checks your work. He points out, “Oi, your nails are loose here, and that plank is crooked!” He’s not trying to scold you; he just wants your bench to be sturdy and safe.

**ESLint** is like that Pakcik Linter for your ReactJS code. It’s a tool that scans your code to catch mistakes, bad habits, or things that could break your app later. For example:
  * It spots if you forgot a semicolon (like forgetting a nail).
  * It warns you if you’re using a variable that doesn’t exist (like trying to use a tool you don’t have).
  * It enforces kampung rules—like making sure everyone writes code the same way so the team doesn’t get confused.
In ReactJS, ESLint can catch things like:
  * Unused variables in your components.
  * Missing key props in lists (a common React mistake).
  * Code that doesn’t follow your team’s style guide (e.g., “Always use arrow functions for event handlers”).
You set up ESLint with a configuration file (like telling Pakcik what rules to enforce), and it’ll nag you in your code editor (like VS Code) whenever you stray. For example, if you write:
```javascript

function MyComponent() {
  let name = "Ali"; // Unused variable
  return <div>Hello, world!</div>;
}
```
ESLint will highlight that name isn’t used and suggest fixing it. It’s like Pakcik saying, “Why you bring this extra wood if you’re not using it?”
# Prettier: The Tidy Neighbor Who Beautifies Your House
Now, picture your neighbor, Makcik Prettier, who loves everything neat and organized. You build your bench, but it looks a bit messy—nails sticking out, paint uneven. Makcik comes over, grabs her tools, and automatically polishes it up: aligns the nails, smooths the surface, and makes it look professional. You don’t even have to ask her—she just does it!

**Prettier** is that neighbor for your code. It’s an opinionated code formatter that automatically fixes your code’s appearance to make it consistent and pretty. It doesn’t care about the logic (that’s Pakcik Linter’s job); it just makes sure your code looks nice and follows a standard style. For example:
  * It fixes indentation (like straightening the rows of your padi field).
  * It adds or removes spaces around operators (like making sure your kampung signboard is readable).
  * It enforces consistent quotes (single or double) and line endings.
In a ReactJS project, you might write messy code like this:
```javascript

function MyComponent(){return<div>Hello,world!</div>}
```
Prettier swoops in and reformats it to:
```javascript

function MyComponent() {
  return <div>Hello, world!</div>;
}
```
It’s like Makcik Prettier sweeping your porch and arranging your flower pots without you lifting a finger. You can set Prettier to run every time you save a file in your editor, so your code always looks cantik.
# TypeScript: The Wise Teacher Who Plans Ahead
Now, meet Cikgu TypeScript, the wise kampung teacher who insists you plan your work carefully. When you’re building that bench, Cikgu says, “Before you start hammering, tell me exactly what kind of wood you’re using, how many nails, and what size the bench will be.” By planning ahead, you avoid mistakes like using weak wood or making a bench that’s too small.

**TypeScript** is like Cikgu for your ReactJS code. It’s a superset of JavaScript that adds types to your code, so you define what kind of data you’re working with upfront. This helps catch errors before your app even runs. For example:
  * You say a variable is a string, so TypeScript won’t let you accidentally treat it as a number.
  * You define what props a React component expects, so you don’t pass the wrong data.
Here’s a React component without TypeScript:
```javascript

function MyComponent(props) {
  return <div>Hello, {props.name}</div>;
}
```
If you pass a number to name by mistake (e.g., <MyComponent name={123} />), it might break or display weirdly, and you’d only find out when the app crashes.

With TypeScript, you define the types:
```typescript

interface Props {
  name: string;
}

function MyComponent({ name }: Props) {
  return <div>Hello, {name}</div>;
}
```
Now, if you try <MyComponent name={123} />, TypeScript will complain before you run the app, saying, “Oi, name must be a string, not a number!” It’s like Cikgu catching your mistake during planning, so your bench doesn’t collapse when someone sits on it.
# How They Work Together in the Kampung
In a ReactJS project, these three are like the perfect kampung team:
* **ESLint (Pakcik Linter)** checks that your code follows the rules and doesn’t have mistakes. It’s the quality control.
* **Prettier (Makcik Prettier)** makes sure your code looks neat and consistent, so everyone in the kampung (your team) can read it easily.
* **TypeScript (Cikgu TypeScript)** forces you to plan your code with types, catching errors early and making your app more reliable.

You set them up in your project like this:
* **ESLint:** Install it (npm install eslint --save-dev), run eslint --init to create a config file, and add React-specific rules (like eslint-plugin-react).
* **Prettier:** Install it (npm install prettier --save-dev), add a .prettierrc file for your style preferences, and integrate it with ESLint so they don’t fight.
* **TypeScript:** Add it to your project (npm install typescript --save-dev), rename your .js files to .tsx, and create a tsconfig.json to set type-checking rules.
When you code, your editor (like VS Code) will show ESLint warnings, auto-format with Prettier on save, and TypeScript will flag type errors. It’s like having Pakcik, Makcik, and Cikgu watching over your kampung project, making sure your ReactJS app is solid, pretty, and ready for the world.
