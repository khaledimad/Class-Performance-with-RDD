# Class-Performance-with-RDD

## Explore the data and see whether grades depend on the class size. 
From plotting and quantiles of the 2 variables ( “class_size”, “mean_test_score”), we can see the
mean_test_score’s relationship with class_size is not obvious as class_size increases. However,
there is a cut-off near class_size = 30, separating the different ranges of mean_test_score before
and after. The mean_test_score drops sharply after the cut-off.<br>
The correlation between the mean test scores and class size is -0.57, which is significantly large.
Meaning, the mean test score decreases as the class sizes decrease. We think the cut-off is a
stronger indicator of the relationship between mean_test_score and class_size. The overall
relationship between the two variables is not continuous.

![Class Size](https://github.com/khaledimad/Class-Performance-with-RDD/blob/master/Images/Image01.png)

## Look at summary statistics of the original research
The class mean size is 31.4, we could assign the students from the class with sizes between 27 -
31 in the treatment group and students from the classes with size between 31 - 36 in the control
group. But based on the plot, we could observe the cut-off point as 30. Hence it is hard to tell
where the cut-off is based on summary statistics – the point where the mean_test_score sharply
drops as class_size increases.<br>
Regression Discontinuity Design (RDD) is an appropriate tool for this case. The running variable
would be the class size. The measurement would be on the mean test scores. Treatment Xi is
determined by some threshold of a continuous variable Wi. The RDD utilizes observations with a
Wi close to the threshold to estimate treatment effect. We then could assume that they have a
similar pre-test condition and could attribute all the difference that we see in the post-test to the
treatment.<br>
Step 1: Construct data for RDD and set a cut-point point based on observation.<br>
Step 2: Run a regression on the RDD dataset to get an estimate of the treatment effect. We accept
different slopes before and after the cut-off.<br>
Step 3: Summarize the RDD model, we get a coefficient of estimate of the treatment effect.

![RDD](https://github.com/khaledimad/Class-Performance-with-RDD/blob/master/Images/Image02.png)

## Trying out RDD from Part 1 and apply the procedure to Part 2 above
From the summary of the model and the plot, we conclude when class_size exceeds 29.5, the
mean_test_score will drop approximately 10 points. Therefore, class_size does impact students’
grades.
![RDD on Data](https://github.com/khaledimad/Class-Performance-with-RDD/blob/master/Images/Image03.png)

When class_size is larger than the cut-off point, students’ grades severely drop. When class_size
is less than 29.5, the difference in mean_score is negligible. The same applies when class_size is
greater than 29.5. We recommend keeping the class size below 30.
