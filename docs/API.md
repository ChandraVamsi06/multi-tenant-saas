# API Documentation

Base URL: `http://localhost:5000/api`

## Authentication
### Register Tenant
* **POST** `/auth/register-tenant`
* **Body:** `{ "tenantName": "Acme", "subdomain": "acme", "adminEmail": "...", "adminPassword": "..." }`
* **Response:** `201 Created`

### Login
* **POST** `/auth/login`
* **Body:** `{ "email": "...", "password": "...", "tenantSubdomain": "..." }`
* **Response:** `200 OK` (Returns JWT Token)

### Get Me
* **GET** `/auth/me`
* **Header:** `Authorization: Bearer <token>`
* **Response:** `200 OK` (User details)

## Projects
### List Projects
* **GET** `/projects`
* **Response:** `200 OK` (Array of projects)

### Create Project
* **POST** `/projects`
* **Body:** `{ "name": "New Project", "description": "..." }`
* **Response:** `201 Created`

## Tasks
### Create Task
* **POST** `/projects/:id/tasks`
* **Body:** `{ "title": "Fix Bug", "priority": "high" }`
* **Response:** `201 Created`

### Update Status
* **PATCH** `/tasks/:id/status`
* **Body:** `{ "status": "completed" }`
* **Response:** `200 OK`

## Team
### List Members
* **GET** `/tenants/:id/users`
* **Response:** `200 OK`

### Add Member
* **POST** `/tenants/:id/users`
* **Body:** `{ "fullName": "...", "email": "...", "password": "...", "role": "user" }`
* **Response:** `201 Created`