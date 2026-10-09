# Logistics & Shipment Exception Management

## Overview
This project models the end-to-end lifecycle of a courier shipment using BPMN 2.0 in Camunda Modeler.

## Objective
To represent the shipment process from booking and pickup to hub transit, last-mile delivery, and closure, including exception handling.

## Happy Path
1. Shipper creates a shipment booking.
2. The system validates shipment details and calculates charges.
3. Pickup is scheduled and the parcel is collected.
4. Physical parcel movement and tracking updates proceed in parallel.
5. The parcel is sorted and transported through the hubs.
6. The recipient is notified and delivery is attempted.
7. Proof of delivery is captured, the shipment is closed, and an invoice is generated.

## Implemented Exception Paths
- E1: Pickup failure and rescheduling.
- E2: Address correction and return to sender.
- E3: Damaged parcel and claims handling.
- E4: Lost parcel tracing and compensation.

## BPMN Elements Used
- User Tasks
- Service Tasks
- Business Rule Tasks
- Send Tasks
- Exclusive Gateways
- Parallel Gateways
- Timer Boundary Events
- Intermediate Timer Events
- Sub-processes
- Start and End Events

## Files
- `Logistics_Shipment_Exception_Management.bpmn`: Editable BPMN diagram.
- `diagrams/`: Exported process diagrams.
- `documentation/Failure_Path_Register.md`: Exception register.

## Tool
Camunda Modeler

## Status
The main shipment flow and exception paths E1–E4 have been modelled. Additional exception paths and final validation remain outstanding.
