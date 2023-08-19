### **Clustering**
using supervised techniques for detection of stray/deviated behaviour may be a good idea in other cases, but in a scenario like ours where we can't say for sure if someone is cheating or not (which would label the data), we shift to clustering; to analysing data as it is and not prediction. We work with K means. 

### **optimal_clusters.ipynb**

We start with a dataset of name, ques_no, response_time, age, gender and prev_gpa. Now to find optimal clusters for clustering first we select relevant numeric variables, which would be response_time, age and prev_gpa (not ques_no). We work with two well known methods of finding optimal clusters for kmeans clustering: (1) Elbow method - iterates through a number of clusters and then chooses the number where there's a sharp dip in the error. (2) Silhouette method - it is a measure of how similar a data point is within a cluster compared to other clusters. We choose the cluster that maximizes the silhouette score.

### **rough_calc_final.ipynb**

in this notebook we make an effort to segregate the assessment variables (score and time) further by including filters (on the basis of difficulty level and if response == correct). We find (for each student) 'time_spent' and 'score' for each difficulty level (time they spent on low level questions, mid level and so forth) and if the answer is correct.

To explain further, for a student 'x', we will have their response time for :
1. low difficulty questions AND if they answered correctly (so two seperate columns)
2. medium difficulty questions AND correct/not correct
3. high difficulty question AND correct/not correct.

We also have their scores for each difficulty level. To reiterate, one single aspect can't really be used to come to conclusion, we need as much info as possible. We then declare a const of relaxation_period of 10 secs (no real method was used to come up with this number, maybe std dev could've been used. this is just being used to study the data regardless) and find 'flags', where students straying from the norm by more than 10 secs are flagged. In the end, we have a dataset using which we could possibly perform some clustering. 

We have the variables:
1. students
2. total score (out of 15)
3. total time spent on the exam (on 15 questions)
4. flags (if their response times are +-10 of the average response time)
5. flagged when correct (same as flags but question was answered correctly)
6. low/mid/high_diff_rt: collective response time of each student for each difficulty level
7. low/mid/high_diff_rt_correct: same as (6) but the questions are answered correctly.
