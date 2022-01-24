# Data References

Below are some list of data references that you require to use our API's.

## Remittance Statuses

Key | Description
--------- | -----------
COMPLETED | The sending transaction has confirmed transmission of the remittance.
FAILED | Remittance could not be transferred to the recipient due to certain errors.

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

## Agent Codes

ID | Key | Description
--------- | --------- | -----------
0620b618-b2ab-46cf-ab23-679a78945b5e | POS | POS Indonesia

## Source of Funds

Key | Description
--------- | -----------
INVESTMENT | Bonds, fixed deposits, preference shares, business ownership/equity or property ownership
PERSONAL_SAVINGS | Funds kept in an account in a bank or a similar organization
BUSINESS_REVENUE | Income from a business or a company
LEGACY | Inherited money from a will
BUSINESS_ARRANGEMENT | Any understanding, procedure, course of dealing, or arrangement between a creditor and a seller
LOAN | A sum of money that is borrowed
SALARY | A fixed regular payment made by an employer
OTHER | Other
