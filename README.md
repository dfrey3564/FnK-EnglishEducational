**EDUCATIONAL ENGLISH TEMPLATE**
# Fine & Kinney Risk Assessment: SQL to Power BI Pipeline 

## Project Overview
This project digitizes the **Fine & Kinney** risk assessment methodology in English, transforming static safety data into a dynamic, relational database and an interactive BI dashboard. It is designed to give Health, Safety, and Environment (HSE) leadership immediate visibility into facility threat levels and the operational status of hazard mitigation plans.

## Architecture & Tools
* **Database Engine:** PostgreSQL (pgAdmin)
* **Data Visualization:** Microsoft Power BI
* **Data Modeling:** Star Schema (1-to-Many Relational Model)
* **Language:** SQL, DAX

## Database Design
The backend relies on a normalized relational database structure to ensure data integrity and prevent orphaned records.
* `fine_kinney_risk`: The primary dimension table storing established hazards, calculated risk scores (Probability × Frequency × Effect), and priority levels.
* `action_plan`: The fact/tracking table utilizing a Foreign Key (`risk_id`) to tie multiple mitigation strategies (Engineering, Administrative, Substitution) and their operational statuses directly to the core hazards.

## Dashboard Features
The Power BI dashboard translates the raw database views into actionable insights:
1. **Interactive Risk Matrix:** A scatter plot mapping Probability vs. Effect.
2. **Mitigation Workflow:** A donut chart tracking the real-time status of assigned action plans (Open, In Progress, Closed).
3. **Critical KPI Tracking:** A DAX-powered card dynamically calculating the Maximum Active Risk Score across the facility.
4. **Cross-Filtering:** Fully interactive visual elements allowing stakeholders to filter the tabular data by clicking specific matrix points or workflow statuses.
## SQL Pipeline Highlights
Key database operations include strict state constraints (`CHECK (status IN ('Open', 'In Progress', 'Closed'))`), dynamic `INSERT` mapping to avoid hardcoded IDs, and `VIEW` generation for seamless Power BI integration.
