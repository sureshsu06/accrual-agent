# Accrual Agent Assignment

## Overview

Your assignment is to build an AI agent system that can automate the accrual process in financial operations. This is a critical part of the month-end close process where companies need to record expenses that have been incurred but not yet invoiced or paid.

The goal is to demonstrate how AI agents can transform a traditionally manual process into an intelligent workflow that can identify, calculate, and manage accruals while collaborating with human users.

## Assignment Objective

Create a prototype application that implements an agentic workflow for handling expense accruals. Your solution should:

1. Analyze historical transaction patterns to identify potential missing expenses
2. Calculate appropriate accrual amounts based on historical data and contracts
3. Generate documentation for audit purposes
4. Implement a thoughtful UI/UX 

## Dataset Description

The provided datasets represent a simplified version of the data you would encounter in a real financial system:

1. `historical_transactions.csv`: Past 12 months of vendor transactions
2. `contracts.csv`: Current vendor contracts with payment terms
3. `gl_accounts.csv`: General ledger account structure
4. `previous_accruals.csv`: History of past accruals and their accuracy
5. `vendors.csv`: Vendor master data
6. `current_month_transactions.csv`: Transactions for the current month (April 2025)

## Technical Requirements

1. Implement at least three distinct AI agent roles:
   - Analysis Agent: Identifies missing accruals by analyzing patterns
   - Calculation Agent: Determines appropriate accrual amounts
   - Documentation Agent: Prepares supporting evidence
   - (Bonus) Communication Agent: Prepares outreach to vendors or employees for missing details

2. Create a user interface that:
   - Displays recommended accruals with confidence levels
   - Allows users to review, modify, or approve accruals
   - Provides explanations for how each accrual was determined
   - Captures feedback for system improvement

3. Include workflows that handle:
   - Normal case: Clear pattern of regular expenses
   - Edge case: Unusual or first-time accruals
   - Learning case: System improves based on corrections
   - Vendor follow-up case: System identifies vendors who typically bill monthly but haven't submitted an invoice, and prepares appropriate communication

## Vendor Communication Feature

As part of the assignment, implement a workflow where the system:

1. Identifies vendors who regularly bill on a monthly basis but haven't submitted an invoice for the current period
2. Analyzes historical billing patterns to estimate the expected amount
3. Prepares an email draft to the vendor requesting information about unbilled services
4. Allows the user to review and send the communication
5. Tracks responses and updates accruals accordingly

This feature demonstrates how AI agents can not only identify issues but also take proactive steps to resolve them while keeping humans in the loop.

## Technology Choices

You may use any technologies you're comfortable with, but we recommend:
- Frontend: React, Vue, or similar modern framework
- Backend: Node.js, Python, or similar
- Database: Any SQL or NoSQL solution (or even flat files for this prototype)
- AI tools: You may leverage OpenAI, Anthropic, or other AI APIs

## Evaluation Criteria

We'll evaluate your submission based on:
1. **Functionality**: Does it correctly identify and calculate accruals?
2. **Agent Design**: How thoughtfully have you designed your agent system?
3. **User Experience**: How intuitive and helpful is the interface?
4. **Code Quality**: Is the code well-structured and maintainable?
5. **AI Integration**: How effectively have you leveraged AI capabilities?
6. **Documentation**: How clearly have you explained your approach?

## Submission Instructions

Please provide:
1. Source code in a GitHub repository
2. README with setup instructions and approach explanation
3. A brief demo video (5 minutes max) walking through the key features

## AI Tools

Feel free to use AI tools to act as a thought partner, but the overall design and approach should be your own.

## Questions

If you have any questions about the assignment, please reach out to us for clarification.

Good luck!
