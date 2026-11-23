Phase 1- Business Process Modeling

 The Business Process Definition.
 
Process Name: Credit Limit Increase Request & Risk Review.
Purpose: To evaluate a client's request for a higher credit limit securely.
Problem Addressed: Previously, tellers approved limit increases without checking if the client had a history of late payments, exposing the bank to bad debt.
Expected Outcome: A limit increase that is either automatically approved (for good payers), automatically blocked (for late payers), or escalated to a manager, with every action permanently logged.

Actors and Responsibilities

Client: Initiates the request for a higher credit limit.

Customer Service Officer (CSO): Receives the request and inputs the application into the banking system.

Database System (Automated): Triggers a background check on the client's repayment history. It approves, denies, or flags the request.

Credit Risk Manager: Reviews flagged cases (e.g., a client with one late payment 2 years ago) and makes a final manual decision.

Security/Audit System: Captures every attempt (approved or denied) and generates the monitoring dashboard.


Business Process Explanation

[Business Process Explanation.pdf](https://github.com/user-attachments/files/35280330/Business.Process.Explanation.pdf)


