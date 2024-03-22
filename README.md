# jrnl
Command line time tracking and journaling utility

## Overview
jrnl is a set of bash utilities used to record and query time spent on activities.  

There are currently three utilities:

* jrnl: records the time spent on an activity, 
* jrnl_proj: queries time spent on a specific activity,
* jrnl_date: queries which activities were worked on during a specific day.

## jrnl
jrnl records the time you spent on a specific activity.  It allows recording of activity or work item numbers, project codes, a description on the activity, and the time spent (in hours).

Each time the utility is run, a new entry is added to a plain text file called journal.txt.

Multiple project codes and activity numbers can be specified for each entry.

Project codes and activity numbers (work items) are alphanumeric and do not have a fixed length.

### Usage:
`> ./jrnl project_code work_item "brief description" hours`

#### Example:
`> ./jrnl 001 jrnl_time_tracking "Wrote README.md for jrnl utilities" 0.5`

In this example, a project code of 001 is specified.
The work item is jrnl_time_tracking, and the time spent is 0.5 hours.

#### Example:
`> ./jrnl 8472/74656 98765 "Added annotations to map" 1.5`

In this example, the work item 98765 belongs to two different project codes, 8472 and 74656.  The time spent on this activity was 1.5 hours.

## jrnl_proj
jrnl_proj queries the journal.txt file and returns the time spent on the specified activity or project.

The query is not case sensitive.

### Usage:
`> ./jrnl_proj number`

#### Example:
`> ./jrnl_proj jrnl_time_tracking`
 
` 2021-06-27:	test note`                                                             
`Total hours:0.5`

This query returns the date and total time spent on the jrnl_time_tracking activity.

#### Example:
`> ./jrnl_proj 8572`

` 2021-06-28:	Investigated error in navigation algorithm`                            
` 2021-06-29:	Started work on correcting error in navigation algorithm`              
` 2021-06-30:	Completed correction to fix error in navigation algorithm`             
` 2021-07-01:	Added annotations to map`                                              
`Total hours:16.5`

This query returns the dates and total time spent on project 8472.

## jrnl_date
jrnl_date displays the activies worked on during the specified date.  If no date is specified, it returns the activies worked on today.

### Usage:
`> ./jrnl_date [YYYY-MM-DD]`

#### Example:
`> ./jrnl_date`

`Entries for 2021-07-01`

`8472/74656 :98765          Added annotations to map                                    : 1.5`

`----`

`Total8472/74656  hours:       1.5`

`Total hours:                 1.5`

#### Example:
`> ./jrnl_date 2021-06-30`

`Entries for 2021-06-30`

`8472/74656 :98764          Completed correction to fix error in navigation algorithm   :  2.0`

`-----`

`Total8472/74656  hours:         2`

`Total hours:                   2`
