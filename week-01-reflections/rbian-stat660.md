
# Questions about Assigned Quiz Problems and Recipes


[Course Structure Quiz, Problem 1]
* Question (rbian-stat660): Are all the Week 1 Setup components required to be completed every week?
* Answer (rbian-stat660): Yes.


[Course Structure Quiz, Problem 2]
* Question (rbian-stat660): Is the requirement to complete 6 of 7 forum posts to allow people to "slack off" at the end of the academic term, or is it to accommodate students enrolling in the course late, or both?
* Answer (rbian-stat660): Both; however, students are encouraged to complete all assignments as written, even if they have no impact on their course grade.


[Course Structure Quiz, Problem 3]
* Question (rbian-stat660): Is the requirement to complete 6 of 7 weekly reflections to allow people to "slack off" at the end of the academic term, or is it to accommodate students enrolling in the course late, or both?
* Answer (rbian-stat660): Both; however, students are encouraged to complete all assignments as written, even if they have no impact on their course grade.


[Course Structure Quiz, Problem 4]
* Question (rbian-stat660): How will code reviews for projects be conducted? Will they involved comments on code in GitHub, meetings with the instructor, or both?
* Answer (rbian-stat660): Both; Code Reviews will involve 1:1 meetings with the instructor held through Google Hangouts, during which project code will discussed and commented on.


[Course Structure Quiz, Problem 5]
* Question (rbian-stat660): How similar to Weekly Reflection problems will final exam problems be? In other words, if I want to best prepare for the final exam throughout the course, should I primarily focus on thoroughly understanding weekly reflection problems?
* Answer (rbian-stat660): The best way to prepare for the Final Exam is to work through every assigned Weekly Reflection Problem and to develop an understanding of all concepts involved to the point that the problems can be thoroughly answered without consulting reference materials.


[Course Structure Quiz, Problem 6]
* Question (rbian-stat660): Is the ability to earn five total achievements at all related to the common employee rating scale of 0-5, with 5 being the highest possible level of performance?
* Answer (rbian-stat660): Yes, I think so.


[Course Structure Quiz, Problem 7]
* Question (rbian-stat660): What's the intention of encouraging resubmission of incomplete assignments? Is it to encourage students to focus on iteratively creating projects that can be added to work-sample portfolios?
* Answer (rbian-stat660): Yes. I think all assignments are intended to help students better understand what we have learnt and can create a complete project used for work-sample portfolios.


[Course Structure Quiz, Problem 8]
* Question (rbian-stat660): Why does the instructor give extra credit for catching mistakes he's made? Is it to reassure students that everyone makes mistakes, or help him proofread his course materials, or both?
* Answer (rbian-stat660): Both.


[Course Structure Quiz, Problem 9]
* Question (rbian-stat660): Instead of a carrier pigeon, what about an unladen swallow?
* Answer (rbian-stat660): An African swallow maybe, but not a European swallow.


[Course Structure Quiz, Problem 10]
* Question (rbian-stat660): What does it mean to check GitHub daily? Does this mean accessing the class GitHub organization daily to check in on the status of the repos I might be asked to contribute to?
* Answer (rbian-stat660): Yes.


[hello-world Week 1 SAS Recipe]
* Question (rbian-stat660): Is there a way of having SAS print to a different output destination than the log?
* Answer (rbian-stat660): Yes. We can use the PRINTTO procedure, route output to an XPRINTER device or to a terminal.


[fizz-buzz Week 1 SAS Recipe]
* Question (rbian-stat660): Is the mod function at all related to how clocks work, with hours counting from 1 to 12, and then starting back at 1 again?
* Answer (rbian-stat660): Yes. It works like a 12 hour clock.


***



# Recipes Exploration Results


```SAS

* Recipe: hello-world ;

* original recipe;
data _null_;
    put 'Hello, World!';
run;


* modified to print the content of a macro variable;
* note the need to switch to double-quote for the macro variable to render;
%let className = STAT 660;
data _null_;
    put "Hello, &className.!";
run;

```


```SAS

* Recipe: fizz-buzz ;

* original recipe;
data _null_;
    do i = 1 to 100;
        if mod(i,3) = 0 then put 'Fizz';
        else if mod(i, 5) = 0 then put 'Buzz';
        else put i=;
    end;
run;


* modified to use macro variables to parametrize what's printed when;
* note the need to switch to double-quote for macro variables to render;
%let mod1 = 3;
%let mod1msg = Fizz;
%let mod2 = 5;
%let mod2msg = Buzz;
data _null_;
    do i = 1 to 100;
        if mod(i,& mod1.) = 0 then put "&mod1msg.";
        else if mod(i, &mod2.) = 0 then put "&mod1msg.";
        else put i=;
    end;
run;

```
