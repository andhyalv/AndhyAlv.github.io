im ## This can be a template for an internal prject

**Project description:** You can use this template to create projects in the future. Simply duplicate the page and change the text and images. 

Be sure to follow *The Interesting Project Template* as shown in [**The Data Science Project Studio**](https://www.datacareerjumpstart.com/products/the-data-science-project-studio/categories/2150357707/posts/2158441592). 

### 1. You can have sections and text.

Just like this. And you can even add internal coding blocks

```python
print('this is the python code I used to solve this problem')
```

### 2. You can add any images you'd like. 

<img src="images/dummy_thumbnail.jpg?raw=true"/>

# Title
![IMG]()

### Introduction


### What will you learn
a)

b)

c)

d)

e) 

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
#### b) Your boss has asked you to explore the relationship between number of lab procedures and time spent in the hospital. Specifically, they asked for a few, average, and many procedure group.
#### c) Give the hospital director a list of the medical specialties that have an average number of procedure count above 2.5 with the total procedure count above 50.
The hospital director is looking for a list of medical specialties with an average number of procedure count above 2.5 and with a total procedure count above 50. In order to find this we use the query below.
QUERY.

The output is the following table:
OUTPUT.

From this output, we can see that (Describe relationships)

#### d) Provide a list of all patients who had an emergency but left the hospital faster than the average.
#### e)Research needs a list of all patient numbers who are African-America or have a "Up" to metformin
#### f) Our health care data analyst boss wants to know what the distribution of time spent in the hospital looks like. 
The distribution of time spent in the hospital is displayed by this query.

The output is a Histogram.

They're also curious to know if the majority stay less than 7 days. Once patients stay over 7 days, the hospital wants to ensure these patients are very acute.
#### g)

### Conclusion

### Call to Action
If you were interested in discussing the dataset further or have feedback on the analysis, feel free to message me on [LinkedIn!](https://www.linkedin.com/in/andhyalvarez/)








