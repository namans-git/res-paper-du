## [Research Paper](https://www.researchgate.net/publication/371121916_Detection_of_Internet_Cheating_in_Online_Assessments_Using_Cluster_Analysis), Student Research Asst.


### **STARTING NOTE** 

I worked under [Mrs. Manika Garg Shandilya](https://scholar.google.com/citations?user=rl6x0sIAAAAJ&hl=en) for a period of 8-9 months in my final year during which I assisted her with her research paper. It was my first experience at something outside college coursework and I couldn't have asked for a better mentor and opportunity.
Talking about the notebooks in this repo, they can be understood, in conjunction, as a timeline of trying different machine learning and analysis techniques. Learning what works and how our thought processes evolved. Some notebooks might have no conclusions to them but they all play a role in figuring stuff out.

 ### res_paper_linreg.ipynb

using two independent variables 'diff_lvl'(difficulty level) (categorical- 1, 2 and 3 implying increasing order of difficulty) and 'prev_gpa' (previous gpa/test_score), we create a lin_reg model for predicting 'resp_time' (response time). Students who stray from what the model then predicts (assuming they've given the correct answer) can be flagged. But not every stray should be flagged/is worth flagging. For eg. A student with low 'prev_gpa' attempting a high 'diff_lvl' question and answering correctly well below the predicted response time should probably be flagged. But a student with the same independent variables answering wrongly plus taking a lot more time than the predicted response time even though strays from the norm, should not be flagged.

Now of course, like with everything 'outliers' exist, and in this particular situation (student exam data) even more so. A student can answer quickly and be correct or take longer than usual to answer and be wrong, and we couldn't really conclude anything from it but the idea is to raise 'flags' as we go through each model and look at things collectively.


### average_resp_time.ipynb

trivial. Classifying students on the basis of the relation of their respective response times to the class average. 

### dtree_rforest.ipynb

we have three numerical variables to work on this time. Grades, Exam duration (in secs) and attempt submission time (string format turned to datetime then to epoch). We scale these variables. Now, we have assigned a flagged behaviour '1' to every suspect student (which we've flagged ourselves by going through the data) and every other student the default behaviour '0' (how we've done is this shown in a notebook later on). The pairplot advocates for the classification in the fact that the 'std_scaled_submtime' is abnormally close for the flagged students (see pairplot). We now try the supervised techniques decision trees and random forests. the performance metrics aren't the best as one would imagine since exam data consisting of scores and times can't really be modelized. The idea remained the same regardless, if given enough data we create a model and if a new student strays from the expected, he/she is flagged. 

### svm.ipynb

we try another ml supervised algo called svm by classifying suspect students (the labels) and letting the algo create a model. The metrics are pretty bad even after tuning hyper parameters (which in theory increases performance). 


### time&diff.ipynb

in this script we solely work with **question difficulty** and the **time spent** on that question. first, we do some eda. A lot of it is what one would expect i.e low difficulty - lesser time spent (on average). What we want to work with is the average time spent on each question. The rest of the script revolves around that. First, by sorting students in descending order on the basis of time spent, we find many students answering instantaneously (0 seconds) whereas the average for those questions is around 80 seconds (also worth noting is the fact that the zero brings down the average itself).\
We also have the choice to sort students on the basis of the time difference (difference b/w their resp times and the avg for that particular question).\
After that, we find the avg resp times for each difficulty for each student (for eg KASHISH NA	took 3.285714 seconds on an avg for low difficulty questions, 22.4 seconds on an avg for med and	8 seconds for high diff questions). What we can do then is compare these particular averages to the class average. For eg. MANPREET SINGH took way less time than the avg for each difficulty, which can be flagged.\
Also we can work with the idea of 'time slope'. Even for the smartest student (unless he/she already knows of the question), a hard question should in theory take more time than an easy question. If students stray from that 'slope' (low diff -> lesser time, med diff -> relatively more time and so on), for eg answering all questions in an avg time of 4-6 seconds, he/she can be flagged (see MANPREET SINGH in final plot). If we add scores to this we can decipher if they're guessers/cheaters/extremely talented individuals.


### variable_importance.ipynb

Though there are only two var in this script, we find that later on that changes. We're only looking at the methods we want to use right now. There are broadly 4 unsupervised techniques for feature selection/variable importance namely filter methods, wrapper methods, embedded methods and hybrid methods. We only work with the filter methods for now. They pick up the intrinsic properties of the features measured via univariate statistics. They can effectively remove irrelevant features but are unable to remove redundant ones (which we can work on ourselves). Information gain is an entropy based method. It can be defined as the amount of information provided by the feature. The second one is the Extra Trees Classifier which utilizes multiple decision trees and selects features based on their importance scores, making it less sensitive to noise and irrelevant features. Finally, we work with a correlation matrix which is a very simple idea. Simply the feature that correlates more with the cluster variable is more important.


### EllipticEnvelope.ipynb

after scaling, we try using sklearn's object EllipticEnvelope which detects outliers in a Gaussian distributed dataset. We can play around with the contamination parameter, i.e. the proportion of outliers in the data set.

**NOTE** -- we start to look at unsupervised techniques in the form of clustering and certain analysis techniques developed from scratch.
