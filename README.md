# GreenTrack – Environmental Monitoring Database (SQL Server)

## Overview
GreenTrack is a robust relational database system designed for urban environmental monitoring. It acts as the data backbone for a smart city framework by collecting, managing, and indexing real-time data streams from distributed IoT sensors. The system tracks critical environmental matrices such as air quality, water pollution, temperature shifts, and waste management efficiency. 

Furthermore, GreenTrack captures sudden environmental events (e.g., toxic leaks, pollution spikes) and provides an audit trail for public servants to log mitigation actions, ensuring prompt responses to ecological hazards.

---

## Features
* **Asset & Location Management:** Tracks physical IoT hardware units, their deployment status, and pairs them with specific geospatial city locations.
* **Time-Series Data Logging:** Continuously records and timestamps raw metric feeds (AQI, PPM, Temperature, Fill Levels) from active sensors.
* **Incident Escalation:** Captures and classifies sudden environmental events based on descriptive impact and severity levels (`Low` to `Critical`).
* **Response Management:** Logs real-time actions taken by public servants or emergency teams to resolve open incidents.
* **Role-Based Reporting:** Facilitates structured data querying to generate tailored reports for citizens, environmental groups, and administrative teams.
* **Automated Logic:** Leverages T-SQL stored procedures and triggers to automate event logging, alert handling, and status updates.

---

## Database Architecture (3NF)
The relational schema is highly normalized to **Third Normal Form (3NF)** to ensure transactional speed and data integrity:

* `Locations` (LocationID [PK], LocationName, Latitude, Longitude, Description)
* `Users` (UserID [PK], Username, Email, PasswordHash, UserType, CreatedAt)
* `Sensors` (SensorID [PK], LocationID [FK], SensorType, Status, InstallationDate)
* `EnvironmentalData` (DataID [PK], SensorID [FK], Timestamp, Value, Unit)
* `Events` (EventID [PK], LocationID [FK], EventType, SeverityLevel, Description, DetectedAt, Status)
* `Actions` (ActionID [PK], EventID [FK], UserID [FK], ActionTaken, ActionDate)
* `Reports` (ReportID [PK], UserID [FK], ReportType, GeneratedAt, Content)

---

## Technologies
* **Database Engine:** Microsoft SQL Server (2019 / 2022+)
* **Management Client:** SQL Server Management Studio (SSMS) or Azure Data Studio
* **Language:** T-SQL (Transact-SQL)

---

## How to Run

1. Open **SQL Server Management Studio (SSMS)** and connect to your SQL Server Instance.
2. Clone this repository or download the source files to your local machine.
3. Open and execute the SQL scripts located in the `database/` folder sequentially in the following order:

```text
├── database/
│   ├── 01_create_database.sql      -- Allocates system storage and creates the DB
│   ├── 02_tables_constraints.sql   -- Sets up tables, Primary Keys, and Foreign Keys
│   ├── 03_insert_sample_data.sql   -- Populates baseline mock data for testing
│   ├── 04_procedures_triggers.sql  -- Compiles automation logic and alert thresholds
│   └── 05_queries.sql              -- Runs sample analytics and data-view scripts

```
## Authors : 
Malindu Indumina – Lead Developer & Database Designer







