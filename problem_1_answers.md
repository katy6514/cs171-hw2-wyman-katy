Homework 2 
==========

Problem 1 
---------

Chosen Repository: https://github.com/syntagmatic/parallel-coordinates/

Contributors to a repository
Commits Activity
Code Frequency
Punch card
Pulse of a repository
Calendar Map

For each of the visualizations listed above, answer the following questions:

1. Who is the audience? (e.g. project manager, contributor, project user, visitor, etc.)

2. What data have been used? How can you get the data using the GitHub API? (Note that it can be the combination of multiple queries and their processing).

3. Those visualizations are updated over time. What happens if suddenly a contributor pushes many commits in a short time interval? How would you address this particular issue?


Contributors to a repository
----------------------------

	1. This visualization seems like it's intended for use by a project manager. By glancing at the commit contribution view, a manager can get an idea of progress over time of the project. He/she can see when a large number of commits to the repository took place, and by looking at each contributor's individual chart, they can see who has been doing how much work and when. The manager can also filter the view to just look at additions or deletions for the overall repository as a function of time, or for an individual contributor over time. 

	2. To recreate this chart, you'd have to start with this API call: https://api.github.com/repos/syntagmatic/parallel-coordinates/commits.  This gets you information on each commit, and the information necessary to recreate these charts are time of commit and author of commit. They also grab information about lines deleted and lines added, as well as their avatar URL. For lines added/deleted per commit you'd have to do another API call similar to the one above but on and individual SHA number for each commit to find out the lines deleted and lines added.

	3. Many commits in a short amount of time would register on these charts as a sharp increase in activity, with not a lot of detail. To make this chart more informative in situations like this, I would make it scalable, a user could zoom in on a time period of the chart (whereas now it's static), the scaling would allow for more detail on commit activity in short time periods.


Commits Activity
----------------

	1. These charts are a little more time-specific then the "Contributors to a Repository" charts. They are probably still intended for project managers, but perhaps also for contributors. A viewer can get more specific time information about the progress of a project namely when commits were pushed per week and per day once you've selected a week.

	2. These charts make use of the data found form the same commit API call: https://api.github.com/repos/syntagmatic/parallel-coordinates/commits and appears just to use the time of commit. These charts bin the data used in the previous charts into weeks, and really only displays the number of commits: per week on the top chart (in bar format), and then broken up per day of week on the bottom (in a line chart format).

	3. Many commits in a short amount of time would register in two ways on this page. For the bar chart I assume it would rescale the vertical axis so other week's bar charts would appear shorter in comparison to a week with a large number of commits.  If the high-activity week grows too large so that other weeks all appear too small, I would probably rescale the cart so the vertical axis is a log scale, this would allow for all bars to appear on the same scale without the small ones getting scaled down so small that they barely register. This solution would also work for the weekly line chart at the bottom.


Code Frequency
--------------

	1. 














