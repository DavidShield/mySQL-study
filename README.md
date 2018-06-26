# mySQL-study

## Normalization of Database (mySQL 三大范式）

###  1NF normalization rule: atomic columns (列不可分)
    One column can only contains single value which means there cannot be multiple values.

    All the column should have unique name.
    

###  2NF normalization rule: no partial dependency (列不可分)
For example:

    grade_id	student_id	project_id	grade	    class
    1	        10	        1	        70	    Intro to AI
    2	        10	        2	        75	    Machine Learning
    3	        11	        1	        80	    Intro to AI
    
Here we got a table and we combine the student_id and project_id to be the primary key.

However, we can see that the class only depends on project_id, which means project 1 is from Intro to AI and project 2 is from Machine Learing.
The class name do nothing with student_id. This is partial dependency. 

How to remove partial dependency?

One simplest way is to remove class from the table and create a new table to store this info.

    project_id  class
    1           Intro to AI
    2           Machine Learning
    
### 3NF normalization rule: no transitive dependency
For example:

    score_id	student_id	subject_id	marks	exam_name	total_marks

Well, the column total_marks depends on exam_name as with exam type the total score changes. For example, practicals are of less marks while theory exams are of more marks.

But, exam_name is just another column in the score table. It is not a primary key or even a part of the primary key, and total_marks depends on it.

This is Transitive Dependency. When a non-prime attribute depends on other non-prime attributes rather than depending upon the prime attributes or primary key.

Refer from :https://www.studytonight.com/dbms/database-normalization.php 
