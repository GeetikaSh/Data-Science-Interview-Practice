# Data Quality

**Data Quality** refers to the accuracy, completeness, consistency, and reliability of data, ensuring it is fit for its intended purpose.
High-quality data is essential for effective decision-making, analytics, and operational efficiency.

## Key Dimensions of Data Quality:
1. **Accuracy:** Data must represent the real-world entity or event correctly.
2. **Completeness:** No critical data points should be missing.
3. **Consistency:** Data should remain uniform across systems and over time.
4. **Timeliness:** Data should be updated and available when needed.
5. **Validity:** Data must conform to the required formats, ranges, or business rules.
6. **Uniqueness:** Avoid duplicate records that could distort analysis.

## Benefits of Maintaining Data Quality:
- Improves decision-making.
- Enhances operational efficiency.
- Reduces costs associated with errors or inconsistencies.
- Builds trust in data-driven processes.

## Steps to Improve Data Quality:
1. **Establish Data Governance:** Assign roles such as Data Stewards to oversee quality.
2. **Conduct Data Audits:** Regularly evaluate data for issues across dimensions.
3. **Implement Validation Rules:** Use automated checks to prevent errors during data entry or integration.
4. **Leverage Data Cleaning Tools:** Use software to deduplicate, validate, and enrich data.
5. **Foster a Data-Driven Culture:** Train teams to prioritize data accuracy and quality in their workflows.

## **What steps do you take to ensure data quality?**
Ensuring data quality is crucial for reliable insights and outcomes. Here are the steps I typically follow:

1. **Understand the Source and Context**  
   - Collaborate with data owners and stakeholders to understand the data's source, purpose, and key business requirements.

2. **Data Profiling**  
   - Use tools or write scripts to analyze data distributions, check for missing values, and detect outliers or anomalies.

3. **Validation Against Business Rules**  
   - Cross-check the data against predefined business rules and logic to ensure it aligns with expectations.

4. **Automated Data Cleansing**  
   - Apply ETL (Extract, Transform, Load) processes to handle missing, duplicate, or inconsistent records.

5. **Data Pipeline Testing**  
   - Build automated tests to validate data integrity throughout the pipeline.

6. **Documentation**  
   - Maintain a clear record of data sources, transformations, and quality checks for transparency and reproducibility.

7. **Continuous Monitoring**  
   - Set up monitoring systems to detect future data quality issues proactively.

This structured approach has helped me deliver high-quality data models and analyses throughout my career.

## Handling Conflicting Definitions of the Same Data Field

When two departments have conflicting definitions for the same data field, the situation requires a structured and collaborative approach to resolve. Here's how I would handle it:

1. **Understand Both Perspectives**  
   Schedule meetings with representatives from each department to understand their definitions, use cases, and the rationale behind their perspectives. This will help in identifying the root cause of the conflict.

2. **Analyze the Impact**  
   Evaluate how each definition affects business operations, reporting, and decision-making. Quantify the impact of inconsistencies to prioritize resolution.

3. **Engage Key Stakeholders**  
   Involve stakeholders such as data stewards, business analysts, and leadership to mediate the discussion. Ensure all voices are heard and documented.

4. **Define a Common Business Glossary**  
   Work with both departments to agree on a unified definition or establish a shared glossary with context-specific variations. For instance:
   - **Global Definition:** A primary, overarching definition used across the organization.
   - **Context-Specific Variations:** Additional definitions tailored to specific departmental needs, with clear documentation.

5. **Document the Resolution**  
   Publish the agreed-upon definitions in a centralized knowledge base or data dictionary. Ensure all teams have access to this resource.

6. **Implement and Communicate Changes**  
   Update the metadata, reporting systems, and any downstream processes. Communicate changes clearly across the organization to ensure alignment.

7. **Establish Governance**  
   Set up a data governance framework to prevent future conflicts. Include procedures for validating and approving changes to critical data fields.

By following these steps, I ensure consistency, minimize misunderstandings, and foster collaboration between departments.


## Common Cause of Poor Data Quality and How can you mitigate it?
1. **Human Errors** (e.g., data entry mistakes, typos)
- **Solution:** Implement data validation rules, auto-correction, and training programs for data entry personnel.

2. **Inconsistent Data Across Systems**
- **Solution:** Use data governance frameworks and centralized data management to ensure uniformity.

3. **Missing or Incomplete Data**
- S**olution:** Implement mandatory fields, default values, and imputation techniques to handle missing data.

4. **Duplicate Records**
- **Solution:** Use deduplication algorithms and enforce unique identifiers for records.

5. **Outdated Data**
- **Solution:** Set up automated data updates and review cycles to keep data fresh.

6. **Integration Issues from Multiple Sources**
- **Solution:** Standardize data formats, use ETL (Extract, Transform, Load) pipelines, and perform data validation during ingestion.

## How would you handle missing data in a dataset? What techniques would you use?
Handling missing data depends on the type and extent of missingness:

1. **Deletion Methods:**
- **Listwise Deletion:** Remove rows with missing values (useful if missing data is minimal).
- **Pairwise Deletion:** Use available data without dropping entire rows (for correlation analysis).

2. **Imputation Techniques:**
- **Mean/Median/Mode Imputation:** Replace missing values with statistical measures (best for numerical data with low missingness).
- **Forward/Backward Fill:** Use previous or next values (works well for time series data).
- **K-Nearest Neighbors (KNN) Imputation:** Predict missing values based on similar data points.
- **Regression Imputation:** Predict missing values using regression models.
- **Multiple Imputation:** Create multiple datasets with different imputed values for better robustness.

3. **Advanced Techniques:**
- **Deep Learning Models:** Autoencoders or GANs for imputing complex patterns.
- **Using Domain Knowledge:** Consulting experts to fill in gaps logically.

The best approach depends on the dataset size, missing data pattern, and business requirements.

### How do you detect and handle duplicate records in a dataset?
1. **Detecting Duplicates:**
- **Using Unique Identifiers:** Check for repeated IDs or primary keys.
- **Row-wise Comparison:** Identify duplicate rows using functions like df.duplicated() in Pandas.
- **Fuzzy Matching:** Use Levenshtein Distance or Jaccard Similarity for near-duplicates (e.g., typos).
- **Aggregation Checks:** Summarize key attributes (e.g., count unique names per email).

2. **Handling Duplicates:**
- **Drop Exact Duplicates:** df.drop_duplicates() removes identical records.
- **Merge Similar Records:** Keep the most recent or most complete entry.
- **Apply Business Rules:** Define criteria (e.g., same name & email = duplicate).
- **Standardize Data Before Deduplication:** Convert text to lowercase, remove spaces, and unify formats.

---
