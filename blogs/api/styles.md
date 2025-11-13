<h1>🌐 What Is an API Style?</h1>

<p>An API style defines how systems communicate — the rules, format, and structure of requests and responses. Different styles suit different needs, from strict enterprise systems to flexible mobile apps.</p>

<h2>🧩 Overview of API Styles</h2>

<table>
  <thead>
    <tr>
      <th>API Style</th>
      <th>Stands For</th>
      <th>Key Trait</th>
      <th>Common Use Case</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>REST</td>
      <td>Representational State Transfer</td>
      <td>Resource-based, flexible</td>
      <td>Web/mobile apps, microservices</td>
    </tr>
    <tr>
      <td>SOAP</td>
      <td>Simple Object Access Protocol</td>
      <td>XML-based, strict rules</td>
      <td>Enterprise, banking</td>
    </tr>
    <tr>
      <td>RPC</td>
      <td>Remote Procedure Call</td>
      <td>Function-style, lightweight</td>
      <td>Internal services, gRPC</td>
    </tr>
    <tr>
      <td>GraphQL</td>
      <td>Graph Query Language</td>
      <td>Client-driven, efficient</td>
      <td>Modern apps, real-time data</td>
    </tr>
  </tbody>
</table>

<h2>🧠 REST (Representational State Transfer)</h2>

<p><strong>🔹 What It Is:</strong><br>
REST is the most popular API style. It treats everything as a resource (like users, products, orders) and uses standard HTTP methods.</p>

<h3>🔧 Example REST Endpoints</h3>

<pre><code class="http">
GET /users           → Get all users
POST /users          → Create a new user
GET /users/123       → Get user with ID 123
PUT /users/123       → Update user 123
DELETE /users/123    → Delete user 123
</code></pre>

<p><strong>✅ Best For:</strong></p>
<ul>
  <li>Web and mobile apps</li>
  <li>Microservices</li>
  <li>Public APIs (e.g., Twitter, GitHub)</li>
</ul>

<h2>🧼 SOAP (Simple Object Access Protocol)</h2>

<p><strong>🔹 What It Is:</strong><br>
SOAP is a protocol that uses XML for messaging. It’s strict, standardized, and supports advanced features like security and transactions.</p>

<h3>🔧 Example SOAP Request</h3>


```xml
<soap:Envelope>
  <soap:Body>
    <GetUser>
      <UserId>123</UserId>
    </GetUser>
  </soap:Body>
</soap:Envelope>
```

<p><strong>✅ Best For:</strong></p>
<ul>
  <li>Enterprise systems</li>
  <li>Banking and finance</li>
  <li>When formal contracts and security are critical</li>
</ul>

<h2>🔁 RPC (Remote Procedure Call)</h2>

<p><strong>🔹 What It Is:</strong><br>
RPC lets you call functions on a remote server as if they were local. It’s simple and fast, often used internally.</p>

<h3>🔧 Example RPC Call</h3>

```json
{
  "method": "getUser",
  "params": [123]
}
```

<p><strong>✅ Best For:</strong></p>
<ul>
  <li>Microservices</li>
  <li>Internal APIs</li>
  <li>Lightweight communication</li>
</ul>

<h2>🔍 GraphQL (Graph Query Language)</h2>

<p><strong>🔹 What It Is:</strong><br>
GraphQL lets clients ask for exactly the data they need. It uses a single endpoint and supports nested queries.</p>

<h3>🔧 Example GraphQL Query</h3>

```graphql
{
  user(id: 123) {
    name
    email
    orders {
      id
      total
    }
  }
}
```

<p><strong>✅ Best For:</strong></p>
<ul>
  <li>Mobile and web apps</li>
  <li>Complex data models</li>
  <li>Real-time data needs</li>
</ul>

<h2>📊 Comparison Table</h2>

<table>
  <thead>
    <tr>
      <th>Feature</th>
      <th>REST</th>
      <th>SOAP</th>
      <th>RPC</th>
      <th>GraphQL</th>
    </tr>
  </thead>
  <tbody>
    <tr><td>Format</td><td>JSON, XML</td><td>XML</td><td>JSON/XML/Binary</td><td>GraphQL syntax</td></tr>
    <tr><td>Flexibility</td><td>Medium</td><td>Low</td><td>Medium</td><td>High</td></tr>
    <tr><td>Speed</td><td>Fast</td><td>Slower</td><td>Fast</td><td>Fast</td></tr>
    <tr><td>Security</td><td>Custom</td><td>Built-in</td><td>Custom</td><td>Custom</td></tr>
    <tr><td>Tooling</td><td>Postman, Swagger</td><td>SOAP UI, WSDL</td><td>gRPC, JSON-RPC</td><td>Apollo, GraphQL Playground</td></tr>
    <tr><td>Endpoint Style</td><td>Multiple URLs</td><td>Single WSDL file</td><td>Function calls</td><td>Single endpoint</td></tr>
  </tbody>
</table>
