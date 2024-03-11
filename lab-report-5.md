# Minjoo O: CSE15L Lab Report 5


## How to fix error in grade script?
**Minjoo O**\
*2 hours ago in Labs*\
Hello, during lab we were supposed to create our own grading script, and I think that I was able to get most of it right. Only, when I try to
run `grade.sh` on the corrected student sample, the terminal still outputs "Score: 0/1" instead of the expected "100%". It worked fine with the incorrect student sample.
![image](https://github.com/ominjoo/cse15l-lab-reports/assets/149638043/19033ac8-b82d-4427-85bf-d03b6c93b1d9)\
It's also saying that `grading-area` and `student-submission` already exist, even though it didn't say that the first time, so maybe that has something to do with this issue?
Or, maybe the bug is in calculating the score itself. Maybe, student submissions with no errors create an incorrect output for
this grading script because the code cannot calculate to "100%" effectively. I'm not sure.

---

**Taycher Asystin `staff`**\
Hi! If you want to narrow down which inputs cause failures, try testing out more sample student submissions! The unexpected
output may not be related to whether or not the the student submission has errors.\
As for the error messages regarding `grading-area` and `student-submission`:
Try to think of what happens when the grade server clones the contents of the student's repository into `student-submission`.
More importantly, think of what *remains* in `student-helper` from the last repositiory you graded each time you run grade.sh with a new repository. 
When you make a new `grading-area` directory for one student submission, what will happen if try to make the same directory *again* for another student submission?

---
**Minjoo O**
![image](https://github.com/ominjoo/cse15l-lab-reports/assets/149638043/5bd91a1c-162f-4f57-9cd3-f0f434233965) \
Ok, after trying out the other sample submissions, I figured out that whether the submission had a compile error, jUnit test fail,
wrong files, etc. they ALL gave the output of "Score: 0/1". Each time after the first submission, the terminal output that `grading-area`
and `student-submission` already exist. I'm thinking that the grading script is reading from the contents within those directories
created from the *first* student submission I tested. That's why it keeps outputting "Score: 0/1", because that's the result of running
tests on the first submission. I think that the bug may be that I lack the code that allows for a new `grading-script` and `student-submission` 
each time I run the script. I could probably do this by adding `rm -rf student submission` and `rm -rf grading-area` to the top of the script file,
so that the existing directories are deleted and remade.

---







  
