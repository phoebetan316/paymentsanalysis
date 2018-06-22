---
layout: single
title: "Payments analysis"
author: tanp
author_profile: true
sidebar:
  nav: product
---

{% include toc %}


# Overview
In order to enable data driven decision making for the payments service (both in terms of prioritisation and enabling the migration of merchants), we have to understand the usability of the payments features and the customer verticals that it serves. The objectives for this analysis work is further outlined below: 
- Provide a good migration experience from  initial comms to go live
-	Understand which customers we can board and when so we can measure customers / colleague expectations
-	Ensure that we can handle the complexity of customer integrations and ensure of API supports that complexity
-	Ensure feature prioritisation aligns to the migration merchant so we can access more merchants quickly


## Merchant Properties (WPG)
Thorough analysis on merchant's WPG properties and how it feeds into the payment features. This helps us understand what we need to build into the API to enable the boarding of different types of merchant, and prevents instances of boarding customers that we are unable to support.  
This analysis addresses a few key questions, such as: 
- What are the properties that can be applied to a merchant / admin code?
-	What do the properties do?
-	What are the configuration options?
-	Under which scenarios is the property applicable?
-	How often is each property used?
-	What impact does each property have on the API construct?


To read more about this, please navigate [here](https://github.devops.worldpay.local/pages/com-worldpay-gateway/com-worldpay-gateway-site/product/paymentsanalysis/MerchantProperties/index). 

## Currency exponents 
Analysis carried out to understand which currencies we can / should support.
This analysis will address questions below: 
-	What values can be submitted in the exponent field? 
-	How often are different exponent values used?
-	Which Worldpay supported currencies apply to each exponent?
-	Current process: GBP using currency exponent 2  

For more information, please navigate [here](https://github.devops.worldpay.local/pages/com-worldpay-gateway/com-worldpay-gateway-site/product/paymentsanalysis/PaymentsFeature/currencyexponent).


## Payment Features 
Analysis undertaken to support the prioritisation of different feature types. 
This analysis is broken down into these categories: 
- List of payments features supported today
-	Functionality of each feature and the problem it solves for merchants
-	Usage level for each feature
-	Types of merchants that use the feature


Find out more about this analysis [here](https://github.com/phoebetan316/paymentsanalysis/blob/master/paymentfeatures/index.md).


## Competitor view and future state
Analysis conducted on Worldpay's competitors in order to understand what drives merchants to move to or away from Worldpay and the differentiating factors (e.g. Ease of integration / features supported). 
This analysis will address these questions: 
-	Who are our main competitors?
-	What’s different about their implementation of features which Worldpay supports?
-	What do they support that Worldpay doesn’t?
-	What do our merchants dislike about our implementation of features and why?
-	What features are difficult for Worldpay to support and why? 


For more information please refer to this [page](). 

## Conclusion 

This will be the summary of the analysis and the findings that the team produced. Please click [here]()





