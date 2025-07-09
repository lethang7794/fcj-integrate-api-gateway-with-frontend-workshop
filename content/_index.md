---
title: Integrate API Gateway with frontend hosted in S3
weight: 1
chapter: false
---

# Integrate API Gateway with frontend hosted in S3

In previous workshop, you use API Gateway to create an REST API that backed by Lambda functions.

In this workshop, you will:

- Integrate a frontend application with your REST API, which means:

  - Configuring the frontend application to connect to your REST API.
  - Configuring CORS for the API Gateway to allow communication from the frontend application.

- Deploy your frontend application using S3 _static website hosting_ feature.

The final architecture looks like this

![alt text](/images/diagrams/workshop-3--api-gateway--rest-api--event.drawio.png)

<!-- TODO: add diagram -->
