Proposal


LimitGuard: Credit Card Limit Review and Control System
1. Problem Statement
Credit card issuers raise and cut credit limits throughout the life of an account. When these changes are approved without a systematic check of the cardholder’s repayment history, the issuer takes on avoidable credit risk. When there is no record of who approved a change and why, the decision cannot be explained or audited. Credit managers and risk officers are affected, and so are cardholders whose limits change without a clear reason.
https://fininclusion.bnr.rw/credit

 



2. Proposed Solution
LimitGuard is an Oracle PL/SQL database that stores cardholders, their monthly repayment history and limit-change requests, and controls how limits are changed. The main objective is that every credit limit change is checked against repayment history and recorded in an audit log. The specific objectives are to: (1) load the dataset into third normal form (3NF) tables; (2) block limit increases for clients with late payments using a trigger; (3) record every request, approval and denial in an audit log; and (4) run a nightly job that lists accounts needing a limit review.
3. Data Source
The project uses the Default of Credit Card Clients dataset from the UCI Machine Learning Repository (dataset 350, https://archive.ics.uci.edu/dataset/350/default+of+credit+card+clients). It contains 30,000 records and 23 features: credit limit, sex, education, marital status, age, and six months (April to September 2005) of repayment status, bill amount and payment amount. It is licensed CC BY 4.0, which allows educational use, and clients appear only as anonymous numbers. The data comes from Taiwan in 2005, not from Rwanda. It serves as real data for building and testing the system, and its quality will be checked in Phase II.
4. Planned Tables
Draft only; the final 3NF design is made in Phase II.
•	clients, education_levels, marital_statuses: the cardholders and their coded attributes.
•	credit_accounts: each client’s account and current credit limit.
•	monthly_statements: repayment status, bill amount and payment amount for each account and month.
•	limit_change_requests: requested limit, status, reviewer and decision reason.
•	audit_log: who changed what, when, with the old and new values.
•	review_alerts: accounts flagged for review by the nightly job.
5. Planned PL/SQL Features
•	A BEFORE UPDATE trigger blocks a limit increase on an account with late payments.
•	An AFTER trigger writes every limit change to the audit log.
•	A function counts an account’s late-payment months and returns a risk level.
•	Procedures record a limit-change request and approve or deny it.
•	A cursor loops over all accounts in the nightly review.
•	A package groups the limit-control functions and procedures.
•	Exception handling covers an unknown account, an invalid limit and a request from a late payer.
6. Innovation
Option: Smart automation. Tool: DBMS_SCHEDULER. A nightly job runs a PL/SQL review procedure and writes the accounts that need a limit review into an alerts table. The business rules stay in PL/SQL, and the scheduler only runs them. It will be demonstrated live in the final presentation.
7. References (APA)
Yeh, I.-C. (2009). Default of credit card clients [Dataset]. UCI Machine Learning Repository. https://doi.org/10.24432/C55S3H

https://www.google.com/search?q=national+bank+of+rwanda+statistics+about+credit+cards&biw=1024&bih=599&sca_esv=2d313c7a5f5eabbc&sxsrf=AKL5yDihpkP4RUJPvroQSQio8S_LCWBgpw%3A1795285287234&ei=J-EBa8bSDb-AhbIPk8urmQg&oq=N&gs_lp=Egxnd3Mtd2l6LXNlcnAiAU4qBAgAGCcyBBAjGCcyBBAjGCcyBBAjGCcyCxAAGIAEGIoFGJECMgoQABiABBiKBRhDMhEQLhiABBiKBRiRAhjHARjRAzILEAAYgAQYigUYkQIyCxAAGIAEGIoFGJECMgsQABiABBiKBRiRAjIIEAAYgAQYsQNImDRQ5x1Y5x1wAXgBkAEAmAGGA6ABhgOqAQMzLTG4AQHIAQD4AQGYAgKgAvcDqAIKwgIHECMY6gIYJ8ICDRAuGMcBGNEDGOoCGCeYA0PxBZSGQNipM8ECkgcFMS40LTGgB5UJsgcDNC0xuAe0A8IHBTQtMS4xyAdQgAgB&sclient=gws-wiz-serp




