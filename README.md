# SkyHack 3.0: A Deep Dive into United Airlines' ORD Operations

### Team: Hacks on Crack (Anshu Rashi, Arihant Sharma)

![Python](https://img.shields.io/badge/Python-3.9+-blue.svg)
![Libraries](https://img.shields.io/badge/Libraries-Pandas%20%7C%20Seaborn%20%7C%20Scikit--learn-orange.svg)
![Status](https://img.shields.io/badge/Status-Completed-success.svg)

### An end-to-end data analysis of United's Chicago O'Hare hub, transforming raw operational data into a predictive scoring model and actionable strategic insights.

---

## 📂 Project Structure

This repository is organized to clearly separate data, code, outputs, and documentation.

```
├── 📁 data/
│   ├── 📄 Flight Level Data.csv
│   ├── 📄 Bag+Level+Data.csv
│   ├── 📄 PNR+Flight+Level+Data.csv
│   ├── 📄 PNR Remark Level Data.csv
│   └── 📄 Airports Data.csv
│
├── 📁 code/
│   ├── 📓 1_EDA_and_Visualization.ipynb
│   ├── 📓 2_Difficulty_Score_Development.ipynb
│   └── 📓 3_Post_Analysis_and_Insights.ipynb
│
├── 📁 output/
│   ├── 📄 test_Hacks_on_Crack.csv
│   └── 🖼️ visualizations/
│       ├── viz_delay_by_carrier_and_day.png
│       └── ... (all other generated charts)
│
├── 📁 report/
│   └── 📄 Final_Presentation.pdf
│
└── 📄 README.md
```

---

## 🎯 The Challenge

Frontline teams at United Airlines are tasked with ensuring every flight departs on time. However, operational complexity varies significantly between flights due to factors like tight ground times, high passenger loads, complex baggage transfers, and extensive passenger service needs. The current method of identifying these "difficult" flights relies on manual processes and local team experience, which is inconsistent and not scalable.

This project, developed for the **SkyHack 3.0 hackathon**, tackles this challenge by building a systematic framework to understand, quantify, and predict flight difficulty.

---

## 🚀 Our Analytical Approach

The project was structured into three core stages, reflecting a complete data science workflow from exploration to recommendation.

### 1. Exploratory Data Analysis (EDA) & Visualization
Before building any models, a deep dive into the five provided datasets was conducted to understand the operational landscape at ORD. Relational charts were created to uncover deeper patterns, such as how departure delays fluctuate by carrier type and hour of the day, revealing critical operational choke points.

*Example Insight: Average departure delays for both Mainline and Express carriers spike during the evening rush hour (4-8 PM), indicating a critical period for resource allocation.*


### 2. Flight Difficulty Score Development
The centerpiece of the project is a systematic, daily-level scoring model that resets every day to provide a relative measure of complexity.

-   **Feature Engineering:** A robust set of features was engineered to capture the primary drivers of difficulty, including **Ground Time Pressure**, **Baggage Complexity**, **Passenger Service Needs**, and various **Flight Characteristics**.
-   **Scoring Logic**:
    1.  **Daily Normalization:** Features are scaled daily using a Min-Max scaler. This ensures a flight's score is relative to the complexity of *that day's* operations.
    2.  **Weighted Sum**: The normalized features are combined into a final score (1-100) using a weighted sum, with weights informed by the EDA findings.
    3.  **Ranking & Classification**: Flights are ranked daily, and classified into **Difficult**, **Medium**, or **Easy**.

### 3. Post-Analysis & Actionable Insights
The final step translates the data-driven scores into strategic business recommendations.

-   **Difficult Destinations**: The analysis identified that major hubs (e.g., DEN, SFO, LAX) and international destinations (LHR) were consistently the most difficult to manage.
-   **Primary Drivers**: For these destinations, the key drivers were not just high passenger loads, but more specifically **high volumes of transfer bags** and **a large number of special service requests (SSRs)**.
-   **Actionable Recommendations**:
    -   **Targeted Baggage Handling**: Pre-assign dedicated teams to flights flagged with high transfer bag complexity.
    -   **Proactive Passenger Service**: Stage customer service staff at gates for flights with high predicted SSR counts before boarding begins.
    -   **Dynamic Operational Monitoring**: Actively monitor flights with severe ground time pressure to enable proactive crew reallocation.

---

## 🛠️ How to Use This Repository

#### Prerequisites
-   Python 3.8+
-   Jupyter Notebook or any Python IDE
-   Required libraries: `pandas`, `numpy`, `matplotlib`, `seaborn`, `scikit-learn`

#### Setup & Execution
1.  **Clone the repository:**
    ```bash
    git clone [your-repository-url]
    cd [repository-name]
    ```

2.  **Install dependencies:**
    *(It is recommended to create a `requirements.txt` file by running `pip freeze > requirements.txt` in your terminal).*
    ```bash
    pip install -r requirements.txt
    ```

3.  **Run the analysis:**
    Execute the Jupyter Notebooks in the `/code` directory in numerical order:
    -   `1_EDA_and_Visualization.ipynb`: To explore the data and see the initial charts.
    -   `2_Difficulty_Score_Development.ipynb`: To run the full pipeline and generate the final submission file.
    -   `3_Post_Analysis_and_Insights.ipynb`: To analyze the results and generate the final insights.

The primary output, **`test_Hacks_on_Crack.csv`**, will be generated in the `/output` folder upon running the second notebook.
