CSE15L - Week 3 Lab Report
Name: Xiaoxiang(Anna) Ma
Date: 11/27/2022

**Part 1**: grade.sh code

(To complete the lab report, I used a random file because the code of the student I was originally assigned to was barely edited.)

```
set -e

rm -rf student-submission

git clone $1 student-submission &>/dev/null

cd student-submission

if [ ! -e ListExamples.java ]
then
    echo "ListExamples.java is not found!"
    exit 0
fi

cd ..
cp TestListExamples.java student-submission/TestListExamples.java
cd student-submission

set +e

javac -cp .:../lib/hamcrest-core-1.3.jar:../lib/junit-4.13.2.jar *.java 2> error.txt

if [ ! $? -eq 0 ]
then
    echo "Compile Error!"
    exit 1
fi

java -cp .:../lib/hamcrest-core-1.3.jar:../lib/Junit-4.13.2.jar org.junit.runner.JUnitCore TestListExamples > TestResults.txt
 
if grep "OK" TestResults.txt &>/dev/null
    then
        echo "All Tests Passed"
    else
        grep "Tests run" TestResults.txt
        echo "Failed : "
        grep ") " TestResults.txt
fi
```

**Part 2**: screenshots of three different student submissions and their reported grade as loaded in the browser

1. URL: https://github.com/ucsd-cse15l-f22/list-methods-filename

![Image](2022-11-28%2004.18.57.png)

2. URL: https://github.com/ucsd-cse15l-f22/list-methods-compile-error

![Image](2022-11-28%2004.18.53.png)


3. URL: https://github.com/ucsd-cse15l-f22/list-methods-lab3

![Image](2022-11-28%2004.18.48.png)


**Part 3**: trace the code (example 1) - some meaningless lines(or code) are gonna be skipped。

```
set -e
```
This command is used to set or unset shell variables. No stdout and stderr, exit code is 0.

```
rm -rf student-submission
```
It is used to remove the previous directory. No stdout and stderr, exit code is 0.

```
git clone $1 student-submission &>/dev/null
```
It is used to clone the student-submission. No stdout and stderr, exit code is 0.

```
cd student-submission
```
It is used to change the current directory to student-submission. No stdout and stderr, exit code is 0.

```
if [ ! -e ListExamples.java ]
then
    echo "ListExamples.java is not found!"
    exit 0
fi
```
If ListExamples.java can be found in student-submission folder, then the remainder of the code in that section is not run and the exit code is 0. If it is not found, then `echo "ListExamples.java is not found!"` will be run. `fi` means the end of the `if` loop. No stdout and stderr, exit code is 0.

```
cd ..
cp TestListExamples.java student-submission/TestListExamples.java
cd student-submission
```
This part is used to copy the test into the student-submission directory. For these three commands, they all have no stdout and stderr and their exit code are 0.

```
set +e
```
This command is used to turn off `set -e`. No stdout and stderr, exit code is 0.

```
javac -cp .:../lib/hamcrest-core-1.3.jar:../lib/junit-4.13.2.jar *.java 2> error.txt
```
It is used to compile the file. No stdout and stderr, exit code is 0.

```
if [ ! $? -eq 0 ]
then
    echo "Compile Error!"
    exit 1
fi
```
If the compilation exit with exit code other than 0, then there's a compilation error. The if condition `[ ! $? -eq 0 ]` is evaluated to be false in this case, since exit code of the previous command is 0. Therefore, For the commands from `then` to `fi`, they all have no stdout and stderr and their exit code are 0.

```
java -cp .:../lib/hamcrest-core-1.3.jar:../lib/Junit-4.13.2.jar org.junit.runner.JUnitCore TestListExamples > TestResults.txt
```
This command is used to run the program. No stdout and stderr. Since there is one test failed (see from example 3), so the exit code is not 0 but 1.

```
if grep "OK" TestResults.txt &>/dev/null
    then
        echo "All Tests Passed"
    else
        grep "Tests run" TestResults.txt
        echo "Failed : "
        grep ") " TestResults.txt
fi
```
If all test passed, then test results contains "OK". Since there is one test failed, this if condition is false. No stdout and stderr. Therefore, the if statement goes into the else statement block in the fifth line. The commands `then` and `echo "All Tests Passed"` are not executed.

In the `else` block, the stdout of command `grep "Tests run" TestResults.txt` is the line contains "Test run" in TestResults.txt but no stderr, exit code is 0; command `echo "Failed : "` has the stdout "Failed : " but no stderr, exit code is 0; the stdout of command `grep ") " TestResults.txt` is the line contains ") " in TestResults.txt but no stderr, exit code is 0.
