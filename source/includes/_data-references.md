# Data References

Below are some list of data references that you require to use our API's.

## Agent Codes

ID | Key | Description
--------- | --------- | -----------
0620b618-b2ab-46cf-ab23-679a78945b5e | POS | POS Indonesia

## Purpose Codes

Key | Description
--------- | -----------
SELF | Transfer to own account
FAMILY | Family Maintenance
EDUCATION | Education-related student expenses
MEDICAL | Medical Treatment
HOTEL | Hotel Accomodation
TRAVEL | Travel
UTILITIES | Utility Bills
LOAN_REPAYMENT | Repayment of Loans
TAX_PAYMENT | Tax Payment
RESIDENCE_PURCHASE | Purchase of Residential Property
RESIDENCE_RENT | Payment of Property Rental
INSURANCE | Insurance
MUTUAL_FUND | Mutual Fund Investment
SHARES_INVESTMENT | Investment in Shares
DONATIONS | Donations
ADVERTISING | Advertising & Public relations-related expenses
ROYALTY_FEES | Royalty fees, trademark fees, patent fees, and copyright fees
BROKER_FEES | Fees for brokers, front end fee, commitment fee, guarantee fee and custodian fee
ADVISORS | Fees for advisors, technical assistance, and academic purpose, including remuneration for specialists
OFFICE | Representative office expenses
CONSTRUCTION | Construction costs / expenses
SHIPMENT | Transportation fees for goods
EXPORT | For payment of exported goods
DELIVERY | Delivery fees for goods
TRADES | General Goods Trades - Offline trade
SALARY | Salary
REFUND | Refund
LOAN | Loan

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

## Identification Codes

Key | Description
--------- | -----------
KTP | Kartu Tanda Penduduk (national identity card number) of the customer
NPWP | Nomor Pokok Wajib Pajak (tax number) of the customer
SIM | Surat Izin Mengemudi (driver’s licence) of the customer
PASSPORT | Passport of the customer
OTHER | Other identification type of the customer

## Occupation Codes

Key | Desc
--------- | -----------
OTHERS | OTHERS
STUDENT | STUDENT
HOUSEWIFE | HOUSEWIFE
ENTERPRENEUR | ENTERPRENEUR
PRIVATE_EMPLOYEES | PRIVATE EMPLOYEES
STATE_EMPLOYEES | STATE EMPLOYEES
ARMY | ARMY
POLICE | POLICE
LECTURER | LECTURER
TEACHER | TEACHER
DOCTOR | DOCTOR
MIDWIFE | MIDWIFE
NURSE | NURSE
MEMBER_OF_HOUSE_REPRESENTATIVE | MEMBER OF HOUSE REPRESENTATIVE
FARMER | FARMER
BREEEDER | BREEEDER
FISHERMAN | FISHERMAN
HOUSEMAID | HOUSEMAID
LABOR | LABOR
DRIVER | DRIVER
TRADER | TRADER
FARM_WORKERS | FARM WORKERS
STOCKMAN | STOCKMAN
BARBER | BARBER
ELECTRICIAN | ELECTRICIAN
STONEMASON | STONEMASON
CARPENTER | CARPENTER
COBBLER | COBBLER
BLACKSMITH | BLACKSMITH
TAILOR | TAILOR
MECHANIC | MECHANIC
DENTIST | DENTIST
ARTIST | ARTIST
TRADITIONAL_HEALER | TRADITIONAL HEALER
TRADITIONA_MIDWIFE | TRADITIONA MIDWIFE
HAIRDRESSER | HAIRDRESSER
MAKEUP_ARTIST | MAKEUP ARTIST
FASHION_DESIGNER | FASHION DESIGNER
FASHION_DESIGNER | FASHION DESIGNER
JOURNALIST | JOURNALIST
CHEF | CHEF
PROMOTOR | PROMOTOR
TRANSLATOR | TRANSLATOR
RELIGIOUS_LEADER | RELIGIOUS LEADER
PENSIONARY | PENSIONARY
CONSTRUCTION | CONSTRUCTION
TRANSPORTATION | TRANSPORTATION
AMBASSADOR | AMBASSADOR
PILOT | PILOT
LAWYER | LAWYER
NOTARY_PUBLIC | NOTARY PUBLIC
ARCHITECT | ARCHITECT
ACCOUNTANT | ACCOUNTANT
CONSULTANT | CONSULTANT
PHARMACIST | PHARMACIST
PSYCHIATRIST | PSYCHIATRIST
TV_ANNOUNCER | TV ANNOUNCER
RADIO_ANNOUNCER | RADIO ANNOUNCER
SAILOR | SAILOR
RESEARCHER | RESEARCHER
BROKER | BROKER

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
