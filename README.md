# 🎬 CineWave — User Funnel & A/B Test Analysis  
**Portfolio Data Analytics Project (Python • Pandas • Matplotlib • Funnel Modeling • A/B Testing)**  

> This project analyzes the full user conversion funnel of a fictional streaming platform, **CineWave**.  
> The goal is to understand **where users drop off**, **evaluate an A/B onboarding experiment**, and **segment user behavior by device type** to generate real product and growth recommendations.

✅ Funnel Modeling  
✅ A/B Testing  
✅ Conversion Optimization  
✅ Device Segmentation  
✅ Business Recommendations  

---

## ⭐ Executive Summary (TL;DR)

- Final paid conversion rate: **19.6%**
- Biggest drop-off occurs at **onboarding**
- **Web users convert best**, mobile performs the worst
- A/B Test Result: **Variant B slightly improves onboarding, but does not improve subscriptions**
- Recommendation: **Redesign mobile onboarding and improve subscription value proposition**

---

## 📁 Project Structure

cinewave-funnel-analysis/
├── data/
│   ├── events.csv
│   ├── users.csv
│   ├── subscriptions.csv
│   └── content.csv
│
├── notebooks/
│   └── event_data_analysis.ipynb
│
└── README.md


---

## 🧠 Business Problem

CineWave observed that:
- Many users sign up  
- Fewer users engage with content  
- Even fewer become paid subscribers  

### Business Goals:
- Identify where users drop off in the funnel  
- Understand behavioral patterns using segmentation  
- Evaluate an A/B test on onboarding  
- Provide actionable product recommendations to improve activation and revenue  

---

## 📊 Dataset Description

### **events.csv**
- user_id  
- event_timestamp  
- event_type (signup, onboarding_complete, play_video, return_app, subscribe)  
- content_id  
- session_id  

### **users.csv**
- user_id  
- signup_datetime  
- country  
- device_type  
- acquisition_channel  
- initial_plan  
- experiment_variant (A/B)  

### **subscriptions.csv**
- user_id  
- plan_type  
- price  
- renewal_date  

### **content.csv**
- content_id  
- genre  
- length  
- release_year  

---

## 🔁 Funnel Definition

The user conversion funnel follows this sequence:

1. `signup`  
2. `onboarding_complete`  
3. `play_video`  
4. `return_app`  
5. `subscribe`  

---

## 🧹 Step 1 — Data Cleaning & Feature Engineering

Key transformations performed:
- Converted timestamps to datetime format  
- Created:
  - `event_date`
  - `event_hour`
  - `day_since_signup`
- Merged user signup dates into the events table  
- Sorted events chronologically per user  

✅ Outcome: Clean, time-aware dataset ready for funnel modeling.

---

## 🔍 Step 2 — Basic (Unforced) Funnel Analysis

| Step | Users |
|------|--------|
| signup | 2481 |
| onboarding_complete | 2064 |
| play_video | 2924 |
| return_app | 2615 |
| subscribe | 611 |

⚠️ **Observation**  
Some users appear in later steps without appearing in earlier ones.  
This means **the funnel is not sequential** and must be rebuilt using a **forced (true sequential) funnel**.

---

## 🔒 Step 3 — Forced Funnel (True Sequential Funnel)

Only users who completed **all previous steps** are counted.

| Step | Users |
|------|--------|
| signup | 2481 |
| onboarding_complete | 1719 |
| play_video | 1683 |
| return_app | 1463 |
| subscribe | 287 |

### Conversion Rates

| Step Transition | Conversion |
|------------------|------------|
| signup → onboarding | 69% |
| onboarding → play_video | 98% |
| play_video → return_app | 87% |
| return_app → subscribe | **19.6%** |

### 🔥 Key Funnel Insights
- Biggest drop-off happens during **onboarding**
- Users who pass onboarding show **strong engagement**
- **Subscription conversion is weak**, signaling:
  - Pricing friction
  - Weak value proposition
  - Insufficient post-onboarding motivation  

---

## 🧪 Step 4 — A/B Test on Onboarding

CineWave tested a new onboarding experience:
- **Variant A** = Control  
- **Variant B** = New UX  

### Forced Funnel Results

| Step | A Users | B Users |
|------|---------|---------|
| onboarding_complete | 836 | 883 |
| play_video | 820 | 863 |
| return_app | 714 | 749 |
| subscribe | 145 | 142 |

### ✅ A/B Conclusion
- Variant B slightly improves onboarding (~1%)
- Variant A slightly improves subscription (~1%)
- **No statistically meaningful improvement overall**
- ✅ Recommendation: Run a **new onboarding experiment with stronger UX changes**

---

## 📱 Step 5 — Device Type Segmentation

Device Types:
- mobile  
- tablet  
- web  

### Forced Funnel by Device

| Step | Mobile | Tablet | Web |
|------|--------|--------|-----|
| signup | 793 | 829 | 859 |
| onboarding | 537 | 577 | 605 |
| play_video | 526 | 567 | 590 |
| return_app | 452 | 490 | 521 |
| subscribe | 81 | 92 | 114 |

### 📊 Device Insights
- **Web users convert best at every stage**
- **Mobile users struggle the most during onboarding**
- Web UX is strongest → **Mobile onboarding needs redesign**

---

## 📉 Step 6 — Visualizations

The project includes:
- ✅ Full Forced Funnel (All Users)
- ✅ A/B Conversion Rate Comparison
- ✅ Device-Type Funnel Comparison
- ✅ Device-Type Conversion Rate Comparison  

All charts are available in the notebook.

---

## 🧾 Final Business Recommendations

### 1️⃣ Fix Onboarding (Biggest Drop-Off)
- Simplify steps  
- Reduce required fields  
- Add progress indicators  
- Add tooltips or guided tutorial  

### 2️⃣ Improve Mobile Experience
- Mobile has the lowest activation and subscription rate  
- Mobile-first onboarding redesign is critical  

### 3️⃣ Strengthen Subscription Value Proposition
- Low final conversion (19.6%) suggests:
  - Weak perceived value
  - Trial experience could be improved
  - Personalization is missing  

### 4️⃣ A/B Test Needs a Stronger Variant
- Variant B shows **no meaningful uplift**
- Recommend testing:
  - Content previews
  - Rewards on completion
  - Personalized onboarding paths  

### 5️⃣ Future Modeling (Next Iteration)
- Churn prediction  
- Recommendation ranking  
- Content engagement clustering  

---

## 🔧 Tech Stack

- Python  
- pandas  
- numpy  
- matplotlib  
- Jupyter Notebook  
- Funnel Modeling  
- Experimentation (A/B Testing)  
- Segmentation Analysis  
- Feature Engineering  

---

## 🧑‍💼 Who This Project Is For

This project demonstrates skills required for:
- Data Analyst  
- Product Analyst  
- Business Intelligence Analyst  
- Growth Analyst  
- Full-Stack Data Analyst  
- Analytics Engineer  

---

## 🎯 Key Skills Demonstrated

✔ Data Cleaning  
✔ Event Ordering  
✔ Funnel Modeling (Basic + Forced)  
✔ A/B Testing  
✔ Segmentation  
✔ Visualization  
✔ Business Storytelling  
✔ Portfolio-Ready Deliverable  

---

## 📬 Contact

If you’d like to connect or discuss this project:

- **LinkedIn:** *https://www.linkedin.com/in/oumayma-slimani-483776397/?isSelfProfile=true*  
 



