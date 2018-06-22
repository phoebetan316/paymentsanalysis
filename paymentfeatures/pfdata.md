---
layout: single
title: "Payment Facilitator rules"
author: tanp
author_profile: true
sidebar:
  nav: product
---
{% include toc %}
## What is a payment facilitator? 
A Payment Facilitator (formerly Payment Service Provider) is a third party agent that may:
*    Sign a merchant acceptance agreement on behalf of an acquirer
*    Receive settlement of transaction proceeds from an acquirer, on behalf of a sub-merchant
A sub-merchant is a merchant whose payment services are provided by a Payment Facilitator. 
An [ISO](https://usa.visa.com/content/dam/VCOM/download/merchants/tpa-registration-program-faqs.pdf) (independent selling organisation/ member service provider) acts as an authorised agent for the bank to market merchant accounts and is also directly registered with both Visa and MasterCard. ISOs tend to resell the products or services of one or multiple acquirers, hence are able to provide merchants with a wider variety of solutions compared to the acquirers themselves. They can also develop their own or aggregate other value added products and services. 
Refer [here](https://storekit.com/advice/uk-payments-industry/) for a list of ISOs and Payment Facilitators.
![](https://github.devops.worldpay.local/pages/com-worldpay-gateway/com-worldpay-gateway-site/product/paymentsanalysis/PaymentsFeature/payments_pathway(PFv2).png)
Most [card schemes](https://usa.visa.com/dam/VCOM/download/merchants/02-MAY-2014-Visa-Payment-FacilitatorModel.pdf) establish a clear set of responsibilities for all program participants as outlined in the
following table: 
| Participant |  Key Responsibilities | 
| --- | --- | 
| Acquirer  | {::nomarkdown}<li>Contracts with a Payment Facilitator to enable sponsorship of merchants</li>  <li>Monitors compliance of Payment Facilitator in accordance with scheme rules</li>  <li>Conducts due diligence of Payment Facilitator and ensures proper due diligence occurs during the signing of sub-merchants</li>{:/} | 
| Payment Facilitator | {::nomarkdown}<li>Contracts with an acquirer to provide payment services to sub-merchants</li> <li>Contracts with sub-merchants to enable payment acceptance</li> <li>Monitors compliance of sub-merchant activity in accordance with the scheme rules</li> <li>Receives settlement of transaction proceeds from the acquirer on behalf of the sub-merchant</li>{:/} | 
| Sub-Merchant | {::nomarkdown}<li>Contracts with a Payment Facilitator</li> <li>Sells products and services to cardholders of various card schemes</li> <li>Accepts scheme products as payment</li>{:/} | 
When the cardholder makes a purchase, the sub-merchant routes the transaction data to the payment facilitator. The payment facilitator incorporates all necessary transaction and merchant identification data and sends this to the acquirer.
 Payment facilitators must send the additional `subMerchantData` covered on [this page](http://support.worldpay.com/support/kb/gg/corporate-gateway-guide/content/industryschemeextras/paymentfacilitatorrules.htm) with all transactions except refunds.
## SubMerchantData
Example of SubMerchantData: 
```XML
<subMerchantData>
  <pfId>208431</pfId>
  <isoId>208431</isoId>
  <subName>Eleven Finland OY</subName>
  <subId>32971</subId>
  <subStreet>Itamerenkatu 5</subStreet>
  <subCity>Helsinki</subCity>
  <subCountryCode>246</subCountryCode>
  <subPostalCode>00180</subPostalCode>
</subMerchantData>
```
Based on the [WPG guide](http://support.worldpay.com/support/kb/gg/corporate-gateway-guide/content/industryschemeextras/paymentfacilitatorrules.htm#Children) `pfId` is mandatory whilst `isoId` is conditional. However most of the data supplied for the fields seem to indicate that the service provider/agent is usually both a payment facilitator and an ISO at the same time. 
<iframe height="650" width="480" frameborder="0" src="https://logsearch.worldpay.local/en-GB/embed?s=%2FservicesNS%2Fnobody%2Fsearch%2Fsaved%2Fsearches%2Fpayment%2520facilitator%2520ID%2520and%2520ISO%2520ID%2520data&oid=S5qLREp4PNbxq7_SY8df1P_smI7H6zZMTeYRSsDDly3fKrKr7L8sQXZsRtpe2U9HxR%5E0A%5EbVt7Qm9RCXxvKNaGosxE3T3rCkEHh4rBM8NnpAYuOiqUev_JNGO9ihPS3IDsr6PB6OgTWyfBNuMG8ShUtljx69KXSILJiEopTgxNfMUvxt"></iframe>
### Content of SubMerchantData
| Element  |    Format |    M/O/C        | Description                             | 
| -------- | ------- | ------------| ----------------------------------------| 
| `pfId`   |    0-9    | Mandatory   |  Payment facilitator ID -obtained from Mastercard |
| `isoId`  |    0-9    | Conditional | Independent Sales Organisation (ISO) ID provided by Mastercard. If an ISO is involved in the transaction, merchants must send this information. Both the `pfId` and `isoId` are unique to the Service Provider/Agent that is registered with Mastercard. If the Service Provider/Agent is both a payment facilitator and an ISO, then upon registration the same ID is assigned as the `pfId` and `isoId`. | 
## How it currently works on WPG 
### Backoffice Configuration
| Merchant properties | Description  | 
| --- | --- | 
|  excludeFromPaymentFacilitatorMandate | This particular merchant code allows PFs to submit orders without including submerchant data | 
### Live test transaction
#### pfId
XML Request with 
```XML
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE paymentService PUBLIC "-//WorldPay//DTD WorldPay PaymentService v1//EN" "http://dtd.worldpay.com/paymentService_v1.dtd">
<paymentService version="1.4" merchantCode="STUPRODTESTMC1">
 <submit>
  <order orderCode="jsxml372829237887">
   <description>test order</description>
   <amount value="100" currencyCode="GBP" exponent="2"/>
   <orderContent>
    <![CDATA[]]>
   </orderContent>
   <paymentDetails>
    <CARD-SSL>
     <cardNumber>4444333322221111</cardNumber>
     <expiryDate>
      <date month="06" year="2019"/>
     </expiryDate>
     <cardHolderName>Test User</cardHolderName>
     <cvc>777</cvc>
     <cardAddress>
      <address>
       <firstName>Test</firstName>
       <address1>25 Walbrook</address1>
       <address2>London</address2>
       <address3>London</address3>
       <postalCode>EC4N 8AF</postalCode>
       <city>London</city>
       <countryCode>GB</countryCode>
      </address>
     </cardAddress>
    </CARD-SSL>
    <session shopperIPAddress="127.0.0.1" id="ssn728292187"/>
   </paymentDetails>
   <shopper>
    <shopperEmailAddress>phoebe.tan@worldpay.com</shopperEmailAddress>
    <browser>
     <acceptHeader>text/html</acceptHeader>
     <userAgentHeader>Mozilla/5.0 ...</userAgentHeader>
    </browser>
   </shopper>
   <subMerchantData> 
     <pfId>12345678901</pfId>
     <subName>Example Shop</subName>
        <subId>1234567</subId>
        <subStreet>123 Street</subStreet>
        <subCity>San Francisco</subCity>
        <subState>CA</subState>
        <subCountryCode>840</subCountryCode>
        <subPostalCode>94101</subPostalCode>
        <subTaxId>987-65-4321</subTaxId>
   </subMerchantData>
  </order>
 </submit>
</paymentService>
```
XML response 
```XML
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE paymentService PUBLIC "-//WorldPay//DTD WorldPay PaymentService v1//EN"
                                "http://dtd.worldpay.com/paymentService_v1.dtd">
<paymentService version="1.4" merchantCode="STUPRODTESTMC1"><reply><orderStatus orderCode="jsxml372829237887"><payment><paymentMethod>VISA_DEBIT-SSL</paymentMethod><paymentMethodDetail><card number="444433******1111" type="debitcard"/></paymentMethodDetail><amount value="100" currencyCode="GBP" exponent="2" debitCreditIndicator="credit"/><lastEvent>AUTHORISED</lastEvent><CVCResultCode description="APPROVED"/><balance accountType="IN_PROCESS_AUTHORISED"><amount value="100" currencyCode="GBP" exponent="2" debitCreditIndicator="credit"/></balance></payment><token><tokenDetails tokenEvent="MATCH"><paymentTokenID>99465859158201425023</paymentTokenID><paymentTokenExpiry><date dayOfMonth="21" month="06" year="2022" hour="11" minute="36" second="09"/></paymentTokenExpiry><tokenReason>Created during order: jsxml372829237887</tokenReason></tokenDetails><paymentInstrument><cardDetails><expiryDate><date month="06" year="2019"/></expiryDate><cardHolderName><![CDATA[TEST USER]]></cardHolderName><cardAddress><address><address1>25 Walbrook</address1><address2>London</address2><address3>London</address3><postalCode>EC4N 8AF</postalCode><city>London</city><countryCode>GB</countryCode></address></cardAddress><derived><cardBrand>VISA</cardBrand><cardSubBrand>VISA_DEBIT</cardSubBrand><issuerCountryCode>GB</issuerCountryCode><obfuscatedPAN>4444********1111</obfuscatedPAN></derived></cardDetails></paymentInstrument></token></orderStatus></reply></paymentService>
```
#### isoId
XML request 
```XML
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE paymentService PUBLIC "-//WorldPay//DTD WorldPay PaymentService v1//EN" "http://dtd.worldpay.com/paymentService_v1.dtd">
<paymentService version="1.4" merchantCode="STUPRODTESTMC1">
 <submit>
  <order orderCode="jsxml2829237887">
   <description>test order</description>
   <amount value="100" currencyCode="GBP" exponent="2"/>
   <orderContent>
    <![CDATA[]]>
   </orderContent>
   <paymentDetails>
    <CARD-SSL>
     <cardNumber>4444333322221111</cardNumber>
     <expiryDate>
      <date month="06" year="2019"/>
     </expiryDate>
     <cardHolderName>Test User</cardHolderName>
     <cvc>777</cvc>
     <cardAddress>
      <address>
       <firstName>Test</firstName>
       <address1>25 Walbrook</address1>
       <address2>London</address2>
       <address3>London</address3>
       <postalCode>EC4N 8AF</postalCode>
       <city>London</city>
       <countryCode>GB</countryCode>
      </address>
     </cardAddress>
    </CARD-SSL>
    <session shopperIPAddress="127.0.0.1" id="ssn728292187"/>
   </paymentDetails>
   <shopper>
    <shopperEmailAddress>phoebe.tan@worldpay.com</shopperEmailAddress>
    <browser>
     <acceptHeader>text/html</acceptHeader>
     <userAgentHeader>Mozilla/5.0 ...</userAgentHeader>
    </browser>
   </shopper>
   <subMerchantData> 
     <pfId>12345678901</pfId>
     <isoId>12345678901</isoId>
     <subName>Example Shop</subName>
        <subId>1234567</subId>
        <subStreet>123 Street</subStreet>
        <subCity>San Francisco</subCity>
        <subState>CA</subState>
        <subCountryCode>840</subCountryCode>
        <subPostalCode>94101</subPostalCode>
        <subTaxId>987-65-4321</subTaxId>
   </subMerchantData>
  </order>
 </submit>
</paymentService>
```
XML response 
```XML
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE paymentService PUBLIC "-//WorldPay//DTD WorldPay PaymentService v1//EN"
                                "http://dtd.worldpay.com/paymentService_v1.dtd">
<paymentService version="1.4" merchantCode="STUPRODTESTMC1"><reply><orderStatus orderCode="jsxml2829237887"><payment><paymentMethod>VISA_DEBIT-SSL</paymentMethod><paymentMethodDetail><card number="444433******1111" type="debitcard"/></paymentMethodDetail><amount value="100" currencyCode="GBP" exponent="2" debitCreditIndicator="credit"/><lastEvent>AUTHORISED</lastEvent><CVCResultCode description="APPROVED"/><balance accountType="IN_PROCESS_AUTHORISED"><amount value="100" currencyCode="GBP" exponent="2" debitCreditIndicator="credit"/></balance></payment><token><tokenDetails tokenEvent="MATCH"><paymentTokenID>99465859158201425023</paymentTokenID><paymentTokenExpiry><date dayOfMonth="21" month="06" year="2022" hour="11" minute="36" second="09"/></paymentTokenExpiry><tokenReason>Created during order: jsxml372829237887</tokenReason></tokenDetails><paymentInstrument><cardDetails><expiryDate><date month="06" year="2019"/></expiryDate><cardHolderName><![CDATA[TEST USER]]></cardHolderName><cardAddress><address><address1>25 Walbrook</address1><address2>London</address2><address3>London</address3><postalCode>EC4N 8AF</postalCode><city>London</city><countryCode>GB</countryCode></address></cardAddress><derived><cardBrand>VISA</cardBrand><cardSubBrand>VISA_DEBIT</cardSubBrand><issuerCountryCode>GB</issuerCountryCode><obfuscatedPAN>4444********1111</obfuscatedPAN></derived></cardDetails></paymentInstrument></token></orderStatus></reply></paymentService>
```
### Errors 
List of errors can be found [here](http://support.worldpay.com/support/kb/gg/corporate-gateway-guide/content/industryschemeextras/paymentfacilitatorrules.htm#Errors). 
## How it currently works on HCG
### 
