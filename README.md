# Risk, Artificial Intelligence and Discrete Geometry

![ci](https://github.com/munichpavel/risk-ai-workshop/actions/workflows/ci-cd.yml/badge.svg)

## Quick-start


### Obtaining the repository

Either

`git clone` the repository

OR

download a zipped-version of this repo from GitHub

then `cd` into the created folder

### Running the workshop notebooks in [noteebooks](notebooks/)

#### Option 1, local installation

* create a virtual environment (recommended)  e.g. with [venv](https://docs.python.org/3/library/venv.html), [conda](https://docs.conda.io/en/latest/) or other.
* install python dependencies with `pip install -r requirements.txt` in a virtual environment. Note: the [fake-data-for-learning package](https://github.com/munichpavel/fake-data-for-learning) has some non-python dependencies; see its [installation instructions](https://github.com/munichpavel/fake-data-for-learning/blob/main/README.md#installation).

#### Option 2, Google Colab

If you don't mind giving Google access to even more of your data, another option is to use the Google Colab version of hosted notebooks.

**Steps**

1. either clone or download this repository as above
1. Upload the repository folder to your Google Drive.
1. To open a notebook in Colab, navigate in your google drive to the notebooks folder, and double click on the notebook you want to open. It should look something like this:
![openining a notebook from google drive](readme-graphics/open-notebook-from-drive.png)
1. At the top of each Colab notebook you want to run, add a cell and paste in the contents
```python
import os
from google.colab import drive
from google.colab import drive
drive.mount('/content/drive')

os.chdir('/content/drive/My Drive/risk-ai-workshop-main')
# Debug: if you don't see the top level contents of https://github.com/munichpavel/risk-ai-workshop/tree/d78309e23a2200d6e8dc71f657cefd0693bab51b
# from the below print statement, then something has gone wrong
print(os.listdir())

!pip install -r requirements.txt
```

It should look something like this (after you run it):

![Additional first cell if using Colab](readme-graphics/colab-first-cell.png)

Notes:

* Google will ask you for permissions to access your Google Drive. Please consider carefully before you grant this access.
* Since Colab already has many dependencies installed, you will likely get a message saying you will have to restart your runtime, hence losing any saved variable values. Once you are sure you have saved anything you don't want to lose, select "Restart Session"

![colab message to restart session for installation of custom dependencies](readme-graphics/colab-restart-session-post-install.png)

## Workshop topics

Slides are built as part of the repo's [ci-cd pipeline](.github/workflows/ci-cd.yml), and be found under [releases](https://github.com/munichpavel/risk-ai-workshop/releases). See e.g. [the v2022.1.1 release](https://github.com/munichpavel/risk-ai-workshop/releases/tag/v2022.1.1).

### Artificial intelligence for risk management

[Examples and exercises](notebooks/introduction-examples-exercises.ipynb)

### Discrete geometry for risk

Examples and exercises: [graphical models](notebooks/graphical-models-exercises.ipynb), [probability polytopes](notebooks/probability-polytope-exercises.ipynb), and [simpson's paradox](notebooks/simpsons-paradox-examples-exercises.ipynb)

### Correlation and causality

[Examples and exercises](notebooks/causal-models-exercises.ipynb)

### Adversarial regularization regimes in classification tasks

* [Examples and exercises](notebooks/adversarial-ml-examples-exercises.ipynb)

## Grading scheme for University of Ljubljana Masters in Mathematical Finance

### 2024 Workshop

Exercise are to be submitted per team to Professor Košir before or on June 24, 2024.

The number of points for a correct solution for each exercise brings is equal to $2^{\mathrm{number\,of\,stars}}$.

The grading for this seminar as part of the course is binary, i.e. "pass" or "no-pass". For a grade of "pass" your team will require

1. at least 8 points, and
1. at least one correctly solved exercise from each of the four sessions from [workshop topics](#workshop-topics) above.

For an example of the 2nd criterion, to satisfy this criterion for the 2nd topic, [Discrete Geometry for Risk](#discrete-geometry-for-risk), you need to successfully solve at least one problem from one of the three exercise notebooks.

## Relate python packages

In the exercise notebooks and `requirements.txt` you see which python packages I used in creating and solving the exercises, though this list is far from exhaustive. Below are some (additional) python packages that may be useful

## Graph visualization

* [graphviz](https://graphviz.readthedocs.io/en/stable/)
* [networkx](https://networkx.github.io/), plus many graph operations

## Bayesian networks, causal inference

* [pgmpy](https://pgmpy.org/)
* [brent](https://koaning.github.io/brent/)
* [causalgraphicalmodels](https://github.com/ijmbarr/causalgraphicalmodels)
* [causality](https://github.com/akelleh/causality)
* [dowhy](https://microsoft.github.io/dowhy/)
* [pyro](https://pyro.ai/)

## Troubleshooting

If you get a `ModuleNotFoundError: No module named 'risk_learning'` in one of the example notebooks, try the following

1. Make sure you are starting jupyter from your virtual environment, e.g. first run `source venv/bin/activate` or `conda activate`.

1. Ensure you've installed the local package, e.g. with `pip install .`

1. Try adding the python path before calling the jupyter notebook via

    ```console
    PYTHONPATH=$(pwd) jupyter notebook
    ```

## Releases

### Process of creating a new workshop release

If the release is for a new workshop year, then first manually change the version in the code-base to `<new-year>.0.0`. This release need not be a tagged release, as it is the same as the final release of the previous workshop in an earlier year.

Once an initial release has been created for a new workshop, create subsequent tagged releases by using [bump2version](https://pypi.org/project/bump2version/).

## Release history

Note: I do not follow [Semantic Versioning](https://semver.org/) for this project. For the first digit (in semver, `major`), I use the year of the target workshop, and for the last (in semver `patch`), I increment when a chunk of work is done towards giving the workshop. The middle digit (in semver, `minor`) stays on 0 until I give the workshop, when it bumps to 1. Fixes to the given workshop get reflected in the patch versions `yyyy.1.<patch-version>`.

### 2024.1.4

* Add missing references for adversariality lecture
* Add google colab instructions
* Update grading schema for 2024 workshop
* Add more proof details from equalities in lecture on correlation and causality

### 2024.1.3

* Add additional output plus commentary for do vs non-do probabilities to `causal-models-exercises` notebook.

### v2024.1.2

* Add concluding slide to introductory presentation
* Remove older version of causal model exercises notebook
* Git ignore common virtual environment folders

### v2024.1.1

Fix 2024 version for workshop, as some new image files were missing

### v2024.0.0

* Add adversarial regularization regime slides and exercises as final session
* Update intro slides
* Update python versions run in ci (drop 3.6, add higher versions)
* Add escaping of model-selection-notebook correlation tex table columns
* Fix latex color theme name for Ubuntu
* Update github action versions for checkout and setup-python
* Remove tox, as it duplicated the ci-cd matrix strategy

### v2022.1.2

Replace slide publishing workaround with instructions on accessing compiled slides under releases.

Remove (now deprecated) static example ATE result in correlation-causality slides.

Remove RY in release process overview

### v2022.1.1

* Fix typos in discrete geometry slides, including definition of d-separation
* Fix hit-rate average treatment effect results in slides
* Add ci / cd release step to make ci / cd slide artifacts publicly available

### v2022.1.0

Refactor introduction and concluding lectures, as well as their exercises

Add simpson's paradox content and exercises to the discrete geometry lecture

Add ci tests of package and notebooks for mac and windows (latest) operating systems

### v2022.0.2

Add github actions workflow for automated testing, with unit, notebook-run and latex-slides-build

Add github actions job for continuous delivery of slide artifacts

Add example of model selection pipeline for artificial credit scoring data

### v2022.0.1

Add initial exercises and methods for Simpson's paradox.

### v2020-02-uni-lj

Created prior to the above versioning scheme, workshop at University of Ljublana in February, 2020.
