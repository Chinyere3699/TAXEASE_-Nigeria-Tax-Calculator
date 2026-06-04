# Tax Methodology Document

## Document Control and Governance

### Version History
We use this table to track changes made to this document over time as tax rules get updated.

| Version | Date | Author | Description of Changes |
| :--- | :--- | :--- | :--- |
| **v1.0.0** | June 2026 | Technical Writing Team | Initial draft rewritten to include the landmark 2025 Tax Reform rules. |

---

### The Tax Laws We Follow
The calculation engine inside the TaxEase app has been completely rebuilt to match the massive overhaul of Nigeria's tax structure. Our system is programmed to follow the four new tax reform bills signed into law on June 26, 2025:

* **Nigeria Tax Act 2025 (Effective January 1, 2026):** The primary law that sets the brand-new personal income tax rates and rules.
* **Nigeria Tax Administration Act 2025:** Rules governing how taxes are managed and tracked.
* **Nigeria Revenue Service Act 2025:** Guidelines from the restructured national revenue authority.
* **Joint Revenue Board Act 2025:** Laws ensuring tax alignment across different states.

These rules ensure our calculations fully align with the current guidance of the Nigeria Revenue Service (NRS).

---

### Important Legal Disclaimer
While we work hard to make our calculations highly accurate to match the 2026 tax system, please remember:

* **For Estimation and Learning Only:** TaxEase provides tax estimates for informational and educational use. It does not constitute official legal, financial, or tax advice.
* **User Responsibility:** Taxpayers remain responsible for double-checking their inputs, as final tax assessments are officially issued by the revenue authorities.
* **Limitations of v1.0.0:** Direct filing of tax paperwork and live payment transactions to the government are not supported in this first version of the platform.

---

## Executive Summary & Scope
This section explains exactly what TaxEase does under the brand-new 2026 tax system, who it is built for, and what features are included or left out of our first app release.

### 1. Objective (What is TaxEase?)
TaxEase is a mobile and web app built to clear up the confusion around taxes in Nigeria. Following the massive tax laws passed by the president, old tax methods (like the CRA) have been completely thrown out and replaced with new systems like Rent Relief and updated tax brackets.

Because these changes are brand new, many everyday citizens, freelancers, and payroll officers find it incredibly hard to know if their calculations are correct. Our app handles all this complex, updated math behind the scenes. It breaks down income tax, business estimates, and deductions in plain, everyday language so everyone can easily understand their true tax numbers.

### 2. Who is this App For? (Target Users)
The calculation paths in our platform are designed to support several different groups of people:

#### Primary Users (Everyday individual and payroll paths):
* **Salaried Employees:** Individual workers who want to double-check their monthly pay slips and understand exactly how much payroll tax (PAYE) should be deducted.
* **Freelancers and Gig Workers:** Independent creators or informal businesses who need a simple way to figure out their tax rates using their National Identification Number (NIN).
* **HR Teams and Payroll Officers:** Administrators who manage employee payments and need to upload bulk files (like CSVs) to calculate payroll taxes for entire teams at once to save time.

#### Secondary Users (Professional support paths):
* **Small Business Owners (SMEs):** Managers running small operations who want to check if their annual turnover qualifies them for tax exemptions.
* **Accountants and Tax Consultants:** Financial professionals who need a fast, trustworthy tool to double-check tax brackets, business taxes, or receipts for their clients.

---

## Glossary of Terms & Variables
To keep things as simple as possible, we have listed the important tax terms used in our system alongside their everyday meanings and the short "variable names" our engineering team uses to build the app's calculation engine.

### 1. Everyday Money Terms
* **Gross Income / Gross Salary (Variable name: `gross_salary`):** This is the total amount of money you earn from your job before any taxes, rent discounts, or retirement savings are taken out. It includes your basic pay plus regular work allowances like housing and transport.
* **Taxable Income / Chargeable Income (Variable name: `taxable_income`):** This is the final portion of your salary that the government can actually touch and tax. It is what remains after we subtract all your approved tax-free deductions and rent reliefs from your Gross Income.
* **Net Salary / Take-Home Pay (Variable name: `net_salary`):** This is the actual amount of money that lands in your bank account at the end of the month. It is calculated by taking your Gross Salary and subtracting your final PAYE tax, pension, NHF, and any other deductions.

### 2. Tax Breaks and Deductions (Tax-Free Money)
* **Rent Relief (Variable name: `rent_relief`):** Under the 2025 reforms, the old Consolidated Relief Allowance (CRA) has been completely abolished. It is replaced by this new Rent Relief system. This is a tax discount based on the actual rent you pay for your home.
* **Pension Contribution (Variable name: `pension_deduction`):** A fixed amount of money kept aside from your paycheck for your official retirement fund. This money is legally tax-free.
* **National Housing Fund / NHF (Variable name: `nhf_deduction`):** A small statutory contribution taken from an employee's basic pay to support government housing plans. This is also processed as a tax-free deduction.

### 3. Personal Income Tax (PAYE) Rules
* **PAYE / Pay As You Earn (Variable name: `annual_paye` / `monthly_paye`):** The standard method used to collect personal income tax from salaried workers. The app calculates your total tax for the year and divides it by 12 so a small portion is deducted every single month.
* **New PAYE Tax Bands (Variable name: `paye_bands`):** The brand-new step-by-step tax rates introduced by the recent reforms. Instead of old percentages, your taxable income is divided into six new levels starting from 0% all the way up to 25%.
* **Tax-Free Minimum Wage Exemption (Variable name: `tax_exemption`):** A government protection rule stating that any low-income earner making ₦800,000 or less annually is 100% exempt from paying personal income tax.

