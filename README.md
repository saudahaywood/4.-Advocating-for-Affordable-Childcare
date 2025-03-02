
# **Advocating for Affordable Childcare**

## **Project Overview**
This project explores the **rising cost of childcare** in the United States, analyzing how it affects families financially. The findings are communicated through **social media posts, flyers, and data visualizations** to educate parents and encourage them to vote for candidates who prioritize **affordable childcare policies**. The analysis focuses on **toddler, preschool, and infant care costs**, identifying **trends, regional disparities, and affordability issues**.

## **Target Audience**
- **Parents** struggling with the increasing cost of childcare.
- **Community advocates** and policymakers.
- **General public** interested in economic and social policy.

## **Communication Mediums**
1. **Facebook Post** – Sharing key findings with visuals and a summary of the childcare crisis.
2. **Instagram Reel** – A short video highlighting shocking statistics on childcare costs.
3. **Flyer** – A handout with essential statistics and a call to action for voting on childcare policies.

---

## **Dataset**
- **Source:** National Database of Childcare Prices
- **Features:**
  - `State_Name`: Name of the state.
  - `County_Name`: County where data was collected.
  - `StudyYear`: Year of data collection.
  - `MFCCToddler`: Cost of toddler care in family childcare centers.
  - `MFCCPreschool`: Cost of preschool care.
  - `_75FCCInfant`: Cost of infant care in family childcare centers.
  - `MHI`: Median Household Income (used to calculate affordability).

---

## **Methodology**
### **1. Data Exploration**
- **Loaded and cleaned** the dataset.
- **Checked for missing values** and outliers.
- **Explored trends in childcare costs** over the years.
- **Compared costs by state and county** to identify regional disparities.

#### **Key Insights:**
- Childcare costs have been **rising steadily** over time.
- **Massachusetts, Washington, D.C., and California** have the highest costs.
- Families in **low-income counties** spend **a significant percentage** of their income on childcare.

---

### **2. Affordability Analysis**
- Calculated **percentage of household income** spent on childcare.
- Identified counties where childcare costs exceed **30% of median income**.
- Found that for **low- and middle-income families**, childcare costs often take up a **large portion of their income**.

#### **Affordability Calculation:**
```python
childcare_df['Toddler_Cost_Percentage_Income'] = (childcare_df['MFCCToddler'] / childcare_df['MHI']) * 100
childcare_df['Preschool_Cost_Percentage_Income'] = (childcare_df['MFCCPreschool'] / childcare_df['MHI']) * 100
childcare_df['Infant_Cost_Percentage_Income'] = (childcare_df['_75FCCInfant'] / childcare_df['MHI']) * 100
```

---

### **3. Data Visualization**
#### **Trend of Childcare Costs Over Time**
```python
import matplotlib.pyplot as plt

# Group data by year and calculate average childcare costs
avg_cost_by_year = childcare_df.groupby('StudyYear')[['MFCCToddler', 'MFCCPreschool', '_75FCCInfant']].mean()

# Plot the trend over time
plt.figure(figsize=(8, 5))
plt.plot(avg_cost_by_year, marker='o')
plt.title('Average Childcare Costs Over Time')
plt.xlabel('Year')
plt.ylabel('Cost ($)')
plt.legend(['Toddler Care', 'Preschool Care', 'Infant Care'])
plt.grid(True)
plt.show()
```
#### **Comparison of Childcare Costs by State**
```python
# Group data by state and calculate average childcare costs
avg_cost_by_state = childcare_df.groupby('State_Name')[['MFCCToddler', 'MFCCPreschool', '_75FCCInfant']].mean()

# Display top 10 states with the highest average toddler childcare costs
print(avg_cost_by_state.sort_values(by='MFCCToddler', ascending=False).head(10))
```

#### **Childcare Costs vs. Household Income**
```python
plt.figure(figsize=(8,5))
plt.scatter(childcare_df['MHI'], childcare_df['MFCCToddler'], alpha=0.5, label='Toddler Care Cost', color='blue')
plt.scatter(childcare_df['MHI'], childcare_df['MFCCPreschool'], alpha=0.5, label='Preschool Care Cost', color='green')

plt.title('Childcare Costs vs Household Income')
plt.xlabel('Median Household Income ($)')
plt.ylabel('Childcare Costs ($)')
plt.legend()
plt.grid(True)
plt.show()
```

---

## **Findings & Insights**
- **Childcare costs have significantly increased** over time.
- **High-income states tend to have more expensive childcare**.
- **Low-income families struggle to afford childcare**, with some spending **over 30% of their income** on it.
- **Lack of government support exacerbates the problem**.

---

## **Challenges & Limitations**
- **Missing Data:** Some counties lacked complete records, requiring imputation.
- **Local Policies Not Considered:** The dataset does not include **subsidies or government assistance programs**.
- **Statewide Averages:** Costs vary **widely** within states, making county-level comparisons more relevant.

---

## **Future Improvements**
1. **Incorporate Policy Data** – Analyze **childcare subsidy programs** by state.
2. **Compare Minimum Wage vs. Childcare Costs** – Investigate how **wages impact affordability**.
3. **Expand the Scope** – Analyze **daycare waitlists and availability** in addition to pricing.
4. **Create an Interactive Dashboard** – Use **Power BI or Tableau** to present findings dynamically.

---

## **Call to Action**
This project **advocates for affordable childcare policies** by highlighting **the financial burden** placed on families. Parents should **vote for candidates** who support childcare subsidies and **push for policy changes** to make childcare more accessible.

**Key Actions for Parents:**
✔️ **Educate yourself** about childcare costs in your state.  
✔️ **Support policies** that reduce childcare costs.  
✔️ **Vote for candidates** who prioritize affordable childcare.  

---

## **Required Libraries**
To run this project, install the necessary Python libraries:
```bash
pip install pandas numpy matplotlib seaborn
```

---

## **References**
- [National Database of Childcare Prices](https://www.acf.hhs.gov/opre/research/project/national-database-of-childcare-prices)
- [U.S. Department of Labor - Childcare Costs](https://www.dol.gov)
- [Child Care Aware of America](https://www.childcareaware.org)
