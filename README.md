# Tenure-Track Faculty Prospects of Doctoral Students (by school and field)
## By Spencer Alliston

### Story Pitch

The American academy is, in many ways, the academic envy of the developed world. It also has a math problem. There have been numerous studies and articles indicating the outisize influence of a small number of elite institutions, as well as several discussing the increasing gap between the number of doctoral degrees granted in the United States and the number of tenure-track faculty hired. What has so far not been analyzed is what the odds are of the most successful students becoming faculty members. For a prospective graduate student, there is no guidance on the likelihood of success, even if she can get into the most competitive programs. In order to better look at the odds, hiring data was merged with degree conferrals to show the actual chance of a doctoral student at a given school becoming faculty within 4 years of graduation. As expected, top schools provided better chances for their graduates, though the percentages remained lower than students might hope. Then, a more granular analysis was done on the top 5 faculty-producing institutions (Berkeley, Harvard, Michigan, Stanford, and Wisconsin) to examine how placement rates fluctuated with field of study. Surprisingly, a humanities Ph.D. from any of these schools has better odds of a faculty placement than their STEM counterparts, though stubbornly below 50%

By looking at the number of new hires that came from doctoral-degree granting schools in 2011-2020 as well as the degrees conferred by those schools, it is possible to see where an aspiring faculty member should most seriously consider pursuing their graduate studies. This closes the gap in previous reporting which either took a high-minded institutional approach, or failed to recognize the need for individuals to evaluate options at such schools. For prospective graduate students and faculty, this shows where you are most likely able to have the biggest impact if your goal is a career in American avademia.

### Additional Sources
Daniel Larremore, Associate Professor of Computer Science at CU-Boulder (daniel.larremore@colorado.edu). Daniel is the corresponding auther of the Nature paper that was one of the major data sources for this work. Their paper was on the outsize influence of certain institutions on the American academy. By looking at the data more granularly, the conclusions from their study could be made much stronger. In particular, the number of students graduated and the number of faculty members present (by field) could indicate where professors have the most influence via their student placements. This would reveal the outsize influence of individuals in the academy as opposed to institutions.

Chris Dames, Dept. Chair of Mechanical Engineering at UC Berkeley (cdames@berkeley.edu). Chris has overseen several faculty hires at the top faculty producing university in one of the fields of interest for this work. Chris could comment, qualitatively, on how the home institution of prospective faculty influences the discussion around them. Additionally, he can comment on how many students from Berkeley become faculty vs. how many faculty are being hired by Berkeley.

