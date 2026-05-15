# City of Los Angeles Civil Service Data Visualization Plan

**Thesis:** Credential barriers and internal mobility structures in the City of Los Angeles civil service system create differential pathways to public sector employment and compensation, with formal education requirements not consistently predicting higher salaries across job classifications.

---

## Note on Original Research Questions

Several proposed research questions cannot be answered with the available dataset and are excluded from this plan:

- **Q2** (approaching-retirement demographics) — no age or hire-date data in the bulletins
- **Q7** (English-only publishing) — all bulletins are in English; no contrast group exists to visualize
- **Q11** (demographic makeup of applicants) — no applicant records are included in the dataset
- **Q12** (informal knowledge networks) — no neighborhood or network data
- **Q13** (criminal records + experience gaps) — no applicant history data

The four visualizations below draw from research questions that are directly answerable using salary ranges, education requirements, experience requirements, and exam-access language parsed from the ~683 raw job bulletin `.txt` files.

---

## Visualization 1 — Bar Chart

**Research Question:** How do average salary ranges across job classification types — public safety, administrative, technical/engineering, trades, and health/social services — reveal which kinds of labor the City of Los Angeles values most, and how do those valuations map onto broader hierarchies of class and race?

**Chart:** Horizontal bar chart
- **Title:** Average Annual Salary by City Job Classification Sector
- **X-axis:** Average salary midpoint (USD)
- **Y-axis:** Job sector (Public Safety, Technical/Engineering, Trades, Administrative, Health/Social Services)
- **Error bars:** ± 1 standard deviation across job titles in each sector
- **Data source:** Salary ranges parsed from all bulletins via regex; job titles keyword-classified into sectors

**Chart Type Rationale and Description:**
A horizontal bar chart is the clearest tool for comparing a single continuous value — average salary midpoint — across a small number of discrete, named categories. Orienting the bars horizontally accommodates the length of sector labels and makes cross-sector differences immediately readable. Each bar represents the average of all salary midpoints within that sector, with error bars communicating how much variation exists within each category. The chart will reveal not only which sectors pay more on average but also which sectors have the widest internal spread — indicating either a well-structured pay ladder within that field or highly inconsistent compensation. Sectors such as Public Safety and Technical/Engineering are expected to anchor the upper end, while Administrative and Health/Social Services may show lower or more compressed ranges.

**Meaning in Context:**
This visualization directly interrogates the thesis's claim about differential valuation of labor. If Public Safety salaries significantly exceed those in Administrative or Health/Social Services roles, the chart makes visible a political choice: the City has historically invested its compensation structure in enforcement and infrastructure while paying caregiving, clerical, and social-service work at lower rates. These sector hierarchies are not arbitrary — they track longstanding patterns in which fields are coded as masculine, technical, or high-status versus feminized, relational, or invisible. Because city employment has been a historically significant route to middle-class stability for communities of color in Los Angeles, where a sector lands in this ranking also reflects who has had access to those higher-paying classifications and who has been concentrated at the lower end.

---

## Visualization 2 — Bar Chart

**Research Question:** Do higher formal education requirements in City of Los Angeles job bulletins consistently predict higher annual salaries across job classifications, or do credential requirements operate independently of compensation — functioning as access barriers rather than markers of valued expertise?

