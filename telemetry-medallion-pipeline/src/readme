Cloud-Native Telemetry & WFM Analytics Platform
End-to-End Medallion Data Engineering Framework Overview
This repository contains a production-ready technical blueprint and functional ETL framework designed to consolidate contact centre telemetry, Workforce Management (WFM) schedules, and organisational hierarchies into a unified analytics layer.
The solution addresses a common industry challenge: synchronising high-frequency telephony metrics with "messy" time-series schedule data to enable accurate, multi-dimensional performance analysis.
Architecture: Medallion Lakehouse
The platform utilizes a Medallion Architecture to manage the data lifecycle, ensuring auditability and high-performance reporting. While implemented here in Python/SQLite for portability, the design is fully optimized for Enterprise Lakehouse environments (e.g., Databricks/Delta Lake):
•	Bronze (Raw): Immutable landing zone for REST API payloads and flat files.
•	Silver (Cleansed): Data standardisation, identity resolution, and the application of custom business logic.
•	Gold (Curated): Business-ready Star Schema with conformed dimensions and historical snapshots.
Key Engineering Innovations
1. Specialized Overlap-Resolution Algorithm
A custom-built chronological engine that resolves conflicting agent states. In WFM data, agents often appear in multiple states simultaneously (e.g., "Available" and "On Break"). This algorithm:
•	Sorts records chronologically per agent.
•	Dynamically trims end-boundaries of conflicting records.
•	Ensures 100% data integrity where each agent has exactly one active state at any given time.
2. Historical Hierarchy Tracking (SCD Type 2)
To maintain reporting accuracy as agents move between teams and managers, the system implements Slowly Changing Dimensions (Type 2) logic. This is designed to be highly performant in Spark-based environments like Databricks, using window functions to manage effective date ranges and surrogate key assignment.
3. Resilient API Ingestion
A robust framework designed to handle real-world API constraints:
•	Automated OAuth2 Bearer token refreshing.
•	Idempotent upserts at the (date, agent_id) grain.
•	Pagination handling and exponential backoff for HTTP 429 (Rate Limit) errors.
Tech Stack
•	Language: Python 3.x
•	Data Processing: Pandas, NumPy (Scalable to PySpark)
•	SQL Engine: SQLite (In-memory processing for window functions)
•	Architecture: Medallion Lakehouse, Star Schema Modelling
