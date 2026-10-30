# Serverless URL Shortener 🚀

**Author:** Saksham Bhor

## 📝 Project Overview
This project is a highly scalable, fully serverless URL shortener developed as a Third-Year (TE) Cloud Computing mini-project. It demonstrates the practical implementation of Function-as-a-Service (FaaS) and managed NoSQL cloud databases to eliminate manual server provisioning and infrastructure maintenance. 

The application accepts a long web address via a RESTful API and instantly generates a unique 6-character short link that redirects users to the original destination.

## 🏗️ Architecture & Tech Stack
This project follows an event-driven microservices architecture:
* **Frontend:** HTML, CSS, and Vanilla JavaScript (Hosted on Netlify)
* **API Routing:** Amazon API Gateway (REST API with CORS enabled)
* **Compute Engine:** AWS Lambda (Node.js 24.x runtime, AWS SDK v3)
* **Database:** Amazon DynamoDB (Managed NoSQL key-value store)

## ✨ Key Features
* **Zero Infrastructure Overhead:** Operates entirely without traditional monolithic web servers.
* **On-Demand Compute:** Backend logic executes strictly in response to incoming HTTP request events.
* **Instant Redirection:** Utilizes HTTP 301/302 redirect status codes directly from the cloud backend.
* **Cross-Origin Resource Sharing (CORS):** Fully configured to allow secure API calls from external frontend domains.

## ⚙️ How It Works
1. **Shortening (POST):** The user enters a URL on the frontend. The API Gateway proxies this payload to AWS Lambda. Lambda uses the `crypto` library to generate a random 6-character hex string and stores the mapping in DynamoDB.
2. **Redirection (GET):** When a user navigates to the generated short link, API Gateway captures the `shortId` parameter. Lambda queries DynamoDB for the original URL and returns a 301 Redirect response to the browser.
