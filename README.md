# Tenure-Track Faculty Prospects of Doctoral Students (by school and field)
## By Spencer Alliston

### Story Pitch

The American academy is, in many ways, the academic envy of the developed world. It also has a math problem. There have been numerous studies and articles indicating the outisize influence of a small number of elite institutions, as well as several discussing the increasing gap between the number of doctoral degrees granted in the United States and the number of tenure-track faculty hired. What this analysis adds is an analysis of what schools most successfully turn doctoral students into professors.

By looking at the number of new hires that came from doctoral-degree granting schools in 2011-2020 as well as the degrees conferred by those schools, it is possible to see where an aspiring faculty member should most seriously consider pursuing their graduate studies. This advances the previous reporting in very important ways by allowing individuals to better evaluate the odds of success in a grueling career path.


### Additional Sources
Daniel Larremore, Associate Professor of Computer Science at CU-Boulder (daniel.larremore@colorado.edu). Daniel is the corresponding auther of the Nature paper that was one of the major data sources for this work. Their paper was on the outsize influence of certain institutions on the American academy. By looking at the data more granularly, the conclusions from their study could be made much stronger. In particular, the number of students graduated and the number of faculty members present (by field) could indicate where professors have the most influence via their student placements. This would reveal the outsize influence of individuals in the academy as opposed to institutions.

Chris Dames, Dept. Chair of Mechanical Engineering at UC Berkeley (cdames@berkeley.edu). Chris has overseen several faculty hires at the top faculty producing university in one of the fields of interest for this work. Chris could comment, qualitatively, on how the home institution of prospective faculty influences the discussion around them. Additionally, he can comment on how many students from Berkeley become faculty vs. how many faculty are being hired by Berkeley.

Other reports and datasets that would be helpful include articles like ["The Bleak Job Landscape of Adjunctatopia for Ph.D.s"](https://www.nytimes.com/2020/03/05/upshot/academic-job-crisis-phd.html) from the Upshot of the New York Times, which is one of several reports indicating the growing gap between doctoral degrees conferred and new faculty hires. This would allow for an analysis of the continuing trends, by field, that this work neglects.

Additionally, datasets such as the one behind the following paper, subtitled ["PhD Students, Faculty Advisors, and Preferences for Varied Career Options"](https://www.frontiersin.org/articles/10.3389/fpsyg.2021.711615/full) would be helpful in completing this analysis, which currently neglects student career preference. While this may also average out and retain the same takeaway points, there is a chance that the academic culture of schools may attract students of different preferences (e.g. an otherwise comparable student may prefer Berkeley or Harvard for a career in academia v.s. Stanford or MIT for a career in industry).

### Data Visualization


### Data Analysis

Source Data:

* Degrees Conferred in US: [National Center for Education Statistics, Table 312.20](https://nces.ed.gov/programs/digest/d21/tables/dt21_312.20.asp?current=yes)
  * File: "tabn312.20.xls"

* Edgelist/Faculty Affiliations: [Wapman, et al. Nature, 2022](https://www.nature.com/articles/s41586-022-05222-x#Sec2)
  * File: "Edgelist.csv"

* Top 5 School Doctoral Degrees Confirmed:
  * File: "Top5Combined.xlsx"
    * Berkeley: [University of California Degrees Awarded Data](https://www.universityofcalifornia.edu/about-us/information-center/degrees-awarded-data)
    * Harvard: [Harvard Fact Book: Degrees Awarded](https://oira.harvard.edu/factbook/fact-book-degrees/#deg_deg)
    * Michigan: [University of Michigan: Degree Reports, Section 500](https://ro.umich.edu/reports/degrees)
    * Wisconsin: [University of Wisconsin - Madison, Graduate School Degrees](https://grad.wisc.edu/data/degrees-awarded/)
    * Stanford: [Stanford University Degrees Conferred](https://irds.stanford.edu/data-findings/degrees-conferred)


I then compiled them all into one dataset, which contained only the pertinent information. Sheet one contains the combined doctoral degrees granted, and a calculated total number of hirees within 4 years of doctoral degree completion. This dataset, along with the base datasets for degrees conferred across the country and the "edgelist" faculty+school of doctorate sheet.

In the compiled sheet, "FacultyOddsCompiled.xlsx"

Sheet 1 contains the background data involving where faculty are located and where they were trained (condensed replica of "Edgelists.csv")

Sheet 2 contains the total number of doctoral degrees (replica of "tabn312.20")

Sheet 3 contains the compiled data for degrees conferred by academic domain for the top 5 faculty producing institutions (average over relavent time period, condensed from "Taop4Combined.xlsx")

Sheet 4 contains a pivot table.


A few base assumptions are made as well:
1. The timeframe for the data is for degrees conferred from 2011-2020. Where data does not exist, averages are substituted.
2. For nation-wide analyses, all doctoral degrees are considered, including professional doctorates (M.D.s, J.D.s, D.Pharm.s, etc.). As these still can be hired for faculty, the analysis should be mostly internally consistent, but it does inflate the proportional success of schools with only research doctorates (e.g., Georgia Tech does not have a law or med school, all doctoral degrees are Ph.D.s). In the "top-5" analysis, this assumption is no longer present.
3. The faculty network does not indicate when hires were made, so it assumes that the relative proportion of new hires is the same as existing hires. As new hires constitute 20% of the data set and there is a very large number of faculty, this is likely a good assumption.


Questions to answer:
1. Which schools produce the most faculty members?

2. Which schools have the highest portion of doctoral students becoming faculty members?

3. Does the data on the top 5 schools change if we remove professional doctorates (J.D.s, M.D.s)?

4. Which of the departments at the top 5 schools produces the most faculty? Which has the highest percentage students?

5. What doctoral institution gives a prospective engineering faculty member the best chance of success?



