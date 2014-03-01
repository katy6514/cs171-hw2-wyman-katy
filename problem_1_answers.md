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

	1. This chart is most likely intended for project managers or contributors to the project. It gives a visual representation of new lines of code added to the project, or when large amounts of code were removed. If a large amount of code suddenly disappears a contributor could look at this graph to determine when the code was removed.

	2. This chart shows the number of lines added/deleted over time, binned into weeks: Additions in lines of code in green on the positive (top) end of the graph and deletions in red on the bottom. Code written to generate this probably used this API call: https://api.github.com/repos/syntagmatic/parallel-coordinates/commits{/sha} for each commit SHA. Each of these API calls has a time of commit as well as "additions" and "deletions," so once you have a list of all commits, you can iterate through to extract the time of each commit and the lines of code added or deleted.

	3. Many commits in a short amount of time would register as big positive or negative peaks only if a large amount of lines of code were added or subtracted. If that were the case, I would bin the data into time units smaller than a week or possibly use a log scale.


Punch Card
----------

	1. This chart is probably intended for a manager, and shows when during the day a team is making commits to a project repository with the data binned into hours. 

	2. Again this chart probably gets its data from https://api.github.com/repos/syntagmatic/parallel-coordinates/commits and uses time of commit. Binning each commit into the hour it happened, and plotting a circle that scales in size with increasing number of commits, they spread the data into a calendar of weekly commits. Bigger circles means more commits, and you can see most commits (at least for my chosen repository) tend to occur in the evenings or wee hours of the morning.

	3. Many commits in a short amount of time would create larger and larger circles. In that case, I might impose an upper limit on the size of any one circle per hour and perhaps color it differently than the others in the graph signifying that there's more information to explore. On click I might show an expanded hour binned into 10-minute segments and recreate the circle sizes in that heavily-committed hour into the 10-minute intervals.


Pulse of a repository
---------------------

	1. This page looks like a dashboard of sorts for contributors. You can see the immediate status of the repository's requests and issues. You can see who has been making overall the most commits to the repository over a timescale of your choosing: A month, a week (the default), the past 3 days, and the past 24 hours

	2. This page probably makes use of lots of different API calls. Definitely from the commit API call used in the other graphs for things like time of commit and committer name, but also from the pulls_url: https://api.github.com/repos/syntagmatic/parallel-coordinates/pulls{/number} and issues: https://api.github.com/repos/syntagmatic/parallel-coordinates/issues{/number} for status of requests and issues.

	3. Many commits in a short amount of time would effect the bar chart the most, and it would cause the users who were doing most of the commits to have larger bars. I would code the bar chart so that it scales according to the highest bars, and if necessary, make it a log scale instead of linear.


Calendar Map
------------

	1. This map might be meant for a project supervisor? Though it doesn't give much information more than a summary of when commits were made per day of the week over the last year. This could give you an idea of how productive a contributer was and when.

	2. Data shown in this graph again could be recreated from the commit API call used in all other graphs, as well as the pulls and issues API calls. What you would need is the date of the contribution, and then you need to count up all contributions per day. The higher the number of contributions, the darker green the box is. 

	3.Many commits in a short amount of time would show up as very green boxes. If so many commits happened in one day that the dark shade of green stopped being meaningful, I might extend the hue scale to more than 5 shades.












