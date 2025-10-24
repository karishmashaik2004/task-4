# Task 4 — Serverless Function Deployment (AWS Lambda)

## Overview
This project demonstrates the creation and deployment of a **serverless function** using **AWS Lambda** and **API Gateway**.  
The function is triggered via an **HTTP request** and returns a dynamic greeting message, illustrating the principles of **serverless computing** and **Function-as-a-Service (FaaS)**.

---

## Features
- Serverless function that runs without managing servers
- HTTP endpoint via **API Gateway**
- Dynamic greeting using query parameters (e.g., `?name=Karishma`)
- Safe handling of missing or empty parameters
- Easy to deploy and test

---

## Function Behavior
- **Endpoint:** `https://<your-api-id>.execute-api.<region>.amazonaws.com/default/helloWorld`
- **Query Parameter:** `name`
- **Responses:**
  - Without query string:  
    ```
    Hello, Guest! Welcome to AWS Lambda.
    ```
  - With query string:  
    ```
    https://<your-endpoint>?name=Karishma
    Hello, Karishma! Welcome to AWS Lambda.
    ```

---

## Project Structure
code :



---

## Code Example (`lambda_function.py`)
```python
def lambda_handler(event, context):
    # Get query parameters safely
    params = event.get('queryStringParameters')
    name = params.get('name') if params and 'name' in params else 'Guest'
    
    # Return response
    return {
        'statusCode': 200,
        'body': f'Hello, {name}! Welcome to AWS Lambda.'
    }
