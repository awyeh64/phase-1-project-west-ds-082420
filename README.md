# South King County Opportunity Youth

This project offers an updated estimate of the number of Opportunity Youth in South King County using the 2017 5-year American Community Survey [(ACS)](https://www.census.gov/programs-surveys/acs/about.html) Public Use Microdata Survey [(PUMS)](https://www.census.gov/programs-surveys/acs/technical-documentation/pums.html).


# Table of Contents

### Reports
-   [Opportunity Youth in South King County, updated with 2017 data](https://github.com/awyeh64/phase-1-project-west-ds-082420/blob/master/notebooks/report/opportunity_youth_final_notebook.ipynb "Report")
-   [Presentation](https://github.com/awyeh64/phase-1-project-west-ds-082420/blob/master/reports/presentations.pdf "Presentation")

### Exploratory Notebooks
-   [Visualizations](https://github.com/awyeh64/phase-1-project-west-ds-082420/blob/master/notebooks/exploratory/andrew_01_erh_download_and_explore_data.ipynb "Visualizations")
-   [Data Wrangling](https://github.com/awyeh64/phase-1-project-west-ds-082420/blob/master/notebooks/exploratory/Oz_prelim_work_data_tables.ipynb "Data Wrangling")
-   [PUMA Names](https://github.com/awyeh64/phase-1-project-west-ds-082420/blob/master/notebooks/exploratory/puma_names_2017.ipynb "Puma Names")
-   [Maps](https://github.com/awyeh64/phase-1-project-west-ds-082420/blob/master/notebooks/exploratory/Elena_01_erh_download_and_explore_data.ipynb "Maps")

### Helpful Resources
-   [Census Dictionary](https://github.com/awyeh64/phase-1-project-west-ds-082420/blob/master/references/PUMS_Data_Dictionary_2017.pdf "Dictionary")
-   [PUMS Information](https://github.com/awyeh64/phase-1-project-west-ds-082420/blob/master/data/2016_pums/ACS2012_2016_PUMS_README.pdf "Pums")



### Setup Instructions

If you are missing required software (e.g. Anaconda, PostgreSQL), please run the following command in Bash (designed for Mac computers):
```bash
# installs necessary requirements
# note: this may take anywhere from 10-20 minutes
sh src/requirements/install.sh
```

For Windows and Linux computers, you may need to manually ensure that you have installed [Anaconda](https://docs.anaconda.com/anaconda/install/) and [PostgreSQL](https://www.enterprisedb.com/downloads/postgres-postgresql-downloads).

### `oy-env` conda Environment

This project relies on you using the [`environment.yml`](environment.yml) file to recreate the `oy-env` conda environment. To do so, please run the following commands *in your terminal*:

```bash
# create the oy-env conda environment
conda env create -f environment.yml

# activate the oy-env conda environment
conda activate oy-env

# if needed, make oy-env available to you as a kernel in jupyter
python -m ipykernel install --user --name oy-env --display-name "Python 3 (oy-env)"
```

Note that this may take 10 or more minutes depending on internet speed.

**Windows Note:** The same versions of these packages are not available for Windows computers, so all Windows users should use the `windows.yml` file instead of `environment.yml` (this file was generated on Windows 10)

**Linux Note:** The same versions of these packages are not available for Linux computers, so all Linux users should use the `linux.yml` file instead of `environment.yml` (this file was generated on Red Hat)

**Catalina Note:** You may need to modify the `prefix` at the very bottom of `environment.yml` if you are on macOS Catalina.  Run `conda env list` in your terminal to determine the appropriate path by looking at the paths of your existing conda environment(s).  Modify `environment.yml` then try running the installation commands listed above again.

On all operating systems, you will know that you have the required software if the following Bash commands do not return error or "not found" messages:
```bash
which conda
conda list geopandas
which psql
```

### Data Download

To download the relevant data, run the following command *in Python*:

```
data_collection.download_data_and_load_into_sql()
```

Note that this may take 10 or more minutes depending on internet speed.

There is an example notebook in the `notebooks/exploratory` directory with this code already added.

## BACKGROUND

Measuring the successes and barriers faced by our most vulnerable youth is a challenge in the South King County region<sup>1</sup>. While there is a lot of information gathered from K12 districts and colleges about student outcomes, few data exists among Opportunity Youth (OY): young folks between the age 16 through 24 who are disengaged from both work and school<sup>2</sup>. This population is of particular interest to The Seattle Region Partnership (SRP), a multi-sector initiative founded by the Seattle Metropolitan Chamber of Commerce, Seattle Foundation, City of Seattle, and King County<sup>3</sup>.

# South King County Map

![text](https://raw.githubusercontent.com/awyeh64/phase-1-project-west-ds-082420/master/reports/figures/skc_definition.png)

Above we have a map showcasing the counties in King County that we consider part of the South King County region.  Below we have a visualization that shows the distribution of opportunity youths throughout South King County, with areas with a darker color containing significantly more opportunity youths than areas with lighter colors.

![text](https://raw.githubusercontent.com/awyeh64/phase-1-project-west-ds-082420/master/reports/figures/skc_distribution.png)

## PROJECT GOAL

The SRP would like an update on the estimated number of OY in South King County. According to a recent The Seattle Times article, the number of OY in South King County has remained steadfast at 19,000<sup>4</sup>. However, that estimation comes from a report that is over three years old. As Data Science Consultants, your task is to inform the SRP on the current status of OY in South King County using updated data.

# Breakdown of Opportunity Youth Population Growth

![text](https://raw.githubusercontent.com/awyeh64/phase-1-project-west-ds-082420/master/reports/figures/oy_pop_breakdown.png)

  In the leftmost column we can see that from 2017, the population of opportunity youths with a college degree and just a high-school degree have significantly increased.  An insight we can conclude from this is that youths might be able to graduate but aren't prepared for the next part of their life.

  In the middle column, we can see that the main increase comes from a stagnant population of opportunity youths from age 22 to 24.  While the 16 to 18 range and 19 to 21 range have remained roughly stable, we can see that many of the opportunity youths are pooling in the 22 to 24 range and unable to escape.

  In the right column, we see that the population of white ethnicity has increased significantly.  While the accuracy of this data may be questionable, a big influx of population could indeed affect job and education availability and increase the amount of opportunity youths.

# Opportunity Youth Status by Age

![text](https://raw.githubusercontent.com/awyeh64/phase-1-project-west-ds-082420/master/reports/figures/oy_status_by_age_skc.png)

# Our Findings

What we found concerning is the number of OY in the 19 to 24 age range, not only did it increase, but remained high. Furthermore, the college experience within the same age range was really low. In the 19 to 21 age group, only 13% of individuals had any college experience. While that number did improve a little in the 22 to 24 age range, where 20% of individuals here had college experience, those with college degrees was disturbingly low.

What this tells us is that high school, and secondary education in general, aren't doing a good job of placing students in colleges. There is some barrier at this level.

# Recommendations

Therefore we recommend looking at ways to improve secondary education. Finding where there is a disconnect, and how we can help these individuals be motivated about, and pursue, post-secondary education. In addition to that, we also recommend creating organizations that help individuals gain access to not only guidance and mentorship, but also help with researching and applying to colleges, and looking for what kind of financial aid is available to them, at both the state and federal level, and help applying for it.


## Citations

<sup>1</sup> Yohalem, N., Cooley, S. 2016. “Opportunity Youth in the Road Map Project Region”. Community Center for Education Results. Available at: https://bit.ly/2P2XRF3.

<sup>2</sup> Anderson, T., Braga, B., Derrick-Mills, T., Dodkowitz, A., Peters, E., Runes, C., and Winkler, M. 2019. “New Insights into the Back on Track Model’s Effects on Opportunity Youth Outcomes”. Urban Institute. Available at: https://bit.ly/2BuCLr1.

<sup>3</sup> Seattle Region Partnership. 2016. “King County Opportunity Youth Overview: Demographics of opportunity youth and systemic barriers to employment”. Available at: https://bit.ly/2oRGz37.

<sup>4</sup> Morton, N. 2019. “Nearly 19,000 youth in King County are neither working nor in school. How one Seattle nonprofit is changing that.” The Seattle Times. Available at: https://bit.ly/2W5EufR.