**Chart:** Vertical bar chart
- **Title:** Average Annual Salary by Required Education Level Across City Job Classifications
- **X-axis:** Education level tier (No Formal Requirement → High School → Some College → Bachelor's Degree → Graduate)
- **Y-axis:** Average salary midpoint (USD)
- **Annotations:** Job count (n) displayed above each bar
- **Data source:** Education requirements parsed from bulletin requirement sections; matched to salary midpoints

**Chart Type Rationale and Description:**
A vertical bar chart is the appropriate choice here because it maps an ordinal variable — education tier, which has a natural low-to-high ordering — onto the x-axis and places salary on the y-axis, conforming to the conventional expectation that higher inputs produce higher outputs moving left to right. This layout makes it immediately visible whether bars rise monotonically (education consistently predicts salary) or whether the trend is uneven, plateaus, or reverses. Annotating each bar with the number of job classifications it contains contextualizes the averages: a category with n=5 titles is far less reliable than one with n=150. The chart is designed to surface disruptions in the assumed education-to-pay pipeline — for example, whether trades roles requiring only an apprenticeship certificate out-earn administrative roles requiring a bachelor's degree.

**Meaning in Context:**
This visualization is the most direct empirical test of the project's thesis. If the bars do not rise cleanly from left to right — if, for example, jobs requiring no formal education pay comparably to jobs requiring a college degree, or if the bachelor's tier pays less than the "some college" tier — it undermines the rationale that education requirements serve as measures of job complexity and fair compensation. Instead, it suggests that credential requirements function as gatekeeping mechanisms that filter applicants by background rather than as genuine predictors of what the work is worth. For communities with unequal access to higher education — which in Los Angeles maps closely onto race and income — this has real consequences: it determines who can even apply, not just who will be paid fairly.

---

## Visualization 3 — Scatter Plot

**Research Question (new):** How does the minimum required years of work experience in City job bulletins relate to salary range midpoints across job classifications, and does accumulated work experience reliably translate into higher compensation — or do other structural factors disrupt that relationship?

**Chart:** Scatter plot
- **Title:** Required Work Experience vs. Annual Salary Midpoint by Job Sector
- **X-axis:** Minimum years of experience required (continuous)
- **Y-axis:** Annual salary midpoint (USD)
- **Color encoding:** Job sector (Public Safety, Technical/Engineering, Trades, Administrative, Health/Social Services)
- **OLS trend line** overlaid across all points; individual sector trend lines optional
- **Data source:** Experience length parsed from bulletin requirements; matched to salary midpoints and sector labels

**Chart Type Rationale and Description:**
A scatter plot is the right tool for examining the relationship between two continuous variables — years of experience required and salary midpoint — across hundreds of individual job classifications. Unlike a bar chart, which would aggregate and flatten this relationship, a scatter plot preserves each job classification as its own data point, allowing patterns, clusters, outliers, and the overall strength (or weakness) of the experience-to-salary relationship to be seen at once. Color-coding by job sector makes it possible to see whether different sectors occupy distinct regions of the chart — for instance, whether technical jobs cluster at high experience and high salary while administrative jobs cluster at moderate experience and lower salary. An OLS trend line over the full dataset provides a summary of the direction and steepness of the relationship, and points that fall far from the line are candidates for closer textual examination.

**Meaning in Context:**
Experience requirements are often presented as a neutral proxy for skill and readiness, yet this chart will likely reveal that the relationship between experience and pay is far more complicated. Some of the highest-salary roles may require very little formal prior experience — because they are primarily reached through internal promotion, not entry-level hiring. Conversely, some roles requiring four or more years of documented experience may still offer salaries that lag behind less-credentialed but better-compensated sectors. This disrupts the meritocratic narrative that more experience earns more pay, and points instead to sector identity, union structure, and the City's own historical investment decisions as the actual drivers of compensation. In the context of the thesis, it also raises the question of who can afford to accumulate years of qualifying experience before accessing these positions — again a question shaped by race, class, and neighborhood.

---

## Visualization 4 — Box Plot

**Research Question:** What does the distribution of salary ranges for internally-restricted (promotional) versus open-competitive City job classifications reveal about who the civil service structure rewards, and how does the internal mobility advantage vary across job sectors?

**Chart:** Box plot, grouped by sector and split by exam access type
- **Title:** Salary Midpoint Distribution: Promotional vs. Open-Competitive Exams by Job Sector
- **X-axis:** Job sector
- **Y-axis:** Annual salary midpoint (USD)
- **Color encoding:** Exam access type — Promotional (current City employees only) vs. Open Competitive (all applicants)
- **Outlier dots:** Shown for all groups
- **Data source:** Exam-access type parsed from bulletin header text; matched to salary midpoints and sectors

**Chart Type Rationale and Description:**
A box plot is chosen here rather than a simple bar chart because the research question is not about averages — it is about distributions. Knowing that promotional jobs pay "more on average" is less informative than knowing whether the entire salary range for promotional roles is shifted upward, compressed, or skewed compared to open-competitive roles. Box plots display the median, interquartile range, full spread, and outliers for each group simultaneously, making it possible to see whether high-salary outliers in one group are distorting the mean, whether the two distributions overlap substantially, and whether the pattern holds consistently across sectors or only appears in some. Grouping by sector while splitting each sector into the two exam-type boxes allows for both a within-sector comparison (does being an insider matter for this kind of work?) and a cross-sector comparison (which sectors most heavily gate their highest-paying roles behind an internal-only exam process?).

**Meaning in Context:**
The civil service system is formally designed to be a meritocracy open to all residents, but this visualization tests whether the internal promotional structure effectively creates a two-tier system: one in which higher-paying roles are disproportionately accessible only to those who already hold City employment. If promotional-only roles consistently show higher salary midpoints and lower salary overlap with open-competitive roles — particularly in sectors like Public Safety or Technical/Engineering — it constitutes strong evidence that the civil service functions as a credentialing escalator for insiders while presenting a lower ceiling to external applicants. This matters enormously for first-generation applicants, those who lack a family or community connection to City employment, and those who were historically excluded from the initial hiring wave that built the City's current workforce. The internal mobility structure does not just reward experience — it rewards the accident of already being inside.
