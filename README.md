# Project Overview

This project loads multiple AdventureWorks CSV files hosted on GitHub directly into ADLS Gen2 using a dynamic ingestion pipeline. The process uses a JSON configuration file to control:

- Source GitHub file paths

- Sink folder names

- Sink filenames

After ingestion, the data lands in the Bronze layer of the Medallion architecture.

# Architecture
![](https://github.com/abigailmwanza/Adventure-Works-DataEngineering-Project/blob/main/Images/Screenshot%202025-12-04%20at%2011.49.23.png)
