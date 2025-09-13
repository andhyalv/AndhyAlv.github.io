# Healthcare Investigation
![IMG](images/hospital.jpg "banner")

### Introduction
There are countless relationships to be discovered from Healthcare data. The relationships found in these datasets are important in understanding the efficacy of procedures, medications and the fair treatment of all patients. In this project I aim to understand several of these relationships that can be found in Healthcare data, with the goal of learning what is done well and what could be improved. I will provide the SQL queries and images of the outputted table. Some queries will have comments to clarify what each aspect of the query does.

### What will you learn from the data of this specific Hospital
a) In terms of the average number of lab procedures, all races are treated equally.

b) The average time spent in the hospital has a correlation with the number of procedures received.

c) The most common procedures are Cardiology and Radiology visits, along with Surgery of the Thoracic and Vascular systems.

d) The amount of patients that left the hospital faster than average after an emergency.

e) The number of patients who are African-American or have an "Up" to metformin.

f) The distribution of time spent in the hospital.

g) A list of the top 3 medications ranked per age group 

### Dataset and tools

### Data Analysis

#### a) The nurse director needs to know if we are subconsciously treating races differently. Show the average number of lab procedures broken down by race. 
In order to figure out if the hospital is subconsciously treating races differently, we looked at the average number of lab procedures by race. We used the query below
```SQL
select 
	d.race, 
    round(avg(h.num_lab_procedures),1) 
from health as h
	join demographics as d on h.patient_nbr = d.patient_nbr
    group by d.race
    order by avg(h.num_lab_procedures) DESC;
```
![race](images/RaceQuery.png "output")
#### b) Your boss has asked you to explore the relationship between number of lab procedures and time spent in the hospital. Specifically, they asked for a few, average, and many procedure group.
```SQL
select
	avg(time_in_hospital) as avg_time,
	case when num_lab_procedures >= 0
		and num_lab_procedures <= 25
		then 'few'
	when num_lab_procedures >= 25
		and num_lab_procedures < 55
		then 'average'
	else 'many'
    end as procedure_frequency
from health
group by procedure_frequency
order by avg_time desc;
```
![procedures](images/averagetimeprocedurefrequency.png "output")

#### c) Give the hospital director a list of the medical specialties that have an average number of procedure count above 2.5 with the total procedure count above 50.
The hospital director is looking for a list of medical specialties with an average number of procedure count above 2.5 and with a total procedure count above 50. In order to find this we use the query below.
```SQL
Select distinct medical_specialty,
	ROUND(AVG(num_procedures), 1) as avg_procedures, -- Gets the average first, than rounds it up to 1 decimal place in acolumn called avg_procedures.
	count(*) as count -- gives a count of the number of specciality procedures.
from health
group by medical_specialty -- Condensed list of specialities.
having count > 50
and avg_procedures > 2.5
order by avg_procedures DESC;
```
The output is the following table.

![ListofMed](images/ListofProceduresQuery.png "Output")

From this output, we can see that (Describe relationships)

#### d) Provide a list of all patients who had an emergency but left the hospital faster than the average.
```SQL
WITH avg_time AS (
	SELECT AVG(time_in_hospital) 
	FROM health
	) 
SELECT * FROM patient.health 
	WHERE admission_type_id = 1 
	AND time_in_hospital < (SELECT * FROM avg_time);
```
![Emergency](images/HospitalSuccess.png "Output")

#### e) Research needs a list of all patient numbers who are African-America or have a "Up" to metformin
```SQL
SELECT patient_nbr FROM patient.demographics WHERE race = 'AfricanAmerican'
UNION
SELECT patient_nbr FROM patient.health
WHERE metformin = 'Up';
```
![AA](images/AfricanUPMetformin.png "Output")
#### f) Our health care data analyst boss wants to know what the distribution of time spent in the hospital looks like. 
The distribution of time spent in the hospital is displayed by this query.
```SQL
Select round(time_in_hospital, 1) as bucket 
, count(*) as count 
, rpad('', count(*)/100, "*") as bar
```

The output is a Histogram.
![Histogram](images/HistogramQuery.png "Output")

The top 3 medications ranked, per age group.
#### g)
```SQL
WITH long_health_cte AS (
SELECT patient_nbr, 'metformin' AS medication, metformin AS med_usage FROM patient.health
UNION
SELECT patient_nbr, 'glipizide' AS medication, glipizide AS med_usage FROM patient.health
UNION
SELECT patient_nbr, 'insulin' AS medication, insulin AS med_usage FROM patient.health
)
SELECT
age, -- Takes the imported and aggregated age column.
medication, -- Uses the newly created medication column.
COUNT(*) AS total_uses, -- Creates a new column called total_uses, which determines how many are in the adjacent bucket. (Age/Medication)
RANK() OVER (PARTITION BY age ORDER BY COUNT(*) DESC) AS medication_rank -- Final column. Partitions it by age buckets. Order the age buckets by count in descending manner. Creates a ranking out of this order.
FROM long_health_cte -- Temporary table that we are using.
JOIN patient.demographics ON long_health_cte.patient_nbr = demographics.patient_nbr -- Allows for the age column to be used. Common column identified is patient_nbr.
WHERE med_usage NOT IN ('No') -- Excludes any instances where medicine is not used
GROUP BY medication, age -- Allows for similar medication, followed by similar ages to be combined into the same bucket for counting.
ORDER BY age, medication_rank; -- Orders by the age, then the medication rank. Default is from smallest to largest.
```

### Conclusion

### Call to Action
If you were interested in discussing the dataset further or have feedback on the analysis, feel free to message me on [LinkedIn!](https://www.linkedin.com/in/andhyalvarez/)

