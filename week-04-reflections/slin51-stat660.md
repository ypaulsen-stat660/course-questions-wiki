
# Questions about Assigned Quiz Problems and Recipes


[Textbook Chapter 5, Problem 2]
* Question (slin51-stat660): Does the label double noobs replace the column maxrates?
* Answer (slin51-stat660): no, noobs stands for no observations and removes the obs column

[Textbook Chapter 5, Problem 6]
* Question (slin51-stat660):  Is sort by default in ascending or descending order?


[Textbook Chapter 6, Problem 1]
* Question (slin51-stat660): Why is noobs and label specified after the proc print statement instead of on a separate line?


[Textbook Chapter 6, Problem 3]
* Question (slin51-stat660):  Is in evaluating the vector of values as logicals?


[Textbook Chapter 6, Problem 4]
* Question (slin51-stat660): When referring to a data set, do we always need to use DATA=?
* Answer (slin51-stat660): yes, it specifies the data to be read


[Textbook Chapter 6, Problem 6]
* Question (slin51-stat660): Is it necessary to specify OUT=?
* Answer (slin51-stat660): no, if out= is not specified, PROC SORT overwrites the data set that is specified in DATA=


[Textbook Chapter 6, Problem 7]
* Question (slin51-stat660): Is there a way to call the sum function to all the selected variables?


[Textbook Chapter 6, Problem 8]
* Question (slin51-stat660):  Is eq an appropriate substitute for =?
* Answer (slin51-stat660): yes


[Textbook Chapter 7, Problem 7]
* Question (slin51-stat660): Can new columns be added to the beginning of the data set instead of the end?


[Textbook Chapter 7, Problem 9]
* Question (slin51-stat660):  What does the length function do?


[Textbook Chapter 9, Problem 11]
* Question (slin51-stat660): Are observations initially set to missing and then with each iteration, the observations are filled in?


***



# Recipes Exploration Results



```
* Recipe: basic-load-remote-excel-file ;

filename tempfile TEMP;
proc http
    method="get" 
    url="https://tinyurl.com/stat660-sat15" 
    out=tempfile
    ;
run;
proc import
        file=tempfile
        out=sat15_raw
        dbms=xls; 
run;
filename tempfile clear;

```

* Question (slin51-stat660): Why is the semicolon on a separate line on its own?


```

* Recipe: advanced-load-remote-excel-file ;

%macro loadDataIfNotAlreadyAvailable(dsn,url,fileType);
	%put &=dsn;
	%put &=url;
	%put &=filetype;
	%if
		%sysfunc(exist(&dsn.)) = 0
	%then
		%do;
			%put Loading dataset &dsn. over the wire now...;
			filename tempfile TEMP;
			proc http
				method="get"
				url="&url."
				out=tempfile
				;
			run;
			proc import
				file=tempfile
				out=&dsn.
				dbms=&filetype.;
			run;
			filename tempfile clear;
		%end;
	%else
		%do;
			%put Dataset &dsn. already exists. Please delete and try again.;
		%end;
%mend;
%loadDataIfNotAlreadyAvailable(
	sat15_raw,
	https://tinyurl.com/stat660-sat15,
	xls
)

```
* Question (slin51-stat660): What does %mend do?

