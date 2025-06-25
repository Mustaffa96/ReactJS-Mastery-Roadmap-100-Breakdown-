# What is React Router?
Imagine your kampung as a big website, and each house, shop, or surau (mosque) is a different page. React Router is like the village paths and signboards that guide people to the right place. It helps users move between pages in a React app without reloading the whole website, making navigation smooth like riding a bicycle through the kampung.

# 1. Dynamic Routing: Flexible Paths to Any House
In the kampung, every house has an address, like “Kampung Sejahtera, House No. 5.” But what if a new family moves in, and you don’t know their house number in advance? You’d use a general direction like “Go to any house with a blue gate.” That’s what dynamic routing does in React Router.
* **What is it?**
Dynamic routing lets you create flexible paths (URLs) that work for different data without hardcoding every single route. For example, instead of making a separate path for every user’s profile page (like `/user1`, `/user2`, `/user3`), you create one path that works for all users, like `/user/:id`. The :id part is like a placeholder that changes based on the user.

* **Kampung Example:**
Say you’re delivering nasi lemak to villagers. Instead of writing a route for every house (`/house1`, `/house2`), you use a general path like `/house/:houseNumber`. If someone orders from House No. 7, the path becomes `/house/7`, and your app knows to show the details for that house.

* **How it works in React Router:**
You define a route with a placeholder (like `:id`) in your Route component. For example:
```jsx

import { BrowserRouter, Route, Routes } from 'react-router-dom';

function App() {
  return (
    <BrowserRouter>
      <Routes>
        <Route path="/house/:houseNumber" element={<HouseDetails />} />
      </Routes>
    </BrowserRouter>
  );
}

function HouseDetails() {
  const { houseNumber } = useParams(); // Gets the houseNumber from the URL
  return <h1>Welcome to House No. {houseNumber}</h1>;
}
```
If the user visits `/house/7`, the HouseDetails component shows “Welcome to House No. 7.” The :houseNumber is dynamic, so it works for any house number.

* **Why is it useful?**
It saves you from creating endless routes for similar pages. Whether you have 10 houses or 1,000, one dynamic route handles them all.

# 2. Nested Routes: Rooms Inside a House
Now, imagine you’re inside a house in the kampung. The house is one page, but it has different rooms—like the living room, kitchen, or bedroom. Each room is a smaller part of the house, and you can navigate between them without leaving the house. Nested routes in React Router work the same way.
* **What is it?**
Nested routes let you create routes within routes, so you can show sub-pages inside a main page. For example, a user’s profile page (`/user/:id`) might have sub-sections like `/user/:id/posts` or `/user/:id/settings`.

* **Kampung Example:**
Let’s say you visit Pak Ali’s house (`/house/ali`). Inside his house, there are different areas: the living room (`/house/ali/living-room`) or the kitchen (`/house/ali/kitchen`). Nested routes let you show these “rooms” while keeping the main “house” page layout (like a menu or header) the same.

* **How it works in React Router:**
You use the <Outlet> component to tell React Router where to display the nested content. Here’s an example:
```jsx

import { BrowserRouter, Route, Routes, Outlet } from 'react-router-dom';

function App() {
  return (
    <BrowserRouter>
      <Routes>
        <Route path="/house/:houseNumber" element={<House />}>
          <Route path="living-room" element={<LivingRoom />} />
          <Route path="kitchen" element={<Kitchen />} />
        </Route>
      </Routes>
    </BrowserRouter>
  );
}

function House() {
  const { houseNumber } = useParams();
  return (
    <div>
      <h1>House No. {houseNumber}</h1>
      <Outlet /> {/* This is where nested routes (rooms) will show */}
    </div>
  );
}

function LivingRoom() {
  return <h2>Welcome to the Living Room!</h2>;
}

function Kitchen() {
  return <h2>Welcome to the Kitchen!</h2>;
}
```
  * If you visit `/house/7/living-room`, you’ll see “House No. 7” at the top (from the House component) and “Welcome to the Living Room!” below (from the LivingRoom component).

  * The `<Outlet>` is like a placeholder where the nested route’s content appears.

* **Why is it useful?**
It keeps your app organized. The main page (the “house”) can have a consistent layout (like a navigation bar), and the nested routes (the “rooms”) can change the content inside without reloading the whole page.

# 3. Route Guards: The Village Gatekeeper
In the kampung, not everyone can enter certain places. For example, only family members can enter the private rooms of a house, and you need permission to enter the surau during a special event. Route guards in React Router are like these gatekeepers—they control who can access certain pages.
* **What is it?**
Route guards are ways to protect routes so only authorized users can access them. For example, you might block a user from seeing a “dashboard” page unless they’re logged in.

* **Kampung Example:**
Imagine you’re trying to enter Pak Mat’s private office (`/office`). The kampung guard (route guard) checks if you have a key (like a login token). If you don’t, the guard redirects you to the village entrance (`/login`) instead.

* **How it works in React Router:**
You can create a guard by wrapping a route with a component that checks conditions (like if the user is logged in). Here’s an example:
```jsx

import { BrowserRouter, Route, Routes, Navigate } from 'react-router-dom';

function App() {
  return (
    <BrowserRouter>
      <Routes>
        <Route path="/login" element={<Login />} />
        <Route
          path="/office"
          element={<ProtectedRoute component={<Office />} />}
        />
      </Routes>
    </BrowserRouter>
  );
}

function ProtectedRoute({ component }) {
  const isLoggedIn = checkIfUserIsLoggedIn(); // Your logic to check login status
  return isLoggedIn ? component : <Navigate to="/login" />;
}

function Office() {
  return <h1>Welcome to the Private Office!</h1>;
}

function Login() {
  return <h1>Please Log In</h1>;
}

function checkIfUserIsLoggedIn() {
  // Example: Check if there's a token in localStorage
  return !!localStorage.getItem('token');
}
```
  * If the user visits `/office` and `isLoggedIn` is true, they see the Office component.

  * If isLoggedIn is false, they’re redirected to `/login`.

* **Why is it useful?**
It keeps sensitive pages secure. You don’t want just anyone wandering into private areas of your app, like an admin dashboard or a user’s personal settings.

# Putting It All Together in the Kampung
Let’s say your kampung website has:
* **Dynamic Routing:** A path like `/house/:houseNumber` to visit any house in the village.

* **Nested Routes:** Inside each house, you can visit rooms like `/house/:houseNumber/kitchen` or `/house/:houseNumber/living-room`.

* **Route Guards:** Some houses, like the village chief’s office (`/office`), require a special pass (login) to enter.

React Router ties all this together to make navigation smooth, flexible, and secure, like a well-planned kampung with clear paths and a friendly guard.

# Quick Tips for the Kampung Coder
* **Dynamic Routing:** Use `:param` in your paths for flexible URLs (e.g., `/user/:id`).

* **Nested Routes:** Use `<Outlet>` to show sub-pages inside a main page.

* **Route Guards:** Check conditions (like login status) before allowing access to a route, and redirect if needed.

