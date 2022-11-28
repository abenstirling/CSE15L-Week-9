# Week 9 Lab Report: Autograder

---

# Student: ***[Ben Stirling](https://github.com/abenstirling)***
# Professor: ***[Joe Politz](https://github.com/jpolitz)***
# Date: ***9/29/22***

---

In this lab, we will be demonstrating an autograding script that mimics some of the neat features of educational platforms like Gradescope 

---

Below, I attached my grade.sh file. 

```bash
# Author @abenstirling
set -e
GRADE=0
git clone student-submission
if [ -f ListExamples.java]
then 
	echo "Nice work, file is located!"
else 
	echo "Please make sure your file is in the repo!"
	echo "Temporary grade is 0%"
	exit 1
fi 
javac -cp .:../lib/hamcrest-core-1.3.jar:../lib/junit-4.13.2.jar *.java 2> outError.txt
java -cp .:../lib/hamcrest-core-1.3.jar:../lib/junit-4.13.2.jar org.junit.runner.JUnitCore TestListExamples > testResult.txt
if [$? -eq 0]
then 
	echo "Nice work! Your repo compiled!"
	echo "Here are your junit results (100%!)"
	cat testResult.txt
elif [$? -eq 2]
then 
	echo "Nice work! Your repo compiled!"
	echo "Nice work! Your junit results (50%)"
	cat testResult.txt
else
	echo "Unfortunately, your compiling failed. Please try again!"
	echo "Temporary grade is 0%"
	cat outError.txt
fi 

```

### Testing On Submissions

---

Below we can see that the file from [github.com/ucsd-cse15L-f22/list-methods-compile-error](http://github.com/ucsd-cse15L-f22/list-methods-compile-error) fails a few tests when it compiles, resulting in a score of 0%. Not fantastic unfortunately. 

![list-methods-compile-error](list-methods.png)

Below we can see that the file from  [github.com/ucsd-cse15L-f22/list-methods-](http://github.com/ucsd-cse15L-f22/list-methods-compile-error)lab3 fails a test, resulting in a score of 50%. Better prospects!

![list-methods-lab3](list-methods-l3.png)

Below we can see that the file from  [github.com/ucsd-cse15L-f22/list-methods-](http://github.com/ucsd-cse15L-f22/list-methods-compile-error)corrected and it passes all the tests, resulting in a perfect score of 100%! Awesome work!

![list-methods-corrected](list-methods-right.png)

### Tracing Script

---

Tracing is where you follow the value of a specific variable as the loop and program is being executed. It is specifically useful for debugging, or in our case to see how the program is firing line by line. 

Commented is where the tracing is noted: 

```bash
# Author @abenstirling
set -e
GRADE=0
git clone student-submission
#Above we have no stdout or stderr

if [ -f ListExamples.java]
#Above nothing here, just continue if exists
then 
	echo "Nice work, file is located!"
else 
	echo "Please make sure your file is in the repo!"
	echo "Temporary grade is 0%"
	exit 1
	#stderr above 
fi 
javac -cp .:../lib/hamcrest-core-1.3.jar:../lib/junit-4.13.2.jar *.java 2> outError.txt
java -cp .:../lib/hamcrest-core-1.3.jar:../lib/junit-4.13.2.jar org.junit.runner.JUnitCore TestListExamples > testResult.txt
#stdout exists for both above, which are redirected into outError and testResults respectively. 
if [$? -eq 0]
#Testing exit code
then 
	echo "Nice work! Your repo compiled!"
	echo "Here are your junit results (100%!)"
	cat testResult.txt
#Above no standard err or output
elif [$? -eq 2]
#Testing exit code
then 
	echo "Nice work! Your repo compiled!"
	echo "Nice work! Your junit results (50%)"
	cat testResult.txt
#Above no standard err or output
else
	echo "Unfortunately, your compiling failed. Please try again!"
	echo "Temporary grade is 0%"
	cat outError.txt
#Above no standard err or output
fi 

```

### Conclusion

---

This was a wonderful class for several reasons: 

- We learned modern and valueable techniques that will give us a foundation for being efficient and effective while we develop in the future.
- We learned how to interact with other developers (fellow students) and develop software that addresses a need (our assignment).
- We learned time management as we had to balance the coursework of several classes.

A massive thank you to Professor Politz and all of the tutors and TAs of this class for the amazing semester!

<3 Ben Stirling