### 4. Other Business Tax Terms
* **Company Income Tax / CIT (Variable name: `cit_tax`):** The tax that registered businesses and organizations must pay on their annual profits. Under the new laws, small businesses making under ₦50 million a year pay 0% CIT.
* **Value Added Tax / VAT (Variable name: `vat_amount`):** A standard 7.5% consumption tax added to the price of taxable goods and services.
* **Withholding Tax / WHT (Variable name: `wht_deducted`):** An advance tax that is automatically taken out at the source when making certain contract payments to vendors or individuals.

---

## Algorithmic Architecture & Order of Operations
To calculate your exact taxes and take-home pay under the landmark 2025 reforms, our app’s calculation engine follows a strict, step-by-step math recipe. It runs these steps in a precise linear order to ensure all business logic and personal pay slips are computed perfectly every single time.

Here is the exact order of how the app processes the numbers behind the scenes:

### Step 1: Add Up Your Total Earnings (Gross Income)
First, the app takes everything you earn from your job before any deductions happen and adds them together into an annual pool.

### Step 2: Check for Low-Income Exemption (The ₦800,000 Rule)
Before running any heavy math, the app looks at your total annual earnings from Step 1. Under the new laws, minimum wage earners making ₦800,000 or less a year are 100% exempt from personal income tax. If you qualify, the app immediately sets your PAYE tax to ₦0 and skips directly to the final paycheck step.

### Step 3: Subtract Your Tax-Free Retirement Savings (Deductions)
If you earn more than ₦800,000, the app calculates your approved tax-free retirement deductions and takes them out next so you don't get taxed on them:
* **Pension Fund:** The app calculates $8\%$ of the total of your Basic, Housing, and Transport allowances combined.
* **National Housing Fund (NHF):** The app calculates $2.5\%$ of your Basic Salary alone.

### Step 4: Calculate Your New Rent Relief Tax Discount
Under the new laws, the old Consolidated Relief Allowance (CRA) has been completely abolished. It is replaced by a Rent Relief system based on the actual annual rent you pay. The app compares your rent numbers and picks the lower amount between ₦500,000 or 20% of your annual rent.

### Step 5: Find Your True Taxable Income
Now, the app finds the exact remaining part of your salary that can legally be taxed. It takes your Gross Income from Step 1 and subtracts your retirement savings from Step 3 and your rent relief from Step 4.

### Step 6: Run the Money Through the New 2026 Tax Bands
The app takes your Taxable Income and splits it across the brand-new progressive tax levels. As your income moves into higher stages, the tax rate increases:
* **First ₦800,000** is taxed at **0%** (Completely Tax-Free!)
* **Next ₦2,200,000** is taxed at **15%**
* **Next ₦9,000,000** is taxed at **18%**
* **Next ₦13,000,000** is taxed at **21%**
* **Next ₦25,000,000** is taxed at **23%**
* **Any leftover money above ₦50,000,000** is taxed at **25%**

The app adds the tax from each level together to get your final Annual PAYE tax bill.

### Step 7: Calculate Final Net Salary (Take-Home Pay)
Finally, the app processes the net salary output using our official platform formula. This final amount represents the exact money landing in the user's bank account.

---

## Temporal Conversions & Core System Variations
This section explains how the app breaks down massive yearly tax rules into normal monthly paychecks, and how the system handles real-life workplace updates without breaking the math.

### 1. Breaking Yearly Rules into Monthly Paychecks (Temporal Conversion)
Even though Nigeria's official tax laws are always written as big yearly numbers (like the ₦800,000 tax-free limits or yearly rent caps), real businesses pay workers every month. To prevent math errors, the TaxEase system uses a strict "Multiply-Then-Divide" rule:

* **Step A (Multiply):** When you type in your monthly basic salary and work allowances, the app automatically multiplies them by 12 to find your estimated yearly income.
* **Step B (Process):** The app runs this big yearly income through all the official 2026 tax calculation rules we described earlier (deducting pension, applying rent relief, and matching the progressive tax bands).
* **Step C (Divide):** Once the app finds your final tax bill for the whole year, it divides that number by 12 to give you your exact, single Monthly PAYE Deduction.

### 2. Handling Real-Life Workplace Changes (System Variations)
Workplaces are dynamic, so our app is built to handle sudden income changes smoothly:

* **Mid-Year Salary Changes:** If you get a promotion or a raise in the middle of the year, the app does not try to rewrite your past months' history. Instead, it takes your new monthly earnings, projects them forward as your new estimated yearly path, and adjusts your upcoming monthly tax cuts so you stay fully compliant with the tax levels.
* **Starting a Job Mid-Month:** For workers who join a company halfway through a month, the system avoids overtaxing them. It calculates their actual earnings for the exact number of active days they worked that month and runs that specific amount through the standard calculation path.

### 3. Extra Core Tools (Other Tax Tracks)
While individual personal tax (PAYE) is our main focus, the app also includes quick-check tools for small businesses and freelancers using these updated rules:

* **Value Added Tax (VAT) Track:** For small business users checking sales tax, the app applies a simple formula based on the official 7.5% rate.
* **Withholding Tax (WHT) Track:** For freelancers and vendors receiving contract payments, the app tracks advance tax deductions using a simple baseline rate check.
* **Company Income Tax (CIT) Check:** Small business owners can instantly check their compliance status. The app is programmed to automatically flag an organization as 100% exempt from profit tax if their yearly turnover is under ₦50 million.

