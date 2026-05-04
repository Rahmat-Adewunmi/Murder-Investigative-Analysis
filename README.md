## 🕵️‍♂️ Solving the Murder of Roland Greene

## 📌 Project Overview
This project is a data-driven investigation into the murder of Roland Greene, a prominent art collector who was found dead in the Vault Room of his private estate at exactly 8:00 PM. Notably, he received a phone call at 7:55 PM—just minutes before his death.
Although all 30 guests present at the estate claimed to have solid alibis, the evidence suggests that one of them is not telling the truth.
Using structured datasets and SQL-based analysis, this project aims to uncover inconsistencies in the suspects’ stories, reconstruct the sequence of events, and ultimately identify the individual responsible for the crime. It demonstrates my ability to work with relational data, perform investigative analysis, and draw meaningful conclusions from complex datasets.

## 🎯 Objectives
Analyze suspect behavior using access logs, call records, and forensic data
Identify suspicious patterns such as unusual access attempts or inconsistent timelines
Detect contradictions between alibis and actual recorded activities
Reconstruct a timeline of events leading up to and following the murder
Present a clear, data-backed conclusion identifying the most likely suspect
Visualize key events or timelines to support findings

## 📊 Dataset Description
The analysis is based on four key tables:
#### 1. Access Logs Table
Tracks movement within the estate.
log_id
suspect_id
access_time
door_accessed
success_flag
#### 2. Call Records Table
Captures phone activity of suspects.
call_id
suspect_id
call_time
call_duration
recipient_relation
#### 3. Forensic Events Table
Contains key forensic timestamps and observations.
event_time
event_description
#### 4. Suspects Table
Provides background information on all individuals present.
suspect_id
name
role
relation_to_victim
alibi

## 🧠 Methodology
The investigation began by combining multiple datasets to create a comprehensive view of each suspect’s activities.
First, I performed joins across the Access Logs, Call Records, and Suspects tables to identify individuals who both moved within the estate and made phone calls around the time of the murder.
 
_SELECT s.suspect_id,c.call_time,c.call_duration,s.name,a.access_time,a.door_accessed,
a.success_flag,s.relation_to_victim, s.alibi
FROM  suspects s
JOIN  call_records c
ON s.suspect_id = c.suspect_id
JOIN access_logs a
ON c.suspect_id = a.suspect_id
WHERE call_time > '2025-06-01 19:50:00.0000000'
ORDER BY call_time desc_

I then narrowed the analysis by examining:
Access Logs + Suspects to track physical movement
Call Records + Suspects to analyze communication patterns
This step-by-step breakdown allowed me to compare each suspect’s claimed alibi against their actual recorded behavior.

_SELECT s.suspect_id,s.name,a.access_time,a.door_accessed,
a.success_flag,s.relation_to_victim, s.alibi
FROM  suspects s
JOIN access_logs a
ON s.suspect_id = a.suspect_id
WHERE access_time > '2025-06-01 19:50:00.0000000' 
ORDER BY access_time asc_

_SELECT s.suspect_id,c.call_time,c.call_duration,s.name,s.relation_to_victim, s.alibi
FROM  suspects s
JOIN  call_records c
ON s.suspect_id = c.suspect_id
WHERE call_time > '2025-06-01 19:50:00.0000000' 
ORDER BY call_time desc_

## 🔍 Key Findings
Through detailed querying and cross-referencing of the datasets:
I identified inconsistencies between recorded activities and stated alibis
Detected unusual access attempts and suspicious timing patterns
Narrowed down the list of suspects to five individuals with notable anomalies
Further deep-dive analysis into these five suspects revealed critical insights into their actions before and after the murder.

## 🛠️ Tools & Skills Demonstrated
SQL (Joins, Filtering, Aggregations, Data Cleaning)
Data Analysis & Investigation
Critical Thinking & Problem Solving
Relational Database Exploration
Storytelling with Data

## 🚨 Final Suspect Reveal
Following a comprehensive analysis of access logs, call records, and forensic timelines, the investigation identified a small group of individuals whose activities significantly deviated from their stated alibis. While multiple suspects exhibited suspicious behavior, the evidence ultimately converges on a clear primary suspect.
🔍 Persons of Interest
#### Prime Suspects
Jamie Bennett (Staff)

_SELECT s.suspect_id,s.name,a.access_time,a.door_accessed,
a.success_flag,s.relation_to_victim, s.alibi
FROM  suspects s
JOIN access_logs a
ON s.suspect_id = a.suspect_id
WHERE access_time > '2025-06-01 19:50:00.0000000' AND name = 'Jamie Bennett'
ORDER BY access_time asc

SELECT s.suspect_id,c.call_time,c.call_duration,s.name,s.relation_to_victim, s.alibi
FROM  suspects s
JOIN  call_records c
ON s.suspect_id = c.suspect_id
WHERE call_time > '2025-06-01 19:50:00.0000000' AND name = 'Jamie Bennett'
ORDER BY call_time desc_


Robin Ahmed (Former Partner)

_SELECT s.suspect_id,s.name,a.access_time,a.door_accessed, 
a.success_flag,s.relation_to_victim, s.alibi
FROM  suspects s
JOIN access_logs a
ON s.suspect_id = a.suspect_id
WHERE access_time > '2025-06-01 19:50:00.0000000' AND name = 'Robin Ahmed'
ORDER BY access_time asc_

