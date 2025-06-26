# 1. Code Reviews: Like Checking Your Neighbor’s Cooking
Imagine you’re cooking a big pot of rendang for the kenduri (village feast). Before serving it to everyone, you ask your trusted neighbor, Pakcik Ali, to taste it and give feedback. Maybe he says, “Eh, sedap, but tambah sikit garam lah,” or “This part too pedas, tone it down.” That’s what a code review is like in ReactJS.

In a ReactJS project, you write code to build a cool web app (like a fancy online kedai for selling kuih). But before your code goes live, you pass it to your teammates to check. They look at your JavaScript, React components, and logic to make sure:
* It works properly (no bugs, like ensuring your rendang doesn’t burn anyone’s tongue).

* It’s easy to understand (like writing a clear recipe others can follow).

* It follows the team’s “village rules” (coding standards, like “always use functional components” or “keep variable names clear like userName instead of x”).

For example, if you wrote a React component like this:
```jsx

function Button() {
  return <button>Click me</button>;
}
```
Your teammate might say, “Eh, add an onClick handler lah, or this button macam kuih without filling—tak best.” They might also check if your code is reusable and doesn’t break the app.

**In kampung terms:** Code reviews are like asking your kampung elders to check your work before the big kenduri. They make sure your code is sedap and won’t embarrass you in front of the whole village.

# 2. Linting: Like Your Makcik’s Housekeeping Rules
Picture your Makcik who’s super particular about keeping the house clean. Before anyone steps into her kampung house, she makes sure the floor is swept, the cushions are neat, and no dirty dishes are lying around. She’s got a checklist: “No shoes inside! Fold the kain pelikat properly!” That’s what linting does for your ReactJS code.

Linting is like an automated Makcik (a tool like ESLint) that checks your code for messiness. It enforces rules to keep your ReactJS code clean and consistent. For example:
* **No unused variables:** Like telling you, “Oi, why you buy 10kg of rice but only cook 1kg? Remove the extra!”

* **Proper formatting:** Like saying, “Indent your code properly, macam how you line up the ketupat neatly.”

* **Best practices:** It flags things like, “Don’t use var in React, use const or let—more modern lah.”

For instance, if you write this messy React code:
```jsx

function MyComponent() {
var x = 10;
  return <div>Hello</div>
}
```
ESLint will scold you like Makcik: “Why no semicolon? Why var? Why indent macam longkang? Fix it!” It might suggest:
```jsx

const MyComponent = () => {
  const x = 10;
  return <div>Hello</div>;
};
```
You set up linting in your project with tools like ESLint and Prettier, and they run automatically to catch issues before you even share your code for review. It’s like having Makcik sweep through your code before the kenduri.

**In kampung terms:** Linting is your Makcik making sure your code is tidy, follows the kampung coding rules, and doesn’t embarrass you when guests (other developers) see it.
# 3. CI/CD Pipelines: Like the Village Gotong-Royong for Your App
In the kampung, when there’s a big event like a wedding, everyone works together in a gotong-royong (community effort). One group prepares the nasi minyak, another sets up the tent, and someone else tests the sound system—all to make sure the event runs smoothly. CI/CD pipelines are like that for your ReactJS app.

**CI (Continuous Integration)** is like the kampung team working on the event prep. Every time you add new code (like a new React component), you “check it in” to a shared system (like GitHub). The CI pipeline automatically:
* Runs tests to make sure your code doesn’t break anything (like checking if the nasi minyak tastes right).

* Runs linting to catch messy code (like Makcik checking the tent setup).

* Builds your React app to make sure it compiles properly (like making sure the whole kenduri setup is ready).

For example, you push this React code to GitHub:
```jsx

const Welcome = () => <h1>Selamat Datang to My App!</h1>;
export default Welcome;
```
The CI pipeline (using tools like GitHub Actions or Jenkins) runs your tests, checks for linting errors, and builds the app to ensure everything works.

**CD (Continuous Delivery/Deployment)** is like serving the kenduri food to the guests. Once your code passes all checks, the pipeline automatically deploys it to a server (like AWS or Vercel) so users can access your shiny new React app. It’s like the kenduri going live for the whole kampung to enjoy.
For example, a CI/CD pipeline might:
* Run npm test to check your React tests.

* Run npm run lint to enforce Makcik’s rules.

* Build the app with npm run build.

* Deploy it to a hosting platform like, “Okay, the app is live at kampung-app.com!”

**In kampung terms:** CI/CD is like a gotong-royong where the whole kampung (tools and processes) works together to test, check, and launch your React app smoothly, so it’s ready for everyone to use without any malu (embarrassment).
### Putting It All Together
Imagine you’re building a ReactJS app for a kampung online marketplace:
* **Code reviews** are like asking your pakcik and makcik to taste-test your kuih code before it goes to the market.

* **Linting** is Makcik making sure your code is clean and follows the kampung’s high standards.

* **CI/CD** pipelines are the gotong-royong team that tests, builds, and sets up your app stall automatically, so customers can buy your kuih online without any hiccups.

By using these practices, your ReactJS app stays sedap, reliable, and ready for the whole kampung (and beyond) to enjoy! 

