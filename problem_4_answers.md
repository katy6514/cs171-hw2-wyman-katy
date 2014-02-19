Homework 1 
==========

Problem 4 
---------

Q1. The domain() function is the data range upon which the scale is calculated. What does d3.selectAll("tbody tr")[0].length-1 mean?
	
	It is selecting all the rows and finding the number of rows. Subtracting one so the iteration works out right. This will set up the correct range for domain() to iterate over.

Q2. Add the snippet in your code. Describe, in words, what the following function calls return: color(0), color(10) and color(150)?

	Each call to color() returns an approriate scaled color that corresponds to the number input.

Q3. If the array passed to domain() was the minimum and maximum rate values, how would that change the scale? In what situations would this be appropriate?

	As it is we're getting 50 evenly spaced colors spread amongst the chart