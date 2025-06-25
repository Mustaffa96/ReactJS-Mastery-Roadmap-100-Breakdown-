# What’s Testing in ReactJS?
In the kampung, when you build a bicycle, you don’t just ride it straight away. You check if the wheels spin, the brakes work, and the chain doesn’t fall off. Testing in ReactJS is like that—it’s about making sure your app’s buttons, forms, and pages work as expected before you “ride” it (launch it for users).
There are two main types of tests we’ll talk about:
  * **Unit tests:** Checking small parts, like testing just the bicycle’s bell to make sure it rings.
  * **Integration tests:** Checking how parts work together, like making sure the bell, brakes, and pedals all play nice when you ride.
Now, let’s meet the tools: Jest, React Testing Library, and Cypress. Think of them as your kampung toolbox for fixing and checking the bicycle.
# 1. Jest: The Kampung Mechanic’s Wrench
### What is it?
Jest is like a trusty wrench you use to check if small parts of your app work. It’s a testing framework that runs your tests, checks if they pass or fail, and gives you a report. It’s great for unit tests (testing small pieces of code, like a function or a React component).
### How does it work in the kampung?
Imagine you made a bell for the bicycle. You want to test if it rings when you press it. Jest lets you write a test like: “If I press the bell, it should make a ‘ding’ sound.” You run Jest, and it tells you if the bell works or if it’s broken.
### Example in ReactJS:
Say you have a React component called KampungButton that shows “Hello, Kampung!” when clicked. A Jest test might look like this:
```javascript

test('KampungButton says hello when clicked', () => {
  const button = <KampungButton />;
  // Simulate a click
  button.click();
  // Check if it says "Hello, Kampung!"
  expect(button.text()).toBe('Hello, Kampung!');
});
```
Jest runs this and says, “Pass!” if the button works, or “Fail!” if it doesn’t.
Why use Jest?
  * It’s fast, like fixing a bicycle tire in 5 minutes.
  * It works well for small, isolated tests (unit tests).
  * It’s already included when you create a React app with create-react-app, so no extra setup.
**Kampung tip:** Jest is your go-to for checking individual parts, but it’s not great for testing how the whole bicycle (your app) feels when you ride it. For that, you need React Testing Library or Cypress.
# 2. React Testing Library: The Kampung Test Ride
### What is it?
React Testing Library (RTL) is like taking the bicycle for a test ride to see how it feels for the rider (the user). It focuses on testing how your React components behave from the user’s perspective, not the tiny nuts and bolts. It’s great for unit tests and integration tests.
### How does it work in the kampung?
Instead of checking if the bell’s spring is perfect (like Jest might), RTL checks if the bell rings when the user presses it. It tests things the way a kampung kid would use the bicycle: “Can I press the button? Does the page show what I expect?”
### Example in ReactJS:
Let’s say you have a KampungForm component where a user types their name and submits it to see a greeting. An RTL test might look like this:
```javascript

import { render, screen, fireEvent } from '@testing-library/react';

test('KampungForm shows greeting after submit', () => {
  // Render the form
  render(<KampungForm />);
  // Find the input and type "Ali"
  const input = screen.getByLabelText('Name');
  fireEvent.change(input, { target: { value: 'Ali' } });
  // Find the submit button and click it
  const button = screen.getByText('Submit');
  fireEvent.click(button);
  // Check if the greeting says "Hello, Ali!"
  expect(screen.getByText('Hello, Ali!')).toBeInTheDocument();
});
```
RTL mimics how a user interacts with the form and checks if the app responds correctly.
### Why use React Testing Library?
  * It tests things the way users see them, like riding the bike instead of inspecting the parts.
  * It encourages you to write tests that don’t break when you tweak the app’s design.
  * It works hand-in-hand with Jest (Jest runs the tests, RTL helps you write them).
**Kampung tip:** Use RTL when you want to make sure your app feels right for the user, like ensuring the bicycle is fun and easy to ride, not just mechanically sound.
# 3. Cypress: The Kampung Road Trip Inspector
### What is it?
Cypress is like taking the bicycle on a full road trip through the kampung to see how it handles bumps, turns, and long rides. It’s a tool for end-to-end tests, which are a type of integration test that checks the entire app in a real-world setting (a real browser). It’s less about small parts and more about the whole experience.
### How does it work in the kampung?
Imagine you want to test the bicycle by riding it from your house to the kampung market. You check if you can pedal, brake, and ring the bell along the way. Cypress opens your app in a browser, clicks buttons, fills forms, navigates pages, and checks if everything works as expected.
### Example in ReactJS:
Let’s say your app has a flow where a user logs in, goes to a dashboard, and sees their profile. A Cypress test might look like this:
```javascript

describe('Kampung App Login Flow', () => {
  it('logs in and shows profile', () => {
    // Visit the login page
    cy.visit('/login');
    // Type username and password
    cy.get('input[name=username]').type('Ali');
    cy.get('input[name=password]').type('secret123');
    // Click login button
    cy.get('button').contains('Login').click();
    // Check if dashboard shows "Welcome, Ali!"
    cy.get('.dashboard').should('contain', 'Welcome, Ali!');
    // Navigate to profile page
    cy.get('a').contains('Profile').click();
    // Check if profile page loads
    cy.url().should('include', '/profile');
  });
});
```
Cypress runs this in a browser, like a real user riding through the app.
### Why use Cypress?
* It tests the app as a whole, like a full kampung road trip.
* It’s great for catching bugs that only show up when parts work together (e.g., navigation or API calls).
* It’s easy to debug because you can watch the tests run in a browser.
**Kampung tip:** Cypress is slower than Jest or RTL because it tests the whole app in a real browser. Use it for big, important flows (like login or checkout), not for every tiny button.
# How Do They Work Together in the Kampung?
Think of building a bicycle:
* **Jest** checks if the bell, brakes, and pedals work on their own (unit tests).
* **React Testing Library** takes the bicycle for a short spin to see if it rides smoothly for the user (unit and integration tests).
* **Cypress** takes the bicycle on a long trip to the kampung market to make sure it holds up in the real world (end-to-end integration tests).
In a React app, you’d use:
* **Jest + RTL** for most of your tests (80-90%), like testing components and user interactions.
* **Cypress** for a few key flows (10-20%), like testing login, signup, or payment processes.
# Which Tool Should You Pick?
* **Jest:** Use it as the base to run tests. It’s like the toolbox that holds everything together.
* **React Testing Library:** Use it with Jest to test components and user interactions. It’s your main tool for unit and integration tests.
* **Cypress:** Use it for big, real-world tests when you need to check the whole app in a browser.
**Kampung analogy:** If you’re fixing a bicycle, use Jest and RTL to check the parts and take short rides. Use Cypress when you’re ready to race it across the kampung to make sure it won’t break down.
# Final Kampung Wisdom
Testing is like making sure your kampung bicycle is safe and fun to ride. Start small with Jest and RTL to test buttons, forms, and pages. Then, use Cypress to test the big journeys, like going from login to checkout. With these tools, your React app will be as reliable as a kampung uncle’s old motorbike—always ready to roll!
