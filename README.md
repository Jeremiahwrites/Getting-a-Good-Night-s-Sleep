
# 💤 Sleep Health & Lifestyle Analysis

**Client:** SleepInc
**Project:** SleepScope Data Insights
**Tools:** Python, Pandas

---

## 📌 Project Overview

SleepInc provided anonymized user data from their sleep tracking app **SleepScope**, with the goal of uncovering how lifestyle factors influence sleep quality.

This project explores relationships between:

* 🏃 Physical activity
* 🧑‍💼 Occupation
* ⚖️ BMI category
* 😰 Stress levels
* 🛌 Sleep duration & quality

The dataset contains **374 individuals** with averaged health and lifestyle metrics over a six-month period.

---

## 📂 Dataset

**File:** `sleep_health_data.csv`
**Records:** 374 individuals
**Features:** 13 columns

Key variables include:

* Sleep Duration (hours)
* Quality of Sleep (1–10 scale)
* Physical Activity (minutes/day)
* Stress Level (1–10 scale)
* BMI Category
* Occupation
* Sleep Disorder (None, Insomnia, Sleep Apnea)

---

## 🎯 Objectives

* Identify occupations most affected by poor sleep
* Analyze whether sleep duration aligns with sleep quality
* Investigate the relationship between BMI and insomnia
* Extract actionable insights for improving sleep health

---

## 🧪 Methodology

Using **Pandas**, the following steps were performed:

1. Grouped data by **Occupation** to compute:

   * Average sleep duration
   * Average sleep quality

2. Identified:

   * Occupation with the **lowest sleep duration**
   * Occupation with the **lowest sleep quality**

3. Created a derived column:

   * `insomnia_disorder` → Boolean flag for insomnia

4. Calculated:

   * **Insomnia ratios per BMI category**

---

## 📊 Key Findings

### 🧑‍💼 Occupation & Sleep

* **Sales Representatives** have:

  * The **lowest average sleep duration**
  * The **lowest sleep quality**

* ✅ This confirms a strong alignment between **short sleep duration and poor sleep quality** in this occupation.

**Insight:**
High-pressure, target-driven roles may significantly impact both quantity and quality of sleep.

---

### ⚖️ BMI & Insomnia Risk

| BMI Category | Insomnia Ratio |
| ------------ | -------------- |
| Normal       | 0.04           |
| Overweight   | 0.43           |
| Obese        | 0.40           |

**Insights:**

* Individuals with **Overweight and Obese BMI** categories show a **~10x higher likelihood of insomnia** compared to those with Normal BMI.
* Normal BMI individuals have **minimal insomnia prevalence (4%)**.

**Interpretation:**
There is a strong association between **higher BMI and sleep disorders**, especially insomnia.

---

### 🔍 Pattern Summary

* Poor sleep duration often correlates with poor sleep quality
* Occupation plays a **critical role in sleep health**
* BMI is a **major risk factor for insomnia**
* Lifestyle factors likely interact (stress, activity, work demands)

---

## 💡 Business Recommendations for SleepInc

Based on these insights, SleepInc can:

### 1. 🎯 Target High-Risk Occupations

* Create tailored sleep programs for **Sales professionals**
* Offer stress management and recovery tools

### 2. 🏃 Promote Healthy Lifestyle Habits

* Encourage physical activity through in-app nudges
* Integrate fitness tracking insights

### 3. ⚖️ BMI-Based Personalization

* Provide targeted sleep improvement plans for:

  * Overweight
  * Obese users

### 4. 📈 Predictive Sleep Insights

* Build models to **predict sleep disorders** using:

  * BMI
  * Stress
  * Occupation

---

## 🧾 Code Snippet

```python
import pandas as pd

sleep_health = pd.read_csv('sleep_health_data.csv')

# Lowest sleep duration by occupation
occupation_sleep = sleep_health.groupby('Occupation')['Sleep Duration'].mean()
lowest_sleep_occ = occupation_sleep.sort_values().index[0]

# Lowest sleep quality by occupation
sleep_quality = sleep_health.groupby('Occupation')['Quality of Sleep'].mean()
lowest_sleep_quality_occ = sleep_quality.sort_values().index[0]

# Compare both
same_occ = lowest_sleep_occ == lowest_sleep_quality_occ

# BMI vs insomnia
sleep_health['insomnia_disorder'] = sleep_health['Sleep Disorder'] == 'Insomnia'
ratio_series = sleep_health.groupby('BMI Category')['insomnia_disorder'].mean()
bmi_insomnia_ratios = ratio_series.round(2).to_dict()
```

---

## 🚀 Conclusion

This analysis highlights how **work demands and physical health significantly impact sleep outcomes**.

The strongest signals observed:

* Occupation affects both **sleep duration and quality**
* BMI is strongly linked to **insomnia prevalence**

These insights can help SleepInc build **smarter, personalized sleep solutions** and improve user well-being.

---

## 👨‍💻 Author

**Kehinde Olalekan Jeremiah**

* Data Analyst | Python | SQL | Data Visualization

---
