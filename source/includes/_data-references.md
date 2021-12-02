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

## Account Codes

Key | Description
--------- | -----------
ACEH | BPD Aceh
ACEH_UUS |	BPD Aceh UUS
AGRIS |	Bank Agris
AGRONIAGA |	Bank BRI Agroniaga
AMAR | Bank Amar Indonesia (formerly Anglomas International Bank)
ANZ | Bank ANZ Indonesia
ARTA_NIAGA_KENCANA |	Bank Arta Niaga Kencana
ARTHA | Bank Artha Graha International
ARTOS | Bank Artos Indonesia
BALI | BPD Bali
BAML | Bank of America Merill-Lynch
BANGKOK	| Bangkok Bank
BANTEN	| BPD Banten (formerly Bank Pundi Indonesia)
BCA	| Bank Central Asia (BCA)
BCA_DIGITAL	| Bank Central Asia Digital (BluBCA)
BCA_SYR	| Bank Central Asia (BCA) Syariah
BENGKULU | BPD Bengkulu
BISNIS_INTERNASIONAL | Bank Bisnis Internasional
BJB | Bank BJB
BJB_SYR | Bank BJB Syariah
BNI | Bank Negara Indonesia (BNI)
BNI_SYR | Bank BNI Syariah
BNP_PARIBAS | Bank BNP Paribas
BOC | Bank of China (BOC)
BRI | Bank Rakyat Indonesia (BRI)
BRI_SYR | Bank Syariah BRI
BSI | Bank Syariah Indonesia (BSI)
BTN | Bank Tabungan Negara (BTN)
BTN_UUS | Bank Tabungan Negara (BTN) UUS
BTPN_SYARIAH | BTPN Syariah (formerly Bank Sahabat Purba Danarta and Bank Tabungan Pensiunan Nasional UUS)
BUKOPIN | Bank Bukopin
BUKOPIN_SYR | Bank Syariah Bukopin
BUMI_ARTA | Bank Bumi Arta
CAPITAL | Bank Capital Indonesia
CCB | China Construction Bank Indonesia (formerly Bank Antar Daerah and Bank Windu Kentjana Int)
CENTRATAMA | Centratama Nasional Bank
CHINATRUST | Bank Chinatrust Indonesia
CIMB | Bank CIMB Niaga
CIMB_UUS | Bank CIMB Niaga UUS
CITIBANK | Citibank
COMMONWEALTH | Bank Commonwealth
DAERAH_ISTIMEWA | BPD Daerah Istimewa Yogyakarta (DIY)
DAERAH_ISTIMEWA_UUS | BPD Daerah Istimewa Yogyakarta (DIY) UUS
DANAMON | Bank Danamon
DANAMON_UUS | Bank Danamon UUS
DBS | Bank DBS Indonesia
DEUTSCHE | Deutsche Bank
DINAR_INDONESIA | Bank Dinar Indonesia
DKI | Bank DKI
DKI_UUS | Bank DKI UUS
EXIMBANK | Indonesia Eximbank (formerly Bank Ekspor Indonesia)
FAMA | Bank Fama International
GANESHA | Bank Ganesha
GOPAY | GoPay
HANA | Bank Hana
HARDA_INTERNASIONAL | Bank Harda Internasional
HSBC | Hongkong and Shanghai Bank Corporation (HSBC) (formerly Bank Ekonomi Raharja)
ICBC | Bank ICBC Indonesia
INA_PERDANA | Bank Ina Perdania
INDEX_SELINDO | Bank Index Selindo
INDIA | Bank of India Indonesia
JAMBI | BPD Jambi
JAMBI_UUS | BPD Jambi UUS
JASA_JAKARTA | Bank Jasa Jakarta
JAWA_TENGAH | BPD Jawa Tengah
JAWA_TENGAH_UUS | BPD Jawa Tengah UUS
JAWA_TIMUR | BPD Jawa Timur
JAWA_TIMUR_UUS | BPD Jawa Timur UUS
JPMORGAN | JP Morgan Chase Bank
JTRUST | Bank JTrust Indonesia (formerly Bank Mutiara)
KALIMANTAN_BARAT | BPD Kalimantan Barat
KALIMANTAN_BARAT_UUS | BPD Kalimantan Barat UUS
KALIMANTAN_SELATAN | BPD Kalimantan Selatan
KALIMANTAN_SELATAN_UUS | BPD Kalimantan Selatan UUS
KALIMANTAN_TENGAH | BPD Kalimantan Tengah
KALIMANTAN_TIMUR | BPD Kalimantan Timur
KALIMANTAN_TIMUR_UUS | BPD Kalimantan Timur UUS
KESEJAHTERAAN_EKONOMI | Bank Kesejahteraan Ekonomi
LAMPUNG | BPD Lampung
MALUKU | BPD Maluku
MANDIRI | Bank Mandiri
MANDIRI_ECASH | Mandiri E-Cash
MANDIRI_SYR	Bank | Syariah Mandiri
MANDIRI_TASPEN | Mandiri Taspen Pos (formerly Bank Sinar Harapan Bali)
MASPION | Bank Maspion Indonesia
MAYAPADA | Bank Mayapada International
MAYBANK | Bank Maybank (formerly BII)
MAYBANK_SYR | Bank Maybank Syariah Indonesia
MAYORA | Bank Mayora
MEGA| Bank Mega
MEGA_SYR | Bank Syariah Mega
MESTIKA_DHARMA | Bank Mestika Dharma
MITRA_NIAGA | Bank Mitra Niaga
MITSUI | Bank Sumitomo Mitsui Indonesia
MIZUHO | Bank Mizuho Indonesia
MNC_INTERNASIONAL | Bank MNC Internasional
MUAMALAT | Bank Muamalat Indonesia
MULTI_ARTA_SENTOSA | Bank Multi Arta Sentosa
NATIONALNOBU | Bank Nationalnobu
NUSA_TENGGARA_BARAT	BPD | Nusa Tenggara Barat
NUSA_TENGGARA_BARAT_UUS | BPD Nusa Tenggara Barat UUS
NUSA_TENGGARA_TIMUR	BPD | Nusa Tenggara Timur
NUSANTARA_PARAHYANGAN | Bank Nusantara Parahyangan
OCBC | Bank OCBC NISP
OCBC_UUS | Bank OCBC NISP UUS
OKE | Bank Oke Indonesia (formerly Bank Andara)
OVO | OVO
PANIN | Bank Panin
PANIN_SYR | Bank Panin Syariah
PAPUA | BPD Papua
PERMATA | Bank Permata
PERMATA_UUS | Bank Permata UUS
PRIMA_MASTER | Prima Master Bank
QNB_INDONESIA | Bank QNB Indonesia (formerly Bank QNB Kesawan)
RABOBANK | Bank Rabobank International Indonesia
RBS | Royal Bank of Scotland (RBS)
RESONA | Bank Resona Perdania
RIAU_DAN_KEPRI | BPD Riau Dan Kepri
RIAU_DAN_KEPRI_UUS | BPD Riau Dan Kepri UUS
ROYAL | Bank Royal Indonesia
SAHABAT_SAMPOERNA | Bank Sahabat Sampoerna
SBI_INDONESIA | Bank SBI Indonesia
SHINHAN | Bank Shinhan Indonesia (formerly Bank Metro Express)
SINARMAS | Sinarmas
SINARMAS_UUS | Bank Sinarmas UUS
STANDARD_CHARTERED | Standard Chartered Bank
SULAWESI | BPD Sulawesi Tengah
SULAWESI_TENGGARA | BPD Sulawesi Tenggara
SULSELBAR | BPD Sulselbar
SULSELBAR_UUS | BPD Sulselbar UUS
SULUT | BPD Sulut
SUMATERA_BARAT | BPD Sumatera Barat
SUMATERA_BARAT_UUS | BPD Sumatera Barat UUS
SUMSEL_DAN_BABEL | BPD Sumsel Dan Babel
SUMSEL_DAN_BABEL_UUS | BPD Sumsel Dan Babel UUS
SUMUT | BPD Sumut
SUMUT_UUS | BPD Sumut UUS
TABUNGAN_PENSIUNAN_NASIONAL | Bank Tabungan Pensiunan Nasional
TOKYO | Bank of Tokyo Mitsubishi UFJ
UOB | Bank UOB Indonesia
VICTORIA_INTERNASIONAL | Bank Victoria Internasional
VICTORIA_SYR | Bank Victoria Syariah
WOORI | Bank Woori Saudara Indonesia (formerly Bank Himpunan Saudara and Bank Woori Indonesia)
YUDHA_BHAKTI | Bank Yudha Bhakti

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