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

1. **Obtain the current back-ordered parts list with inventory stage and ETA**
   - Includes back order hold type with no picking release date & active part status.
2. **Merge real-time transportation status of parts**
3. **Merge detailed part information** 
   - Includes model, first receipt date, and part grade.
4. **Identify accessory or BER parts**
   - As these are managed with different criteria.
5. **Merge substitute parts data with original parts**
   - Service parts may have substitute parts for flexible management.
6. **Merge demand history data**
   - Allows buyers to understand demand-related reasons behind back orders.
7. **Add new features** 
   - Including "New Part Check," "Streak," "RA history," and "Flag" (based on ETA).
8. **Import the final DataFrame to Tableau** 
   - For a user-friendly real-time tracker.
