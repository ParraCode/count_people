# CORE FINAL PROJECT

A Data Science project to count people.

We’ll count the number of people who are heading “in” or “out” of a department store in real-time using OpenCV.

## Table of contents

<!-- TOC depthTo:3 -->

- [CORE FINAL PROJECT](#core-final-project)
  - [Table of contents](#table-of-contents)
  - [Data Source](#data-source)
  - [Data Analysis with Jupyter Lab](#data-analysis-with-jupyter-lab)
  - [Combining both object detection and object tracking](#combining-both-object-detection-and-object-tracking)
  - [Project structure](#project-structure)
  - [Pre-commit](#pre-commit)
  - [Contributing](#contributing)
  - [Resources](#resources)

<!-- /TOC -->

## Data Source

This project is based on a dataset of [Crowd Human](https://www.crowdhuman.org/) that contains information about bounding box and photos.

There are two directories: `val` that contains 4.370 elements and `train` contains 15.000 elements.

Finally,there are two files in which you can find the information of the bounding box and faces of each element.

## Data Analysis with Jupyter Lab

To make the Exploratory Data Analysis, I've used [Jupyter Lab](https://jupyter.org/)

During the analysis, I've used the following libraries:

- [pandas](https://pandas.pydata.org/)
- [matplotlib](https://matplotlib.org/)
- [seaborn](https://seaborn.pydata.org/)
- [numpy](https://numpy.org/)
- [skcikit-learn](https://scikit-learn.org/stable/)
- [OpenCV](https://pyimagesearch.com/opencv-tutorials-resources-guides/)
- [dlib](http://dlib.net/)
- [imutils](https://github.com/jrosebr1/imutils)

## Combining both object detection and object tracking

Highly accurate object trackers will combine the concept of object detection and object tracking into a single algorithm, typically divided into two phases:

- `Phase 1 — Detecting:` During the detection phase we are running our computationally more expensive object tracker to (1) detect if new objects have entered our view, and (2) see if we can find objects that were “lost” during the tracking phase. For each detected object we create or update an object tracker with the new bounding box coordinates. Since our object detector is more computationally expensive we only run this phase once every N frames.
- `Phase 2 — Tracking:` When we are not in the “detecting” phase we are in the “tracking” phase. For each of our detected objects, we create an object tracker to track the object as it moves around the frame. Our object tracker should be faster and more efficient than the object detector. We’ll continue tracking until we’ve reached the N-th frame and then re-run our object detector. The entire process then repeats.

The benefit of this hybrid approach is that we can apply highly accurate object detection methods without as much of the computational burden. We will be implementing such a tracking system to build our people counter.

## Project structure

## Pre-commit

This project uses `pre-commit` to test the repository files before making a commit.

You need to install it with `pip install pre-commit` within the repository

## Contributing

Pull Requests are welcome! Feel free to contribute to the project.

## Resources

- https://pre-commit.com/index.html
- https://pyimagesearch.com/2018/08/13/opencv-people-counter/