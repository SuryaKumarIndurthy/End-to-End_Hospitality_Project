# 🏨 AtliQ Hospitality Data Analytics & Business Intelligence
<img width="1232" height="727" alt="Dashboard" src="https://github.com/user-attachments/assets/829a38f4-e940-4385-9488-31f8f48aace4" />

## 📌 Project Overview
**AtliQ Hospitality** is a data analytics and business intelligence project designed to analyze the performance and revenue generation of various hotel properties across multiple cities. By leveraging historical booking data spanning May to July, this project provides a comprehensive dashboard that tracks key hospitality metrics such as Revenue, Occupancy %, Average Daily Rate (ADR), and Revenue Per Available Room (RevPAR). 

The goal of this project is to empower stakeholders to make data-driven decisions to optimize pricing, manage capacity, and understand customer booking behaviors across different platforms and room classes.

## 🎯 Objectives
- Build a dynamic Business Intelligence dashboard to monitor hotel performance week over week.
- Calculate and visualize crucial hospitality metrics (RevPAR, ADR, Occupancy %, Realisation %).
- Analyze revenue contributions by hotel category (Luxury vs. Business), city, and booking platform.
- Evaluate cancellation rates and "No Show" percentages to understand revenue loss and optimize booking realization.

## 🗄️ Data Architecture & Modeling
The dataset consists of 5 primary tables structured in a star schema model [file:11]:

### Dimension Tables
- **`dim_date`**: Contains dates from May to July, week numbers, and day types (Weekend/Weekday).
- **`dim_hotels`**: Contains property IDs, names, categories (Luxury, Business), and cities (Bangalore, Mumbai, Hyderabad, Delhi).
- **`dim_rooms`**: Defines room IDs and room classes (Standard, Elite, Premium, Presidential).

### Fact Tables
- **`fact_aggregated_bookings`**: Records successful bookings and total room capacity aggregated by property and date.
- **`fact_bookings`**: Granular transactional data containing individual booking IDs, booking platforms, check-in/out dates, guest counts, ratings, booking status (Checked Out, Cancelled, No Show), and revenue realized.

## 📊 Key Hospitality Metrics (DAX)
Extensive DAX measures were created to extract actionable insights from the raw data:

| Metric | Description | Formula Logic |
| :--- | :--- | :--- |
| **Revenue** | Total revenue realized based on booking status | `SUM(fact_bookings[revenue_realized])` |
| **Occupancy %** | Ratio of successful bookings to total available capacity | `Total Successful Bookings / Total Capacity` |
| **ADR** | Average Daily Rate; ratio of revenue to total rooms booked | `Revenue / Total Bookings` |
| **RevPAR** | Revenue Per Available Room; measures overall revenue generating performance | `Revenue / Total Capacity` |
| **Realisation %** | Percentage of bookings that successfully checked out | `1 - (Cancellation % + No Show rate %)` |
| **DSRN** | Daily Sellable Room Nights; average rooms ready to sell per day | `Total Capacity / No of days` |
| **DURN** | Daily Utilized Room Nights; average rooms successfully utilized per day | `Total Checked Out / No of days` |

*(Note: The project also includes Week-over-Week (WoW) change percentage metrics for Revenue, Occupancy, ADR, RevPAR, and Realisation to track short-term trends).*

## 💻 Dashboard Features
The resulting BI Dashboard provides an intuitive interface for stakeholders:
- **High-Level KPIs:** Instant visibility into Revenue (1.69bn), RevPAR (7,337), Occupancy (57.8%), and ADR (12.70K).
- **Dynamic Filtering:** Users can filter the entire dashboard by City, Room Class, and specific time frames (Weeks 19-31).
- **Trend Analysis:** A line chart tracking RevPAR, ADR, and Occupancy % over time to identify weekly peaks and troughs.
- **Platform Performance:** A combo chart visualizing Realisation % and ADR across different booking platforms (makeyourtrip, logtrip, tripster, direct online/offline).
- **Property-Level Matrix:** A detailed table breaking down total bookings, capacity, and revenue metrics for individual properties (e.g., AtliQ Grands, AtliQ Exotica).

## 🛠️ Tech Stack
- **Data Visualization & BI:** Power BI 
- **Data Modeling:** Power Pivot / Data Analysis Expressions (DAX)
- **Data Transformation:** Power Query

## 🚀 How to Use
1. Clone this repository to your local machine.
2. Download the `.pbix` file.
3. Open the file in **Power BI Desktop**.
4. Use the slicers at the top of the dashboard to filter by City or Room Class and explore the data.
