Cloud-Native Workforce Analytics Platform
Overview
This repository presents a sample data engineering design / case study for integrating operational data into a single analytics platform.
It demonstrates how to combine multiple data sources, clean and standardise time-based data, and enable reliable reporting and analysis.
This is a personal project based on a hypothetical scenario.
Architecture
The solution follows a Medallion Architecture:
•	Bronze (Raw): store data as received 
•	Silver (Clean): apply validation and transformation 
•	Gold (Ready): prepare data for reporting 

Key Features
Overlap Handling
Time-based records can conflict (e.g. multiple states at once).
Records are sorted and adjusted to ensure only one valid state at any point in time.
Historical Tracking
Supports changes over time (e.g. team or manager changes) using effective dates, enabling accurate historical reporting.
Reliable Ingestion
Handles real-world data challenges through incremental loads, duplicate handling, and retry logic.
Data Model
A simple star schema is used:
•	fact tables for activity and performance 
•	dimension tables for entity, hierarchy, and date 

This supports efficient and consistent reporting.
Tech Stack
•	Python 
•	Pandas / NumPy 
•	SQLite 
(Design can scale to Spark or cloud platforms)
