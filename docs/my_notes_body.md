# My Notes #

## Getting Started Questions:
* Do all students have B2 accounts? How are they accessed?
 * They are almost out of B2 units- need to get more?
* Do students run notebooks locally, or on B2/OpenAccess? Both.
* Who is running Windows at 32 bits?
* Do students know javascript? No.


## Getting Started Questions (2)
* Can students download and run something from git? They say yes, but
  it turns out to be no.



## Steps To Set Up Local Jekyll
Once the repo has been cloned, jekyll has to be set up in the new
clone.  Note that github pages need to be explicitly activated from
the github settings tab.

```
git submodule update --init  # to pull in the reveal.js submodule
gem install bundler -v 2.4.22
gem install jekyll
cd docs
cp ~/git/CMU-MS-DAS-Vis-S23/docs/Gemfile .  # to pick up customizations
bundle install
bundle exec jekyll serve  # starts the server on localhost
```



To Do:
* Great comic describing color blindness: ![A Vision in Monochrome](https://thenib.com/a-vision-in-monochrome/)
* Add details on how to do git clone step, or if git hasn't been covered
  in earlier classes, do a whole git lecture.
* Add some force to the prereqs.
* "Where are we with matplotlib" assignment: add requirement that their
  code should work even if the rows of the table are shuffled, and even
  if someone handed them a table from a completely different year.  That's
  just good practice, and it would avoid laziness in picking the minimum date.


To Do (2):
* "Seaborn" assignment: be explicit that they should get the log scale by
  using seaborn or matplotlib commands, *not* by adding a new column of
  logarithms.
* "Maps" assignment: be explicit that travel distances should be between
  centers.  GeoPandas will compute travel distances between boundaries but
  it differs a *lot* from haversine.
* Here is a nice [Haversine reference](https://community.esri.com/t5/coordinate-reference-systems-blog/distance-on-a-sphere-the-haversine-formula/ba-p/902128#:~:text=For%20example%2C%20haversine(%CE%B8),longitude%20of%20the%20two%20points)


To Do (3):
* Add a 'zoom in' before the marching squares slides, showing one square
  in the grid for context.
* Clarify the snow depth map step of the Maps exercise to say that the
  merge needs to be done in a way that preserves the records for which
  the snow depth location has no matching city information in the cities
  data.  Otherwise there is nothing for the geolocator step to do!


To Do (4):
* Add an example to the description of get_rel_path in the GraphViz assignment
  where if you pass the function '/foo/bar', '/foo/bar' it should return
  ('..', '.') and not the other way around.  This case actually happens
  at the very beginning of the iteration.
* Clarify Tableau requirements to say that they should demonstrate that their
  cross-vis filter is working by doing screen caps with two different subsets
  filtered (or all data and one subset).  I'm not sure how to clarify the
  requirement that some data element needs to be "computed".



## Class Calendar:

Class starts Tue Jan 16 and runs through April 25 with no break.
11AM - 12:20PM

* Jan 16: Block 1 part 1
* Jan 18: Git and GitHub
* Jan 23 (Tuesday): Block 1 part 2
* Jan 25 (Thursday): Block 1 colors, Block 2 contours and ggplot
* Jan 30 (Tuesday): Block 2 seaborn 1
* Feb 1 (Thursday): Block 2 seaborn 2


* Feb 6 (Tuesday) Block 3 maps 1; please install GraphViz and Gephi
* Feb 8 (Thursday): Block 3 maps 2, Block 4 web server
* Feb 13 (Tuesday): Block 4 graphs (incl Brendan/Gephi); please install Tableau
* Feb 15 (Thursday): Block 4 D3
* Feb 20 (Tuesday): Block 5 (Tableau); please install VisIt
* Feb 22 (Thursday): Block 5 (Tableau) continued


* Feb 27 (Tuesday): prev Block 6 (VisIt)
* Feb 29 (Thursday): Block 6 (VisIt) continued



## Maps assignment update using geopy

This was originally suggested by Charlie Chen in S22.  This
approach assigns counties to many more of the snowfall locs
than the current method.  This is Chen's regex-based method,
with minor mods.

```
from geopy.geocoders import Nominatim
geolocator=Nominatim(user_agent="joel_learns_geopy")
county = []
for i in snow_df['Location']:
    loc = geolocator.geocode(i + ' Pennsylvania US')
    a = r', (.*?) County'
    if len(re.findall(a, str(loc)))>0:
        county_str = re.findall(a, str(loc))[0].split(" ")[-1]
    else:
        # Try without the suffix
        loc = geolocator.geocode(i)
        if len(re.findall(a, str(loc)))>0:
            county_str = re.findall(a, str(loc))[0].split(" ")[-1]
        else:
            county_str = ""
    print(i,": ",county_str)
    county.append(county_str)
```



### Assignments
1. matplotlib assignment (class 1)
2. grammar of graphics, seaborn (class 4)
4. maps (class 6)
5. Flask exercise happens in class
6. GraphViz (class 8)
7. Tableau (class 10 or 11?)
8. VisIt (class 12)



# LaTeX Math Example

A sample of LaTeX math, so I remember how to do it later:

`$$ J(\theta_0,\theta_1) = \sum_{i=0} $$`



<!-- .slide: data-background="#ff0000" -->
## Color Change Demo ##
This is just a demo of how to change slide color
Note:
This is a note.
