[research paper](https://www.researchgate.net/publication/371121916_Detection_of_Internet_Cheating_in_Online_Assessments_Using_Cluster_Analysis), student research asst. 

**STARTING NOTE** -- the notebooks, in conjunction, can be understood as a timeline of trying different ml, analysis techniques and learning what works best. Some notebooks might have no conclusions to them but they all play a role in figuring stuff out.

**res_paper_linreg.ipynb** -- using two independent variables 'diff_lvl'(difficulty level) (categorical- 1, 2 and 3 implying increasing order of difficulty) and 'prev_gpa' (previous gpa/test_score), we create a lin_reg model for predicting 'resp_time' (response time).

 

Students who stray from what the model then predicts (assuming they've given the correct answer) can be flagged. But not every stray should be flagged/is worth flagging. For eg. A student with low 'prev_gpa' attempting a high 'diff_lvl' question and answering correctly well below the predicted response time should probably be flagged. But a student with the same independent variables answering wrongly plus taking a lot more time than the predicted response time even though strays from the norm, should not be flagged.

Now of course, like with everything 'outliers' exist, and in this particular situation (student exam data) even more so. A student can answer quickly and be correct or take longer than usual to answer and be wrong, and we couldn't really conclude anything from it but the idea is to raise 'flags' as we go through each model and look at things collectively.

**average_resp_time.ipynb** -- trivial. Classifying students on the basis of the relation of their respective response times to the class average. 

**dtree_rforest.ipynb** -- we have three numerical variables to work on this time. Grades, Exam duration (in secs) and attempt submission time (string format turned to datetime then to epoch). We scale these variables. Now, we have assigned a flagged behaviour '1' to every suspect student (which we've flagged ourselves by going through the data) and every other student the default behaviour '0' (how we've done is this shown in a notebook later on). The pairplot advocates for the classification in the fact that the 'std_scaled_submtime' is abnormally close for the flagged students (see pairplot). We now try the supervised techniques decision trees and random forests. the performance metrics aren't the best as one would imagine since exam data consisting of scores and times can't really be modelized. The idea remained the same regardless, if given enough data we create a model and if a new student strays from the expected, he/she is flagged. 

**svm.ipynb** -- we try another ml supervised algo called svm by classifying suspect students (the labels) and letting the algo create a model. The metrics are pretty bad even after tuning hyper parameters (which in theory increases performance). 

**note** -- we start to look at unsupervised techniques in the form of clustering and certain analysis techniques developed from scratch.

**time&diff and corr matrices**
