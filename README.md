# F1-Sponsorship-Insights - Identifying Top Teams and Rising Drivers (2021–2024)
A data-driven exploration of Formula 1 performance between 2021–2024 — uncovering which teams deliver the strongest brand exposure and which young drivers show championship-level potential.

**Data Cleaning Notes :**
The available data has NULLS across the board prior to 2021.
So, all records prior to 2021 are deleted on Excel, manually.
All rows with "\N" are replaced with "" for use on Google Big Query.
No other cleaning is necessary.
<br><br>

## Option 1 - High budget option

**“Which F1 team delivers the greatest sponsorship visibility and performance worldwide to maximize our brand’s exposure and prestige?”**

Basically, we need to identify which team who scored the highest between 2021 and 2024 season.

<h3>🏎️ Data / Tables Used</h3>
<p><em>(These three need to be joined to create the full dataset.)</em></p>

<table>
  <tr>
    <th>File Name</th>
    <th>Description</th>
    <th>Purpose</th>
  </tr>
  <tr>
    <td><b>constructors.csv</b></td>
    <td>Contains F1 team names and references</td>
    <td>Defines <b>who</b> the team is</td>
  </tr>
  <tr>
    <td><b>results.csv</b></td>
    <td>Summarizes race event outcomes (positions, points, etc.)</td>
    <td>Explains <b>what happened</b></td>
  </tr>
  <tr>
    <td><b>races.csv</b></td>
    <td>Lists each race event with date and location</td>
    <td>Identifies <b>when and where</b> it happened</td>
  </tr>
</table>

<img width="768" height="640" alt="tables1" src="https://github.com/user-attachments/assets/2eb5adeb-ca6d-41b3-95bb-23657966d4b4" />




