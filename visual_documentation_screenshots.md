# Workflow Screenshots & Visual Documentation

This document maintains the complete image log for the **Azure Databricks Dynamic Auto Loader Pipeline**.

---

### 1. Compute Cluster Configuration
* **Description:** Configuration of the Databricks Single Node cluster (`Standard_D4ds_v4`) used for dynamic Auto Loader execution.
* **File Reference:** `docs/screenshots/01_compute_cluster.png`
<img width="940" height="352" alt="image" src="https://github.com/user-attachments/assets/051cb495-2f79-451e-9d93-217c01ba6ba3" />

---

### 2. Databricks Auto Loader Stream Execution
* **Description:** Reading Parquet files using `cloudFiles` and writing them out with checkpointing enabled.
* **File Reference:** `docs/screenshots/02_autoloader_stream.png`

<img width="940" height="500" alt="image" src="https://github.com/user-attachments/assets/b58ae93b-c78e-4e4d-9e4f-b2897532771e" />


---

### 3. Azure Storage - Bronze Container (`orders`)
* **Description:** Output `.snappy.parquet` data files created in the ADLS Gen2 `bronze` container.
* **File Reference:** `docs/screenshots/03_bronze_parquet_files.png`

<img width="940" height="236" alt="image" src="https://github.com/user-attachments/assets/50d5f091-70a5-4a16-b62e-bf101f5077ff" /> 





---

### 4. Azure Storage - Checkpoint Directory (`checkpoint_orders`)
* **Description:** Auto Loader state and offset tracking directory structure (`commits`, `offsets`, `sources`, `metadata`).
* **File Reference:** `docs/screenshots/04_checkpoint_storage.png`

<img width="940" height="273" alt="image" src="https://github.com/user-attachments/assets/9c1485ee-c48b-4922-85c2-e09823629617" />


---

### 5. Source Data Upload (`orders_second.parquet`)
* **Description:** Uploading new incremental data batch into Azure Blob Storage container to test Auto Loader streaming.
* **File Reference:** `docs/screenshots/05_upload_new_data.png`

<img width="940" height="221" alt="image" src="https://github.com/user-attachments/assets/8bc9cf06-6456-421d-a7cd-cb770bd10d91" />


---

### 6. Incremental Load Verification
* **Description:** Spark DataFrame record count updated automatically from 9,990 to 10,000 records without duplicate ingestion.
* **File Reference:** `docs/screenshots/06_incremental_verification.png`

<img width="940" height="492" alt="image" src="https://github.com/user-attachments/assets/d1f69260-92ed-414a-b238-5ba1263abd76" />


---

### 7. Databricks Widgets Setup
* **Description:** Interactive text widget defined using `dbutils.widgets.text()` to make the pipeline dataset-agnostic.
* **File Reference:** `docs/screenshots/07_widgets_setup.png`

<img width="940" height="583" alt="image" src="https://github.com/user-attachments/assets/723ceef1-b641-4fc4-8777-c1501348a9f9" />


---

### 8. Dynamic Read and Write Notebook Pipeline
* **Description:** Parameterized path strings utilizing `f"{p_file_name}"` for schema location, source path, and output path.
* **File Reference:** `docs/screenshots/08_dynamic_pipeline.png`

<img width="940" height="434" alt="image" src="https://github.com/user-attachments/assets/cfe06175-8651-4994-9afb-a44ecc2437c7" />


---

### 9. Databricks Job DAG (For-Each Task)
* **Description:** Orchestration workflow using a `For-each` loop to pass dynamic dataset parameters down to notebook tasks.
* **File Reference:** `docs/screenshots/09_job_workflow_graph.png`

### Databricks Task Parameter Mapping
* **Description:** Task configuration panel mapping dynamic key-value parameters (`file_name` $\rightarrow$ `{{input.file_name}}`).
* **File Reference:** `docs/screenshots/10_job_task_parameters.png`

<img width="540" height="211" alt="image" src="https://github.com/user-attachments/assets/e60f0220-37ef-4b40-81aa-58d5f0b43a94" /> 

<img width="540" height="211" alt="image" src="https://github.com/user-attachments/assets/93a0a85d-d0bb-4115-b81d-218339d1623d" />

### 10. Silver Schema in Catalog Explorer

- **Description:** `databricks_cata.silver` schema with the four silver tables and quarantine tables , data loaded in silver layer with the help of 4 notebooks where initially we performed transformation and at last load to tgt ( "(df.write.mode("append").format("delta").save("abfss://silver@datalaketanish.dfs.core.windows.net/customers") ")
  <img width="1632" height="842" alt="image" src="https://github.com/user-attachments/assets/104ac873-9ed1-45be-b0de-29119834c123" />
  <img width="500" height="300" alt="image" src="https://github.com/user-attachments/assets/64e12e8c-38e1-4db6-ad4a-11a406da7727" />
  <img width="500" height="300" alt="image" src="https://github.com/user-attachments/assets/c7a2b260-a6cc-4e44-82ea-6b57511be0a8" />




### 11. Silver_Orders Notebook

- **Description:** Transformation notebook with type casting, data quality rules, deduplication and MERGE.
- **File Reference:** `docs/screenshots/12_silver_orders_notebook.png`

### 12. Silver_Customers Notebook

- **Description:** Customer standardisation and validation notebook.
- **File Reference:** `docs/screenshots/13_silver_customers_notebook.png`

### 13. Silver_Products Notebook

- **Description:** Product standardisation and validation notebook.
- **File Reference:** `docs/screenshots/14_silver_products_notebook.png`

### 14. Silver_Regions Notebook

- **Description:** Regions cleaning notebook reading from `databricks_cata.bronze.regions`.
- **File Reference:** `docs/screenshots/15_silver_regions_notebook.png`

### 15. Catalog-Level Functions

- **Description:** `discount_func` and other Unity Catalog functions listed under the schema in Catalog Explorer.
- **File Reference:** `docs/screenshots/16_catalog_functions.png`

### 16. Silver Job Run

- **Description:** Job run graph showing bronze tasks followed by the four silver tasks.
- **File Reference:** `docs/screenshots/17_silver_job_run.png`

---




