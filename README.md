# F1-Sponsorship-Insights - Identifying Top Teams and Rising Drivers (2021–2024)
( written on October 25 2025 )

**Executive Summary :**

This project is made for a luxury brand who wants to advertise through Formula 1 and find the best team or driver to sponsor. Using race data from 2021–2024, the analysis looks at total points, average rank, and fastest laps to measure which teams bring the most exposure and value for sponsors.

The results show that Red Bull Racing gives the highest visibility, leading by +762 points over Mercedes and winning across multiple seasons. Mercedes and Ferrari are also strong choices for brands that value heritage, precision, and global recognition. For smaller budgets, Oscar Piastri stands out as a fast-growing young driver who can connect with a younger audience.

In short, this report helps a luxury brand choose where to invest in F1 — finding the best balance between prestige, visibility, and growth potential.

**Data Cleaning Notes :**
The available data has NULLS across the board prior to 2021.
So, all records prior to 2021 are deleted on Excel, manually.
All rows with "\N" are replaced with "" for use on Google Big Query.
No other cleaning is necessary.
<br><br>

## Option 1 - High budget option

**“Which F1 team delivers the greatest sponsorship visibility and performance worldwide to maximize our brand’s exposure and prestige?”**

Basically, we need to identify which team who scored the highest between 2021 and 2024 season.
<br><br>

<h3>🏎️ Data / Tables Used</h3>
<p><em>(These three need to be joined to create the full dataset.)</em></p>

The tables can be downloaded here :

