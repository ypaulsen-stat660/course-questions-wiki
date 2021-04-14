
# Questions about Assigned Quiz Problems and Recipes


[Textbook Chapter 12, Problem 3]
* Question (slin51-stat660): Is there a maximum character length to a new format's name?
* Answer (slin51-stat660): Yes, 32,767 characters


[Textbook Chapter 12, Problem 4]
* Question (slin51-stat660):  Why are commas not needed to separate each label?


[Textbook Chapter 12, Problem 5]
* Question (slin51-stat660): Why is the maximum numeric value 1500?


[Textbook Chapter 12, Problem 6]
* Question (slin51-stat660):  How was the number 32,767 decided?


[Textbook Chapter 12, Problem 7]
* Question (slin51-stat660): Why was the keyword OTHER picked instead of MISSING? MISSING is more intuitive.


[Textbook Chapter 15, Problem 4]
* Question (slin51-stat660): What is the purpose of BY if CLASS offers more flexibility and does the same thing?


[Textbook Chapter 15, Problem 5]
* Question (slin51-stat660):  Is there a limit to the number of variables the CLASS produced table will display?


[Textbook Chapter 15, Problem 6]
* Question (slin51-stat660): Where are the labels for AvgAge, AvgHeight, and AvgWeight?


[Textbook Chapter 15, Problem 9]
* Question (slin51-stat660):  Where is htfmt. and wtfmt. defined?


[Textbook Chapter 15, Problem 10]
* Question (slin51-stat660): Why is the specification of table information to exclude separate by a /?


***



# Recipes Exploration Results



```
* Recipe: printing-a-dataset ;

proc print data=sashelp.iris(obs=20);
    id SepalLength SepalWidth; 
    var Species;
run;


```

* Question (slin51-stat660): Can you also specify in the options that obs=20?


```

* Recipe: sorting-a-dataset ;

proc sort
    	data=sashelp.iris
	out=Work.iris_sorted
    ;
    by
        descending SepalLength
	SepalWidth
    ;    
run;

```

* Question (slin51-stat660): Why is there a Work. in front of the iris_sorted?



```
* Recipe: checking-for-duplicates ;

proc sort
    	nodupkey
    	data=sashelp.iris
	out=_null_
    ;
    by
        SepalLength
	SepalWidth
    ;    
run;


```

* Question (slin51-stat660): What does the output _null_ mean?


