# <img itemprop="image" class="avatar flex-shrink-0 mb-3 mr-3 mb-md-0 mr-md-4" src="https://avatars.githubusercontent.com/u/89392827?s=200&amp;v=4" width="100" height="100" alt="@CMU-MS-DAS-Vis-Mini Spring 2025"> CMU-MS-DAS-Vis-25
CMU MS-DAS Visualization Class course materials, Spring 2025

## Quick Start ##

This class uses a lot of different tools, and they do not all work well together.  Thus several different requirements.txt files are
provided.  To set up a generic Python environment for the class using conda, do:
```
$ conda create --name VisClassEnv python=3.8
$ conda activate VisClassEnv
$ pip install -r https://raw.githubusercontent.com/jswelling/CMU-MS-DAS-Vis-S25/main/requirements_generic.txt
$ python -m ipykernel install --user --name VisClassEnv --display-name "Python (VisClassEnv)"
```
Any specific example from the class may require a different environment, but they are installed from their requirements.txt files in the same way.
