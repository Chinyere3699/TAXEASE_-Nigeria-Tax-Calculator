# Tax Methodology Document

## Document Control

### Version History

| Version | Date | Author | Description of Changes |
| :--- | :--- | :--- | :--- |
| **v1.0.0** | June 2026 | Technical Writing Team | Initial draft|

## Introduction

This document explains how Taxease computes PAYE (Pay As You Earn) tax for individuals and payroll users based on Nigerian personal income tax rules.

It breaks down:
- Income structure
- Allowable deductions
- Relief application
- Tax band computation
- Final net salary output

## Scope

This methodology applies to:
- Employees
- Freelancers
- Payroll Officers
- SMEs using batch payroll

It covers only **tax computation logic**, not payment or filing processes.

## Income Structure

TaxEase begins computation using **Gross Income**:

Gross Income includes:
- Basic salary
- Allowances
- Bonuses (if applicable)

## 4. Allowable Deductions (Non-Taxable Components)

These are subtracted before tax is applied:

### 4.1 Pension Contribution
Statutory employee pension deduction.

### 4.2 NHF Contribution
National Housing Fund contribution.

### 4.3 Other Approved Statutory Deductions
As defined by Nigerian tax regulations.

## 5. Reliefs

### Rent Relief
TaxEase applies rent relief as part of tax computation where applicable.

> Note: CRA is no longer used. It has been replaced with Rent Relief in line with updated product requirements.

## 6. Taxable Income Calculation

The system computes taxable income as:

Gross Income  
- Pension  
- NHF  
- Other allowable deductions  
- Rent Relief  
= **Taxable Income**


## 7. Tax Band Application (PAYE)

TaxEase applies progressive tax bands to taxable income:

- 0% on first ₦800,000  
- 15% on next band  
- 18% on next band  
- 21% on next band  
- 23% on next band  
- 25% on income above threshold  

(Exact thresholds are defined in backend configuration and tax rules module)


## 8. Final Tax Computation

After applying tax bands:

- Annual PAYE Tax is calculated
- Monthly PAYE Tax is derived (Annual ÷ 12)


## 9. Net Salary Calculation

Net Salary is computed as:

Gross Income  
- Pension  
- NHF  
- PAYE Tax  
= **Net Salary**

## 10. Output Summary

The system returns:

- Gross Income
- Total Deductions
- Rent Relief Applied
- Taxable Income
- Annual PAYE Tax
- Monthly PAYE Tax
- Net Salary

## 11. Assumptions

- Tax rules are configured in backend and may change over time
- Rent relief replaces CRA
- Users provide accurate salary and deduction data
- TaxEase provides estimates, not legal tax filings

## 12. Future Enhancements

- Dynamic tax rule updates via admin dashboard
- Integration with official tax authority APIs
- Real-time tax policy updates
