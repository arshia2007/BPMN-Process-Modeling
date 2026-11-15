# PBJ-2 Practical Assignment
## Camunda 8 End-to-End Workflow Automation (Labs 1–3)

This repository contains three workflow automation labs implemented using Camunda 8, Spring Boot Job Workers, DMN Decision Tables, and REST Connectors.

**Note:** All data is synthetic. No real payment credentials, secrets, or patient data are used.

## 1. Labs Overview

| Lab | Process | Worker Port |
|---|---|---|
| 1 | Loan Approval | 8081 |
| 2 | Order Processing & Fulfilment | 8082 |
| 3 | Hospital Appointment & Triage (Educational) | 8083 |

## 2. Technology Stack

- Camunda 8 Run (8.8)
- Java 21–23
- Spring Boot
- Apache Maven
- Camunda Desktop Modeler
- Zeebe gRPC (Port 26500)
- DMN Decision Tables
- REST Connectors
- Camunda Operate and Tasklist

## 3. Architecture

```text
              Camunda 8 Run
          (Zeebe, Operate, Tasklist,
               Connectors)
                   |
             gRPC :26500
                   |
            Spring Boot Worker
             /           \
       Job Workers     Mock REST API
                           |
             -------------------------
             |           |           |
           Q1            Q2          Q3
          :8081       :8082       :8083
```

All services run locally. No cloud account or external tunnel is required.

## 4. Setup Instructions

### Start Camunda 8 Run

1. Download and extract Camunda 8 Run (version 8.8).
2. Navigate to the `c8run` directory.
3. Start Camunda:

```bash
./start.sh
```

For Windows, follow the Camunda Run Windows startup instructions.

4. Open [http://localhost:8080/operate](http://localhost:8080/operate).

**Login:** `demo` / `demo`

### Start a Lab Worker

1. Open the required lab's `worker/` folder in IntelliJ IDEA.
2. Load the Maven dependencies.
3. Run the corresponding `LabNApplication` class.
4. Verify that the worker connects to `localhost:26500`.

## 5. Deploy and Test

1. Open the lab's `Ex.4/` folder in Camunda Desktop Modeler.
2. Deploy all `.dmn` and `.form` files first.
3. Deploy the `.bpmn` process file.

**Deployment configuration:**

- Target: Camunda 8 Self-Managed
- URL: `http://localhost:8080`
- Authentication: None

4. Open Tasklist and start the process using values from `test-inputs/*.json`.
5. Complete the user tasks.
6. Monitor process instances, variables, and incidents in Operate.

## 6. Incident and Recovery Scenarios

The following failure scenarios demonstrate incident handling and recovery.

| Lab | Failure Scenario | Recovery |
|---|---|---|
| 1 | Worker failure during Validate applicant | Set `simulateWorkerFailure=false` in Operate and Retry |
| 2 | Payment service outage | Disable outage and Retry incident |
| 3 | Scheduling service outage | Disable outage and Retry incident |

**Lab 2 – Enable/Disable Payment Outage**

```bash
curl -X POST "http://localhost:8082/admin/outage/payment?enabled=true"
curl -X POST "http://localhost:8082/admin/outage/payment?enabled=false"
```

Test input: `t5-payment-outage.json`

**Lab 3 – Enable/Disable Scheduling Outage**

```bash
curl -X POST "http://localhost:8083/admin/outage/scheduling?enabled=true"
curl -X POST "http://localhost:8083/admin/outage/scheduling?enabled=false"
```

Test input: `t5-scheduling-outage.json`

For Lab 1, use `t5-worker-failure.json`.

After restoring the service or correcting the variable, retry the incident in Operate and verify successful execution.

> Admin outage endpoints are unauthenticated and intended only for local testing. Do not expose them publicly.

## 7. Evidence Collection

Capture and store the following in each lab's `screenshots/` folder:

- BPMN process diagram
- DMN decision table
- Deployment confirmation
- Tasklist tasks and completed forms
- Operate process instance history
- Incident before and after recovery
- Terminal showing the worker running

Include these screenshots in the final assignment report.

## 8. Current Project Status

| Component | Status |
|---|---|
| BPMN/DMN XML validation | Completed |
| Model layout and routing validation | Completed |
| Java compile-check against API stubs | Completed |
| Maven build | Pending |
| Camunda Modeler verification | Pending |
| Deployment and end-to-end testing | Pending |

---

