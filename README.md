# 📊 IVT Traffic Analysis Project

## 🧭 1. Objective
The goal of this project was to identify and explain **traffic behavior patterns** across six mobile apps —  
three that were **never marked as IVT (Invalid Traffic)**, and three that were **flagged as IVT** at different points (early, mid, late).

> **Key Question:**  
> *We have 3 apps whose data was not marked as IVT, and 3 apps that were marked IVT at different points of time.  
> Why did some get marked IVT earlier, some later, and some never at all?*

---

## 🧩 2. Data Overview

**Dataset Summary**

| Metric | Description |
|--------|--------------|
| Time Period | ~30 days (hourly data) |
| Total Apps | 6 (App1–App6) |
| IVT Status | 3 Non-IVT, 3 IVT (early, mid, late) |
| Key Variables | IVT%, IDFA Count, UA Ratio (User Agent ratio), Impressions |

**Value Ranges:**
- UA Ratio: `0.2 – 0.8`
- IDFA Count: `1,000 – 35,000 per day`
- IVT%: `0 – 65%` depending on the app

---

## ⚙️ 3. Methodology
1. **Data Cleaning:** Removed missing timestamps and normalized UA ratios.  
2. **Feature Engineering:**  
   - `IVT% = Invalid Traffic / Total Traffic`  
   - `UA Ratio = Unique User Agents / Total Requests`
3. **Visualization:** Plotted hourly trends of IVT%, IDFA, and UA Ratio for all apps.  
4. **Comparative Analysis:** Separated IVT vs Non-IVT apps.  
5. **Pattern Detection:** Examined volatility and correlation patterns before IVT flagging.

---

## 📈 4. App-Wise Numerical Analysis

| App | IVT Status | Avg UA Ratio | Max UA Ratio | Avg IDFA Count | Peak IDFA | IVT% Range | Observation |
|------|-------------|--------------|---------------|----------------|------------|-------------|-------------|
| **App 1** | Non-IVT | 0.31 | 0.38 | 12,340 | 14,210 | 0–1% | Stable organic growth |
| **App 2** | Non-IVT | 0.28 | 0.36 | 10,875 | 12,100 | 0–2% | Consistent, normal trend |
| **App 3** | Non-IVT | 0.34 | 0.42 | 14,980 | 15,900 | 0–3% | Slight fluctuation but no anomalies |
| **App 4** | IVT (Early) | 0.46 | 0.79 | 18,200 | 26,500 | 25–60% | Sudden spike early; IVT flagged quickly |
| **App 5** | IVT (Mid) | 0.39 | 0.63 | 17,600 | 29,700 | 10–50% | Shift in mid-period; gradual IVT growth |
| **App 6** | IVT (Late) | 0.37 | 0.68 | 16,980 | 27,000 | 0–45% | Stable initially, IVT later |

---



## 📊 Power BI Dashboard

Here’s a snapshot of the Power BI dashboard created for the IVT Ad Traffic Fraud Analysis project:


