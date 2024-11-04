# OEWS-Employment-and-Wage-Data-Project

This project focuses on analyzing and storing Occupational Employment and Wage Statistics (OEWS) data in a PostgreSQL database. The data, sourced from the Bureau of Labor Statistics (BLS), provides detailed information on employment, wages, and occupation statistics across various U.S. states.

* Project Overview
    * Using data from the May 2023 OEWS release, which offers employment and wage estimates for numerous occupations across the United States. This project entails loading the data into a relational database for querying and further analysis.

* Data Source
    * Occupational Employment and Wage Statistics (OEWS)
    * Learn more about OEWS data here: https://www.bls.gov/oes/oes_emp.htm

* Download May 2023 Data
    * The May 2023 OEWS data is available for download here: https://www.bls.gov/oes/tables.htm
    * Check the second tab for field descriptions.

* OEWS Occupation Profiles
    * Overview of the occupation categories in the dataset. View here: https://www.bls.gov/oes/current/oes_stru.htm

* OEWS Documentation
    * For technical notes and background methodology, read here. https://www.bls.gov/oes/oes_doc.htm

* Frequently Asked Questions
    * Access the FAQ for working with the OEWS data here. https://www.bls.gov/oes/oes_ques.htm

* OEWS Maps
    * Explore data visualizations here. https://www.bls.gov/oes/current/map_changer.htm

# Database Schema
* The PostgreSQL database was designed to store the cleaned OEWS data, comprising three main tables: EmploymentWage_Table, State_Table, and Occupation_Table. Below is an entity-relationship diagram (ERD) illustrating the relationships between the tables.
![ERD Table](oews_erd-1.png)

# Table Descriptions
* EmploymentWage_Table
    * Stores employment and wage data by state and occupation levels.
    * Primary Key: (area, occ_code)
    * Foreign Keys: area (references State_Table), occ_code (references Occupation_Table)

* State_Table
    * Stores state-level geographic information.
    * Primary Key: area

* Occupation_Table
    * Stores occupation details, including occupation codes and titles.
    * Primary Key: occ_code

# Database Connection Code

You can use psycopg2 to connect to PostgreSQL:

        import psycopg2
        import os

        connection = psycopg2.connect(
            host=os.getenv('DB_HOST2'),
            port=os.getenv('DB_PORT2'),
            database=os.getenv('DB_NAME2'),
            user=os.getenv('DB_USER2'),
            password=os.getenv('DB_PASS2')
        )
        cursor = connection.cursor()


# Ethical Considerations
Since the OEWS data is anonymized and aggregated, no personally identifiable information (PII) is included, ensuring privacy protection. I followed the BLS guidelines for public data access, aiming for transparency, accuracy, and clarity in reporting employment and wage data. The project highlights key economic trends while maintaining ethical standards in data usage and communication.


