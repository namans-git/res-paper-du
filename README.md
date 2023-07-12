# research paper, student research asst. 
https://link.springer.com/chapter/10.1007/978-981-99-1414-2_7

**res_paper_linreg.ipynb** -- using two independent variables 'diff_lvl'(difficulty level) (categorical- 1, 2 and 3 implying increasing order of difficulty) and 'prev_gpa' (previous gpa/test_score), we create a lin_reg model for predicting 'resp_time' (response time).

 

Students who stray from what the model then predicts (assuming they've given the correct answer) can be flagged. But not every stray should be flagged/is worth flagging. For eg. A student with low 'prev_gpa' attempting a high 'diff_lvl' question and answering correctly well below the predicted response time should probably be flagged. But a student with the same independent variables answering wrongly plus taking a lot more time than the predicted response time though strays from the norm, should not be flagged.

Now of course, like with everything 'outliers' exist, and in this particular situation even more so. A student can answer quickly and be correct or take longer than usual to answer and be wrong. The idea is to raise 'flags' as we go through each model and look at things collectively.
