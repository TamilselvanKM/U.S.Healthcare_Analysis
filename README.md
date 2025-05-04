# U.S. Metropolitan Healthcare Analysis

## Project Overview
This project analyzes healthcare infrastructure and social security stress across 83 U.S. metropolitan areas using Power BI. It highlights resource gaps, elderly population growth, and risk patterns to support better planning and healthcare delivery.

---
## Dataset Summary
**Source**  : U.S. Metropolitan Healthcare Dataset
**Scope**   : 83 U.S Cities
**Columns** : City, NumMDs, RateMDs, NumHospitals, NumBeds, RateBeds, NumMedicare, PctChangeMedicare, MedicareRate, SSBNum, SSBRate, SSBChange, NumRetired, SSINum, SSIRate, SqrtMDs

---
## Data Preparation
1. Checked for duplicate/missing values - none found
2. Ensured correct data types
3. Validated non-negative values for doctors, hospitals, beds.

---
## Exploratory Analysis & Visualizations
### Summary Statistics
1. Total physicians, average physicians per city
2. Total hospitals and beds across all cities
   
   ![Screenshot 2025-04-21 203157](https://github.com/user-attachments/assets/b6af6bc7-993f-4b82-afe8-8d957e22e3f1)

###  Visualizations
**Bar Chart**: Distribution of doctors across cities.

   ![Screenshot 2025-04-21 203926](https://github.com/user-attachments/assets/9ef87222-a7fe-4140-9902-0c42c723181f)

**Scatter Plot**: Correlation between hospitals and beds.

![Screenshot 2025-04-21 204048](https://github.com/user-attachments/assets/5db6ba73-f35d-424d-b112-e45f6d795df1)

**Histogram**: Cities categorized by Social Security Recipients.

![Screenshot 2025-04-21 204238](https://github.com/user-attachments/assets/d4bb3496-3f61-478b-b82b-ee600901798e)

---
## Healthcare Risk Analysis
- Cities with **high Medicare rates but low physician availability** need urgent attention.
  
![Screenshot 2025-04-21 204440](https://github.com/user-attachments/assets/a8acb1e3-e7d9-4439-9193-525201a882a7)

- Some cities have **many hospitals but few beds**, indicating inefficiency.

![Screenshot 2025-04-21 204527](https://github.com/user-attachments/assets/231cdda4-48ff-486a-a67f-102cb4f15ae0)
 
- **Outlier detection** (via scatter plots and color-coded visuals) identified cities with unusual healthcare distributions.
   - A city with many physicians but low physicians' rate may be an underserved population
   - Z score calculation : Z_Score_NumMDs = (MetroHealth83[NumMDs]- AVERAGE(MetroHealth83[NumMDs]))/STDEV.P(MetroHealth83[NumMDs])
     
     ![Screenshot 2025-04-21 205421](https://github.com/user-attachments/assets/fb0e1e61-2cea-443c-91f0-113eb8b4d063)

   - A city with many beds but low bed rate may be an underserved bed
   - Z score calculation: Z_Score_NumBeds = ((MetroHealth83[NumBeds])-AVERAGE(MetroHealth83[NumBeds]))/STDEV.P(MetroHealth83[NumBeds])

     ![Screenshot 2025-04-21 205918](https://github.com/user-attachments/assets/f81e4d01-af47-419a-9798-b07a15e88be2)

   - Here bright color indicates cities with high percentage and high Medicare rate

     ![Screenshot 2025-04-21 210048](https://github.com/user-attachments/assets/d0fd328f-0fd6-4a50-9cf1-68f6b45f7326)

---

## Data Analysis Techniques
### Univariate Analysis
- Distribution of key metrics like:
  -  Doctors, hospitals, beds
    
    ![Screenshot 2025-04-21 210159](https://github.com/user-attachments/assets/5d622a9d-e777-433a-bcf3-e9ca5b5124a8)

  -  Social security (SSI) recipients
     - Dax Calculation : 	SSIRateRange = IF(MetroHealth83[SSIRate]>0 && MetroHealth83[SSIRate]<= 1000,"0-1000",IF(MetroHealth83[SSIRate]>1000 && MetroHealth83[SSIRate]<= 2000,"1001-2000",IF(MetroHealth83[SSIRate]>2000 && MetroHealth83[SSIRate]<= 3000,"2001-3000",IF(MetroHealth83[SSIRate]>3000 && MetroHealth83[SSIRate]<= 4000,"3001-4000","4001-5000"
       
    ![Screenshot 2025-04-21 210319](https://github.com/user-attachments/assets/103d0a2b-496b-4fff-acce-de2bea10387c)

### Bivariate Analysis
-  **Hospital vs Beds** – Strong positive correlation expected.
  
  ![Screenshot 2025-04-21 211249](https://github.com/user-attachments/assets/fdffb8a9-a86f-4582-a35f-3d0cba208557)

-  **SSBRate vs NumRetired** – Measures how well retirement population aligns with social support.
  
  ![Screenshot 2025-04-21 211335](https://github.com/user-attachments/assets/44f5d268-50cb-4d29-beae-37e71089c165)


---

## Feature Engineering
New calculated columns created for deeper insight:
- BedsPerHospital = MetroHealth83[NumBeds]/MetroHealth83[NumHospitals] 
- DoctorsPerHospital = MetroHealth83[NumMDs]/MetroHealth83[NumHospitals] 
- BedsPerDoctors = MetroHealth83[NumBeds]/MetroHealth83[NumMDs]
- RetiredPerHospital = MetroHealth83[NumRetired]/MetroHealth83[NumHospitals]
- MedicareToSSBRatio = MetroHealth83[NumMedicare]/MetroHealth83[SSBNum]
- ResourceEfficiency = (MetroHealth83[NumBeds]+MetroHealth83[NumMDs])/(MetroHealth83[SSBNum]+MetroHealth83[NumRetired])

---

## Key Findings
- **Physician Shortages in Aging Cities** – Risk of medical overload.
- **Hospital Bed Inequality** – Gaps in infrastructure.
- **Rapid Medicare Growth** – Upcoming pressure on systems.
- **Outlier Cities** – Need tailored audits and investments.

---

## Dashboard Snapshot
> _Interactive visuals were created using Power BI

![Screenshot 2025-04-21 213030](https://github.com/user-attachments/assets/764a9418-ac47-4496-87ec-cf6798364756)

 _Decomposition Tree: Retired population vs Infrastructure_

![Screenshot 2025-04-21 212831](https://github.com/user-attachments/assets/4fa5dde4-e831-4546-b738-a28b9c625376)

_Dashboard Overview_

## Recommendations
- Hire more physicians in aging cities.
- Expand hospital bed capacity where shortages exist.
- Audit outlier cities for data accuracy and resource mismatch.
- Use feature engineering for ongoing monitoring.

---

## Real-Wolrd Impact
- **Resource Optimization** – Helps planners target cities with the most need.
- **Health Equity** – Supports underserved cities.
- **Policy Influence** – Evidence-based funding decisions.

---

## Future Enhancements

- Use real-time or recent data (post-2004).
- Add demographic attributes (age, gender, income).
- Build predictive models for shortages.
- Expand analysis to state or national level.

---
