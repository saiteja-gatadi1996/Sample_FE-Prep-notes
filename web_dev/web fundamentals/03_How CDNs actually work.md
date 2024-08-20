### What is a CDN?

- CDN stands for **_Content Delivery Network._**
- It is a distributed network of servers located in various data centers around the world.
- The **_primary purpose of a CDN_** is **_to efficiently deliver content_**, such as web pages, images and videos and other files <u>**_to users based on their geographical location_**</u>.
- When you access a website or an online service, your request is typically directed to the origin server where the website's data is stored.
- However, when a website uses a CDN, the content is distributed across multiple edge servers located closer to the end-users.
- These edge servers acts as caches for the website's content.

<img src="https://miro.medium.com/v2/resize:fit:1100/format:webp/1*Qa-S69TlpJWMpFN0_3MwpQ.png">

**_1. Content replication:_**

- The **_CDN provider copies the website's static files_**(images, CSS and JS) and sometimes dynamic content (e.g API responses) **_to multiple edge servers across different geographic locations_**.

**_2. Geographic proximity:_**:

- When a user requests content from a website using a CDN, the **_request is routed to the nearest edge server based on the user's location_**.
- This reduces latency and improves the website's loading speed.

**_3. Load Distribution_**:

- **_Since the content is distributed across several servers_**, _<u>the load is distributed among them, reducing the burden on the origin server</u>_ and preventing it from becoming overwhelmed during traffic spikes or DDos attacks

**_4. Caching_**:

- The **_edge servers cache the content they deliver_** to users.
- If a **_users requests the same content later_** or **_if other users in the same location request the same content_**, the _CDN can serve it directly from the nearest edge server_, reducing the need to fetch it from the origin server repeatedly.

---

In summary, a CDN is a ***network infrastructure designed to accelerate and optimize content delivery***, resulting in a better user experience and improved performance for websites and online services.
