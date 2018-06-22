---
layout: single
title: "Payments Feature analysis"
author: tanp
author_profile: true
sidebar:
  nav: product
---
{% include toc %}

At present, Worldpay supports a large variety of features on it's existing payment gateways. This analysis is undertaken to understand the breadth and depth of the features currently offered by both WPG and HCG, and how this could be translated across to Gateway 2.0's Access Worldpay strategy to prioritise and build out features to support customer migrations. 

## Payment features supported today 
For the full list of existing features supported by Worlday's payment gateways, navigate [here](https://github.devops.worldpay.local/pages/com-worldpay-gateway/com-worldpay-gateway-site/product/gatewayanalysis).
## Payment features - functionality and usability 
This section addresses these key questions: 
- What does each feature do? 
- What problem does it solve
- what value does it add for our merchants?

|Features | Description | Use case | 
|---|---|---|
| Authentication: AVS | [Address verification (AVS)](http://support.worldpay.com/support/kb/bg/riskmanagement/rmm7015.html) is performed by comparing the billing address from the request message with address data on file at the issuing bank. | Deters fraudulent activity for non-face-to-face transactions and greatly reduces the merchant’s risk of a chargeback. Most fraudsters that have obtained card data do not have the real cardholder's address so this is a useful check. |
| Authentication: AAV |  [AAV]() is a service set up by American Express for their card transactions. It checks the cardholder name, the telephone number, and the email address (entered by the shopper) against the equivalent records held by American Express.  | Allows the  merchant to assess the risk associated with a transaction  | 
| Authentication: CVC | Card Verification Code (CVC) is an extra code printed on a debit or credit card. It is usually the final three digits of the number printed on the signature strip on the reverse of a card. On AMEX cards, it is usually a four digit code on the front. | Supplying the CVC code in a transaction is intended to verify that the customer has the card in their possession, thereby reducing the possibility of fraud and limiting chargebacks | 
| Shopper Browser information | The Shopper's IP address and Shopper's IP country  |  merchants can cross-reference the country displayed in the shopper's IP country field against the country displayed in the Customer's Address. If this is not a match, the merchant can investigate the transaction, flag it as high risk or block further transactions from the IP address if they suspect it as fraudulent. | 
| 3DS | 3DS is an XML-based protocol designed to be an additional security layer for online credit and debit card transactions | Decreases risk by requiring customers to enter an additional password which cannot be copied off their card and by reducing risk from security incidents at online merchants since the merchant does not capture the password. | 
| [Tokenisation: `Create` - with payment](https://github.devops.worldpay.local/pages/com-worldpay-gateway/com-worldpay-gateway-site/product/paymentsanalysis/PaymentsFeature/CreateTokens/index) | Tokenization is the process of protecting sensitive data by replacing it with an algorithmically generated number called a token. | Protect customer's sensitive information and prevent credit card fraud. Tokenization presents a more secure way of transmitting customer data and helps merchants defend their business from a potential data breach. | 
| [Tokenisation: `Create` - without payment](https://github.devops.worldpay.local/pages/com-worldpay-gateway/com-worldpay-gateway-site/product/paymentsanalysis/PaymentsFeature/CreateTokens/index) | If a shopper adds a credit or debit card to their account, merchants can store the details as a token by creating a token without a payment request. | Storing card details as a token also provides a more streamlined shopping experience for the customer as they would not have to repeat the process for consecutive purchases and this results in a higher sales conversion rate for the merchant. | 
| [Dynamic statement narrative](https://github.devops.worldpay.local/pages/com-worldpay-gateway/com-worldpay-gateway-site/product/paymentsanalysis/PaymentsFeature/DynamicStatementNarrative/index) | A unique reference that is  placed against transactions on the shopper's bank statement. This can be a dynamic value based on the merchant's configuration settings in WPG or MERLIN.  | Provide a better customer experience with statement narratives that reflect the name of the merchant's subsidiary companies, local outlets, or, if the merchant is a payment service provider, the sub- merchants.  |  
| Dynamic MCC  | If merchants have multiple merchant category codes, the `dynamicMCC` element lets them send a different merchant category code per transaction. | MCCs can have an effect on whether credit card payments are accepted by Issuing Bank. Having the right MCCs can increase payment conversion rates and reduce merchant processing fees whilst ensuring the merchant remains compliant with scheme rules. | 
| Capture delay override  | A [capture delay](http://support.worldpay.com/support/kb/bg/businessmanager/wh0145.htm) is the delay between authorisation and when a capture message is sent. Capture delay override allows a merchant to dynamically override this configuration. |  | 
| Dynamic 3DS | Dynamic 3DS (D3DS) offers merchants control over their payment security by targeting areas where acceptance can be improved    | By optimising D3DS, merchants can improve their transaction acceptance rates and lower chargebacks while ensuring a smooth customer experience as it allows lower-risk consumers to pay much more easily. |
| [Payment facilitator rules](https://github.devops.worldpay.local/pages/com-worldpay-gateway/com-worldpay-gateway-site/product/paymentsanalysis/PaymentsFeature/PayFacRules) | Payment facilitators (PayFac) take the role of a service provider, and would incorporate all necessary transaction and merchant identification data to be sent on to the acquirer. Sub-merchant data is mandatory on any merchant code flagged as a PayFac, hence merchants will receive an error if this data isn't supplied. |  Ensures compliance with MasterCard/any other card scheme's mandate for this data | 

## WPG Payment features requirement by eCommerce vertical 
For more details on feature requirements by vertical please refer to this [page](https://github.devops.worldpay.local/pages/com-worldpay-gateway/com-worldpay-gateway-site/product/paymentsanalysis/PaymentsFeature/VerticalFeatureRequirements/).

## Gap analysis 
This section addresses these key areas: 
* features currently available on WPG and HCG
* new features that can be built as a microservice to support HCG customer migration or enable cross-selling to VAP. 
For more details please refer to these links: 
*  [HCG](https://github.devops.worldpay.local/pages/com-worldpay-gateway/com-worldpay-gateway-site/product/paymentsanalysis/PaymentsFeature/HCG/index) 
*  [VAP](https://github.devops.worldpay.local/pages/com-worldpay-gateway/com-worldpay-gateway-site/product/paymentsanalysis/PaymentsFeature/VAP/index)
 

## Customer pipeline for migration based on features
This section outlines the pilot customers that can be targeted in the migration to GW2.0 and/or WPG. 
* [HCG Customer Matrix](https://github.devops.worldpay.local/pages/com-worldpay-gateway/com-worldpay-gateway-site/product/paymentsanalysis/PaymentsFeature/HCGCustomerMatrix)
### Related links 
* [Customer engagement](https://github.devops.worldpay.local/pages/com-worldpay-gateway/com-worldpay-gateway-site/customer/engagement/)
* [Customer model](https://github.devops.worldpay.local/pages/com-worldpay-gateway/com-worldpay-gateway-site/product/customeranalysis)
