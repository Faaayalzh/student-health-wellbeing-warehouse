# Student Health and Well-Being: Data Integration and Warehousing

Integrating students' sleep, lifestyle, academic, and mental-health data from several sources into a MySQL data warehouse, to explore what drives student well-being.

> Group project for the Data Integration and Warehousing course (DS2202), Data Science Department, Umm Al-Qura University.

## Data Sources
| Source | Type | Content |
|--------|------|---------|
| Sleep Health & Lifestyle | CSV, 400 records | Sleep duration and quality, physical activity, stress, BMI, heart rate, sleep disorders |
| Student Sleep Patterns | CSV, 500 records | Sleep habits, study hours, screen time, caffeine, physical activity |
| Student Depression Dataset | CSV, about 1,000 records | Demographic, academic, lifestyle, and mental-health indicators |
| Teen Mental Health Chatbot | Text (unstructured) | Free-form teen messages about emotions and concerns |

## What Was Done
| Step | Details |
|------|---------|
| Structured vs. unstructured data | Identified fixed-schema CSV data vs. free-text chatbot data that needs NLP preprocessing |
| Cleaning and preprocessing | Removed invalid CGPA values and non-student ages, imputed missing stress values (mode) and sleep disorders ("None"), converted decimal times, split blood pressure into two numeric columns, extracted emotion labels with sentiment analysis |
| Schema matching | Matched the Student Depression and Sleep Health schemas (match, partial match, no match, with confidence levels) |
| Schema mapping | Defined mapping rules (direct 1:1 mappings and a conditional rule: Depression Level → Sleep Disorder) |
| Data warehouse and ETL | Star schema in MySQL: one fact table (`FACT_STUDENT_HEALTH`) and three dimensions (Student, Academic, Lifestyle), integrated from three sources |
| OLAP analysis | Four strategic questions answered with analytical queries and a dashboard |

## Findings (in the small loaded sample)
The warehouse was loaded with a small sample (10 rows per dimension, 15 fact rows), so these are illustrative and should not be generalized.
- Health-related tracks (Medicine, Nursing, Psychology) showed the highest depression rates in the sample.
- Higher academic pressure went with lower sleep quality and higher stress.
- Good sleep (7 hours or more) with an active routine showed the lowest stress.
- High financial stress was associated with depression, especially with a family history of mental illness.

## Lessons Learned
- Insights need linked domains, not isolated data.
- A star schema simplifies analytical querying.
- Resolve schema and data-quality issues before loading.

## Tools Used
MySQL, SQL, CSV data, sentiment analysis

## Team
- Fay Salman Alzahrany
- Retaj Khaled Alashqar
- Bayan Bandar Almatrafi