_SELECT s.suspect_id,c.call_time,c.call_duration,s.name,s.relation_to_victim, s.alibi
FROM  suspects s
JOIN  call_records c
ON s.suspect_id = c.suspect_id
WHERE call_time > '2025-06-01 19:50:00.0000000' AND name = 'Robin Ahmed'
ORDER BY call_time desc_

Samira Shaw (Friend)

_SELECT s.suspect_id,s.name,a.access_time,a.door_accessed, 
a.success_flag,s.relation_to_victim, s.alibi
FROM  suspects s
JOIN access_logs a
ON s.suspect_id = a.suspect_id
WHERE access_time > '2025-06-01 19:50:00.0000000' AND name = 'Samira Shaw'
ORDER BY access_time asc_

_SELECT s.suspect_id,c.call_time,c.call_duration,s.name,s.relation_to_victim, s.alibi
FROM  suspects s
JOIN  call_records c
ON s.suspect_id = c.suspect_id
WHERE call_time > '2025-06-01 19:50:00.0000000' AND name = 'Samira Shaw'
ORDER BY call_time desc_

#### Potential Accomplices

Mason Shaw (Employee)

_SELECT s.suspect_id,s.name,a.access_time,a.door_accessed,   
a.success_flag,s.relation_to_victim, s.alibi
FROM  suspects s
JOIN access_logs a
ON s.suspect_id = a.suspect_id
WHERE access_time > '2025-06-01 19:50:00.0000000' AND name = 'Mason Shaw'
ORDER BY access_time asc_

_SELECT s.suspect_id,c.call_time,c.call_duration,s.name,s.relation_to_victim, s.alibi
FROM  suspects s
JOIN  call_records c
ON s.suspect_id = c.suspect_id
WHERE call_time > '2025-06-01 19:50:00.0000000' AND name = 'Mason Shaw'
ORDER BY call_time desc_

Alex Shaw (Staff)

_SELECT s.suspect_id,s.name,a.access_time,a.door_accessed,   
a.success_flag,s.relation_to_victim, s.alibi
FROM  suspects s
JOIN access_logs a
ON s.suspect_id = a.suspect_id
WHERE access_time > '2025-06-01 19:50:00.0000000' AND name = 'Alex Shaw'
ORDER BY access_time asc_

_SELECT s.suspect_id,c.call_time,c.call_duration,s.name,s.relation_to_victim, s.alibi
FROM  suspects s
JOIN  call_records c
ON s.suspect_id = c.suspect_id
WHERE call_time > '2025-06-01 19:50:00.0000000' AND name = 'Alex Shaw'
ORDER BY call_time desc_

#### Additional Suspect
Victor Shaw (Rival)

_SELECT s.suspect_id,s.name,a.access_time,a.door_accessed, 
a.success_flag,s.relation_to_victim, s.alibi
FROM  suspects s
JOIN access_logs a
ON s.suspect_id = a.suspect_id
WHERE access_time > '2025-06-01 19:50:00.0000000' AND name = 'Victor Shaw'
ORDER BY access_time asc_

_SELECT s.suspect_id,c.call_time,c.call_duration,s.name,s.relation_to_victim, s.alibi
FROM  suspects s
JOIN  call_records c
ON s.suspect_id = c.suspect_id
WHERE call_time > '2025-06-01 19:50:00.0000000' AND name = 'Victor Shaw'
ORDER BY call_time desc_

## 🧠 Analytical Breakdown
#### Inconsistent Alibis
Several individuals provided statements that did not align with recorded call activity or access logs. Notably, the prime suspects showed clear discrepancies between their claimed whereabouts and system-generated timestamps.
#### Suspicious Movement Patterns
Access log data revealed that certain individuals—particularly within the prime suspect group—were active around restricted areas near the time of the murder. These movements were either unexplained or directly contradicted their alibis.
#### Coordinated Activity Indicators
Patterns observed between Mason Shaw and Alex Shaw suggest possible coordination, indicating they may have played supporting roles in enabling or covering up the crime.
#### Motive and Proximity
While Victor Shaw had a clear motive as a rival, the data does not strongly place him at the scene within the critical time window.

#### SQL Evidence Supporting Final Verdict
The query below highlight the inconsistency and suspicious activity that led to identifying Jamie Bennett as the primary suspect.
Access to Restricted Areas Near Time of Death
_SELECT s.name, a.access_time, a.door_accessed, a.success_flag
FROM access_logs a
JOIN suspects s 
    ON s.suspect_id = a.suspect_id
WHERE CAST(a.access_time AS TIME) 
      BETWEEN '19:50:00' AND '20:05:00'
  AND a.door_accessed LIKE '%Vault%'
ORDER BY a.access_time;_

## ⚖️ Final Verdict
After correlating all available evidence, Jamie Bennett emerges as the primary suspect in the murder of Roland Greene.
The data shows that Jamie Bennett’s recorded movements and call activity directly conflict with their alibi, placing them within the vicinity of the Vault Room at the critical time. No other suspect demonstrates the same level of inconsistency combined with opportunity.
Additionally, the involvement of Mason Shaw and Alex Shaw suggests the possibility of accomplice support, although further investigation would be required to confirm their exact roles.

## 🧾 Conclusion
This investigation demonstrates how structured data analysis can be used to reconstruct events, expose false narratives, and identify key actors in complex scenarios. By integrating multiple datasets and validating each claim against factual records, it becomes possible to move from uncertainty to a clear, evidence-based conclusion.
