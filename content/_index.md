---
title: Integrate API Gateway with frontend hosted in S3
weight: 1
chapter: false
---

In previous workshops, you have:

- Created Lambda functions and invoked them directly via function URLs.
- Created an REST API using API Gateway that backed by these Lambda functions; then invoke your REST API with `curl` (a web client that supports HTTPS).

In this workshop, you will:

- Integrate a frontend application (written in React) with your REST API.

  - Configure the application
  - Configure CORS for the API Gateway to allow communication from the frontend application.

- Deploy your frontend application using S3 _static website hosting_ feature.
