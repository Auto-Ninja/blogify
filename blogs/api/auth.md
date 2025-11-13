<h1>🔐 Authentication & Authorization in APIs</h1>

<h2>🧠 What They Mean</h2>

<table>
  <thead>
    <tr>
      <th>Term</th>
      <th>Purpose</th>
      <th>Example</th>
    </tr>
  </thead>
  <tbody>
    <tr><td>Authentication</td><td>Verifies who you are</td><td>Logging in with username/password</td></tr>
    <tr><td>Authorization</td><td>Verifies what you’re allowed to do</td><td>Accessing admin-only data</td></tr>
  </tbody>
</table>

<p>They are essential for protecting APIs from unauthorized access and misuse.</p>

<h2>🎯 Why, When, and How They’re Used</h2>

<ul>
  <li><strong>Why:</strong> To protect sensitive data and ensure only trusted users or systems can access or modify it.</li>
  <li><strong>When:</strong> Every time an API handles private, secure, or user-specific data (e.g., banking, healthcare, cloud services).</li>
  <li><strong>How:</strong> By requiring credentials (like tokens or keys) and checking permissions before processing requests.</li>
</ul>

<h2>🔑 Key Differences</h2>

<table>
  <thead>
    <tr>
      <th>Feature</th>
      <th>Authentication</th>
      <th>Authorization</th>
    </tr>
  </thead>
  <tbody>
    <tr><td>Purpose</td><td>Who are you?</td><td>What can you do?</td></tr>
    <tr><td>Comes First</td><td>✅ Yes</td><td>❌ Only after authentication</td></tr>
    <tr><td>Example</td><td>Login with token</td><td>Access only your own data</td></tr>
    <tr><td>Data Used</td><td>Username/password, token</td><td>Roles, permissions, scopes</td></tr>
  </tbody>
</table>

<h2>🛠️ Common Types of API Authentication & Authorization</h2>

<table>
  <thead>
    <tr>
      <th>Method</th>
      <th>Description</th>
      <th>How to Identify in Request</th>
    </tr>
  </thead>
  <tbody>
    <tr><td>API Key</td><td>A unique key passed in headers or URL</td><td>Authorization: ApiKey abc123 or ?apikey=abc123</td></tr>
    <tr><td>Basic Auth</td><td>Username and password encoded in Base64</td><td>Authorization: Basic dXNlcjpwYXNz</td></tr>
    <tr><td>Bearer Token (OAuth 2.0 / JWT)</td><td>Token issued after login</td><td>Authorization: Bearer eyJhbGci...</td></tr>
    <tr><td>Windows Authentication</td><td>Uses Windows login credentials</td><td>Integrated with Active Directory</td></tr>
    <tr><td>OAuth 2.0</td><td>Delegated access via third-party login (e.g., Google, Azure)</td><td>Authorization: Bearer &lt;access_token&gt;</td></tr>
  </tbody>
</table>

<h2>🔍 How to Identify Auth in a Request</h2>

<p>Look at the Authorization header or query parameters:</p>

<h3>🔸 Example 1: API Key in Header</h3>

<pre><code class="http">
GET /users HTTP/1.1  
Authorization: ApiKey abc123
</code></pre>

<h3>🔸 Example 2: Bearer Token (OAuth or JWT)</h3>

<pre><code class="http">
GET /profile HTTP/1.1  
Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...
</code></pre>

<h3>🔸 Example 3: Basic Auth</h3>

<pre><code class="http">
GET /admin HTTP/1.1  
Authorization: Basic dXNlcm5hbWU6cGFzc3dvcmQ=
</code></pre>

<h2>🔐 Authentication Methods Explained</h2>

<h3>1. 🧾 Basic Authentication</h3>

<p>Sends username and password in every request (Base64 encoded).<br>
Simple but insecure unless used over HTTPS.</p>

<pre><code class="http">
Authorization: Basic dXNlcm5hbWU6cGFzc3dvcmQ=
</code></pre>

<p><strong>Use Case:</strong> Internal tools, quick testing.</p>

<h3>2. 🪟 Windows Authentication (Active Directory)</h3>

<p>Uses Windows login credentials.<br>
Common in enterprise environments.<br>
Integrated with Active Directory.</p>

<p><strong>Example:</strong> Automatically authenticates user logged into a Windows domain.</p>
<p><strong>Use Case:</strong> Internal enterprise apps, intranet systems.</p>

<h3>3. 🔑 OAuth 2.0 (Used by Azure & Google)</h3>

<p>Token-based authentication.<br>
Users log in via a trusted provider (Google, Microsoft).<br>
App receives an access token to call APIs.</p>

<pre><code class="http">
Authorization: Bearer ya29.a0AfH6SM...
</code></pre>

<p><strong>Use Case:</strong> Public APIs, mobile/web apps, secure delegated access.</p>

<h2>🏢 What Is Active Directory?</h2>

<p>Active Directory (AD) is Microsoft’s on-premises identity management system.</p>

<h3>🔹 Features</h3>
<ul>
  <li>Centralized user and device management</li>
  <li>Uses LDAP and Kerberos</li>
  <li>Supports Group Policy for device control</li>
</ul>

<h3>🔹 Use Cases</h3>
<ul>
  <li>Corporate networks</li>
  <li>Windows domain-joined devices</li>
  <li>Internal authentication and access control</li>
</ul>

<h2>☁️ What Is Azure Active Directory?</h2>

<p>Azure Active Directory (Azure AD) is Microsoft’s cloud-based identity and access management service.</p>

<h3>🔹 Features</h3>
<ul>
  <li>Cloud-based authentication</li>
  <li>Supports OAuth 2.0, OpenID Connect, SAML</li>
  <li>Enables Single Sign-On (SSO) and Multi-Factor Authentication (MFA)</li>
  <li>Integrates with Microsoft 365, Azure, and third-party apps</li>
</ul>

<h3>🔹 Use Cases</h3>
<ul>
  <li>Remote work and cloud apps</li>
  <li>Hybrid identity management</li>
  <li>Secure access to SaaS platforms</li>
</ul>

<h2>🔁 AD vs Azure AD — Comparison</h2>

<table>
  <thead>
    <tr>
      <th>Feature</th>
      <th>Active Directory (AD)</th>
      <th>Azure Active Directory (Azure AD)</th>
    </tr>
  </thead>
  <tbody>
    <tr><td>Location</td><td>On-premises</td><td>Cloud-based</td></tr>
    <tr><td>Protocol</td><td>LDAP, Kerberos</td><td>OAuth 2.0, OpenID Connect, SAML</td></tr>
    <tr><td>Device Management</td><td>Windows domain-joined devices</td><td>Cloud and mobile devices</td></tr>
    <tr><td>SSO Support</td><td>Limited</td><td>Extensive</td></tr>
    <tr><td>Integration</td><td>Local network only</td><td>Cloud and hybrid apps</td></tr>
    <tr><td>Use Case</td><td>Internal corporate network</td><td>Cloud apps, remote work</td></tr>
  </tbody>
</table>

<h2>🔧 How They Work Together</h2>

<p>Many organizations use both:</p>
<ul>
  <li><strong>AD</strong> for local infrastructure</li>
  <li><strong>Azure AD</strong> for cloud services</li>
</ul>

<p>They connect them using <strong>Azure AD Connect</strong>, which syncs users and credentials between the two systems.</p>
