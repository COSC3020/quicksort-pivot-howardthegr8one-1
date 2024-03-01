[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-24ddc0f5d75046c5622901739e7c5dd533143b0c8e959d652212380cedb1ea36.svg)](https://classroom.github.com/a/IF3rQO50)
# Quicksort Pivots

in the lectures I only briefly mentioned strategies for determining a good pivot
for quicksort. The implementation on the slides simply picks the leftmost
element in the part of the array that we consider as a pivot. I also mentioned a
few other ways of picking a good pivot, e.g. randomly.

Median-of-three is also a good way of picking a pivot -- inspect the first,
middle, and last elements of the part of the array under consideration and
choose the median value. Using the probabilities for picking a pivot in a
particular part of the array (in the same way as we did on slide 34), argue
whether this method is more or less (or equally) likely to pick a good pivot
compared to simply choosing the first element. Assume that all permutations are
equally likely, i.e. the input array is ordered randomly.

Your answer must derive probabilities for choosing a good pivot and
quantitatively reason with them.

Add your answer to this markdown file. [This
page](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/writing-mathematical-expressions)
might help with the notation for mathematical expressions.

## Median of Three Pivot Selection

When choosing a pivot randomly (or by selecting the first or last element) results in choosing a good pivot roughly $\frac{1}{2}$ of the time, as half of the elements of a random array could be good pivots. 

By choosing median of three the probablity that the pivot we choose is good rises to $68.75$%. The reason for this is because of the following: 

The first $\frac{1}{4}$ and last $\frac{1}{4}$ of the array contain bad pivots, while the middle two $\frac{1}{4}$'s contain good pivots, in other words we have $B_{1}, G_{1}, G_{2}, B_{2}$ as our possible pivots. Since we're taking the median of three then we have $4\cdot4\cdot4 = 64$ total pivot possibilities. 

Whenever we choose a permuation where two or more of the pivots come from the same bad section then we'll have a bad pivot that doesn't divide the array effectively. Thus the following would all result in bad pivots:

$B_{1}, G_{1}, B_{1}$

$B_{1}, G_{2}, B_{1}$

$B_{1}, B_{1}, B_{2}$

$B_{1}, B_{2}, B_{2}$

$B_{2}, G_{2}, B_{2}$

$B_{2}, G_{1}, B_{2}$

Since there are six combos above and each has 3 permuations then we've found 18 bad possible pivots. There are two more though:

$B_{1}, B_{1}, B_{1}$

$B_{2}, B_{2}, B_{2}$

Neither of these have different permuations and thus we have 20 bad pivot options and we have 64 total pivots, therefore $\frac{44}{64}=\frac{22}{32}=\frac{11}{16}=68.75$% of our pivots will be good using the median of three method, making it more efficient than choosing randomly. 
