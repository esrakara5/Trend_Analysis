# Trend Analysis with Power BI – Jotun Powder Coatings Quality Control Project

## 1. Introduction

This project was carried out within the Quality Control Department of the Jotun Paints Çerkezköy Powder Coatings Plant. The need arose for a dynamic and interactive data visualization tool to be used in monthly reports presented to upper management. To address this, a **trend analysis study using Power BI** was implemented, aimed at interpreting the data obtained from quality tests and enabling advanced filtering and analysis capabilities.

In general terms, the primary goal of trend analysis is to identify, assess, and eliminate any factors that may negatively affect product quality. Trend analysis serves as a particularly valuable monitoring tool when there are changes in production-related processes.

The **data collection and preparation phase** is a fundamental step for the Quality Control Department. It involves gathering various quality-related measurements such as dimensional tolerances, color consistency, and surface roughness. Additionally, data related to production processes — including production speed, defect rates, and material consumption — are collected.

Once collected, the data is cleaned and organized to ensure accuracy and consistency. Any missing or incorrect entries are corrected or completed. The processed data is stored in databases or electronic formats, making it ready for analysis in Power BI.

---

## 2. Objective

The Quality Control Department collects samples from each production batch and conducts a series of tests to determine compliance with globally standardized quality specifications. Based on the results, each batch is either approved or rejected.

The **objective of this trend analysis** is to identify which product types are most frequently failing quality tests by detecting values that fall inside or outside of specification limits. This enables the department to take preventive and corrective actions accordingly.

If defects are concentrated around a specific test and the values are significantly beyond acceptable limits, the project also aims to evaluate and potentially adjust the specification range for that test. Ultimately, this study supports ongoing **quality improvement** and **process optimization** efforts within the factory.

---

## 3. Scope

A total of **21 quality control tests** are applied within the production facility. However, the specific tests selected vary depending on the **type of coating**, the **environment in which the coating will be used**, and **customer requirements**.

Below is a list of the test codes and their descriptions:

| **Norm Type** | **Description**                        |
|---------------|----------------------------------------|
| QC062         | Colour CieLab                          |
| QC073         | Curing Temperature                     |
| QC074         | Curing Time                            |
| QC075         | Film Thickness                         |
| QC063         | Colour CmC (1:1)                       |
| QC006         | Gloss 60°                              |
| QC017         | Sames Fluidity                         |
| QC009         | Malvern < 10 Micron                    |
| QC011         | Malvern > 80 Micron                    |
| QC010         | Malvern > 32 Micron                    |
| QC016         | Flow and Finish (Visual)               |
| QC004         | Impact Resistance (Direct)             |
| QC005         | Impact Resistance (Reverse)            |
| QC014         | Alpine > 150 Micron                    |
| QC078         | Malvern > 120 Micron                   |
| QC020         | Kleber Tribo – Current                 |
| QC002         | Bend Test – Conical Mandrel            |
| QC065         | Malvern d(0.5)                         |
| QC061         | Flow PCI                               |
| QC015         | Alpine > 250 Micron (N/A)              |
| QC026         | Gel Time – Functional Hot Plate (205°C)|

**Figure 1. Quality Control Test Types**

---

### Focused Tests for Trend Analysis

For the purpose of this trend analysis project, **only the following five tests** were considered. These are referred to under the **"Norm Type"** column in the dataset:

- **QC006** – Gloss 60 deg  
- **QC009** – Malvern < 10 micron  
- **QC010** – Malvern > 32 micron  
- **QC011** – Malvern > 80 micron  
- **QC062** – Colour CieLab  

---

### Data Time Frame and Project Continuity

The dataset used for this project covers the period from **January 10, 2022, to March 8, 2024**. The Power BI dashboard is designed to be **sustainable and updatable**, allowing future data to be seamlessly integrated and analyzed.

---

### Specification Criteria

Each test result is evaluated based on custom-defined thresholds:

