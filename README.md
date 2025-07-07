# Dynamic-Pricing-For-Urban-Parking-Lots
A

---

## 📌 **Title:**

Dynamic-Pricing-For-Urban-Parking-Lots

---

## 🎯 **Project Goal**

The aim is to develop an intelligent pricing system that continuously updates parking fees for urban lots in response to real-time factors like current occupancy, wait lines, surrounding traffic, vehicle category, timestamp, and competing lots in close proximity.

---

## 🗂️ **Problem Context**

Urban centers struggle with inefficient parking usage due to static price structures. This mismatch between demand and fixed prices leads to overcrowded lots or underused spaces. This project solves that by introducing a real-time, data-driven pricing mechanism that adapts on the fly to live demand signals.

---

## ✔️ **Key Objectives**

* Develop a dynamic price calculation for each parking lot that:

  * Reacts instantly to:

    * Past occupancy trends
    * Queue lengths
    * Local traffic flow
    * Event days or special occasions
    * Vehicle category (bike, car, truck, etc.)
    * Nearby competitor lot prices
  * Starts with a standard base fee of **\$10**
  * Ensures price adjustments remain gradual and logically justifiable, avoiding sudden swings

---

## 📈 **Dataset Details**

The dataset consists of **18,368 entries** covering **14 parking lots** across a **73-day period**, with:

* **Location:** Latitude & Longitude
* **Lot Capacity:** Maximum vehicle limit
* **Occupancy:** Number of vehicles currently parked
* **Queue:** Count of vehicles waiting
* **Vehicle Type:** Cycle, bike, car, truck, etc.
* **Traffic Level:** Classified as low, medium, or high
* **Special Days:** Indicator for holidays or events
* **Timestamps:** Date and time data for each record

---

## 🛠️ **Technology Stack**

| Category          | Tools / Libraries                   |
| ----------------- | ----------------------------------- |
| **Programming**   | Python                              |
| **Data Handling** | pandas, numpy                       |
| **Streaming**     | pathway (real-time processing)      |
| **Time Handling** | datetime, time                      |
| **Visualization** | bokeh, matplotlib                   |
| **Pricing Logic** | Custom rule-based calculations      |
| **Output**        | Interactive Bokeh plots, PNG charts |

---

## 🗺️ **Solution Architecture (Mermaid Diagram)**

```mermaid
graph TD

A[Raw Data (CSV)] --> B[Cleaning & Merging Timestamps (pandas)]
B --> C[Stream Table (Pathway)]
C --> D[Pricing Logic: Model 1, Model 2, Model 3]
D --> E[Dynamic Price Computation]
E --> F[Pathway Output Table]
F --> G[Live Line Chart (Bokeh)]
F --> H[Nearby Lots Bar Chart (Bokeh)]
G --> I[Dashboard & Reports]
H --> I
```

---

## ⚙️ **Models Developed**

**➊ Model 1: Basic Linear Adjuster**

* **Formula:**
  `Price = Last_Price + α × (Occupancy ÷ Capacity)`
* Uses a straightforward link between occupancy and price.
* Serves as a baseline to compare more advanced strategies.
* Tuning parameter: α (rate of price change); price always stays within lower/upper limits.

---

**➋ Model 2: Multi-Factor Demand Pricing**

* **Demand Formula:**
  `Demand = α×Occupancy + β×Queue + γ×Traffic + δ×Event + ε×VehicleWeight`
  `Price = Base_Price × (1 + λ×Normalized_Demand) × Vehicle_Weight`
* Blends multiple real-world influences into a single demand score.
* Includes vehicle-specific pricing (e.g., heavier vehicles may pay more).
* Traffic levels and special days act as demand boosters.
* Uses `tanh` normalization to keep pricing changes stable.

---

## 📌 **Implementation Highlights**

**✔️ Real-Time Data Pipeline**

* **Pathway Streaming:** Ingests and processes live records in timestamp order.
* **Live Price Updates:** Computes prices for each lot on each tick.
* **Scalable Setup:** Capable of handling dozens of lots concurrently.

**📊 Interactive Visualization Dashboard**

* **Bokeh Plots:** Real-time line graphs for price tracking per lot.
* **Comparative Charts:** See current lot price vs. competitors in the vicinity.
* **Demand Insight:** Show demand scores evolving over time.
* **Geospatial Mapping:** Visualize competitive pressure geographically.

**💡 Business Insights**

* **Smart Routing:** Suggests alternative lots when one is full or overpriced.
* **Competitive Monitoring:** Keeps tabs on surrounding lot rates.
* **Peak Demand Patterns:** Highlights high-traffic times and days.
* **Revenue Boost:** Supports optimal pricing to balance occupancy and revenue.

---


---

If you’d like, I can prepare this as a **PDF/Word report**, a **PowerPoint pitch**, or a **Colab-ready notebook template** — just say **`yes`** and I’ll generate it for you! 🚀
