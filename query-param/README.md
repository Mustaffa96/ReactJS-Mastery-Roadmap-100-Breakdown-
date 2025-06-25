# What Are Query Params? (Macam Papan Tanda kat Jalan)
Query params are like little notes or signs you stick on the road to tell you extra info about where you’re going. In a URL, they come after a ? and look like key=value pairs. For example:
```
http://kampungstore.com/products?category=makanan&price=cheap
```
Here, category=makanan and price=cheap are query params. They’re like telling the shopkeeper, “Oi, tunjuk saya makanan yang murah je!”
In ReactJS, query params help your app know what the user wants to see or do, like filtering products or searching for something specific.
# How to Handle Query Params in ReactJS (Macam Baca Papan Tanda)
To read these “notes” (query params) in ReactJS, you usually use a library called react-router-dom (think of it as the village map). Here’s how you do it:
* **Install the Map (react-router-dom):**
Make sure you have react-router-dom installed in your project. It’s like getting a good map to navigate the village roads.
```bash

npm install react-router-dom
```
* **Read the Query Params (Baca Nota kat URL):**
In React, you can use the useLocation or useSearchParams hooks from react-router-dom to grab the query params. Imagine you’re checking the signs on the road to know what the user is looking for.
```jsx

import { useSearchParams } from 'react-router-dom';

function KampungShop() {
  const [searchParams] = useSearchParams();

  // Ambil nilai dari query params, macam baca papan tanda
  const category = searchParams.get('category'); // Dapat "makanan"
  const price = searchParams.get('price'); // Dapat "cheap"

  return (
    <div>
      <h1>Selamat datang ke Kedai Kampung!</h1>
      <p>Kategori: {category || 'tak ada kategori'}</p>
      <p>Harga: {price || 'tak ada harga'}</p>
    </div>
  );
}
```
In this example, if the URL is http://kampungstore.com/products?category=makanan&price=cheap, the page will show:
Kategori: makanan

Harga: cheap

It’s like walking into the shop and seeing only the stuff you asked for based on the signs.

* **Update Query Params (Tukar Papan Tanda):**
If you want to change the query params (like adding a new filter), you can use setSearchParams to update the URL without reloading the page.
```jsx

import { useSearchParams } from 'react-router-dom';

function KampungShop() {
  const [searchParams, setSearchParams] = useSearchParams();

  const handleFilter = () => {
    // Macam tulis nota baru kat papan tanda
    setSearchParams({ category: 'minuman', price: 'mahal' });
  };

  return (
    <div>
      <h1>Kedai Kampung</h1>
      <button onClick={handleFilter}>Tukar ke Minuman Mahal</button>
    </div>
  );
}
```
When you click the button, the URL changes to ?category=minuman&price=mahal, and the page updates to show drinks that are expensive. No need to ride your motorbike to a new page!

# Programmatic Navigation (Pandu Motorbike ke Tempat Lain):
Sometimes, you don’t just want to change the signs (query params); you want to ride your motorbike to a completely different part of the village (a new page). This is called programmatic navigation, where you tell React to take the user to a new URL without them clicking a link.
In React, you use the useNavigate hook from react-router-dom to do this. Think of it like hopping on your motorbike and zooming to a new spot.
```jsx

import { useNavigate } from 'react-router-dom';

function KampungShop() {
  const navigate = useNavigate();

  const goToCheckout = () => {
    // Pandu motorbike ke halaman checkout
    navigate('/checkout?item=nasi-lemak&total=5');
  };

  return (
    <div>
      <h1>Kedai Kampung</h1>
      <button onClick={goToCheckout}>Pergi ke Checkout</button>
    </div>
  );
}
```
When the user clicks the button, they’re taken to /checkout?item=nasi-lemak&total=5. It’s like saying, “Aku nak beli nasi lemak, bawa aku ke kaunter bayar!”

# Putting It All Together (Macam Jalan-Jalan kat Kampung):
Imagine you’re building a small e-commerce app for the kampung. You want users to filter products (using query params) and go to different pages (using navigation). Here’s a full example:
```jsx

import { BrowserRouter, Routes, Route, useSearchParams, useNavigate } from 'react-router-dom';

function App() {
  return (
    <BrowserRouter>
      <Routes>
        <Route path="/products" element={<KampungShop />} />
        <Route path="/checkout" element={<Checkout />} />
      </Routes>
    </BrowserRouter>
  );
}

function KampungShop() {
  const [searchParams, setSearchParams] = useSearchParams();
  const navigate = useNavigate();

  const category = searchParams.get('category');
  const price = searchParams.get('price');

  const handleFilter = () => {
    setSearchParams({ category: 'minuman', price: 'murah' });
  };

  const goToCheckout = () => {
    navigate('/checkout?item=minuman-kopi&total=2');
  };

  return (
    <div>
      <h1>Kedai Kampung</h1>
      <p>Kategori: {category || 'tak ada'}</p>
      <p>Harga: {price || 'tak ada'}</p>
      <button onClick={handleFilter}>Tukar ke Minuman Murah</button>
      <button onClick={goToCheckout}>Pergi ke Checkout</button>
    </div>
  );
}

function Checkout() {
  const [searchParams] = useSearchParams();
  const item = searchParams.get('item');
  const total = searchParams.get('total');

  return (
    <div>
      <h1>Checkout</h1>
      <p>Item: {item || 'tak ada item'}</p>
      <p>Total: RM {total || '0'}</p>
    </div>
  );
}

export default App;
```
# How It Works in the Kampung (Ringkasan):
* **Query Params:** Macam papan tanda kat jalan, bagi tahu app apa yang user nak (e.g., filter barang). Guna useSearchParams untuk baca atau tukar tanda tu.

* **Programmatic Navigation:** Macam pandu motorbike ke tempat lain tanpa user kena tekan link. Guna useNavigate untuk bawa user ke page baru.

* Together, they make your app feel smooth, like cruising through the kampung without getting lost.

