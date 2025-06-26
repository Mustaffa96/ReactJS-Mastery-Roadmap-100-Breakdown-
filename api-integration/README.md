# What’s API Integration in ReactJS? (Macam Beli Ikan di Pasar)
An API is like a pasar (market) where your React app goes to beli (fetch) data or hantar (send) data. Imagine your app is a kedai runcit (small shop), and you need fresh ikan (fish) from the pasar. The API is the middleman who brings the ikan to you or takes your duit to the supplier.

In ReactJS, managing API integrations means your app knows how to:
Talk to the API (like shouting to the ikan seller, “Oi, bagi ikan segar!”).

Wait for the response (ikan sampai or “Eh, ikan habis la”).

Show the ikan (data) nicely in your app or tell customers (users) if something went wrong.
*Here’s how it works in kampung terms:
### Making the API Call (Pergi Pasar):
You use tools like fetch or axios in React to send a request to the API. It’s like sending your adik to the pasar with a list: “Ambil ikan, sayur, and cili.”
```javascript
fetch('https://api.pasarmalaysia.com/ikan')
  .then(response => response.json())
  .then(data => console.log(data)) // Ikan sampai!
  .catch(error => console.log('Aiyyo, pasar tutup!')); // Problem la.
```
###Storing the Data (Simpan dalam Peti Ais):
Once the API sends back the ikan (data), you store it in React’s “peti ais” called state using useState. This way, your app can show the data to users anytime.
```javascript
import React, { useState, useEffect } from 'react';

function KedaiIkan() {
  const [ikan, setIkan] = useState([]); // Peti ais kosong dulu

  useEffect(() => {
    fetch('https://api.pasarmalaysia.com/ikan')
      .then(response => response.json())
      .then(data => setIkan(data)) // Simpan ikan dalam peti ais
      .catch(error => console.log('Aiyyo, tak dapat ikan!'));
  }, []); // Pergi pasar sekali je masa buka kedai

  return (
    <div>
      {ikan.map(item => <p>{item.nama}</p>)} // Tunjuk ikan kat pelanggan
    </div>
  );
}
```
###Using useEffect (Macam Set Alarm Pergi Pasar):
The useEffect hook is like setting an alarm to go to the pasar when your kedai opens or when you need fresh stock. It runs the API call at the right time so you don’t flood the pasar with requests.
###Error Handling in ReactJS (Apa Nak Buat Kalau Ikan Busuk?)
Sometimes, the pasar sends you ikan busuk, or worse, the pasar is closed (API fails). Error handling is how your app deals with these problems without panicking and scaring your pelanggan (users).
Here’s how to handle it, kampung-style:
# Catch the Problem (Check Ikan Busuk Tak):
When you make an API call, use .catch() or try/catch to spot problems like network errors or bad responses.
```javascript
async function ambilIkan() {
  try {
    const response = await fetch('https://api.pasarmalaysia.com/ikan');
    const data = await response.json();
    console.log('Ikan segar: ', data);
  } catch (error) {
    console.log('Aiyyo, ikan busuk atau pasar tutup: ', error);
  }
}
```
###Tell Users Nicely (Jangan Marah Pelanggan):
If something goes wrong, don’t just show a blank kedai. Use state to show a friendly message like, “Maaf la, ikan habis. Cubalah esok.”
```javascript
import React, { useState, useEffect } from 'react';

function KedaiIkan() {
  const [ikan, setIkan] = useState([]);
  const [error, setError] = useState(null); // Simpan masalah kalau ada
  const [loading, setLoading] = useState(true); // Tunjuk kedai tengah prepare

  useEffect(() => {
    async function ambilIkan() {
      try {
        setLoading(true); // Pergi pasar dulu
        const response = await fetch('https://api.pasarmalaysia.com/ikan');
        const data = await response.json();
        setIkan(data); // Simpan ikan
        setError(null); // Tiada masalah
      } catch (err) {
        setError('Aiyyo, tak dapat ikan hari ni. Pasar tutup!'); // Beritahu masalah
      } finally {
        setLoading(false); // Selesai pergi pasar
      }
    }
    ambilIkan();
  }, []);

  if (loading) return <p>Tunggu sekejap, tengah ambil ikan...</p>;
  if (error) return <p>{error}</p>; // Tunjuk mesej kalau ikan busuk
  return (
    <div>
      {ikan.map(item => <p>{item.nama}</p>)} // Tunjuk ikan segar
    </div>
  );
}
```
###Loading State (Tunjuk Kedai Tengah Siap):
While waiting for the API (ikan to arrive), show a “loading” message or spinner. It’s like telling pelanggan, “Sabar ya, ikan tengah sampai.”
Use a loading state to control this (see code above).
###Retry or Fallback (Cari Pasar Lain):
If the API fails, you can let users retry (like going to another pasar) or use backup data (ikan kering from your stor).
```javascript
function KedaiIkan() {
  const [ikan, setIkan] = useState([]);
  const [error, setError] = useState(null);
  const [loading, setLoading] = useState(true);

  const ambilIkan = async () => {
    try {
      setLoading(true);
      const response = await fetch('https://api.pasarmalaysia.com/ikan');
      const data = await response.json();
      setIkan(data);
      setError(null);
    } catch (err) {
      setError('Pasar tutup! Nak cuba lagi?');
    } finally {
      setLoading(false);
    }
  };

  useEffect(() => {
    ambilIkan();
  }, []);

  return (
    <div>
      {loading && <p>Tunggu sekejap, tengah ambil ikan...</p>}
      {error && (
        <div>
          <p>{error}</p>
          <button onClick={ambilIkan}>Cuba lagi</button> // Retry button
        </div>
      )}
      {!loading && !error && ikan.map(item => <p>{item.nama}</p>)}
    </div>
  );
}
```
###Tips for Smooth API Integration (Macam Jadi Penjual Ikan Pro)
**Use a Library like Axios:** It’s like hiring a fast runner to go to the pasar for you. Axios makes API calls easier and handles errors better than plain fetch.

**Centralize API Calls: Instead of sending adik to the pasar from every pa**ge, create a “pasar helper” (a separate file) to manage all API calls.
```javascript
// api/pasar.js
import axios from 'axios';

export const ambilIkan = async () => {
  const response = await axios.get('https://api.pasarmalaysia.com/ikan');
  return response.data;
};

 Then use it in your component:
javascript
import { ambilIkan } from './api/pasar';

useEffect(() => {
  ambilIkan()
    .then(data => setIkan(data))
    .catch(err => setError('Pasar tutup!'));
}, []);
```
###Handle Rate Limits: Some APIs are like strict pasar aunties who say, “Jangan datang banyak kali!” Check the API’s rate limits and use caching (like keeping extra ikan in the peti ais) to avoid overloading it.

Test Your Error Handling: Try “closing the pasar” (turn off your internet or use a fake API) to make sure your app doesn’t crash when things go wrong.
###Summary (Macam Nota di Papan Kedai)
**API Integration:** Your React app talks to the pasar (API) to get or send data. Use fetch or axios, store data in useState, and control when to fetch with useEffect.

**Error Handling:** Plan for ikan busuk or pasar tutup. Use try/catch, show friendly error messages, add a loading state, and maybe a retry button.

**Pro Tips:** Use libraries like Axios, centralize API calls, and test for failures to make your kedai run smoothly.
