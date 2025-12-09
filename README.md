# Chronic Disease Monitoring System (CDMS)

[![Oracle](https://img.shields.io/badge/Oracle-21c%20XE-red?logo=oracle)](https://www.oracle.com/)
[![Power BI](https://img.shields.io/badge/Power%20BI-Analytics-yellow?logo=powerbi)](https://powerbi.microsoft.com/)
[![PL/SQL](https://img.shields.io/badge/PL%2FSQL-Database-blue)](https://www.oracle.com/database/technologies/appdev/plsql.html)

A comprehensive healthcare platform for monitoring chronic disease patients, generating real-time alerts, and supporting clinical decisions through advanced analytics and interactive dashboards.

---

## Table of Contents
- [Overview](#overview)
- [Problem Statement](#problem-statement)
- [Project Goals](#project-goals)
- [Target Users](#target-users)
- [System Architecture](#system-architecture)
- [Database Design](#database-design)
- [Code Samples](#code-samples)
- [Power BI Dashboards](#power-bi-dashboards)
- [Installation & Setup](#installation--setup)
- [Sample Queries](#sample-queries)
- [Tech Stack](#tech-stack)
- [Business Intelligence Insights](#business-intelligence-insights)
- [Future Enhancements](#future-enhancements)

---

## Overview

The **Chronic Disease Monitoring System (CDMS)** is designed to help healthcare providers efficiently track patients with chronic illnesses, monitor vital signs in real-time, and generate timely alerts for critical health conditions. 

The system integrates **Oracle Database (CDM_PDB)**, **PL/SQL triggers and procedures**, and **Power BI dashboards** to provide a comprehensive solution for healthcare data management and visualization.

### Key Features
- Centralized patient health records
- Automated alert generation for abnormal vitals
- Real-time monitoring dashboards
- Disease prevalence analytics
- Audit logging for compliance

---

## Problem Statement

Healthcare providers face significant challenges in managing chronic disease patients:

| Challenge | Impact |
|-----------|--------|
| **Manual Monitoring** | Slow, inefficient, and error-prone patient tracking |
| **Delayed Alerts** | Critical complications due to late detection of abnormal vitals |
| **Fragmented Data** | Patient information scattered across multiple systems |
| **Limited Analytics** | Difficulty identifying trends and high-risk patients |

**CDMS solves these problems** by providing a unified, automated, and intelligent monitoring platform.

---

## Project Goals

### 1. Centralize Patient Data
Consolidate patient demographics, diagnoses, health metrics, and alerts into a single Oracle database (CDM_PDB) for seamless access and management.

### 2. Automate Alert Generation
Implement PL/SQL triggers to automatically generate alerts when patient vitals exceed predefined thresholds, ensuring timely medical intervention.

### 3. Enable Real-Time Monitoring
Provide Power BI dashboards that visualize patient health status, alert severity, and disease trends in real-time for proactive healthcare delivery.

### 4. Improve Clinical Efficiency
Reduce manual workload for healthcare providers, minimize response times to critical conditions, and enhance overall patient safety and care quality.

---

## Target Users

- **Doctors** — Monitor patients and make clinical decisions
- **Nurses** — Track vitals and respond to alerts
- **Hospital Administrators** — Oversee operations and resource allocation
- **Medical Data Analysts** — Analyze trends and generate reports

---

## System Architecture

### BPMN Diagram
![BPMN Process Flow](images/bpmn-diagram.png)

*Business Process Model showing the workflow from patient data entry through alert generation to clinical response*

The CDMS follows a three-tier architecture:

1. **Data Layer** — Oracle 21c XE Database (CDM_PDB)
2. **Business Logic Layer** — PL/SQL triggers, procedures, and packages
3. **Presentation Layer** — Power BI dashboards and reports

---

## Database Design

### Core Tables

| Table | Description | Key Columns |
|-------|-------------|-------------|
| **PATIENT** | Patient demographics | `PATIENT_ID`, `FIRST_NAME`, `LAST_NAME`, `GENDER`, `DATE_OF_BIRTH` |
| **DOCTOR** | Registered doctors | `DOCTOR_ID`, `FIRST_NAME`, `SPECIALTY` |
| **DISEASE** | Chronic diseases monitored | `DISEASE_ID`, `DISEASE_NAME`, `CATEGORY` |
| **HEALTH_METRICS** | Patient vital signs | `METRIC_ID`, `PATIENT_ID`, `BLOOD_PRESSURE`, `PULSE_RATE`, `TEMPERATURE` |
| **DIAGNOSIS** | Patient-disease assignments | `DIAGNOSIS_ID`, `PATIENT_ID`, `DISEASE_ID`, `DOCTOR_ID` |
| **ALERT** | Auto-generated health alerts | `ALERT_ID`, `PATIENT_ID`, `ALERT_TYPE`, `SEVERITY_LEVEL` |
| **ALERT_ACTIONS** | Actions taken on alerts | `ACTION_ID`, `ALERT_ID`, `ACTION_TAKEN` |
| **THRESHOLD** | Alert threshold values | `THRESHOLD_ID`, `METRIC_TYPE`, `MIN_VALUE`, `MAX_VALUE` |
| **TREATMENT** | Patient treatments | `TREATMENT_ID`, `PATIENT_ID`, `TREATMENT_TYPE` |
| **AUDIT_LOG** | System activity tracking | `LOG_ID`, `ACTION`, `TIMESTAMP` |

### Entity Relationship Diagram (ERD)

![ERD Diagram](images/erd-diagram.png)

*Entity Relationship Diagram showing database structure and relationships*

### Key Relationships
- **One Patient** → **Many Diagnoses** (1:N)
- **One Patient** → **Many Alerts** (1:N)
- **One Patient** → **Many Health Metrics** (1:N)
- **One Doctor** → **Many Diagnoses** (1:N)
- **One Disease** → **Many Diagnoses** (1:N)

---

## Code Samples

### Table Creation
```sql
