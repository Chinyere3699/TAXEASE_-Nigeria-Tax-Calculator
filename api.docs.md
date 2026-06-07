# TaxEase API Documentation

## Overview

This document describes the API endpoints available in the TaxEase platform.

# Authentication APIs

## Sign Up

**Method:** POST

**Endpoint:** `/sign_up`

**Description:** Creates a new user account.

### Authentication Required
No

### Request Body
To be updated by Backend Team.

### Response
To be updated by Backend Team.

## Login

**Method:** POST

**Endpoint:** `/login`

**Description:** Authenticates a user and grants access.

### Authentication Required
No

### Request Body
To be updated by Backend Team.

### Response
To be updated by Backend Team.

## Refresh Token

**Method:** GET

**Endpoint:** `/refresh_token`

**Description:** Generates a new access token.


# Tax APIs

## Calculate Tax

**Method:** POST

**Endpoint:** `/calculate`

**Description:** Calculates PAYE tax based on user inputs.

### Authentication Required
No

### Request Body
To be updated by Backend Team.

### Response
To be updated by Backend Team.

## Get Tax Rules

**Method:** GET

**Endpoint:** `/rules`

**Description:** Retrieves applicable tax rules and tax bands.

## Save Calculation

**Method:** POST

**Endpoint:** `/save`

**Description:** Saves a tax calculation for future reference.

### Authentication Required
Yes

## Get Calculation History

**Method:** GET

**Endpoint:** `/history`

**Description:** Retrieves saved tax calculations.

### Authentication Required
Yes

## Delete Calculation History

**Method:** DELETE

**Endpoint:** `/history/:id`

**Description:** Deletes a saved calculation.

### Authentication Required
Yes


# Payroll APIs

## Upload Payroll CSV

**Method:** POST

**Endpoint:** `/upload`

**Description:** Uploads and processes payroll data from a CSV file.

### Authentication Required
Yes

### Constraints
- CSV files only
- Maximum file size: 10 MB

## Get Payroll Uploads

**Method:** GET

**Endpoint:** `/uploads`

**Description:** Retrieves all payroll upload records.

### Authentication Required
Yes

## Get Payroll Results

**Method:** GET

**Endpoint:** `/uploads/:id/results`

**Description:** Retrieves payroll calculation results for a specific upload.

### Authentication Required
Yes


# Reports APIs

## Generate Individual PDF Report

**Method:** GET

**Endpoint:** `/individual/pdf`

**Description:** Generates a PDF tax report.

### Authentication Required
Yes

## Export Payroll CSV

**Method:** POST

**Endpoint:** `/payroll/csv`

**Description:** Exports payroll records in CSV format.

### Authentication Required
Yes

## Export Payroll Excel

**Method:** POST

**Endpoint:** `/payroll/excel`

**Description:** Exports payroll records in Excel format.

### Authentication Required
Yes

## Download Report

**Method:** GET

**Endpoint:** `/:id/download`

**Description:** Downloads a generated report.

### Authentication Required
Yes


# Error Responses

This section will be updated when backend response formats are finalized.


# Authentication

This section will be updated when the backend team confirms the authentication mechanism.
