# 🚪 AWS API Gateway — DVA-C02 Notes

Amazon API Gateway is a fully managed AWS service used to **create, publish, secure, monitor, and manage APIs**.

---

# 📌 1. What is API Gateway?

API Gateway acts as a front door for applications to access backend services.

Common architecture:

```text
Client
  ↓
API Gateway
  ↓
Lambda
  ↓
DynamoDB
```

### Key benefits

* Create and manage APIs
* Authentication and authorization
* Throttling
* Caching
* Monitoring
* Request/response transformation
* Integration with AWS services and HTTP endpoints

---

# 🧱 2. API Gateway API Types ⭐⭐⭐

API Gateway supports three major API types.

## REST API

* Feature-rich
* Supports many API Gateway features
* Supports API keys and usage plans
* Supports request/response transformations
* Supports resource policies

## HTTP API

* Simpler than REST API
* Lower cost
* Lower latency
* Good for simple APIs and Lambda integrations

## WebSocket API

Used for **real-time, two-way communication**.

Examples:

* Chat applications
* Real-time notifications
* Live dashboards

### Exam Shortcut

```text
REST API    → Feature-rich
HTTP API    → Simple, low-cost, low-latency
WebSocket   → Real-time communication
```

---

# 🔗 3. API Gateway Integration ⭐⭐⭐

API Gateway can integrate with:

* AWS Lambda
* HTTP endpoints
* AWS services
* Mock integrations

Most common DVA-C02 architecture:

```text
Client
   ↓
API Gateway
   ↓
Lambda
   ↓
DynamoDB
```

---

# ⚡ 4. Lambda Proxy Integration ⭐⭐⭐

Very important for DVA-C02.

With Lambda proxy integration, API Gateway passes the incoming request information to Lambda.

Lambda can receive:

* HTTP method
* Path
* Headers
* Query parameters
* Path parameters
* Request body

Example Lambda event:

```json
{
  "httpMethod": "GET",
  "path": "/users",
  "queryStringParameters": {
    "id": "123"
  },
  "body": null
}
```

Lambda returns a response such as:

```json
{
  "statusCode": 200,
  "headers": {},
  "body": "{\"message\":\"Success\"}"
}
```

---

# 🛣️ 5. Resources and Methods

A **resource** represents the API path.

Example:

```text
/users
/users/{id}
```

A **method** represents the HTTP operation.

```text
/users
   ├── GET
   └── POST

/users/{id}
   ├── GET
   └── DELETE
```

### Remember

```text
Resource = URL path
Method   = HTTP operation
```

---

# 🚀 6. Stages ⭐⭐

Stages represent different environments or deployments.

Common stages:

```text
/dev
/test
/prod
```

Example:

```text
API Gateway
     ↓
    /dev
    /test
    /prod
```

Stages can have different configurations.

---

# 🔐 7. Authorization ⭐⭐⭐

API Gateway supports different authorization mechanisms.

## IAM Authorization

Uses AWS IAM credentials and policies.

```text
Client
  ↓
IAM Authentication
  ↓
API Gateway
```

Useful for AWS users, applications, and services.

## Lambda Authorizer

A Lambda function evaluates the request and determines whether it should be allowed.

```text
Client
  ↓
API Gateway
  ↓
Lambda Authorizer
  ↓
Allow / Deny
```

## Amazon Cognito

Used for user authentication with Cognito user pools.

```text
User
 ↓
Cognito
 ↓
API Gateway
 ↓
Backend
```

---

# 🔑 8. API Keys and Usage Plans ⭐⭐

API keys can be used to identify and control API consumers.

Usage plans can define:

* Throttling
* Quotas
* API stages associated with the plan

### Important

API keys are primarily for **usage control and identification**, not strong user authentication.

---

# 🌐 9. CORS ⭐⭐

CORS = **Cross-Origin Resource Sharing**

It is important when a browser-based frontend calls an API hosted on a different origin.

Example:

```text
Frontend
https://myapp.com
      ↓
API Gateway
https://api.example.com
```

CORS allows the browser to permit the cross-origin request when properly configured.

---

# 🚦 10. Throttling ⭐⭐⭐

API Gateway can limit the number of requests sent to your API.

This protects backend services from excessive traffic.

Example:

```text
大量 requests
      ↓
API Gateway
      ↓
Throttling
      ↓
429 Too Many Requests
```

### Remember

```text
429 = Too Many Requests
```

---

# 💾 11. API Gateway Caching ⭐⭐

API Gateway can cache responses.

Without caching:

```text
Client
  ↓
API Gateway
  ↓
Lambda
  ↓
Database
```

With caching:

```text
Client
  ↓
API Gateway
  ↓
Cache → Response
```

Caching can reduce:

* Backend requests
* Lambda invocations
* Database load
* Response latency

---

# 🌍 12. Custom Domain Names

Instead of using the default API Gateway URL, you can use a custom domain.

Example:

```text
api.example.com
```

Instead of:

```text
xxxx.execute-api.region.amazonaws.com
```

---

# ❌ 13. Common HTTP Status Codes ⭐⭐⭐

| Code | Meaning               |
| ---- | --------------------- |
| 200  | Success               |
| 201  | Created               |
| 400  | Bad Request           |
| 401  | Unauthorized          |
| 403  | Forbidden             |
| 404  | Not Found             |
| 429  | Too Many Requests     |
| 500  | Internal Server Error |
| 502  | Bad Gateway           |
| 504  | Gateway Timeout       |

---

# 🔄 14. Request Flow

Typical API Gateway + Lambda flow:

```text
Client
   ↓
API Gateway
   ↓
Authorization
   ↓
Throttling
   ↓
Integration
   ↓
Lambda
   ↓
DynamoDB
   ↓
Lambda Response
   ↓
API Gateway
   ↓
Client
```

---

# 🧠 15. DVA-C02 Exam Shortcuts

### API Type

```text
Real-time communication → WebSocket
Simple RESTful API → HTTP API
Feature-rich API → REST API
```

### Authorization

```text
AWS IAM users/services → IAM Authorization
Custom authorization logic → Lambda Authorizer
User authentication → Cognito
```

### Traffic

```text
Too many requests → Throttling → 429
```

### Performance

```text
Repeated requests → API Gateway Cache
```

### Architecture

```text
API → Lambda → DynamoDB
```

is one of the most common DVA-C02 patterns.

---

# 🔥 Most Important Topics to Master

For DVA-C02, prioritize these:

1. ⭐⭐⭐ Lambda integration
2. ⭐⭐⭐ Lambda Proxy Integration
3. ⭐⭐⭐ IAM authorization
4. ⭐⭐⭐ Lambda Authorizer
5. ⭐⭐⭐ Cognito authorization
6. ⭐⭐⭐ API Gateway throttling
7. ⭐⭐ REST vs HTTP API
8. ⭐⭐ Stages
9. ⭐⭐ CORS
10. ⭐⭐ API keys and usage plans
11. ⭐⭐ Caching
12. ⭐⭐ Custom domains
13. ⭐⭐ Error/status codes

---

# 🎯 Quick Revision

```text
API Gateway
│
├── API Types
│   ├── REST
│   ├── HTTP
│   └── WebSocket
│
├── Integration
│   ├── Lambda
│   ├── HTTP
│   └── AWS Services
│
├── Security
│   ├── IAM
│   ├── Lambda Authorizer
│   └── Cognito
│
├── Traffic Management
│   ├── Throttling
│   └── Quotas
│
├── Performance
│   └── Caching
│
└── Configuration
    ├── Stages
    ├── CORS
    └── Custom Domains
```