Other reports and datasets that would be helpful include articles like ["The Bleak Job Landscape of Adjunctatopia for Ph.D.s"](https://www.nytimes.com/2020/03/05/upshot/academic-job-crisis-phd.html) from the Upshot of the New York Times, which is one of several reports indicating the growing gap between doctoral degrees conferred and new faculty hires. This would allow for an analysis of the continuing trends, by field, that this work neglects.

Additionally, datasets such as the one behind the following paper, subtitled ["PhD Students, Faculty Advisors, and Preferences for Varied Career Options"](https://www.frontiersin.org/articles/10.3389/fpsyg.2021.711615/full) would be helpful in completing this analysis, which currently neglects student career preference. While this may also average out and retain the same takeaway points, there is a chance that the academic culture of schools may attract students of different preferences (e.g. an otherwise comparable student may prefer Berkeley or Harvard for a career in academia v.s. Stanford or MIT for a career in industry).

### Data Visualization

First, a bar chart showing [the total number of faculty that each U.S. university has trained.](https://www.datawrapper.de/_/EyUTB/)

!['Bar Chart of Undergraduate Majors and Their Starting Median Salaries','A bar chart with 50 different undergraduate majors listed vertically on the left-hand side of the bar chart, while the associated starting median salary amount is indicated right next to the major, on the bar itself, in dollar amounts. The bars are colored a mint green, and "physician assistant" and "Spanish" is bolded to highlight that they are the highest and the lowest earning majors, respectively.  Physician assistant ranking the highest with $74,300 and Spanish ranking the lowest with $34,000.'](EyUTB-active-faculty-produced-by-universities (1).png)

Second, a bar chart showing [the odds of a given student at each of those universities becoming tenure-track faculty.](https://www.datawrapper.de/_/kiWyA/)


### Data Analysis

Source Data:

* Degrees Conferred in US: [National Center for Education Statistics, Table 312.20](https://nces.ed.gov/programs/digest/d21/tables/dt21_312.20.asp?current=yes)
  * File: "tabn312.20.xls"

* Edgelist/Faculty Affiliations: [Wapman, et al. Nature, 2022](https://www.nature.com/articles/s41586-022-05222-x#Sec2)
  * File: "edge-lists.csv"

* Top 5 School Doctoral Degrees Confirmed:
  * File: "Top5Compiled.xlsx"
    * Berkeley: [University of California Degrees Awarded Data](https://www.universityofcalifornia.edu/about-us/information-center/degrees-awarded-data)
    * Harvard: [Harvard Fact Book: Degrees Awarded](https://oira.harvard.edu/factbook/fact-book-degrees/#deg_deg)
    * Michigan: [University of Michigan: Degree Reports, Section 500](https://ro.umich.edu/reports/degrees)
    * Wisconsin: [University of Wisconsin - Madison, Graduate School Degrees](https://grad.wisc.edu/data/degrees-awarded/)
    * Stanford: [Stanford University Degrees Conferred](https://irds.stanford.edu/data-findings/degrees-conferred)


I then compiled them all into one dataset, which contained only the pertinent information. Sheet one contains the combined doctoral degrees granted, and a calculated total number of hirees within 4 years of doctoral degree completion. This dataset, along with the base datasets for degrees conferred across the country and the "edgelist" faculty+school of doctorate sheet, can be found in this repo.

### Database Development

In the compiled sheet, "FacultyOddsCompiled.xlsx"

Sheet 1 contains the background data involving where faculty are located and where they were trained (condensed replica of "edge-lists.csv")

Sheet 2 contains the total number of doctoral degrees (condensed replica of "tabn312.20.xls" with institution ID numbers)

Sheet 3 contains the compiled data for degrees conferred by academic domain for the top 5 faculty producing institutions (average over relavent time period, condensed from "Top5Compiled.xlsx")



Compiling the new dataset before setting out to answer questions.:
For sheet 2, I directly imported "edge-lists.xlsx". Then, I deleted all values without the TaxonomyLevel "Domain" to prevent double counting and to allow for the Top5 Analysis.

For sheet 1, I copied the school names and the doctoral degrees granted per year from the NCES resource. I then matched school names with ID numbers assigned to them from the more complex edge-list dataset, so that vlookup could be used later. Then, I deleted any schools without matching IDs from the Nature dataset. I also deleted schools with fewer than 50 doctoral degrees granted per year, to remove any outlier effects. These were mostly secondary campuses of flagship state universities.

For sheet 3, I found the number of doctoral degrees granted by academic domain for each of the 5 schools, and compilked them into a single format by year. For years without available data, I replaced the dataset with a 5-year median of surrounding years. Note that most domain-level data was not available for Harvard.

### Underlying Assumptions to Analysis
1. The timeframe for the data is for degrees conferred from 2011-2020. Where data does not exist, averages are substituted.
2. For nation-wide analyses, all doctoral degrees are considered, including professional doctorates (M.D.s, J.D.s, D.Pharm.s, etc.). As these still can be hired for faculty, the analysis should be mostly internally consistent, but it does inflate the proportional success of schools with only research doctorates (e.g., Georgia Tech does not have a law or med school, all doctoral degrees are Ph.D.s). In the "top-5" analysis, this assumption is no longer present.
3. The faculty network does not indicate when hires were made, so it assumes that the relative proportion of new hires is the same as existing hires. As new hires constitute 20% of the data set and there is a very large number of faculty, this is likely a good assumption, though it will not reflect universities that have recently gotten much stronger (e.g., Georgia Tech, Carnegie Mellon)
4. Hires are only considered at other doctoral-granting universities, so some tenure-track academic positions are neglected. This is standard for such analyses.
5. Finally, public data is compiled for schools which fail to grant a certain number of undergraduate degrees, which leaves out some elite options (e.g. Dartmouth), but captures most of the schools in consideration. For the sake of completeness, top 10 "prestige" schools (as determined by the Nature paper) were added back in manually. This ended up being CalTech, MIT, Princeton, and Yale. According to the same list, the most likely significant occlusions because of this are as follows: Carnegie Mellon, Brandeis, Brown, Rochester, and Rice. Other significant schools which were left out primarily grant professional degrees, such as UC-San Francisco, or were below 40 in "prestige", such as Vanderbilt.


## Questions to answer:
### 1. Which schools produce the most faculty members?

In order to do this, create a new column for existing faculty members. To do so, use SUM(FILTER()) to mimic VLOOKUP for all instances of a university ID. Filter out to get the school idea and only the taxonomy level "Domain" (otherwise, some faculty double- or triple-counted), then output the "total". Example of the formula shown in the following figure.

![image](https://github.com/spencer-alliston/J124Final/assets/139919855/098d37fe-8916-4ba9-b2be-2bb506e8013f)

Then, sort by this column, and see the top universities as seen below.

![image](https://github.com/spencer-alliston/J124Final/assets/139919855/1b22b97a-9708-4403-8b6e-6ca8a5dd8fad)


### 2. Which schools have the highest portion of doctoral students becoming faculty members?

Now, divide total number of professors by 5 to attain total number hired during the sample period, then by 10 to get an approximation for how many faculty are hired from the university before year. Then divide that by the doctoral degrees conferred per year, which will be an estimate of what percentage of current doctoral students will be hired as faculty within 4 years of degree conferral. The top 20 schools by this metric can also be seen below.

![image](https://github.com/spencer-alliston/J124Final/assets/139919855/ad91e27a-5692-461c-99f6-204e4989be74)


### 3. Which schools are most underestimated by the traditional analysis (of question 1)? Who are the most overestimated?

Here, rank the schools under each method, then define a difference between them and sort. Higher numbers indicate that their students are hired significantly more than you would expect from the classic analysis, negative numbers indicate that students are hired less.

![image](https://github.com/spencer-alliston/J124Final/assets/139919855/a3c1ef33-16e6-4f0b-b823-2d14f6987e2d)

Notable data points from this analysis are that Utah State has a top 20 hire-rate despite not having that many faculty members in total, and UC Santa Barbara is top 10 in hire-rate as well. Similarly, CalTech has the 3rd best rate despite having the 42nd most faculty in the country. This reflects that their class size is smaller, and gives a new dimension to students trying to determine which schools they should attend.

![image](https://github.com/spencer-alliston/J124Final/assets/139919855/75235406-f99c-4131-9450-bad4d60559b6)

On the other end, schools like USC, Florida, NYU, Texas A&M, and Ohio State have faculty placements that would imply a very high hire-rate, but that isn't actually reflected in their numbers. Some of this may be the nature of their doctoral programs, but it remains helpful context. Of the top 5 schools, Michigan seems to be most overestimated by this metric.

### 4. Which of the departments at the top 5 schools produces the most faculty? Which has the highest percentage of students end up faculty?

By using the assembled "Top5Compiled" dataset, can now filter using the formula below, which specifies which domain we are interested in. The specific formula shown is for Engineering, which also specifies to include Computer Science, as they are grouped together in the Ph.D.s dataset.

![image](https://github.com/spencer-alliston/J124Final/assets/139919855/87c8e170-bd47-4646-ab29-cdaeeca2c51a)


By sorting, that reveals the following list of most successful placements, with Berkeley's Natural Sciences division leading the rest.

![image](https://github.com/spencer-alliston/J124Final/assets/139919855/7b630e67-988e-491a-9e28-ef6873e8ac08)


And repeat the steps from question #2 for prospective placements.

![image](https://github.com/spencer-alliston/J124Final/assets/139919855/878d776b-f03b-406a-b08f-153174606a5e)

Here, it is revealed that the humanities actually have higher hiring rates, at least at the most elite schools. This runs against the typical understanding of the situation, so it would be interesting to take a better look at this with the full data set.

### 5. What doctoral institution gives a prospective engineering faculty member the best chance of success?

Now, simply filter for "Engineering" and sort by odds, and see the top schools, ranked. As a prospective engineering faculty member, this is of primary interest for me and those like me.

![image](https://github.com/spencer-alliston/J124Final/assets/139919855/eec589ae-a208-42de-8e77-0d623000e3a4)


