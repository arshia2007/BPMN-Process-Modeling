# BPMN Process Modeling Assignment

## Overview

This repository contains BPMN process models created using **Camunda Modeler**.

The assignment consists of three business process scenarios:

1. Employee Leave Approval
2. Online Purchase Order Processing
3. IT Service Request

The models use basic BPMN building blocks including:

* Start Events
* Tasks
* Exclusive Gateways
* Sequence Flows
* End Events

## Scenarios

### Scenario 1 — Employee Leave Approval

The process models an employee submitting a leave request, checking the available leave balance, obtaining manager approval, and sending the appropriate notification.

[BPMN Model](./Scenario-1-Employee-Leave/employee_leave_approval.bpmn)

[Scenario Explanation](./Scenario-1-Employee-Leave/explanation.md)

### Scenario 2 — Online Purchase Order Processing

The process models an online order from product availability checking through payment, order preparation, shipping, and customer notification.

[BPMN Model](./Scenario-2-Online-Purchase/online_purchase_order.bpmn)

[Scenario Explanation](./Scenario-2-Online-Purchase/explanation.md)

### Scenario 3 — IT Service Request

The process models the handling of an employee IT support request, including severity-based technician assignment, investigation, resolution, and escalation.

[BPMN Model](./Scenario-3-IT-Service/it_service_request.bpmn)

[Scenario Explanation](./Scenario-3-IT-Service/explanation.md)

## Tool Used

**Camunda Modeler**

## BPMN Elements

The diagrams use the basic BPMN building blocks required by the assignment:

| Element           | Purpose                         |
| ----------------- | ------------------------------- |
| Start Event       | Begins the process              |
| Task              | Represents an activity          |
| Exclusive Gateway | Represents a decision           |
| Sequence Flow     | Connects process elements       |
| End Event         | Represents the end of a process |


## Verification

The BPMN models are checked for:

* Complete process flow
* Correct gateway decisions
* Clearly labelled alternative paths
* Connected sequence flows
* Appropriate End Events
* Readability of the BPMN diagrams
