---
layout: single
title: "Vertical Feature requirements"
author: tanp
author_profile: true
sidebar:
  nav: product
---

{% include toc %}

This page outlines the features on WPG that needs to be available for merchants as MVP in order to migrate them to Gateway 2.0 . 
The merchants analysed in this data set are simple set up merchants with direct integration only. 

### Cards

| Feature |  **Retail** | **Digital** |  **Airlines & Travel** | **Gambling** | 
| --- | --- | --- | --- | --- | 
| VISA | x | x | x | x |   
| MasterCard | x | x | x | x |
| Amex | x | x | x | | 
| Diners | |  | | |
| Discover |  |  | | | 
| JCB |  |  | | | 
| Dankort |  |  | | | 
| Carte Bleue |  |  | | | 
| Elo |  |  | | | 
| Carte Bancaire |  |  | | | 

### Integration

| **Feature** |  **Retail**  | **Digital** | **Airlines & Travel** | **Gambling** |
| --- | --- | --- | --- | --- | 
| Direct | x | x | x | x | 
| Client Side Encryption | |  |  | |
| Hosted Payment Page (HPP) | | x |  |  |
| Batch | | | | |

### Testing

| **Feature** |  **Retail**  | **Digital** |  **Airlines & Travel** | **Gambling** |
| --- | --- | --- | --- | --- |
| E2E func test environment | x | | x | |
| Performance |  | | | |

### Payment actions / updates

| **Feature** |  **Retail**  | **Digital** |  **Airlines & Travel** | **Gambling** |
| --- | --- | --- | --- | --- |
| Capture | x | x |  x | x |
| Cancel | x | x  | x | x |
| Refund (direct) | x | x | x | x |
| Customer ref for captures and refunds  | | | | x |
| Refund for APM's with no direct refund | | | | |
| Increase authorisation for tips and delivery charges | | |  | |
| Notifications | x | x | x | x |
| Inquiry | | |  | |


### Value added services 

| **Feature** |  **Retail**  | **Digital** |   **Airlines & Travel** | **Gambling** |
| --- | --- | --- | --- | --- |
| Tokenisation | x | x | x | x |
| Account updater |  |  |  |  |
| Account verification | x | x |  |  |
| IAV | | |  | |
| RMM | x | x | x | x |
| RG | | | | |
| Chargeback | x | x | x | x |
| Idempotency |  |  |  | |
| Payout | x | x | | x |
| 3DS in payment flow | x | x | x | x |
| Intelligent auth (3DS) |  | x |  | x |
| Geolocation | | |  | |
| Age + ID (IdentifyMe) |  | |  | x |
| Transaction review workflow tool  |  |  |  | |
| VISA direct |  | |  | x |
| Omni channel |  |  |  | |
| BIN Lookup |  |  |  | |
| Hosted call centre |  | x |  | |


### Mobile wallets

| **Feature** |  **Retail**  | **Digital** |   **Airlines & Travel** | **Gambling** |
| --- | --- | --- | --- | --- |
| Apple Pay |  |  |  |x |
| Google Pay |  |  |  |x |
| Samsung Pay |  |  |  |x |
| Masterpass | |  |  |  |
| Visa Checkout | |  |  | |
| Amazon Pay |  |  |  | |


### Scheme specifics 

| **Feature** |  **Retail**  | **Digital** |   **Airlines & Travel** | **Gambling** |
| --- | --- | --- | --- | --- |
| Level 2 data |  |  | | |
| Level 3 data | x  |   | x  | |
| Payment facilitator | x  |   |   | |
| Financial services (6012) data requirements |  |   |   | |
| Pre/Final authorisations |  |   |  | |
| Staged Digital Wallets |  |   |   | |
| Merchant initiated transactions  |   |   |   | |
| AVS | x  |   |  x | x |
| CVC |  x  |   |  x | x |
| AAV |  x |   | x | x |
| Extended decline codes | x  |   |   | x |
| Instalments |   |   |   | |

### APM 
#### Gold 

| **Feature** |  **Retail**  | **Digital** |   **Airlines & Travel** | **Gambling** |
| --- | --- | --- | --- | --- |
|Alipay| | | | |
|Bancontact| | | |x |
|CUP| | | | |
|iDEAL| | | | x |
|PayPal| | | | x |
|SEPA| | | | |
|Sofort| | | | x |


### Flexibility 

| **Feature** |  **Retail**  | **Digital** |   **Airlines & Travel** | **Gambling** |
| --- | --- | --- | --- | --- |
| Dynamic statement narratives | x |  | x  |x |
| Dynamic MCC |  |  |  | |
| Dynamic 3DS |   |   |   | |
| Dynamic transaction types |  |  |  | |

### Reporting 

| **Feature** |  **Retail**  | **Digital** |   **Airlines & Travel** | **Gambling** |
| --- | --- | --- | --- | --- |
| Settlement | x | | x | x |
| Chargeback | x |  | x | x |
| Portal (MAI) | x | | x | x  |
| Email delivery |  |  |  | |
| HTTP delivery | | |  | |
| SFTP delivery | | |  | |
| Pazien | |  |  | |
| Analytics | | |  | |

### Security 

| **Feature** |  **Retail**  | **Digital** |   **Airlines & Travel** | **Gambling** |
| --- | --- | --- | --- | --- |
| Basic authentication | x |  | x | x |
| Client certificate  |  |  |  | x |
