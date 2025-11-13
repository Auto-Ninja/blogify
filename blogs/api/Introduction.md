# Application programming interface

## 🧠 What Is an API?
An API is like a messenger between two software systems. It lets one app ask another for information or services — without needing to know how the other app works inside.

## 🍽️ Real-Life Analogy: Restaurant
```Flow
+------------+       Request       +------------+       Response      +------------+
|   You      | ------------------> |   Waiter   | ------------------> |   Kitchen  |
| (App/User) |                     |   (API)    |                     | (Service)  |
+------------+                     +------------+                     +------------+
```
- You ask the waiter for food → like an app asking for data.
- The waiter takes your order to the kitchen → like the API sending a request.
- The kitchen prepares the food → like the server processing the request.
- The waiter brings it back → like the API returning the result.

## ⚙️ How Does an API Work?

Here’s a simple sequence diagram:

```text
User --> API: "Get weather for London"
API --> Server: "Request weather data"
Server --> API: "12°C, Cloudy"
API --> User: "Here’s the weather info"
```

- You (or your app) ask for something.
- The API sends that request to the server.
- The server processes it and sends back the result.
- The API delivers it to you.

## 🧩 Main Components of an API

| Component       | Description                                                       |
|-----------------|-------------------------------------------------------------------|
| Endpoint        | The address where the API lives (like a phone number)             |
| Request         | What you ask for (e.g., “Get weather for London”)                 |
| Response        | What you get back (e.g., “12°C, Cloudy”)                          |
| Authentication  | Security check (e.g., API key or login token)                     |
| Documentation   | Instructions for how to use the API                               |

## 🎯 Why Use APIs?

Here’s a flowchart of why and when APIs are helpful:
```text
[Need Data or Functionality]
        |
        v
[Use API to Request It]
        |
        v
[API Talks to Server]
        |
        v
[Server Sends Back Info]
        |
        v
[App Uses the Info]
```

## ✅ Use an API when:
- You want to connect to another service (e.g., Google Maps, PayPal, Twitter).
- You need data from another system (e.g., weather, stock prices, flight info).
- You’re building modular apps (e.g., microservices).
- You want to automate tasks (e.g., sending emails, uploading files).
- You need to reuse existing functionality without rebuilding it.

## 🌐 Webpage vs API — What’s the Difference?

| Feature        | Webpage/WebUI                     | API                                                  |
|----------------|-----------------------------------|------------------------------------------------------|
| Who uses it    | Humans (you, me)                  | Computers or apps                                   |
| How it looks   | Visual — buttons, text, images    | Invisible — just data                               |
| Purpose        | Show info and let you interact    | Share info between systems                          |
| Example        | A login page                      | A login system that checks your password behind the scenes |


## 🔍 Summary:
- A webpage is for people to see and interact with.
- An API is for apps to talk to each other behind the scenes.

## 🧪 Real-World Examples
- Uber uses APIs to get maps, calculate fares, and send notifications.
- Instagram uses APIs to upload photos, fetch comments, and show likes.
- Banking apps use APIs to check balances, transfer money, and pay bills.