# AfyaMeds Inventory Management System

## Project Overview
The "AfyaMeds Inventory Management System" is a MySQL-based project designed to manage and analyze medical supply inventory for AfyaMeds, a hypothetical organization distributing healthcare supplies across multiple clinics.

## Project Goal
Design a scalable database system to track medical supplies, optimize stock levels, reduce waste, and provide actionable insights for efficient logistics management and healthcare delivery.

## Technical Stack and Implementation
The project uses the following technologies:
### MySQL:
- Used for database management, ensuring robust data storage and querying capabilities.
### Python:
- Utilized through a Jupyter Notebook for data generation, specifically with the `mysql-connector-python` library for database interactions.
### Power BI:
- Employed to create an interactive dashboard for visualizing inventory data and deriving actionable insights.

## Setup and Usage Instructions
To set up and use the project, follow these steps:
### Install MySQL:
- Ensure MySQL is installed and running on your system. You can download it from the [official MySQL website](https://dev.mysql.com/downloads/).
- Create a database named `maishameds_db`.
### Run Schema SQL:
- Navigate to the `AfyaMeds Inventory Management System` folder within the repository. This folder contains the necessary files for the project.
- Execute the file `AfyaMeds Inventory Management System.sql` to create the database schema, including tables and indexes.
### Generate Data:
- Open the Jupyter Notebook `AfyaMeds Inventory Management System.ipynb`, also located in the `AfyaMeds Inventory Management System` folder.
- Ensure you have Jupyter installed (`pip install jupyter`) and update the MySQL connection credentials in the notebook (`host`, `user`, `password`, `database`).
- Run all cells in the notebook to populate the database with sample data. This generates over 10,000 rows, including:
  - 20 unique supplies
  - 50 clinics across 5 regions
  - 5,000+ inventory records with quantities and expiration dates
  - 5,000+ order records over the last 6 months
- The notebook ensures realistic data, simulating real-world scenarios.
### Explore Queries:
- Return to the `AfyaMeds Inventory Management System.sql` file for analysis queries.
- Execute the provided queries to generate insights, such as low-stock alerts, expiry tracking, and order trends.

## Features of Sample Queries
### Running Order Totals:
- Tracks cumulative orders per supply over time for demand tracking.
### Overstock Supplies:
- Detects excess stock beyond maximum limits to free up capital.
### Clinics Rankings:
- Ranks clinics by inventory value within each region.
### Inventory Value by Region:
- Aggregates stock value regionally for resource allocation.
### Top Ordered Supplies Last 90 Days:
- Analyzes demand trends to forecast future needs.
### Low Stock Alerts:
- Identifies clinics with supplies below minimum thresholds.
### Expiring Supplies Within 60 Days:
- Flags items at risk of expiry to prevent waste.

## Insights
Based on the dataset and queries, the following insights emerge:
- **Low Stock Risks**: Approximately 14 items, particularly in regions like Eldoret (2.89% of inventory value, $23,023.75), show critical shortages
- **Expiry Waste**:  Around 62.2% of inventory (3110 units, including Syringe 10ml, Thermometer, Gauze, IV Fluid, Ibuprofen) is at risk of expiry within 30 days, posing significant loss risks if not redistributed.
- **Cost Distribution**: Thika holds a high inventory value (17.63%, $140,343.50), suggesting uneven distribution that could be balanced with regions like Eldoret
- **Demand Trends**: Alcohol Swabs show a sharp demand increase (68913 to 517687 units from Oct 2024 to Aug 2025).
- **Overstock Issues**: Overstock worth $22,440, particularly in regions like Thika, ties up capital that could address shortages in understocked clinics like Eldoret.

## Recommendations
- Prioritize restocking for low-stock clinics in high-demand regions (Transfer $22,440 in overstocked supplies from high-inventory regions like Thika to low-stock regions like Eldoret)
- Implement a "first-expire, first-out" policy and transfer 3110 expiring units (e.g., Syringe 10ml, Thermometer) within 30 days to high-demand regions to avoid losses,
- Increase Alcohol Swabs orders to meet the rapid demand rise (68913 to 517687 units)
- Reallocate stock from high-inventory regions (Thika, Nyeri, Kericho) to understocked regions (Eldoret, Machakos, Nakuru) to reduce disparities
- Set up daily alerts for low stock (14 items) and expiring supplies (3110 units) to enhance responsiveness.

## Power BI Dashboard
Developed an interactive Power BI dashboard titled **"AfyaMeds Inventory Management Dashboard"** (`AfyaMeds Inventory Management Dashboard.pbix`) to visualize the MySQL data, enhancing decision-making with real-time insights. The dashboard includes KPIs, regional stock values, demand trends, and expiry risks, using a healthcare-themed color scheme (Blue `#0078D4`, Green `#28A745`, Red `#DC3545`).

### Connecting Power BI to MySQL
To connect Power BI to the `maishameds_db` MySQL database:
1. **Install MySQL Connector**:
   - Downloaded and installed the MySQL Connector/NET from [MySQL’s official site](https://dev.mysql.com/downloads/connector/net/).
   - Restarted Power BI Desktop after installation.
2. **Access Data**:
   - Opened Power BI Desktop > **Home** > **Get Data** > **MySQL Database**.
   - Entered server details:
     - **Server**: `localhost` (or your server IP if hosted remotely).
     - **Database**: `afya_db`.
   - Selected **DirectQuery** mode for live updates (or Import mode for static data).
3. **Authenticate**:
   - Provided MySQL credentials:
     - **Username**:  `root`.
     - **Password**: [Your MySQL password].
   - Clicked **Connect**.
4. **Load Tables**:
   - In the Navigator window, selected tables: `Supplies`, `Clinics`, `Inventory`, `Orders`.
   - Verified relationships (e.g., `supply_id`, `clinic_id`) were recognized.
   - Clicked **Load** to bring data into Power BI.
5. **Troubleshooting**:
   - Ensured MySQL server was running (`mysql -u root -p` in terminal).
   - Confirmed port 3306 was open (default MySQL port).

### Dashboard Insights and Recommendations
*Date: April 14, 2025*

#### Insights
- **Value**: $796,000 total inventory, with Thika leads at 17.63% ($140,343.50) and Eldoret at 2.89% ($23,023.75).
- **Stock**: 14 items below minimum stock, $22,440 overstocked, and 62.2% (3110 units) expiring within 30 days.
- **Demand**: Alcohol Swabs demand increased rapidly (68913 - 517687) from Oct 2024 to Aug 2025
- **Expiry**: Top 5 expiring supplies (Syringe 10ml, Thermometer, Gauze, IV Fluid, Ibruprofen) total 3110 units, all expiring in <30 days.
- **Clinics**: Eldoret region critically low and Thika region higher hence, stock imbalances.

#### Recommendations
1. **Redistribute Excess**: Transfer $22,440 overstock from high-stock regions like Thika to low-stock regions like Eldoret to address 14 low-stock items.
2. **Prevent Waste**: Transfer 3110 expiring units (e.g Syringe 10ml) within 30 days to to region with high inventory like Thika to avoid loss.
3. **Adjust Orders**: Increase Alcohol Swabs orders due to a demand rise.
4. **Balance Regions**: Allocate more stock to Eldoret, Machakos and Nakuru from Thika, Nyeri and Kericho to reduce regional disparities.
5. **Automate Monitoring**: Implement daily alerts for low stock (14 items) and expiring supplies to improve responsiveness.

## Learning Outcomes
- Database design and optimization with indexes and constraints.
- Advanced query writing, including joins, aggregations, and window functions.
- Data generation and analysis workflows, integrating Python with MySQL.
- Real-world application in healthcare logistics, addressing practical challenges like waste reduction and resource allocation.

## Future Development
### Predictive Analytics:
- Use historical order data to forecast restocking needs, potentially integrating machine learning models via Python.
### Supplier Module:
- Add a table to track vendor details, lead times, and costs for a complete supply chain view.
### User Interface:
- Develop a simple front-end for non-technical users to interact with the system, enhancing accessibility.

## Repository Structure
The repository is named "AfyaMeds-Inventory-Management-System" with:
A folder named "AfyaMeds Inventory Management System" with:
### AfyaMeds Inventory Management System.ipynb:
- Jupyter Notebook for data generation.
### AfyaMeds Inventory Management System.sql:
- SQL file with schema and analysis queries.
This `README.md` file providing documentation and setup instructions.

## Contact
For collaboration and any other question contact me through:
- **Email**: rocjeschaulo@gmail.com
- **Phone number (WhatsApp)**: +254715287781
