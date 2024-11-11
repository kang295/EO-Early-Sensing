# E&O Parts Early Sensing Tool

**Description**

This project automatically detects parts likely to become Excessive and Obsolete (E&O) by analyzing three years of demand trends. The goal is to identify at-risk parts early, sharing the list with buyers to guide order placement and prevent unnecessary purchases. This process also enables buyers to cancel orders on obsolete parts, saving approximately $13,000 monthly in transportation costs and supporting optimal warehouse management.

For some parts, demand graphs may show occasional ongoing demand, though in very low quantities (fewer than three). In such cases, our team chooses air transportation rather than warehousing, minimizing storage costs while ensuring availability.

---

## ⚙️ Technologies

- **Python**: Data processing and analysis
  - **Pandas**: Data cleaning and manipulation
  - **GCSFS**: Integration with Google Cloud Storage
  - **Seaborn & Matplotlib**: Data visualization (Demand quantity Trend across 3 years)
- **Google Cloud Platform (GCP)**: Data import and storage

---

## 📊 Dataset

The dataset used in this project is internal to the organization, containing the past demand history per parts.

---

## ✅ Task List

1. **Obtain the Demand History of All HA Parts**
   - Data is retrieved via SQL from the EDW (Enterprise Data Warehouse).
   - Detailed part information, including item status, grade, and creation date, is imported.
   - Substitute part information and demand are also included to assess part activity and filter out original parts from the E&O list based on substitute demand.

2. **Merging and Filtering on Dataframe**
   - Include only parts registered for more than 1.5 years (parts registered under 1.5 years are generally not considered E&O).
   - Filter parts based on item status (Active).
   - Exclude original parts if substitute parts show an average monthly demand greater than 1 over the past 3 months.
   - Handle large orders from PD (high-volume customers) by adjusting orders that exceed the average demand by 300% to zero, ensuring model generalization.

3. **Building Logic to Flag Potential E&O Parts**
   - Divide demand history into three sectors (Sector 1, 2, and 3) to analyze increasing or decreasing demand trends.
   - Using the E&O list generated from this logic and actual E&O parts registered in the system, I identified the overlapping parts and calculated the average demand decline between sectors for validation: Sector 1 to Sector 2 (38.8%) and Sector 2 to Sector 3 (57.7%).

4. **Visualizing Potential E&O Parts with Demand Trends**
   - Display demand changes over time for E&O parts, enabling trend validation and illustrating the decrease in demand for items on the E&O list.



