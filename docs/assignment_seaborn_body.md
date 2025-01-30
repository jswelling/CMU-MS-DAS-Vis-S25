### Working with seaborn

This assignment involves using seaborn to examine some statistical data.  It should be
possible to do the assignment in a jupyter notebook running the *generic_requirements.txt*
environment.  Hand in the notebook on Canvas.


There are two files in the class data directory, *california_counties.tsv* and
*covid_surge_offsets.tsv*.  The first contains information about the counties in California,
including their area and population.  The second contains the date offsets of the four COVID
wave peaks we saw earlier in the *covidcases_test.csv* dataset.



#### Step 1: Read in and merge the data.

Read in the county information and the surge offset information.  Use a Pandas "merge" operation
to merge the two datasets, matching the key "area" in the *covid_surge_offsets* dataset with
the key "name" in the *california_counties* dataset.



#### Step 2: Add a population density column.

Just divide the population of each county by its area in square miles.



#### Step 3: Create a scatterplot with seaborn.

Try plotting surge_offset_4 against the population density.  It's informative to
use different symbols for the counties that based on their "general_law_or_charter"
characteristic.

Use a log scale in the population_density direction to make the correlation clearer.
Set the Y axis of the graph to log scale explicitly; do not add a column of log
values to your dataframe!