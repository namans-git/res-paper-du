[research paper](https://www.researchgate.net/publication/371121916_Detection_of_Internet_Cheating_in_Online_Assessments_Using_Cluster_Analysis), student research asst. 

**STARTING NOTE** -- the notebooks, in conjunction, can be understood as a timeline of trying different ml, analysis techniques and learning what works best. Some notebooks might have no conclusions to them but they all play a role in figuring stuff out.

**res_paper_linreg.ipynb** -- using two independent variables 'diff_lvl'(difficulty level) (categorical- 1, 2 and 3 implying increasing order of difficulty) and 'prev_gpa' (previous gpa/test_score), we create a lin_reg model for predicting 'resp_time' (response time).

 

Students who stray from what the model then predicts (assuming they've given the correct answer) can be flagged. But not every stray should be flagged/is worth flagging. For eg. A student with low 'prev_gpa' attempting a high 'diff_lvl' question and answering correctly well below the predicted response time should probably be flagged. But a student with the same independent variables answering wrongly plus taking a lot more time than the predicted response time even though strays from the norm, should not be flagged.

Now of course, like with everything 'outliers' exist, and in this particular situation (student exam data) even more so. A student can answer quickly and be correct or take longer than usual to answer and be wrong, and we couldn't really conclude anything from it but the idea is to raise 'flags' as we go through each model and look at things collectively.

**average_resp_time.ipynb** -- trivial. Classifying students on the basis of the relation of their respective response times to the class average. 

**dtree_rforest.ipynb** -- we have three numerical variables to work on this time. Grades, Exam duration (in secs) and attempt submission time (string format turned to datetime then to epoch). We scale these variables. Now, we have assigned a flagged behaviour '1' to every suspect student (which we've flagged ourselves by going through the data) and every other student the default behaviour '0' (how we've done is this shown in a notebook later on). The pairplot advocates for the classification in the fact that the 'std_scaled_submtime' is abnormally close for the flagged students (see pairplot). We now try the supervised techniques decision trees and random forests. the performance metrics aren't the best as one would imagine since exam data consisting of scores and times can't really be modelized. The idea remained the same regardless, if given enough data we create a model and if a new student strays from the expected, he/she is flagged. 

**svm.ipynb** -- we try another ml supervised algo called svm by classifying suspect students (the labels) and letting the algo create a model. The metrics are pretty bad even after tuning hyper parameters (which in theory increases performance). 

**NOTE** -- we start to look at unsupervised techniques in the form of clustering and certain analysis techniques developed from scratch.

**time&diff** -- in this script we solely work with **question difficulty** and the **time spent** on that question. first, we do some eda. A lot of it is what one would expect i.e low difficulty - lesser time spent (on average). What we want to work with is the average time spent on each question. The rest of the script revolves around that. First, by sorting students in descending order on the basis of time spent, we find many students answering instantaneously (0 seconds) whereas the average for those questions is around 80 seconds (also worth noting is the fact that the zero brings down the average itself). 
We also have the choice to sort students on the basis of the time difference (difference b/w their resp times and the avg for that particular question).
After that, we find the avg resp times for each difficulty for each student (for eg KASHISH NA	took 3.285714 seconds on an avg for low difficulty questions, 22.4 seconds on an avg for med and	8 seconds for high diff questions). What we can do then is compare these particular averages to the class average. For eg. MANPREET SINGH took way less time than the avg for each difficulty, which can be flagged. 
Also we can work with the idea of 'time slope'. Even for the smartest student (unless he/she already knows of the question), a hard question should in theory take more time than an easy question. If students stray from that 'slope' (low diff -> lesser time, med diff -> relatively more time and so on), for eg answering all questions in an avg time of 4-6 seconds, he/she can be flagged (see MANPREET SINGH in final plot). If we add scores to this we can decipher if they're guessers/cheaters/extremely talented individuals.

**optimal_clusters** -- we work with two well known methods of finding optimal clusters for kmeans: (1) Elbow method - iterates through a number of clusters and then we choose the number where there's a sharp dip in the error. (2) Silhouette method - it is a measure of how similar a data point is within a cluster compared to other clusters. We choose the cluster that maximizes the silhouette score.
