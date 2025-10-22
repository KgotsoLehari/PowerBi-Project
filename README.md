**Project Summary**

This project delivers a single-page Data Survey Breakdown dashboard whose purpose is to turn raw survey responses into quick, decision-ready insights about the data community, who the respondents are, how they’re paid, what they prefer, and how they feel. It highlights respondent volume and age, compares average salary by job title to understand role-based pay, profiles audience geography via a country treemap, reveals favorite programming languages (with job-title context), and surfaces sentiment on work/life balance and salary satisfaction. The aim is to give hiring managers, educators, and community organizers an immediate, trustworthy picture that can guide talent planning, curriculum focus, and engagement strategies.

**ETL Process**

- Extract & Transform (Power Query): Imported the survey sheet, promoted headers, enforced types (numeric for Age/Salary, text for Country/JobTitle/Language), normalized labels (e.g., US variants), trimmed/cleaned text, removed duplicates/empties, filtered clearly invalid salaries, grouped low-frequency countries into “Other,” and added an ordinal DifficultySort column (Very Easy - Very Difficult) for proper chart ordering.

- Model & Relationships: Kept a lean star-like model centered on the Responses table. Added 1–many relationships to two small lookup tables (Difficulty and Country groupings) to enable clean sorting and grouping without calc columns everywhere. Marked lookup tables as dimensions (no summarization) and set cross-filter to single for predictable behavior.

- Core DAX (measures):

  ~ Counts & averages: Total Respondents, Avg Age, Avg Salary, Median Salary .

  ~Sentiment: Avg Work/Life Balance, Avg Salary Satisfaction (0–10 scale).

 `~Composition: Votes and % of Total for donut/stacked visuals (using DIVIDE() + ALL() to remove current context).

  ~Targets & sorting: Target Score and DifficultySort .

  ~Performance tips: measures only with consistent formatting (currency, decimal).

  ~Drill-down & Drillthrough: Enabled drill-down hierarchies such as Job Title and Favorite Language , Region from Country for progressive detail. Added a drillthrough page to jump from aggregated visuals to respondent-level context filtered by the selected job title or country.



**Skills developed**

- Power Query ETL: schema typing, text cleaning, label standardization, grouping/bucketing, and sort-by columns.

- Data modeling: slim star design with dimension lookups and controlled filter direction.

- DAX for analytics: reusable, context-aware measures (counts, averages, medians, % of total, targets).

- Interactive storytelling: drill-down/drillthrough flows, slicer design, and clear visual formatting for fast comprehension.

**Conclusion**

The project shows full-stack BI competency, from ingesting messy survey data to modeling, DAX measurement, and interactive storytelling,producing a concise dashboard that answers “who, what, where, and how satisfied” at a glance. It’s easy to refresh with new waves of data, extend with additional sentiment or experience fields, and repurpose for other audience profiling use cases (recruiting, curriculum planning, community events) while maintaining consistent, explainable metrics.