![Power BI Dashboard Screenshot 1](https://github.com/Rishabh1108ch/IVT-Ad-Trafic-Fraud-Analysis/blob/main/PowerBI%20Screenshot%201.png)
![Power BI Dashboard Screenshot 2](https://github.com/Rishabh1108ch/IVT-Ad-Trafic-Fraud-Analysis/blob/main/PowerBI%20Screenshot%202.png)





## 📊 5. Observed Traffic Patterns

### 🟢 Non-IVT Apps (App1–App3)
- **Low volatility:** UA ratio standard deviation `< 0.05`
- **Strong correlation:** IDFA ↔ Traffic `r = 0.82`
- **Stable hourly trend:** no abnormal peaks (>20% deviation)
- **IVT%:** consistently `0–3%`

### 🔴 IVT Apps (App4–App6)
- **High volatility:** UA ratio std. deviation `> 0.15`
- **Weaker correlation:** IDFA ↔ Traffic `r = 0.42`
- **Traffic spikes:** +60–90% within short windows
- **Flag timing:**  
  - App4 → Early (~Day 2)  
  - App5 → Mid (~Day 10–15)  
  - App6 → Late (~Day 20+)

---

## ❓ 6. Analytical Discussion

### Q1. Why did some apps never get marked as IVT?
- Maintained **consistent UA ratios (0.25–0.35)**  
- IDFA growth aligned with genuine impressions  
- Showed **natural daily/weekly traffic rhythm**

### Q2. Why were some apps marked IVT earlier or later?
| IVT Timing | UA Ratio Volatility | IDFA Spike Timing | Pattern |
|-------------|--------------------|-------------------|----------|
| **Early (App4)** | High (Δ +0.33) | Within 24h | Aggressive bot injection |
| **Mid (App5)** | Moderate (Δ +0.22) | Day 10–15 | Slow drift in traffic quality |
| **Late (App6)** | Low initially → sharp rise | Day 20+ | Late-stage inorganic scaling |

---

## 🔍 7. Correlation Summary

| Relationship | Non-IVT (r value) | IVT (r value) | Interpretation |
|---------------|-------------------|----------------|----------------|
| IDFA ↔ Traffic | 0.82 | 0.42 | Fake traffic lowers correlation |
| UA Ratio ↔ IVT% | 0.18 | 0.77 | IVT rises with UA volatility |
| Time ↔ IVT% | 0.05 | 0.65 | IVT increases over time for manipulated traffic |

---

## 💡 8. Key Findings
- **UA Ratio Volatility** is the strongest IVT predictor (corr = 0.77).  
- **Unnatural IDFA surges** precede IVT detection by 1–2 days.  
- **Stable correlation (r > 0.8)** is characteristic of clean traffic.  
- The **timing of IVT detection** depends on how quickly anomalies emerge.

---

## 🧮 9. Conclusion
- Apps with **stable UA ratios and IDFA patterns** remained non-IVT.  
- Apps that **rapidly increased UA diversity** or **showed uncorrelated IDFA growth** triggered IVT flags.  
- **Early IVT detection** corresponds to rapid anomalies; **late IVT** occurs after gradual drift.  
- Monitoring UA ratio trends enables **predictive IVT risk detection**.

---

## ⚡ 10. Recommendations
- 🔹 **Set UA Ratio alert threshold:** Δ > 0.15 from baseline  
- 🔹 **Flag correlation drop:** IDFA ↔ Traffic correlation < 0.5  
- 🔹 **Detect hourly bursts:** Std. deviation > 2σ  
- 🔹 **Build IVT risk score:** Weighted average of UA volatility & IDFA surge  

---

## 🛠️ 11. Tools & Environment
- **Python (pandas, numpy, matplotlib)** – Data cleaning & analysis  
- **Google Colab** – Code execution and plotting  
- **Excel / Sheets** – Summary verification  
- **GitHub** – Project documentation & version control  

📁 *Visual Outputs:*  
- `App1_ivt_idfa_ua_ratio_trend.png`  
- `App2_ivt_idfa_ua_ratio_trend.png`  
- `App3_ivt_idfa_ua_ratio_trend.png`  
- `App4_ivt_idfa_ua_ratio_trend.png`  
- `App5_ivt_idfa_ua_ratio_trend.png`  
- `App6_ivt_idfa_ua_ratio_trend.png`  

---

## 🧾 12. Project Summary (for Portfolio)
**Project:** IVT Traffic Behavior Analytics  
**Tools:** Python, Pandas, Matplotlib, Google Colab  
**Key Outcomes:**
- Analyzed 6 app datasets for IVT traffic patterns.  
- Identified strong link between UA volatility & IVT detection.  
- Quantified traffic anomalies leading to IVT flags.  
- Delivered numeric + visual insights for proactive traffic quality monitoring.  

---

## 📊 13. Sample Insights Dashboard (Optional Add-on)
| Metric | Non-IVT Avg | IVT Avg | Difference |
|--------|--------------|----------|-------------|
| UA Ratio Std. Dev. | 0.04 | 0.18 | +350% |
| IDFA-Traffic Corr. | 0.82 | 0.42 | ↓ 49% |
| Avg IVT% | 1.8% | 43.3% | +41.5% |
| Avg Peak Traffic Jump | +15% | +78% | +63% |

---

> **📌 Summary Insight:**  
> IVT detection directly correlates with **UA ratio instability** and **unrealistic IDFA growth**.  
> By tracking these metrics, ad traffic quality can be monitored and controlled proactively.

---
  
**Tools Used:** Python, Pandas, Matplotlib, Google Colab, Excel  

## 👨‍💼 About the Author

**Rishabh Chandrakar**  
*Data Analytics Enthusiast*  

📍 Passionate about data analytics, visualization, and insights in the field of supply chain and digital traffic analysis.  
📊 Skilled in Python, SQL, R, and Power BI.  

📫 **Connect with me:**  
🔗 [LinkedIn](https://www.linkedin.com/in/rishabh-chandrakar)  
📞 **Phone:** 8963976273

---
