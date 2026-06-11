# Taxease API Documentation

## Version Information

**Product:** Taxease  
**Version:** 1.0  
**Prepared By:** Technical Writing Team, Group 18  
**Last Updated:** June 2026  

# 1. Overview

The Taxease API provides backend services that support user authentication, tax calculations, payroll processing, and report generation for the TaxEase platform.

The APIs enable frontend and mobile applications to securely interact with the TaxEase system.

# 2. Authentication

TaxEase uses **JSON Web Token (JWT)** authentication to secure protected endpoints.

## Public Endpoints

These endpoints do not require authentication:

- User Registration
- User Login
- Refresh Token
- Forgot Password
- Reset Password

## Protected Endpoints

These endpoints require authentication:

- Save Tax Calculation
- Retrieve Calculation History
- Delete Calculation History
- Payroll Processing
- Report Generation
- Administrative Functions

# 3. API Endpoints

## Authentication APIs

### Register User

| Item | Details |
|--------|----------|
| Method | POST |
| Endpoint | `/api/auth/sign_up` |
| Description | Creates a new user account. |
| Authentication Required | No |


### Login User

| Item | Details |
|--------|----------|
| Method | POST |
| Endpoint | `/api/auth/login` |
| Description | Authenticates users and grants access tokens. |
| Authentication Required | No |


### Refresh Token

| Item | Details |
|--------|----------|
| Method | GET |
| Endpoint | `/api/auth/refresh_token` |
| Description | Generates a new authentication token. |
| Authentication Required | No |

### Forgot Password

| Item | Details |
|--------|----------|
| Method | POST |
| Endpoint | `/api/auth/forgot_password` |
| Description | Initiates password recovery. |
| Authentication Required | No |

### Reset Password

| Item | Details |
|--------|----------|
| Method | POST |
| Endpoint | `/api/auth/reset_password` |
| Description | Resets a user's password. |
| Authentication Required | No |


### Logout User

| Item | Details |
|--------|----------|
| Method | POST |
| Endpoint | `/api/auth/log_out` |
| Description | Logs the user out of the system. |
| Authentication Required | Yes |

# 4. Tax APIs

### Calculate Tax

| Item | Details |
|--------|----------|
| Method | POST |
| Endpoint | `/api/tax/calculate` |
| Description | Calculates PAYE tax obligations using user-provided income information. |
| Authentication Required | No |

### Get Tax Rules

| Item | Details |
|--------|----------|
| Method | GET |
| Endpoint | `/api/tax/rules` |
| Description | Retrieves tax rules and calculation parameters used within the system. |
| Authentication Required | No |

### Save Calculation

| Item | Details |
|--------|----------|
| Method | POST |
| Endpoint | `/api/tax/save` |
| Description | Saves completed tax calculations for future reference. |
| Authentication Required | Yes |

### Retrieve Calculation History

| Item | Details |
|--------|----------|
| Method | GET |
| Endpoint | `/api/tax/history` |
| Description | Retrieves previously saved tax calculations. |
| Authentication Required | Yes |

### Delete Calculation History

| Item | Details |
|--------|----------|
| Method | DELETE |
| Endpoint | `/api/tax/history/:id` |
| Description | Deletes a saved tax calculation record. |
| Authentication Required | Yes |

# 5. Payroll APIs

### Upload Payroll Data

| Item | Details |
|--------|----------|
| Method | POST |
| Endpoint | `/api/payroll/upload` |
| Description | Uploads payroll information for batch tax processing. |
| Authentication Required | Yes |

**Notes:**

- CSV file uploads supported
- Maximum upload size determined by backend configuration

### Retrieve Payroll Uploads

| Item | Details |
|--------|----------|
| Method | GET |
| Endpoint | `/api/payroll/uploads` |
| Description | Retrieves payroll upload records. |
| Authentication Required | Yes |


### Retrieve Payroll Results

| Item | Details |
|--------|----------|
| Method | GET |
| Endpoint | `/api/payroll/uploads/:id/results` |
| Description | Retrieves processed payroll tax results for a selected upload. |
| Authentication Required | Yes |


# 6. Reports APIs

### Generate Individual Tax Report

| Item | Details |
|--------|----------|
| Method | GET |
| Endpoint | `/api/reports/individual/pdf` |
| Description | Generates a downloadable PDF tax summary for individual users. |
| Authentication Required | Yes |

### Export Payroll Report (CSV)

| Item | Details |
|--------|----------|
| Method | POST |
| Endpoint | `/api/reports/payroll/csv` |
| Description | Exports payroll tax information in CSV format. |
| Authentication Required | Yes |

### Export Payroll Report (Excel)

| Item | Details |
|--------|----------|
| Method | POST |
| Endpoint | `/api/reports/payroll/excel` |
| Description | Exports payroll tax information in Excel format. |
| Authentication Required | Yes |

### Download Generated Report

| Item | Details |
|--------|----------|
| Method | GET |
| Endpoint | `/api/reports/:id/download` |
| Description | Downloads previously generated reports. |
| Authentication Required | Yes |

# 7. Administrative APIs

### Retrieve Users

| Item | Details |
|--------|----------|
| Method | GET |
| Endpoint | `/api/admin/users` |
| Description | Retrieves registered users within the system. |
| Authentication Required | Yes |
| Access Level | Administrator |

### Update User Role

| Item | Details |
|--------|----------|
| Method | PATCH |
| Endpoint | `/api/admin/users/:id/role` |
| Description | Updates user access roles. |
| Authentication Required | Yes |
| Access Level | Administrator |

### Create Tax Rules

| Item | Details |
|--------|----------|
| Method | POST |
| Endpoint | `/api/admin/tax-rules` |
| Description | Creates new tax rules within the platform. |
| Authentication Required | Yes |
| Access Level | Administrator |

### Update Tax Rules

| Item | Details |
|--------|----------|
| Method | PATCH |
| Endpoint | `/api/admin/tax-rules/:id` |
| Description | Updates existing tax rules. |
| Authentication Required | Yes |
| Access Level | Administrator |

# 8. Security Features

TaxEase implements several security mechanisms, including:

- JSON Web Token (JWT) Authentication
- Password Hashing using bcrypt
- Protected Route Middleware
- Input Validation
- Role-Based Access Control (RBAC)
- Secure File Upload Handling

# 9. Technologies Used

## Backend Framework

- Node.js
- Express.js

## Database

- MongoDB
- Mongoose

## Authentication

- JSON Web Token (JWT)
- bcrypt

## File Handling

- Multer
- Cloudinary

## Data Processing

- csv-parser
- xlsx

## Report Generation

- PDFKit

## Notifications

- Resend

## Utilities

- dotenv
- cors
- Morgan

# 10. Notes

- Authentication middleware is applied only to protected routes.
- Login and registration endpoints remain publicly accessible.
- Reports are generated and stored according to backend configuration.
- Detailed request payloads and response schemas will be updated as backend validation progresses.


# 11. Revision History

| Version | Date | Description |
|----------|-------|-------------|
| 1.0 | June 2026 | Initial API documentation |