[tables.zip](https://github.com/user-attachments/files/23136327/tables.zip)
<br><br>

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

<br>

<img width="512" height="427" alt="tables1" src="https://github.com/user-attachments/assets/2eb5adeb-ca6d-41b3-95bb-23657966d4b4" />
<br><br>

The SQL code to join the tables :

[sql - table joins.zip](https://github.com/user-attachments/files/23136300/sql.-.table.joins.zip)
<br><br>

The resulting table is called "f1data".

<img width="231" height="341" alt="table_f1data" src="https://github.com/user-attachments/assets/0d152528-e1d1-49a5-af38-a71b13661188" />
<br><br>

The SQL code to find the top 3 scorer between year 2021 - 2024:

[sql - table top3.zip](https://github.com/user-attachments/files/23136475/sql.-.table.top3.zip)
<br><br>

<img width="450" height="570" alt="chart - top3" src="https://github.com/user-attachments/assets/292efacb-417e-4ad5-98c0-956bd817703c" />

Between 2021 and 2024, Red Bull clearly dominated the Formula 1 field, earning 2,711 total points, far ahead of Mercedes (1,949) and Ferrari (1,794). The large margin highlights Red Bull’s consistent top finishes and superior performance across seasons. Mercedes and Ferrari remained competitive but were unable to match Red Bull’s pace or reliability over the four-year span.

## Conclusion : 
If the budget is high, sponsor the Red Bull team for maximum brand exposure and performance across all key metrics.
<br><br><br>

## Option 2 - Low budget option

**“Which Emerging F1 Drivers Represent the Next Generation of Champions — and Smart Early-Stage Sponsorship Opportunities?”**


A driver with a combined score significantly higher than others would be a promising young talent — a potential future champion.
<br><br>

Next, we are going to use the "drivers" table to create another table out of it for future reference. We call this new table "young_drivers", and we only include drivers who by the end of 2024 season is 25 years of age at the maximum.
<br><br>

**Data Cleaning Notes :**

- two columns are deleted manually in excel, they are "number" and "code", because they dont serve any purpose and are mostly contains '\N' anyway.
- In "dob" column, a few rows of data is ##########. I converted them to ''. Also done manually in excel before I brought them to Big Query.

The SQL Query to process **"drivers"** table and make **"young_drivers"** table :
<br>
[sql - young drivers.zip](https://github.com/user-attachments/files/23136790/sql.-.young.drivers.zip)
<br><br>

Here is the result :
<br>
<img width="835" height="266" alt="query_result_02 - drivers under 25" src="https://github.com/user-attachments/assets/e2ec70bc-ab04-4613-ba9b-d708449cef75" />

There are only 7 drivers who by the end of 2024 season is 25 years of age at the maximum. 
<br><br>

For the following process, we need to join these four tables:

<img width="800" height="512" alt="tables2" src="https://github.com/user-attachments/assets/dffcda1d-766f-447b-bc8d-3be774ee7187" />
<br><br>

The 4 csv tables
<br>
[tables - all four.zip](https://github.com/user-attachments/files/23142016/tables.-.all.four.zip)
<br><br>

The SQL Query to join the 4 tables :
<br>
[sql - four tables.zip](https://github.com/user-attachments/files/23136935/sql.-.four.tables.zip)
<br><br>

The resulting table, **"young_drivers"** table ( replacing the previous table ) :
<br>
<img width="142" height="321" alt="tbl_young_drivers_results" src="https://github.com/user-attachments/assets/60a1b8b4-95ca-42bc-aaa9-8297f4bba4fe" />
<br><br>
Now that we have this table, we can figure out the criteria we need to use to determine which young drivers are the most promising ones by answering these questions :
- Do they have good performance in the past 4 years / between 2021 - 2024 ?
- Can we see their performance improvements over time?
<br><br>

## Young driver's performance between 2021 - 2024 :
<br>
Interpretation:
A driver who consistently finishes in the top 5–10, not just once in a while, ensures your brand gets seen regularly. This can be seen by the number of total points they score.
<br><br>

The SQL Query to extract performance information from **young_drivers_result** table :<br>
[sql - young_drivers_performance.zip](https://github.com/user-attachments/files/23143603/sql.-.young_drivers_performance.zip)
<br><br>

The CSV file :<br>
[table - young_drivers_performance.zip](https://github.com/user-attachments/files/23143941/table.-.young_drivers_performance.zip)
<br><br>

<img width="976" height="271" alt="tbl_young_drivers_performance" src="https://github.com/user-attachments/assets/be270149-7619-45d9-aabf-0707d64e57da" />
<br><br>

**Total Points**       
&nbsp;&nbsp;&nbsp;&nbsp;The larger the value, the better the performance.
	
**Fastest Laps counter**        
&nbsp;&nbsp;&nbsp;&nbsp;Everytime a racer managed to do the fastest lap in any race ( meaning the rank is 1, a score of 1 is added.
	
**Average Rank**                    
&nbsp;&nbsp;&nbsp;&nbsp;If a driver is not achieving fastest lap, he is still ranked. This is his average rank. Lower number is better.
<br><br>

<img width="1190" height="602" alt="chart02 - young_drivers_performance" src="https://github.com/user-attachments/assets/4d2ea1d3-c279-4918-8361-b9e6d8ced5e6" />
<br><br>

Tableau File :<br>
[twb - Young_Drivers_Performance.zip](https://github.com/user-attachments/files/23144289/twb.-.Young_Drivers_Performance.zip)
<br><br>

Based on these results, Oscar Piastri appears to be the most promising young racer. By the end of 2024, he was 23 years old, and his total score was significantly higher than that of the second-place driver, Yuki Tsunoda. Piastri achieved three fastest laps across four seasons, and his overall ranking surpassed the rest — making him the clear standout. However, this result alone doesn’t reveal how a driver’s performance has changed over time. To understand that, we need to dig deeper — does the driver’s performance improve, decline, or level off over the seasons? We would not want to sponsor Oscar Piastri if his performance actually went down.
<br><br>

The SQL Query to extract annual performance information from **young_drivers_result** table :<br>
[sql - young_drivers_overtheseasons.zip](https://github.com/user-attachments/files/23143839/sql.-.young_drivers_overtheseasons.zip)
<br><br>

The CSV file :
[table - young_drivers_overtheseasons.zip](https://github.com/user-attachments/files/23145072/table.-.young_drivers_overtheseasons.zip)
<br><br>

<img width="969" height="474" alt="tbl_young_drivers_overtheseasons" src="https://github.com/user-attachments/assets/9782f7e8-4c56-49f7-b188-63b734f40a51" />
<br><br>

<img width="1387" height="789" alt="chart03 - young_drivers_overtheseasons" src="https://github.com/user-attachments/assets/3a51a761-45ea-418e-9d32-5aa7c4d7c8ed" />
<br><br>

Tableau File :<br>
[twb - young_drivers_overtheseasons.zip](https://github.com/user-attachments/files/23145074/twb.-.young_drivers_overtheseasons.zip)
<br><br>

## Conclusion : 

Based on the charts, Yuki Tsunoda appears to be the most experienced driver in the group. He has been racing since 2021, giving him four years of experience by the end of 2024. His average ranking of 11.6 places him fourth among the drivers over the past four seasons. However, his performance trend seems to have plateaued — his total points have remained largely flat year over year. Although his cumulative points from 2021 to 2024 trail just behind Oscar Piastri, the lack of growth suggests he may have already reached his peak performance. Therefore, he may not be an ideal choice as our brand ambassador.

Oliver Bearman consistently appears among the top three drivers in these charts. His average ranking places him second overall, putting him ahead of Yuki Tsunoda. However, by the end of 2024, he has only one year of experience — this is evident in the second chart, where a single data point in 2024 indicates that he began racing that year. Although his performance in the fastest lap rankings looks promising, one season of data isn’t enough to assess his long-term potential. For now, it would be premature to consider him as a brand ambassador.

Oscar Piastri has two years of experience by the end of 2024. He started his rookie season with an impressive 82 points and soared to 265 points in his second year. While two years of data may not be enough to fully predict whether he will become a future star, the evidence we have is compelling. His total points are significantly higher than Yuki Tsunoda’s, despite Tsunoda having twice as much experience. **This performance gap alone makes Piastri the strongest candidate for our future brand ambassador.**
<br><br>

## Business Recommendation : 

After analyzing performance data from 2021–2024, two clear sponsorship paths emerge. Each path serves a different strategic objective — immediate prestige vs. long-term brand equity :

**High-budget / Powerful Luxury Brand focus with immediate impact :** 
Red Bull Racing — unmatched dominance, guaranteed global visibility, and strong alignment with high-performance, innovation-driven luxury values.

Recommended Action:

- Secure co-branding or secondary sponsorship rights with Red Bull Racing for the next 2-3 seasons.
- Leverage the team’s dominance to associate your luxury brand with excellence, precision, and performance.
- Integrate sponsorship assets into digital campaigns (race-week drops, limited-edition merchandise, or hospitality partnerships).
<br><br>

**Lower Budget / Long Term Growth-focused :**  
Oscar Piastri — a rising star who offers long-term brand association potential, lower entry cost, and connection with a younger, digitally engaged audience.

Recommended Action:

- Engage Piastri with a multi-year personal endorsement or co-branded campaign (e.g., “The Next Generation of Precision”).
- Begin partnership before peak fame to capture cost efficiency and brand loyalty early.
- Use data-driven storytelling — highlight his trajectory and your brand’s shared pursuit of excellence.


.


















