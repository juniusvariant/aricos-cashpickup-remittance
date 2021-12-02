# Data References

Below are some list of data references that you require to use our API's.

## Remittance Statuses

Key | Description
--------- | -----------
PENDING_RISK_ASSESSMENT | Request is being processed and assessed in the risk scoring system.
COMPLIANCE_VERIFICATION | Request is considered medium or high risk, and is being reviewed by our compliance team. Our team will contact you via email for extra information for enhanced due diligence.
COMPLIANCE_REJECTED | Request is rejected by compliance.
PROCESSING | Request has been approved and the remittance is queued to be transferred to the recipient.
COMPLETED | The sending bank has confirmed transmission of the remittance.
FAILED | Remittance could not be transferred to the recipient due to certain errors. See [Remittances Failure Codes](#remittances-failure-codes).

## Remittance Failure Codes

Key | Description
--------- | -----------
INSUFFICIENT_BALANCE | The balance in your account is insufficient to make the remittance in the desired amount.
UNKNOWN_BANK_NETWORK_ERROR | The bank networks have returned an unknown error to us. We are unable to predict whether the remittance will succeed should you retry the same remittance request.
TEMPORARY_BANK_NETWORK_ERROR | The bank networks are experiencing a temporary error. Please retry the remittance in 1-3 hours.
TEMPORARY_TRANSFER_ERROR | We’ve encountered a temporary issue while processing this remittance. Please retry the remittance in 1-2 hours.
SWITCHING_NETWORK_ERROR | At least one of the switching networks is encountering an issue. Please retry the remittance in 1-3 hours.
INVALID_DESTINATION | The banks have reported that the destination account is unregistered or blocked. If unsure about this, please retry again or contact the destination bank directly regarding the status of the destination account.
TRANSFER_ERROR | We’ve encountered a fatal error while processing this remittance. Certain API fields in your request may be invalid. Please contact our customer support team for more information.

