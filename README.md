# 🏏 PROJECT REPORT: IPL Match Prediction & Data Analysis System

## 📋 Table of Contents
1. [Project Overview](#1-project-overview)
2. [Objective](#2-objective)
3. [System Features & Modules](#3-system-features--modules)
4. [Hardware & Software Requirements](#4-hardware--software-requirements)
5. [Database Schema & Data Models](#5-database-schema--data-models)
6. [System Workflow & Logic](#6-system-workflow--logic)
7. [Known Limitations](#7-known-limitations)
8. [Future Enhancements](#8-future-enhancements)
9. [Conclusion](#9-conclusion)

---

## 1. Project Overview
The **IPL Match Prediction & Data Analysis System** is a professional, offline-first database application built entirely in **Microsoft Access**. It serves as a comprehensive data management tool designed to analyze historical Indian Premier League (IPL) statistics, manage match records, and facilitate a competitive prediction environment. 

By eliminating the need for complex cloud setups or external APIs, this system relies purely on structured relational database principles to deliver data-driven insights through SQL queries and integrated data visualization.

---

## 2. Objective
The primary objective of this project is to demonstrate the practical application of Relational Database Management Systems (RDBMS). It provides a self-contained environment to:
* Store and organize large sets of historical sports data.
* Allow users to submit and track match outcome predictions.
* Automatically compute prediction accuracy and generate participant rankings.
* Visualize team performance and venue-specific trends using built-in charting tools.

---

## 3. System Features & Modules

### 📊 Performance Dashboard Module
* **Team Performance Charts:** Visual representation of total wins and loss ratios per team.
* **Venue Analysis:** Insights into how teams perform at specific stadiums.
* **Live Stats:** Real-time aggregation of match data via the `Match Summary` query.

### 🔮 Prediction Engine Module
* **User Submissions:** Interface to record predictions for any scheduled or historical match in the database.
* **Automated Scoring:** The system automatically compares the `PredictedWinner` against the `ActualWinner` to award calculation points.
* **Accuracy Tracking:** A dedicated `Accuracy Query` calculates the success percentage of predictions over time.

### 🏆 Leaderboard & Rankings Module
* **Global Standings:** Identifies the top-performing predictors via the `User_Ranking` query.
* **Point System:** Automatically aggregates points from the `Predictions` table and updates the `Users` table cumulative score.

---

## 4. Hardware & Software Requirements

### Software Requirements
* **Database Engine:** Microsoft Access 2016 (or higher) / ACE Engine
* **Query Language:** SQL (Structured Query Language)
* **Operating System:** Windows 10 / Windows 11
* **UI Framework:** MS Access Integrated Forms & Reports

### Hardware Requirements
* **Processor:** Intel Core i3 / AMD Ryzen 3 or higher
* **RAM:** Minimum 4 GB (8 GB recommended for large query processing)
* **Storage:** At least 50 MB of free disk space for the `.accdb` file and future data expansion.

---

## 5. Database Schema & Data Models

The application relies on a strictly typed, normalized relational schema consisting of three core tables:

### Table 1: Matches
Stores the official schedule and outcomes of all IPL games.
| Field Name | Data Type | Description |
| :--- | :--- | :--- |
| `MatchID` | AutoNumber | Primary Key - Unique identifier for the match |
| `Team 1` | Short Text | Name of the first competing team |
| `Team 2` | Short Text | Name of the second competing team |
| `Venue` | Short Text | Stadium where the match is played |
| `ActualWinner` | Short Text | The verified team that won the match |

### Table 2: Predictions
Logs all participant entries and links them to specific matches.
| Field Name | Data Type | Description |
| :--- | :--- | :--- |
| `PredictionID` | AutoNumber | Primary Key |
| `UserID` | Number | Foreign Key linking to the User |
| `MatchID` | Number | Foreign Key linking to the Match |
| `PredictedWinner`| Short Text | The team chosen by the user to win |
| `PointsEarned` | Number | Calculated value (e.g., 10 for Win, 0 for Loss) |

### Table 3: Users
Manages participant profiles.
| Field Name | Data Type | Description |
| :--- | :--- | :--- |
| `UserID` | AutoNumber | Primary Key |
| `UserName` | Short Text | Name of the participant |
| `TotalPoints`| Number | Aggregated score from all successful predictions |

---

## 6. System Workflow & Logic

1. **Data Entry Phase:** Match details (teams, date, venue) are populated into the `Matches` table. Participant details are added to the `Users` table.
2. **Prediction Phase:** A user submits a prediction. The system creates a new record in the `Predictions` table linking their `UserID` to the specific `MatchID`.
3. **Validation & Calculation Phase (SQL Logic):**
   * The system performs an `INNER JOIN` between the `Matches` and `Predictions` tables based on `MatchID`.
   * **Condition:** `IF Predictions.PredictedWinner = Matches.ActualWinner`
   * **Action:** Assign `PointsEarned = 10` (or respective point value).
4. **Aggregation Phase:** The `Leaderboard Query` runs a `SUM()` function on `PointsEarned` grouped by `UserID`, sorting the results in `DESCENDING` order to instantly generate the live leaderboard.

---

## 7. Known Limitations
* **Standalone Architecture:** As a desktop-only `.accdb` file, it currently lacks multi-user cloud concurrency.
* **Manual Result Updates:** Match results must be entered manually; there is no live web-scraping or API integration to fetch real-time game outcomes.
* **Platform Dependency:** The system is exclusively reliant on the Windows OS environment to run Microsoft Access natively.

---

## 8. Future Enhancements
* **VBA UI Automation:** Implementing Visual Basic for Applications (VBA) to create an interactive, app-like Navigation Form with automated buttons.
* **Automated Data Imports:** Adding functionality to bulk-import seasonal match schedules from CSV or Excel files.
* **Advanced Metrics:** Incorporating player-specific data (e.g., Man of the Match, top run-scorer) to allow for micro-predictions.

---

## 9. Conclusion
The **IPL Match Prediction & Data Analysis System** successfully leverages Microsoft Access to build a robust, offline database application. It completely streamlines the process of storing cricket statistics while providing an engaging predictive layer. Through the use of relational data structures and complex SQL queries, the project efficiently demonstrates how raw sports data can be transformed into actionable insights, leaderboards, and visual analytics.


## 👨‍💻 Author

**Ashish** — Data Interpretation Mini Project  
BCA Student | Passionate about building practical software

---
## 📜 License

This project is licensed under the **MIT License** — you are free to use, modify, and distribute it with attribution.

```
MIT License — Copyright (c) 2026 Ashish
```

---

<div align="center">

⭐ **If this project helped you, please give it a star!** ⭐  
*Built with ❤️ *

</div>
