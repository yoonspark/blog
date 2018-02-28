---
layout: post
title: Organizing Project Directory
---

A crucial element for reproducible research is simple, transparent, and consistent organization of data and analysis scripts.  In this post, I share some of the practices I have adopted and developed in my work as a research analyst.

# Consistent Naming Conventions

For effective organization of the project directory, it is helpful to develop and maintain some consistent naming conventions.  For instance, I always put the prefix "mod" to analysis scripts whose major aim is model-fitting; "make_rdata" to scripts that transforms data into a desired set of R objects and save them in RData format; and so on.  This practice helps me to not only quickly come up with an appropriate file name but also more easily locate each file later.  Having a set of consistent naming conventions saves one much time like a well-established habit.

Another practice I have adopted is use capitalized "snake case" to name directories and lowercase one to name files.  Hence, directory names follow the format "Example_Directory_Name"; and file names "example_file_name.extension".  The capitalization helps me (and others who are informed of the convention) to better distinguish directories from files.

Note that directory and file names should be concise yet descriptive enough.  For instance, `mod1.R` is not a good file name; `mod_gpa_vs_demog.R` is better.

# Integrity of Each Project Directory

I strongly recommend maintaining each project-level directory (e.g., teacher survey analysis) as an independent unit.  In other words, minimize each project directory's dependency on external sources as much as possible.  This integrity, or self-sufficiency, of each project directory will help its stable management and maintenance.

A pivotal way to achieve integrity of project directory is to house all relevant raw data *within* each project directory.  If we trace back all activities in data analysis, we eventually arrive at raw data: it is from this fundamental resource that everything else has sprung out -- from cleaned and merged datasets to statistical models.  Hence, as long as we have the raw data in their original state (in the sense of "state at the time of our initial use"), we can potentially replicate every step of data cleaning and analysis we have taken and get to the same place as we currently are (I added "potentially" because full replication requires other elements, as will be discussed below).  In the end, we can conceptualize the entire data project as numerous layers of processing upon raw data.

A recommended practice is to have "Data" sub-directory in every project directory and keep all relevant raw data and data wrangling scripts (as well as derived data sets) in this sub-directory.  Personally, I organize this "Data" directory such that raw data are saved in a separate space (aptly named "Raw_Data") and data wrangling processes are organized into other sub-directories (e.g., "Build_SchoolLevel_Attendance").

Another practice essential to integrity of project directory is to use relative pathnames.  Hence, use
```
../../Data/Build_SchoolLevel_Attendance/attd_schlvl.RData
```
rather than
```
/export/usiccsr/projects/SchoolSupportNetworks/Data/Build_SchoolLevel_Attendance/attd_schlvl.RData
```
This will protect the project directory from broken pathnames that may result from the system-level reorganization.

# Version Control

Once the backbone of the project directory is set in place, the directory should then be version-controlled using such tools as Git.  For more complete reproducibility, we would need to version-control all raw data along with wrangling and analysis scripts.  Given data confidentiality needs and restrictions, however, we may need to confine version-control to wrangling and analysis scripts only.  Even so, we will essentially turn the project directory into a coherent machinery that will always reproduce consistent results as long as the same set of raw data are placed in the right place (i.e. "Raw_Data" sub-directory discussed above).

---

I am aware these discussions may sound quite abstract.  Unfortunately, I cannot put my work projects on the public domain due to confidentiality issues.  Hopefully, I can soon start a new personal project through which I can better demonstrate the points I made in this post.