- **Inner Min**: Minimum acceptable value  
- **Inner Max**: Maximum acceptable value  

A result is considered:
- **"Within Specification"** if it falls between the Inner Min and Inner Max values  
- **"Out of Specification"** if it is lower than the Inner Min or higher than the Inner Max  

Out-of-specification results are analyzed across various product categories, and appropriate **corrective and preventive actions** are proposed. The ultimate aim is to support continuous improvement in product quality through **data-driven decision-making**.

---

## 4. Methodology

### 4.1 Execution of Tests

---

#### 4.1.1 Gloss Test (QC006)

**Purpose:**  
This test measures the glossiness of the powder-coated film. Gloss is evaluated by directing a beam of light at a fixed angle (commonly 60°) onto the surface and measuring the intensity of light reflected at the same angle.

**Procedure:**  
The glossmeter device is first calibrated. It is then placed on the coated panel, and a reading is taken. The built-in light source shines on the surface at a specified angle, and the reflected light reaches the sensor on the opposite side of the device. The intensity of the reflected light is compared to the source, and a numerical value is calculated in **Gloss Units (GU)**.

![Figure 2: Measuring Gloss with a Glossmeter](https://github.com/esrakara5/Trend_Analysis/blob/main/Visualizations/GLOSSMETRE.png)

---

#### 4.1.2 Particle Size Distribution Test – Malvern  
*(QC009: <10 micron, QC010: >32 micron, QC011: >80 micron)*

**Purpose:**  
This test determines the particle size distribution of powder coatings using laser diffraction technology. Samples are taken from the mill output and analyzed using the Malvern PSD device. Based on the results, production may continue or be halted.

**Procedure:**  
The device is powered on. A sample is added to the chamber using a spatula, and the lid is closed. The test is started via the connected computer by entering the sample name. Once completed, the distribution report is displayed. The closer the values are to the specified range, the more homogeneous the distribution. Coarse or uneven particle sizes can negatively affect gloss.

![Figure 3: Particle Size Analyzer](https://github.com/esrakara5/Trend_Analysis/blob/main/Visualizations/tdoc.png)

---

#### 4.1.3 Color Measurement Using Spectrophotometer (QC062 – Colour CieLab)

**Purpose:**  
Spectrophotometers are used to measure and evaluate the color of coated surfaces, making it a vital part of quality control in paint production.

**Procedure:**  
Panels coated with the reference and comparison materials are used for readings. A circular scratch is made on the panel at standard film thickness, and readings are taken from this area using a spectrophotometer. This method is commonly used across industries such as paint, textiles, plastics, and printing.

**Measured Parameters:**

- **L (Lightness):** 0 (black) to 100 (white)  
- **a:** +a = red, –a = green  
- **b:** +b = yellow, –b = blue  

Readings are evaluated with the **Delta E (ΔE)** value, which measures the visible color difference between two samples.

> ΔE = √((L₂ − L₁)² + (a₂ − a₁)² + (b₂ − b₁)²)

- **ΔE ≤ 1.0:** Invisible to the human eye  
- **ΔE > 3.0:** Visible difference requiring correction  

If color deviation is found, corrective pigments are added to bring the product back within specifications.

![Figure 4: Spectrophotometer Device](https://github.com/esrakara5/Trend_Analysis/blob/main/Visualizations/spektro.png)

![Figure 5: ΔE Calculation Result](https://github.com/esrakara5/Trend_Analysis/blob/main/Visualizations/testresult.png)

---

### 4.2 Reporting

In order to ensure the reporting system is sustainable, dynamic, and interactive—and actively used within the plant—**Power BI** was selected as the main reporting tool. The reporting interface is divided into two main parts:

- **Trend Analysis Result**
- **Out of Spec Analysis**

---

#### Trend Analysis

To enable detailed observation, a comprehensive table was first created. The column headers include:

- `Year`
- `Month`
- `Day`
- `Part No`
- `Norm Type`
- `Norm Type Description`
- `Inner Max`
- `Inner Min`
- `Result`
- `Result Status`

![Figure 6. Trend Analysis – Power BI Dashboard](https://github.com/esrakara5/Trend_Analysis/blob/main/Visualizations/trendanalysis.png)


![Figure 7. Trend Analysis Table View](https://github.com/esrakara5/Trend_Analysis/blob/main/Visualizations/ta_table.png)

To highlight whether the `Result` value falls within the specification range, a calculated column named `Result Filter` was created in Power BI Query Editor. This checks if the value lies between `Inner Min` and `Inner Max`. Based on this filter, **conditional formatting** with icons was applied to the `Result` column.

![Figure 8. Conditional Formatting for Result Status](https://github.com/esrakara5/Trend_Analysis/blob/main/Visualizations/kb.png)

To allow users to dynamically filter and explore data, several **slicers** were added:

- Time (Date)
- Norm Type (Test Type)
- Part Definition
- Order Number

Users are restricted to selecting only **one test type at a time** to avoid confusion. Search functionality is also enabled within slicers to handle the high volume of order and part numbers.

![Figure 9. Slicers for Trend Analysis](https://github.com/esrakara5/Trend_Analysis/blob/main/Visualizations/slicer.png)

A pie chart was created to display the **specification distribution** of results based on the selected filters, along with percentage values.

![Figure 10. Specification Distribution Chart](https://github.com/esrakara5/Trend_Analysis/blob/main/Visualizations/spek_dis.png)

A **line chart** was implemented to track deviation trends. It visualizes whether results deviate from specifications and by how much across tests. The X-axis shows `Analysis No`, while the Y-axis displays `Avg Result`, `Avg Inner Max`, and `Avg Inner Min`.

![Figure 11. Line Chart – Trend Analysis Graph](https://github.com/esrakara5/Trend_Analysis/blob/main/Visualizations/ta_grap.png)  

![Figure 12. Specification Analysis Visualization](https://github.com/esrakara5/Trend_Analysis/blob/main/Visualizations/spec_analysis.png)

---

#### Out of Specification Analysis

All out-of-spec results are displayed in a detailed, easily interpretable layout. As in the Trend Analysis page, this view also includes date, part number, part description, and order number slicers—which can be used individually or in combination.

A **Top N slicer** was created to allow filtering the **Top 20 products with the highest non-conformance** values.

![Figure 13. Top 20 Products with Most Deviations](https://github.com/esrakara5/Trend_Analysis/blob/main/Visualizations/top20.png)

A **donut chart** visualizes the distribution of out-of-spec values across different test types.

![Figure 14. Test-Wise Distribution of Out-of-Spec Results](https://github.com/esrakara5/Trend_Analysis/blob/main/Visualizations/donut.png)

The same formatted table and icons from the Trend Analysis page are used here as well. A **bar chart** comparing in-spec and out-of-spec results by test type is also included to allow easy benchmarking.

![Figure 15. Comparison of Test Results by Specification Status](https://github.com/esrakara5/Trend_Analysis/blob/main/Visualizations/comp.png)

---

This structured Power BI reporting system provides actionable insights, real-time filtering, and trend monitoring capabilities that support quality improvement and decision-making processes.

---

### 5. Conclusion

The results obtained from the trend analysis and out-of-specification evaluation were thoroughly examined. Among all test types, the one that most frequently produced out-of-spec values was **QC062 – Colour CieLab**, measured using a spectrophotometer to determine L, a, b values. This finding was communicated to the laboratory for further investigation, improvement studies, and necessary corrective actions.

In addition, for the **Top 20 products** with the highest non-conformance rates, the R&D department was informed to verify whether the issues might be related to the product formulation (recipe). The laboratory was also consulted to conduct improvement studies on these specific products and to investigate the root causes of the issues observed.

Due to corporate confidentiality policies, no further details regarding the outcomes can be disclosed within this report.








