# AI Agent Workflow Assignment: Missing Invoice Detection

## Overview

Your assignment is to build a simple AI assistant that helps accounting teams identify and handle missing vendor invoices. In accounting, at the end of the month companies need to record the month's expenses even if they haven't received an invoice yet for a specific expense. E.g. You know that you use electricity from the grid during the month but you only receive the bill the 15th of next month. As an accountant, you need to estimate what the rough electricity bill for the month would be and 'accrue' the expense, even without a bill. 

Your goal is to build a system that will 1) Help detect what set of expenses will need accrual for the month, 2) Help compute what the accrual amount should be, 3) Get feedback from the accountant when needed, 4) Facilitate communications to external stakeholders to get missing information needed for the accrual

## Dataset Description

We've provided CSV files with sample data:

1. `historical_transactions.csv`: Past vendor payments
2. `vendors.csv`: Information about the company's vendors
3. `current_month_transactions.csv`: Transactions for the current month
4. `previous_accruals.csv`: Accruals that have been done in the past

## Implementation Requirements

Create a simple application with three AI agent components working together:

1. **Analysis Agent**
   - Looks through historical transactions to find vendors who typically bill monthly, and when they typically bill
   - Identifies which of these vendors are missing from the current month's transactions so far - consider past history here
   - Prioritize based on the amount and importance
   - Gives a rationale for each recommendation

2. **Calculation Agent**
   - Estimates the expected invoice amount using the vendor's billing history
   - Provides a confidence level for this estimate
   - Shows reasoning for how it calculated this amount

3. **Communication Agent**
   - Pick a few vendors where your accrual confidence goes below a threshold
   - Highlight to the user that the recommended action is to send an email asking for details
   - Share a draft email to the vendor asking about the missing invoice - the user can review this  
   - Includes relevant details like the expected amount and typical invoice date

## User Interface

Build a simple interface that shows:

1. A list of recommended accruals with:
   - Vendor name
   - Expected amount
   - Confidence level
   - Status (New, Email Drafted, Email Sent, Response Received)

2. For low confidence cases:
   - An explanation of why the system thinks the accrual is needed
   - A draft email that the user can review and edit
   - Buttons to approve/reject the system's recommendations
   - A way to mark when responses are received

## Expected Agent Behaviors

### Analysis Agent

The Analysis Agent should:

1. **Pattern Recognition**
   - Identify vendors who bill on a regular monthly schedule
   - Look for consistent billing amounts or predictable variations
   - Notice typical billing dates (e.g., "usually bills between the 15th-20th")

2. **Gap Detection**
   - Compare current month transactions against expected transactions
   - Identify which regular vendors are missing from current month
   - Prioritize based on dollar amount and consistency of past billing

3. **Reasoning**
   - Explain why it believes an invoice is missing
   - Provide evidence from historical transaction patterns
   - Assign confidence level to its conclusion

**Example Analysis:**
*"Marketing Masters (vendor ID: V007) has sent invoices of $7,500 on the 22nd-23rd of each month for the past 12 months. There is no transaction from this vendor in the current month (April 2025), and we are now past their typical billing date. I'm 95% confident that this invoice is missing and [x] should be accrual amount"*

### Calculation Agent

The Calculation Agent should:

1. **Amount Estimation**
   - Calculate based on historical invoice amounts
   - Consider any trends or seasonal patterns
   - Account for known contract changes if applicable

2. **Confidence Assessment**
   - Provide confidence level for the estimate
   - Higher confidence for consistent amounts
   - Lower confidence for variable or trending amounts

3. **Explanation**
   - Describe calculation methodology
   - Show relevant historical data points
   - Explain any adjustments made to the estimate

**Example Calculation:**
*"Based on the last 12 months of invoices from Marketing Masters, they have consistently billed exactly $7,500.00 each month with no variation. This appears to be a fixed monthly retainer. I'm 98% confident that the missing invoice will be for $7,500.00."*

### Communication Agent

The Communication Agent should:

1. **Email Creation**
   - Draft clear, professional emails
   - Include relevant details (expected amount, service period)
   - Customize tone based on vendor relationship

2. **Content Customization**
   - Adjust wording based on confidence level
   - Include appropriate context and history
   - Format for readability and professionalism

3. **Follow-up Awareness**
   - Suggest appropriate timing for follow-ups
   - Note any special handling based on vendor history
   - Create appropriate urgency based on invoice amount

**Example Communication:**
*"Dear Marketing Masters Team,*

*I hope this email finds you well. Our records indicate that we have not yet received your invoice for marketing services for April 2025.*

*Based on our agreement, we typically receive a monthly invoice of $7,500.00 around the 22nd-23rd of each month. As we are preparing for our month-end close process, we wanted to check if this invoice has been sent or when we might expect to receive it.*

*If you have already sent the invoice, please provide the invoice number and date so we can locate it in our system.*

*Thank you for your assistance.*

*Best regards,*
*[Finance Team Member]*
*[Company Name]*"

## Implementation Approach

Here's how you might approach implementing this system:

### 1. Data Loading and Processing
- Start by loading the CSV files and converting them to a usable format
- Create functions to help filter and analyze the transaction data
- Build helper functions to find patterns in historical transactions

### 2. Agent Framework
- Set up a system where agents can pass information to each other
- Create a basic "brain" for each agent that can be connected to an AI API
- Implement a simple orchestrator that manages the workflow between agents

### 3. AI Integration
- Connect the agents to an AI API (OpenAI, Anthropic, etc.)
- Create prompts that explain the context and desired output
- Implement parsing logic to extract structured information from AI responses

### Example AI Prompts

Here are examples of how you might structure prompts for each agent:

#### Analysis Agent Prompt
```
You are an Analysis Agent that identifies missing vendor invoices.

HISTORICAL TRANSACTIONS:
[List of past transactions for Vendor X]

CURRENT MONTH TRANSACTIONS:
[List of current transactions]

Based on this data, determine if Vendor X typically sends monthly invoices and if we're missing an invoice for the current month. Provide your reasoning and confidence level.
```

#### Calculation Agent Prompt
```
You are a Calculation Agent that estimates invoice amounts.

VENDOR: [Vendor Name]
HISTORICAL INVOICES:
[List of past invoices with amounts and dates]

Based on this data, estimate what the missing invoice amount should be for [Current Month]. Provide your calculation method, confidence level, and explanation.
```

#### Communication Agent Prompt
```
You are a Communication Agent that drafts emails to vendors.

VENDOR: [Vendor Name]
CONTACT: [Contact Email]
RELATIONSHIP: [Relationship notes]
EXPECTED INVOICE: [Amount] for [Service Description]
TYPICAL INVOICE DATE: [Date]

Draft a professional email to this vendor inquiring about the missing invoice. Be polite and specific about what we're expecting.
```

## Technical Guidance

- You can use any frontend framework you're comfortable with (React, Vue, etc.)
- The agents should communicate with each other to complete the workflow
- Use an AI API (like OpenAI or Anthropic) to power the agents' reasoning

## Evaluation Criteria

We'll evaluate your submission based on:
1. How well the agents work together to complete the workflow
2. The quality of the user interface and experience
3. How clearly your system explains its reasoning
4. Code organization and quality
5. Creativity in addressing the problem

## Submission Instructions

Please provide:
1. Source code in a GitHub repository
2. A README with setup instructions

Good luck!
