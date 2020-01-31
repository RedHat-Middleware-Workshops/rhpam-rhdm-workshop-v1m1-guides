# Use Case Overview

You are a business automation specialist consultant who was hired by a credit card issuer company, Pecunia Corp. They need you to automate a critical scenario: the _Credit Card Dispute_.

A credit card dispute is initiated by a credit card owner whenever there is a non-recognized transaction or an incorrect charge.

You should be able to automate the process by creating a flexible process and by automating the decision logic using a more natural language.

## Business Background

Pecunia Corp. is a credit card issuer company going through digital transformation. It is now adopting business automation to improve the performance of internal processes, reduce costs and increase customer satisfaction.

To better understand the scenario of a credit card dispute and the existing gaps, first let's take a look at the involved **actors**:

- _Credit Card Holder_: aka Customer;
- _Credit Card Issuer_: In this case, Pecunia Corp.;
- _Card processing network_: The credit card network processes transactions between merchants and cc issuers;
- _Credit Card Acquirer_: A financial institution that obtains the rights to the merchant’s account and tasked with getting payment on the merchant’s behalf; It facilitates the credit transaction by intermediating issuer and merchant.
- _Merchant_: Seller of the goods and must either fight or accept the chargeback.

With that in mind, let's talk about the internal **processing** and **decisions** that happens when a CC Holder (customer) opens a new credit card dispute:

1. New Dispute created: The Credit Card Holder starts a dispute with the CC Issuer.

2. Define type of processing: The CC Issuer needs to decide what type of processing is required for the dispute (automated chargeback or normal processing). _This decision either leads to step 2.1. or 2.2._

    2.1. Automated processing: the CC Issuer process the automated chargeback. _This leads to step 5.1._

    2.2. Standard Processing: The CC Issuer needs to do standard processing. A risk assessment for the dispute is required.

3. Risk Assessment: CC Issuer assesses the risk of the dispute based on the provided data (credit card holder status, dispute amount, etc.).

    3.1. Needs approval: The CC Issuer requests a manual approval for the dispute from a knowledge worker. _This can lead to step 4.1. or 4.2_

    3.2. Issue Resolved: The CC Issuer based on the data resolves the case by either accepting or rejecting the dispute. _This can lead to step 4.1. or 4.2_

4. Dispute is resolved

    4.1. Dispute accepted: The dispute is accepted and the money reimbursed to the CC Holder and the backoffice chargeback for fee transactions started.

    4.2. Dispute Rejected: The dispute is rejected.

5. Send Notification: The CC Issuer informs the CC Holder of the result.

Most of the complexity with the CC Dispute process comes from the fact that is a multi-step process where every dispute is a one-off situation, the actual outcome of the dispute is a result of the interactions between the different actors and the decision logic. On top of that, the information regarding the case should be available with every interaction. Everyone needs to look at the same data and be observers of updates in it.

### Decision Automation

On the step two, the _CC Issuer_ should analyse a set of data in order to define if the dispute can be automatically processed or not. This is a repeatable decision that is currently being made manually for every dispute.

Pecunia Corp. wants to give benefits to strategic customers by creating a loyalty program. The risk can be defined based on the loyalty level and on the dispute value, an automatic chargeback can be made, leading to a faster response to customers and lower costs on the overall process.

This is the set of rules that can be used to determine the risk involved on the transaction:

- _For a standard customer, and a dispute amount between 0 and 100, the risk is low._
- _For a standard customer, and a dispute amount between 100 and 500, the risk is medium_
- _For a standard customer, and a dispute amount above 500, the risk is high._
- _For a silver customer, and a dispute amount below 250, the risk is low._
- _For a silver customer, and a dispute amount between 250 and 500, the risk is medium._
- _For a silver customer, and a dispute amount above 500, the risk is high._
- _For a gold customer, and a dispute amount below 500, the risk is low._
- _For a gold customer, and a dispute amount over 500, the risk is medium._


#### Functional Requirements:

Have business rules that will take into account consistent criteria defined to assess risk and automate processing. The business user must have the ability to change these criteria anytime if needed, and apply the changes according to the release process of Pecunia Corp.. 


#### Non Functional:

Allow the user to change the criteria without technical assistance. Have the tooling for the user to update the rules but using standard spreadsheet-like decision tables or quasi natural language.
