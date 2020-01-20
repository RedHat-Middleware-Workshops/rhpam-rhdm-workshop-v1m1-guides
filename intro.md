# Introduction

## What this module covers

- Business Use Case;
- Overview of Red Hat Process Automation Manager (RHPAM) 7 architecture components;
- Overview of RHPAM 7 on top of OpenShift Container Platform (OCP)
- Installation of RHPAM 7 on OCP 4.2
- Business Central Security Configurations

_Note: Because of the limitations of the workshop environment, the topics regarding persistence will be omitted._

# The Business Background

It is your first day working in the IT Team of Pecunia Corp. This bank has a division named _Issuer_, and one of the most common, yet expensive, tasks is the dispute of a credit card transaction.

The first process this bank identified as a candidate for automation is the _credit card dispute_ process. Some of the reasons are:
- The cost of this business process is very high, regardless of the amount that is being disputed;
- Also, it is also a heavily regulated process that requires audit trails and mandatory steps to be taken.
- Loyal customers currently have no benefits in this process;

We will automate this process to:

- reduce the processing cost;
- improve customer satisfaction by reducing turnaround time through automation;
- make decisions reproducible by automating business rules;
- provide insight into the process, enabling the use of analytics to analyse and optimize the dispute process.
