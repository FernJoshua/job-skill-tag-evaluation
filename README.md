# AI and ML: How Often Are These Skill Tags Right?

## 1. Evaluation approach

I evaluated all 50 job descriptions against the approved skill list. A predicted tag was marked correct if the skill appeared in the description, either as a required or preferred skill. A tag was marked wrong if it was unsupported by the description or outside the approved skill vocabulary.

I treated phrases such as "bonus if", "nice to have" and "is a plus" as optional requirements. Missing optional skills were not counted as errors. Missing skills were counted only when the description explicitly required them.

I also used a synonym mapping to handle variations such as Node/Node.js, Excel/Microsoft Excel, JS/JavaScript and Postgres/PostgreSQL.

## 2. Results

The evaluation covered 50 job descriptions and 200 predicted tags.

| Metric | Result |
|---|---:|
| Correct predicted tags | 172 |
| Wrong predicted tags | 28 |
| Tag precision | 86.00% |
| Required skills | 179 |
| Correctly identified required skills | 154 |
| Missing required skills | 25 |
| Required-skill recall | 86.03% |
| Missing-skill rate | 13.97% |

The model achieves 86% precision and approximately 86% recall. However, it still produces unsupported tags and misses skills that employers explicitly require.

## 3. Three failure patterns

**1. Missing required skills:** The model fails to identify some required skills. JD010 misses HR Operations and Interviewing. JD043 misses PostgreSQL and REST APIs. JD046 misses Design Systems and Figma.

**2. Irrelevant predictions:** The model adds skills that do not appear in the job description. JD025 includes Kubernetes and Leadership. JD030 includes Blockchain and Leadership. JD040 includes SAP and Leadership.

**3. Inconsistent skill naming:** The model uses different names for equivalent skills. Examples include Node in JD013, Excel in JD020 and JS in JD022. These were handled through synonym normalisation but could cause matching failures without standardisation.

## 4. Recommended improvement

My first recommendation is to introduce a skill normalisation and validation layer between the model and the job-matching system.

This layer should map synonyms to approved skill names, reject unsupported predictions, and distinguish required skills from preferred skills.

I would evaluate the change using the same 50 descriptions and compare precision, required-skill recall and unsupported predictions before and after implementation. My target would be at least 95% precision and recall.

## 5. Conclusion

The model provides a useful starting point for automated job tagging, but its current performance is not sufficient to rely on without validation. Improving skill extraction, standardisation and requirement classification would make job recommendations more accurate and reduce missed opportunities for students.

**Tools:** Python, Pandas and Regular Expressions. AI assistance was used to develop the initial evaluation logic and report structure. The evaluation rules, synonym mapping and results were reviewed against the supplied synthetic dataset.