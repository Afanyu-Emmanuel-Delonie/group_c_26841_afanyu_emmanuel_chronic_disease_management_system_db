# Chronic Disease Monitoring System (CDMS)

A platform for monitoring chronic disease patients, generating alerts, and supporting clinical decisions through analytics.

# Overview

The Chronic Disease Monitoring System (CDMS) helps healthcare providers track patients with chronic illnesses, monitor vital signs, and generate timely alerts.
It uses Oracle Database (CDM_PDB), PL/SQL, and Power BI dashboards for data visualization and analytics.

# Problem Statement

Manual monitoring of chronic patients is slow and error-prone.

Delayed alerts can lead to critical patient complications.

Clinicians need centralized, real-time access to patient data.

# Project Goals

Centralize patient, disease, and alert data in CDM_PDB

Automate alert generation for abnormal health metrics

Provide dashboards for real-time monitoring and decision-making

Improve clinical efficiency and patient safety

# Target Users

Doctors

Nurses

Hospital Administrators

Medical Data Analysts


# Database Entities
Core Tables
Table	Description
PATIENT	Stores patient demographics
DOCTOR	Registered doctors
DISEASE	Monitored diseases
HEALTH_METRICS	Patient vitals (BP, sugar, etc.)
DIAGNOSIS	Assigns diseases to patients (unique per patient per disease)
ALERT	Automatically triggered alerts
ALERT_ACTIONS	Actions taken for alerts
AUDIT_LOG	System activity logs
ERD Diagram
![ERD](./docs/erd.png)

# Database Setup
Connect to PDB
sqlplus AFANYU_EMMANUEL/afanyu@localhost:1521/CDM_PDB

Run Schema Scripts
@tables.sql
@constraints.sql
@triggers.sql
@sample_data.sql

Verify Tables
SELECT table_name FROM user_tables;

# Power BI Integration

Imported Tables:

PATIENT

DISEASE

DIAGNOSIS

HEALTH_METRICS

ALERT

ALERT_ACTIONS

Dashboards Include:

Patient Gender Distribution

Disease Prevalence

Alerts by Severity

Patient–Disease Matrix

Real-time Alert Table (with conditional color formatting)

# Sample Query
SELECT 
    p.first_name || ' ' || p.last_name AS patient,
    d.disease_name,
    a.alert_type,
    a.severity
FROM alert a
JOIN patient p ON p.patient_id = a.patient_id
JOIN disease d ON d.disease_id = a.disease_id
ORDER BY a.severity DESC;

# Tech Stack

Oracle 21c XE (CDM_PDB) — Core database

PL/SQL — Triggers, packages, constraints

Power BI — Data visualization & analytics

UML + BPMN — System modeling

# Business Intelligence Potential

Identify high-risk patients quickly

Track disease trends and alert patterns

Support hospital planning and resource allocation

Improve treatment decisions with real-time insights

# Project Structure
CDMS/
│── database/
│     ├── tables.sql
│     ├── constraints.sql
│     ├── triggers.sql
│     ├── sample_data.sql
│── docs/
│     ├── erd.png
│     ├── bpmn.png
│── powerbi/
│     ├── CDMS_Report.pbix
│── README.md

# Future Enhancements

REST API for mobile/IoT integration

SMS/WhatsApp automated alerts

Predictive analytics for early warning

Patient mobile self-monitoring app
