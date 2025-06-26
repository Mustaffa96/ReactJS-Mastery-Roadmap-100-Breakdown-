# What’s ReactJS?
Imagine you’re building a house in the kampung, but instead of hammering every piece of wood from scratch each time, you’ve got ready-made blocks (like LEGO pieces) for walls, doors, and windows. ReactJS is like that—it’s a JavaScript library that lets you build websites using reusable “blocks” called components. Each component is a piece of your webpage, like a button, a menu, or a photo gallery. You put these components together to create a slick, interactive website that feels alive when people click around.

For example, you make a “profile card” component for one villager’s info (name, photo, etc.). Want to show 10 villagers? Just reuse that component 10 times with different info. Easy, right?

# What’s Next.js?
Now, ReactJS is great for building the house, but it’s like building it in your backyard and then moving it to the kampung square for everyone to see. Sometimes, that moving part can be tricky—especially if you want the house to look good and load fast for visitors (like Google or your kampung folks). That’s where Next.js comes in.

Next.js is like a super-smart contractor who helps you build your ReactJS house in a way that’s optimized for speed, search engines, and user experience. It’s a framework built on top of ReactJS that adds extra powers, like server-side rendering (SSR) and static site generation (SSG), to make your website faster and easier to find on Google.
# What’s Server-Side Rendering (SSR)?
Let’s say you’re hosting a big kenduri (feast) in the kampung. When guests arrive, you want the food ready on the table, not still cooking in the kitchen, right? In the web world, SSR is like preparing the whole webpage on the server (the kitchen) before sending it to the visitor’s browser (the guest).

Normally, with plain ReactJS, the browser gets a mostly empty page and then “cooks” the content (like menus, images, etc.) using JavaScript. This can take a few seconds, especially if the internet is slow (like a bad day in the kampung with spotty Wi-Fi). With SSR in Next.js:
* The server does the hard work of building the full webpage (HTML, CSS, etc.).

* It sends the ready-made page to the browser, so the visitor sees it instantly.

* After that, ReactJS takes over to make the page interactive (like letting guests rearrange their plates).

**Why use SSR?**
* It’s faster for the first view, so your kampung folks don’t wait around.

* Search engines like Google love it because they can “read” the fully cooked page easily, making your site rank better.

* Great for pages with dynamic content, like a village newsfeed that changes often.

# Example in Next.js:
You create a page in Next.js using a special function called getServerSideProps. This tells the server, “Oi, before you send this page to the browser, go grab the latest village news from the database and bake it into the page.” So when someone visits, they see the fresh news right away.
# What’s Static Site Generation (SSG)?
Now, imagine you’re selling kuih at the pasar (market). Instead of baking fresh kuih for every customer (which takes time), you bake a big batch in the morning and display them ready-to-go. Customers grab what they want instantly, and you don’t need to fire up the oven every time.

SSG in Next.js is like that. It “bakes” your webpages into static HTML files when you build the site (not when someone visits). These files are super fast to load because they’re already done—no cooking needed when a visitor shows up.
**How it works:**
  * At build time (when you “bake” your site), Next.js creates HTML files for your pages using a function like getStaticProps.

  * These files are saved and served to visitors as-is, making the site lightning-fast.

  * If your content changes (like adding new kuih flavors), you rebuild the site to update the files.

**Why use SSG?**
* Crazy fast because the pages are pre-made.

* Cheap to host since you’re just serving static files (no heavy server work).

* Perfect for content that doesn’t change often, like a kampung event schedule or a shop’s product list.

* **Google loves it too, because the pages are ready for indexing.

**Example in Next.js:**
You make a page for the kampung’s annual festival. Using getStaticProps, you pull the festival details (date, activities, etc.) from a file or database during the build. Next.js creates a static HTML page, and when someone visits, they see it instantly—no waiting for the server to cook.
* **SSR vs. SSG: Which One to Pick?**
It’s like choosing between cooking nasi lemak on the spot (SSR) or preparing it earlier in the morning (SSG):
* **Use SSR** if your content changes a lot, like a live chat board for kampung gossip or real-time weather updates. The server cooks fresh each time someone visits.

* **Use SSG** if your content is mostly fixed, like a village history page or a menu for your warung. You bake it once, and everyone gets the same fast-loading page.

Next.js also has a cool trick called Incremental Static Regeneration (ISR). It’s like baking a batch of kuih but refreshing a few pieces every hour to keep them fresh without redoing the whole batch. You can set SSG pages to update automatically after a set time (e.g., every 10 minutes) without rebuilding the whole site.
# How to Learn SSR and SSG with Next.js
Here’s how you can start learning this in the kampung way—step by step, no rush:
* **Learn ReactJS Basics First:**
  * Understand components, props, and state. It’s like learning to arrange your kain batik before sewing a baju.

  * Try free tutorials on YouTube or the official ReactJS docs (react.dev).

* **Set Up Next.js:**
  * Install Node.js on your computer (like setting up your kitchen).

  * Run npx create-next-app@latest to create a new Next.js project. It’s like getting a blueprint for your house.

  * Follow the Next.js official tutorial (nextjs.org) to build a simple site.

* **Play with SSG:**
  * Create a page (e.g., pages/festival.js) and add getStaticProps to fetch data, like festival details.

  * Run npm run build and npm run start to see your static site in action.

* **Try SSR:**
  * Make another page (e.g., pages/news.js) and use getServerSideProps to fetch live data, like recent kampung announcements.

  * Test it locally to see how the server “cooks” the page on each visit.

* **Experiment with ISR:**
  * In your SSG page, add a revalidate option in getStaticProps to refresh the page every few minutes.

  * It’s like telling your kuih stall to update the display every hour.

* **Practice with Real Projects:**
  * Build a simple kampung website (e.g., a directory of local shops or a blog about village life).

  * Deploy it for free on Vercel (the company behind Next.js) to show it off to your friends.

* **Learn from Examples:**
  * Check out Next.js’s official examples on GitHub (github.com/vercel/next.js/tree/canary/examples).

  * Watch kampung-style YouTube tutorials (search for “Next.js SSR tutorial” or “Next.js SSG tutorial” in simple terms).

# Why Bother with SSR and SSG?
In the kampung, you want your warung to be famous, right? SSR and SSG make your website:
* **Fast:** Like serving teh tarik in seconds, not minutes.

* **SEO-friendly:** Google finds your site easily, so more people visit.

* **Scalable:** Handle lots of visitors without crashing, like a big kenduri.

* **Cost-effective:** SSG sites can run on cheap hosting since they’re just files.

### Kampung Analogy Recap
* **ReactJS:** Your toolbox of reusable blocks to build a cool, interactive house.

* **Next.js:** The smart contractor who makes your house fast and search-engine-friendly.

* **SSR:** Cooking the webpage fresh on the server for each visitor, great for dynamic stuff like village news.

* **SSG:** Baking webpages in advance for super speed, perfect for fixed content like event schedules.

So, grab your laptop, pretend it’s a kampung workshop, and start building with Next.js. Before you know it, you’ll be serving websites as fast as you serve kuih at the pasar!

