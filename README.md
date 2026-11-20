 Credit Card Limit Review and Control System

Name: Jeannette Uwimpaye 
Student ID: 27745
Project: Final Exam capstone project 
phase:Phase 0, Research, Data Source and Project Proposal

## Problem statement

Credit limit changes on credit cards can be approved without a systematic check of the
cardholder's repayment history and without a record of who approved the change or why.
This exposes the issuer to credit losses and makes the decision impossible to audit.

Low Credit Card Adoption(National Bank of Rwanda) Credit card usage in Rwanda has historically been low relative to other financial instruments.
For example, the FinScope Rwanda 2020 report cited by BNR noted credit card usage at 7% among surveyed banking product users,
well behind savings accounts (60%) and ATMs (46%).

Who is affected: credit managers and risk officers who approve limit changes, and cardholders
whose limits are changed.

## Objectives

 objective: Build an Oracle PL/SQL database that controls credit limit changes for
card clients using their repayment history, and keeps a full audit trail.

Specific objectives:
1. Load the UCI "Default of Credit Card Clients" data into normalised (3NF) Oracle tables.
2. Enforce with a trigger that a limit increase is blocked for clients with late payments.
3. Record every limit-change request, approval and denial in an audit log.
4. Run a nightly scheduled job that lists accounts needing a limit review.

## Data source

 Dataset : Default of Credit Card Clients 
 Source : UCI Machine Learning Repository, dataset 350 
 Link : https://archive.ics.uci.edu/dataset/350/default+of+credit+card+clients


Limitation: the data comes from credit card clients in Taiwan in 2005, not from Rwanda.
But there are some statistics from National Bank of Rwanda as shown above.
It is used as real data to build and test the system. The Rwanda sources in the research log
show why the problem matters locally.

## Innovation

Smart automation. 
Tool: Oracle DBMS_SCHEDULER.
A nightly job reviews each account's repayment history and writes the accounts that need a
limit review into an alerts table. The business rules stay in PL/SQL (procedures and triggers);
the scheduler only runs them. It will be demonstrated live in the final presentation.
Limit documentation.

