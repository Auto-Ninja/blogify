<h1>Request and Response</h1>

<h2>🧾 1. What Is a Request?</h2>

<p><strong>🟢 Beginner View:</strong><br>
A request is like asking a question.<br>
<strong>Example:</strong> “What’s the weather in London?”<br>
You (or your app) send this question to a service (like a weather API), and wait for an answer.</p>

<p><strong>🧠 Advanced View:</strong><br>
An API request is an HTTP message sent from a client to a server. It includes:</p>

<h3>🔧 API Request Structure</h3>

<table>
  <thead>
    <tr>
      <th>Part</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Method</td>
      <td>Action type: GET, POST, PUT, DELETE</td>
    </tr>
    <tr>
      <td>URL/Endpoint</td>
      <td>The address of the API (e.g., https://api.weather.com/london)</td>
    </tr>
    <tr>
      <td>Headers</td>
      <td>Metadata like authentication tokens, content type</td>
    </tr>
    <tr>
      <td>Body</td>
      <td>Data sent with the request (used in POST, PUT)</td>
    </tr>
    <tr>
      <td>Query Params</td>
      <td>Extra info in the URL (e.g., ?city=London&unit=celsius)</td>
    </tr>
  </tbody>
</table>

<h3>📦 Example Request (HTTP)</h3>

<pre><code class="http">
GET /weather?city=London&unit=celsius HTTP/1.1
Host: api.weather.com
Authorization: Bearer abc123
Content-Type: application/json
</code></pre>

<h2>🌐 What Is an HTTP Message?</h2>

<p>An HTTP message is like a digital letter sent between your browser (or app) and a server. There are two types:</p>
<ul>
  <li><strong>Request:</strong> Sent from your browser/app to ask for something (like a webpage or data).</li>
  <li><strong>Response:</strong> Sent back from the server with the result (like the webpage or data you asked for).</li>
</ul>

<h3>🧾 HTTP Request Breakdown</h3>

<pre><code class="http">
GET /weather?city=London HTTP/1.1
Host: api.weather.com
Content-Type: application/json
Authorization: Bearer abc123
</code></pre>

<h4>1. HTTP Verb (Method)</h4>

<table>
  <thead>
    <tr>
      <th>Verb</th>
      <th>Meaning</th>
      <th>Example Use Case</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>GET</td>
      <td>Get data</td>
      <td>View a webpage or fetch info</td>
    </tr>
    <tr>
      <td>POST</td>
      <td>Send new data</td>
      <td>Submit a form or create user</td>
    </tr>
    <tr>
      <td>PUT</td>
      <td>Update existing data</td>
      <td>Edit a profile</td>
    </tr>
    <tr>
      <td>DELETE</td>
      <td>Remove data</td>
      <td>Delete a comment</td>
    </tr>
  </tbody>
</table>

<p><strong>🧠 Beginner Tip:</strong> Think of these like actions — “Get this,” “Post this,” “Update this,” “Delete this.”</p>

<h4>2. URL + Query Parameters</h4>

<pre><code class="http">
GET /weather?city=London&unit=celsius
</code></pre>

<ul>
  <li><code>?</code> starts the query</li>
  <li><code>city=London</code> is a key-value pair</li>
  <li><code>&</code> separates multiple parameters</li>
</ul>

<p><strong>🧠 Beginner Tip:</strong> It’s like filling out a form in the URL.</p>

<h4>3. Headers</h4>

<table>
  <thead>
    <tr>
      <th>Header</th>
      <th>Purpose</th>
      <th>Example</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Content-Type</td>
      <td>Tells the format of the data</td>
      <td>application/json</td>
    </tr>
    <tr>
      <td>Authorization</td>
      <td>Sends login or API key info</td>
      <td>Bearer abc123</td>
    </tr>
    <tr>
      <td>User-Agent</td>
      <td>Identifies the app/browser</td>
      <td>Mozilla/5.0</td>
    </tr>
  </tbody>
</table>

<h4>4. Body (Optional)</h4>

<pre><code class="json">
{
  "username": "john_doe",
  "password": "123456"
}
</code></pre>

<p><strong>🧠 Beginner Tip:</strong> The body is like the contents of a form you submit.</p>

<hr/>

<h2>📩 2. What Is a Response?</h2>

<p><strong>🟢 Beginner View:</strong><br>
A response is the answer you get back.</p>

<p><strong>Example:</strong> “It’s 12°C and cloudy in London.”<br>
The API sends this back after processing your request.</p>

<p><strong>🧠 Advanced View:</strong><br>
An API response is an HTTP message from the server to the client. It includes:</p>

<table>
  <thead>
    <tr>
      <th>Part</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Status Code</td>
      <td>Tells if the request was successful (e.g., 200 OK, 404 Not Found)</td>
    </tr>
    <tr>
      <td>Headers</td>
      <td>Info about the response (e.g., content type, caching)</td>
    </tr>
    <tr>
      <td>Body</td>
      <td>The actual data (usually in JSON or XML format)</td>
    </tr>
  </tbody>
</table>

<h3>📩 HTTP Response Structure</h3>

<pre><code class="http">
HTTP/1.1 200 OK
Content-Type: application/json

{
  "city": "London",
  "temperature": "12°C",
  "condition": "Cloudy"
}
</code></pre>

<h4>1. Status Code</h4>

<table>
  <thead>
    <tr>
      <th>Code</th>
      <th>Meaning</th>
      <th>Example</th>
    </tr>
  </thead>
  <tbody>
    <tr><td>200</td><td>OK (Success)</td><td>Data returned successfully</td></tr>
    <tr><td>201</td><td>Created</td><td>New resource created</td></tr>
    <tr><td>400</td><td>Bad Request</td><td>You sent something wrong</td></tr>
    <tr><td>401</td><td>Unauthorized</td><td>You need to log in</td></tr>
    <tr><td>404</td><td>Not Found</td><td>The thing doesn’t exist</td></tr>
    <tr><td>500</td><td>Server Error</td><td>Something broke on the server</td></tr>
  </tbody>
</table>

<p><strong>🧠 Beginner Tip:</strong> If it starts with 2, it’s good. If it starts with 4 or 5, something went wrong.</p>

<h4>2. Headers (Again)</h4>

<pre><code class="http">
Content-Type: application/json
Cache-Control: no-cache
</code></pre>

<p>These tell your app how to handle the response.</p>

<h4>3. Body (The Data)</h4>

<pre><code class="json">
{
  "city": "London",
  "temperature": "12°C",
  "condition": "Cloudy"
}
</code></pre>

<h3>🔁 Request–Response Lifecycle Diagram</h3>

<pre><code class="plaintext">
+--------+       Request        +--------+       Response       +--------+
| Client | ------------------> | Server | ------------------> | Client |
+--------+                     +--------+                     +--------+
     |                             |                              |
     |  GET /weather?city=London   |                              |
     |---------------------------->|                              |
     |                             | 200 OK + JSON data           |
     |                             |<-----------------------------|
</code></pre>

<h3>