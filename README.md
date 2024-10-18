# Deployement-of-Serverless-Web-Application-on-AWS
This project proviTo deploying a serverless web application using various AWS services, including S3, API Gateway, Lambda, DynamoDB, and CloudFront. The application consists of a static frontend hosted on S3, with a dynamic backend powered by Lambda and API Gateway to handle user requests and perform CRUD operations on a DynamoDB table.

Here’s a more detailed **Documentation** that you can include in your GitHub repository to describe the project in depth. This will help other developers understand the project, set it up, and potentially contribute.

---

# Serverless Web Application on AWS Documentation

## Table of Contents
1. [Introduction](#introduction)
2. [Architecture Overview](#architecture-overview)
3. [Technologies Used](#technologies-used)
4. [Setup Instructions](#setup-instructions)
   - [Frontend Setup](#frontend-setup)
   - [Backend (Lambda & API Gateway) Setup](#backend-lambda--api-gateway-setup)
   - [Database (DynamoDB) Setup](#database-dynamodb-setup)
   - [CloudFront Setup](#cloudfront-setup)
5. [Running the Application](#running-the-application)
6. [Project Structure](#project-structure)
7. [How It Works](#how-it-works)
8. [Contributing](#contributing)
9. [License](#license)

---

## Introduction

This project demonstrates how to deploy a **serverless web application** on AWS using services such as **S3**, **API Gateway**, **Lambda**, **DynamoDB**, and **CloudFront**. The application allows users to interact with a fully serverless backend, storing data in a NoSQL database and delivering content efficiently with CloudFront and HTTPS security.

By following this documentation, you will learn how to set up each component and deploy the project successfully on AWS.

---

## Architecture Overview

The serverless architecture of this web application is designed as follows:

- **S3**: Hosts the static web content (HTML, CSS, JS).
- **API Gateway**: Manages RESTful API requests, routing them to the appropriate backend services.
- **AWS Lambda**: Provides the serverless compute layer to process the API requests (written in Python).
- **DynamoDB**: Serves as the NoSQL database for storing and retrieving data.
- **CloudFront**: Acts as the CDN (Content Delivery Network) to serve the static web content securely over HTTPS.

---

## Technologies Used

- **Amazon S3**: For static website hosting.
- **Amazon API Gateway**: To create and manage RESTful APIs.
- **AWS Lambda**: For backend serverless computing.
- **Amazon DynamoDB**: As the NoSQL database for storing application data.
- **Amazon CloudFront**: To serve static content with HTTPS security.
- **AWS Certificate Manager (ACM)**: For managing SSL certificates (optional for HTTPS).
- **HTML5, CSS3, JavaScript**: Frontend web technologies.
- **Python**: Backend Lambda functions.

---

## Setup Instructions

### Frontend Setup

1. **Create an S3 Bucket**:
   - Go to the **S3 Management Console**.
   - Create a new bucket and name it (e.g., `my-portfolio-bucket`).
   - Enable **static website hosting** in the bucket's settings.

2. **Upload Static Website Files**:
   - Navigate to the `/frontend` folder.
   - Upload all HTML, CSS, and JS files to your S3 bucket.
   - Ensure that the files are publicly accessible by updating the bucket policy to allow public read access.

3. **Test the Static Website**:
   - Open the bucket URL in your browser (e.g., `http://my-portfolio-bucket.s3-website-us-west-2.amazonaws.com`).

---

### Backend (Lambda & API Gateway) Setup

1. **Set up AWS Lambda**:
   - Go to the **Lambda Management Console**.
   - Create two Lambda functions:
     - One for handling **GET requests** (fetching data from DynamoDB).
     - Another for handling **POST requests** (inserting data into DynamoDB).
   - Upload the Python scripts from the `/lambda` folder to the respective Lambda functions.
   - Add the necessary IAM permissions to the Lambda functions to access DynamoDB.

2. **Configure API Gateway**:
   - Go to the **API Gateway Management Console**.
   - Create a new **REST API** and define the resources:
     - **GET** method: Connect it to the corresponding Lambda function for fetching data.
     - **POST** method: Connect it to the Lambda function for adding data.
   - Deploy the API and note the **Invoke URL**.

---

### Database (DynamoDB) Setup

1. **Create DynamoDB Table**:
   - Go to the **DynamoDB Management Console**.
   - Create a table (e.g., `my-data-table`) with a primary key (e.g., `itemId`).
   - Define the necessary attributes to store data for your application.
   
2. **Connect Lambda to DynamoDB**:
   - Ensure the Lambda functions have permission to perform `get`, `put`, and `delete` operations on DynamoDB.

---

### CloudFront Setup

1. **Create a CloudFront Distribution**:
   - Go to the **CloudFront Management Console**.
   - Create a distribution with the **S3 bucket** as the origin.
   - Enable **HTTPS** by associating an SSL certificate from **AWS Certificate Manager (ACM)** (optional but recommended for production).

2. **Serve Content via CloudFront**:
   - Use the CloudFront URL to access the static website securely over HTTPS.
   - CloudFront will act as a CDN, caching your website’s content for faster access globally.

---

## Running the Application

1. **Access the Website**:
   - Open your browser and access the website via the CloudFront URL (e.g., `https://d1xxxxxxxxxxxx.cloudfront.net`).
   - The static content is served from S3, and API requests are handled via Lambda and DynamoDB.

2. **Test API Endpoints**:
   - Use the web interface to make GET and POST requests to the API Gateway endpoints.
   - The Lambda functions will process the requests, performing CRUD operations on DynamoDB.

---

## Project Structure

- **/frontend**: Contains the static website files (HTML, CSS, JavaScript).
- **/lambda**: Python Lambda functions to handle API Gateway requests.
- **/api-gateway**: API Gateway configurations for GET and POST requests.
- **/dynamodb**: Contains the schema setup and configuration details for the DynamoDB table.

---

## How It Works

1. **User Interaction**: Users interact with the frontend hosted on S3 and served through CloudFront.
2. **API Gateway Requests**: User actions trigger API Gateway to send requests to AWS Lambda.
3. **Lambda Processing**: The Lambda functions process the request (GET/POST) and interact with DynamoDB.
4. **DynamoDB**: DynamoDB stores and retrieves the data required by the web application.
5. **CloudFront**: Provides a secure, fast content delivery network (CDN) for serving static content.

---




