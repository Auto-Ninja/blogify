<h1>🧪 How to Test an API</h1>

<p>Testing an API involves checking whether it behaves as expected. You typically:</p>
<ul>
  <li>Send a request to an API endpoint (e.g., <code>GET /users</code>)</li>
  <li>Check the response:
    <ul>
      <li>Status code (e.g., <code>200 OK</code>)</li>
      <li>Headers (e.g., <code>Content-Type</code>)</li>
      <li>Body (e.g., JSON data)</li>
    </ul>
  </li>
  <li>Validate:
    <ul>
      <li>Correct data returned</li>
      <li>Error handling</li>
      <li>Security (e.g., unauthorized access)</li>
      <li>Performance (response time)</li>
    </ul>
  </li>
</ul>

<h2>🛠️ Common Tools for API Testing</h2>

<table>
  <thead>
    <tr>
      <th>Tool</th>
      <th>Purpose</th>
      <th>Notes</th>
    </tr>
  </thead>
  <tbody>
    <tr><td>Postman</td><td>Manual and automated API testing</td><td>Easy UI, great for beginners</td></tr>
    <tr><td>Swagger UI</td><td>Interactive API documentation</td><td>Lets you test directly from docs</td></tr>
    <tr><td>REST-assured</td><td>Automated testing in Java</td><td>Used in backend test automation</td></tr>
    <tr><td>SoapUI</td><td>Testing SOAP and REST APIs</td><td>Enterprise-grade features</td></tr>
    <tr><td>Insomnia</td><td>Lightweight API client</td><td>Similar to Postman</td></tr>
    <tr><td>cURL</td><td>Command-line API testing</td><td>Good for scripting and quick tests</td></tr>
  </tbody>
</table>

<h2>📘 What Is Swagger and Why Is It Used?</h2>

<p>Swagger is a set of tools built around the OpenAPI Specification. It helps developers:</p>
<ul>
  <li>Design APIs before coding</li>
  <li>Document APIs in a readable format</li>
  <li>Generate client SDKs automatically</li>
  <li>Test APIs interactively via Swagger UI</li>
</ul>

<p>Swagger uses a YAML or JSON file to describe the API — including endpoints, parameters, responses, and authentication.</p>

<h3>🧾 Example Swagger Snippet</h3>

<pre><code class="yaml">
paths:
  /users:
    get:
      summary: Get all users
      responses:
        '200':
          description: A list of users
</code></pre>

<p>This makes it easy for developers and testers to understand and interact with the API.</p>

<h2>📖 What Is OpenAPI Specification?</h2>

<p>The <strong>OpenAPI Specification (OAS)</strong> is a standardized format for describing RESTful APIs. It defines how APIs behave and what they offer — including:</p>
<ul>
  <li>Endpoints and HTTP methods</li>
  <li>Request parameters and body schemas</li>
  <li>Response formats and status codes</li>
  <li>Authentication mechanisms</li>
</ul>

<p>OpenAPI files are written in <strong>YAML or JSON</strong> and serve as a contract between API providers and consumers. They enable tools like Swagger UI to generate interactive documentation and support code generation for client SDKs and server stubs.</p>

<p><strong>Benefits:</strong></p>
<ul>
  <li>Improves collaboration across teams</li>
  <li>Enables automated testing and validation</li>
  <li>Supports mock servers and client generation</li>
</ul>

<h2>🔍 Swagger vs Postman — Key Differences</h2>

<table>
  <thead>
    <tr>
      <th>Feature</th>
      <th>Swagger</th>
      <th>Postman</th>
    </tr>
  </thead>
  <tbody>
    <tr><td>Purpose</td><td>API design + documentation</td><td>API testing + interaction</td></tr>
    <tr><td>Format</td><td>YAML/JSON (OpenAPI Spec)</td><td>GUI-based request builder</td></tr>
    <tr><td>Use Case</td><td>Define and share API structure</td><td>Send requests and validate responses</td></tr>
    <tr><td>Automation</td><td>Generates client/server code</td><td>Supports test scripting and automation</td></tr>
    <tr><td>Collaboration</td><td>Share API specs</td><td>Share collections and environments</td></tr>
    <tr><td>Example</td><td>Swagger UI shows <code>/users</code> endpoint and lets you test it</td><td>Postman sends <code>GET /users</code> and checks response</td></tr>
  </tbody>
</table>

<p><strong>Summary:</strong> Swagger is ideal for API creators, while Postman is great for API consumers and testers.</p>

<h2>🔍 Normal API vs RESTful API</h2>

<p><strong>Normal API:</strong><br>
A normal API (Application Programming Interface) is a general term for any interface that allows two systems to communicate. It can follow any protocol or structure — including SOAP, RPC, GraphQL, or custom formats. These APIs may use XML, binary formats, or proprietary messaging systems.</p>

<p><strong>RESTful API:</strong><br>
A RESTful API is a specific type of API that follows the principles of REST (Representational State Transfer). It uses standard HTTP methods like GET, POST, PUT, DELETE and communicates using stateless requests and structured URLs. RESTful APIs typically return data in JSON or XML format.</p>

<h3>🧠 Key Differences</h3>

<table>
  <thead>
    <tr>
      <th>Aspect</th>
      <th>Normal API</th>
      <th>RESTful API</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Protocol</td>
      <td>Can use any protocol (e.g., SOAP, RPC)</td>
      <td>Uses HTTP</td>
    </tr>
    <tr>
      <td>Structure</td>
      <td>May be custom or complex</td>
      <td>Follows REST principles (stateless, resource-based)</td>
    </tr>
    <tr>
      <td>Data Format</td>
      <td>Often XML, binary, or custom</td>
      <td>Typically JSON or XML</td>
    </tr>
    <tr>
      <td>Methods</td>
      <td>Custom or protocol-specific</td>
      <td>Standard HTTP methods (GET, POST, PUT, DELETE)</td>
    </tr>
    <tr>
      <td>Ease of Use</td>
      <td>May require special tools or libraries</td>
      <td>Easy to use with browsers and HTTP clients</td>
    </tr>
  </tbody>
</table>

<p><strong>Summary:</strong> RESTful APIs are a modern, standardized way to build web services that are easy to use, scalable, and compatible with most tools and platforms. Normal APIs may offer more flexibility but often require more setup and custom handling.</p>
