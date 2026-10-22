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

![02_autoloader_stream.png](docs/screenshots/02_autoloader_stream.png)

---

### 3. Azure Storage - Bronze Container (`orders`)
* **Description:** Output `.snappy.parquet` data files created in the ADLS Gen2 `bronze` container.
* **File Reference:** `docs/screenshots/03_bronze_parquet_files.png`

![03_bronze_parquet_files.png](docs/screenshots/03_bronze_parquet_files.png)

---

### 4. Azure Storage - Checkpoint Directory (`checkpoint_orders`)
* **Description:** Auto Loader state and offset tracking directory structure (`commits`, `offsets`, `sources`, `metadata`).
* **File Reference:** `docs/screenshots/04_checkpoint_storage.png`

![04_checkpoint_storage.png](docs/screenshots/04_checkpoint_storage.png)

---

### 5. Source Data Upload (`orders_second.parquet`)
* **Description:** Uploading new incremental data batch into Azure Blob Storage container to test Auto Loader streaming.
* **File Reference:** `docs/screenshots/05_upload_new_data.png`

![05_upload_new_data.png](docs/screenshots/05_upload_new_data.png)

---

### 6. Incremental Load Verification
* **Description:** Spark DataFrame record count updated automatically from 9,990 to 10,000 records without duplicate ingestion.
* **File Reference:** `docs/screenshots/06_incremental_verification.png`

![06_incremental_verification.png](docs/screenshots/06_incremental_verification.png)

---

### 7. Databricks Widgets Setup
* **Description:** Interactive text widget defined using `dbutils.widgets.text()` to make the pipeline dataset-agnostic.
* **File Reference:** `docs/screenshots/07_widgets_setup.png`

![07_widgets_setup.png](docs/screenshots/07_widgets_setup.png)

---

### 8. Dynamic Read and Write Notebook Pipeline
* **Description:** Parameterized path strings utilizing `f"{p_file_name}"` for schema location, source path, and output path.
* **File Reference:** `docs/screenshots/08_dynamic_pipeline.png`

![08_dynamic_pipeline.png](docs/screenshots/08_dynamic_pipeline.png)

---

### 9. Databricks Job DAG (For-Each Task)
* **Description:** Orchestration workflow using a `For-each` loop to pass dynamic dataset parameters down to notebook tasks.
* **File Reference:** `docs/screenshots/09_job_workflow_graph.png`

![09_job_workflow_graph.png](docs/screenshots/09_job_workflow_graph.png)

---

### 10. Databricks Task Parameter Mapping
* **Description:** Task configuration panel mapping dynamic key-value parameters (`file_name` $\rightarrow$ `{{input.file_name}}`).
* **File Reference:** `docs/screenshots/10_job_task_parameters.png`

![10_job_task_parameters.png](docs/screenshots/10_job_task_parameters.png)
