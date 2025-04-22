# Accrual Agent Behavior Guide

This guide provides additional details on the expected behavior of the AI agents in the accrual process.

## Analysis Agent

The Analysis Agent is responsible for identifying expenses that need to be accrued. It should:

1. **Identify Regular Patterns**:
   - Recognize regular monthly expenses (rent, subscriptions, services)
   - Detect quarterly or annual expenses that occur on a schedule
   - Notice utility expenses that are billed several days after month-end

2. **Handle Special Cases**:
   - Identify unexpected one-time expenses that might need accruals
   - Flag unusual patterns or breaks in regular expense cycles
   - Detect when a vendor has changed billing patterns

3. **Perform Gap Analysis**:
   - Compare current month transactions against expected transactions
   - Identify missing vendor invoices based on historical patterns
   - Consider contract terms when identifying missing transactions

4. **Learning Capability**:
   - Improve pattern recognition based on user feedback
   - Adjust confidence levels for predictions based on past accuracy
   - Remember specific vendor behaviors (early/late billing)

## Calculation Agent

The Calculation Agent determines the appropriate amount for each accrual. It should:

1. **Amount Determination Methods**:
   - Use contract values for fixed-amount services
   - Calculate based on average historical amounts for variable expenses
   - Apply partial-period calculations (e.g., for utilities covering end of month)
   - Adjust for known seasonality or expected changes

2. **Confidence Scoring**:
   - Assign higher confidence to contract-based calculations
   - Lower confidence for estimates based on historical averages
   - Consider variance history when determining confidence level
   - Express uncertainty for first-time or unusual accruals

3. **Edge Case Handling**:
   - Handle price changes visible in recent transactions
   - Account for contract renewals or adjustments
   - Deal with irregular expenses or one-time costs

4. **Learning Capability**:
   - Improve estimation accuracy based on past variances
   - Adjust calculation methods based on feedback
   - Remember specific adjustments for particular vendors

## Documentation Agent

The Documentation Agent prepares supporting evidence for each accrual. It should:

1. **Evidence Compilation**:
   - Gather relevant historical transaction patterns
   - Link to contract terms and conditions
   - Document calculation methodology
   - Include references to prior similar accruals

2. **Audit Support**:
   - Format documentation to satisfy audit requirements
   - Provide clear explanation of reasoning
   - Include confidence assessment and potential variance
   - Document any special circumstances or considerations

3. **Visualization**:
   - Create timeline views of recurring expenses
   - Show historical accuracy of similar accruals
   - Visualize calculation methods for complex accruals

4. **Learning Capability**:
   - Improve documentation based on user feedback
   - Learn which supporting evidence is most valued
   - Adjust detail level based on materiality and user preferences

## Communication Agent

The Communication Agent prepares outreach to vendors regarding missing invoices. It should:

1. **Vendor Selection**:
   - Identify vendors with consistent billing patterns who are missing current invoices
   - Prioritize based on materiality and billing cycle reliability
   - Consider relationship history and typical response times

2. **Message Composition**:
   - Generate appropriate email drafts requesting invoice information
   - Personalize communication based on vendor relationship
   - Include relevant details about expected services and amounts
   - Maintain professional tone while conveying urgency

3. **Follow-up Tracking**:
   - Monitor responses from vendors
   - Schedule appropriate follow-up reminders
   - Update accrual status based on vendor feedback
   - Document communication history for audit purposes

4. **Learning Capability**:
   - Refine communication approach based on response rates
   - Learn optimal timing for vendor outreach
   - Adjust message style based on vendor preferences
   - Improve effectiveness of follow-up sequences

## Human-AI Collaboration

The system should enable effective collaboration between AI agents and human users:

1. **Review Process**:
   - Present accruals with clear recommendations
   - Allow for easy acceptance/rejection/modification
   - Provide visual indicators of confidence levels
   - Enable bulk operations for routine accruals

2. **Feedback Mechanism**:
   - Capture specific feedback on rejected or modified accruals
   - Allow users to provide reasoning for changes
   - Enable corrective training based on feedback
   - Track improvement over time

3. **Exception Handling**:
   - Clearly flag unusual or high-uncertainty cases
   - Explain why the system is uncertain
   - Provide options rather than single recommendations when appropriate
   - Allow user to easily override system recommendations

4. **Learning Loop**:
   - Apply feedback to improve future accruals
   - Demonstrate incremental improvement over time
   - Maintain a history of interactions to show learning
   - Explain how the system is incorporating feedback

## Example Scenarios

### Scenario 1: Regular Monthly Service
The Analysis Agent identifies that the monthly office lease payment ($4,500) for April 2025 is missing. The Calculation Agent assigns a high confidence score (95%) based on the contract information. The Documentation Agent provides the contract reference, payment history, and recommends approval.

### Scenario 2: Variable Utility Expense
The Analysis Agent notices that electricity expenses for March 2025 (typically billed around the 22nd of the following month) are not yet recorded. The Calculation Agent estimates approximately $4,580 based on historical patterns, recent trends, and seasonal factors, with a moderate confidence level (80%). The Documentation Agent provides the calculation methodology, historical accuracy of similar estimates, and notes about seasonal patterns.

### Scenario 3: Unusual Expense
The Analysis Agent identifies a potential software license renewal accrual that isn't in the transaction history. The Calculation Agent has low confidence (60%) in the estimated amount because this is a newer vendor with limited history. The Documentation Agent provides the contract information but flags this as requiring additional review.

### Scenario 4: Learning Example
After a user corrects an estimate for water utility expenses from $585 to $610, the system should record this feedback. In subsequent months, the Calculation Agent should adjust its estimation methodology for this vendor, and the Documentation Agent should note the historical adjustment when similar accruals are presented.

### Scenario 5: Vendor Communication
The Analysis Agent identifies that Marketing Masters (vendor ID: V007) consistently bills $7,500 monthly but hasn't submitted an April 2025 invoice. The Communication Agent prepares an email to the vendor's accounting contact, including reference to the contract, expected amount, and historical invoice timing. After the accounting team reviews and approves the email, it's sent to the vendor. When the vendor responds confirming the billable amount, the system updates the accrual with this confirmation and attaches the email thread as supporting documentation.
