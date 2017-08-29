## Seed code - Boilerplate for step 7 - Database Engine Assignment

### Problem Statement

In this assignment step 7, we will try to filter the data from CSV file with much more complex queries using lambda expression. Our query is expected to contain `aggregate functions, group by, order by, aggregate group by`.

For example:
 - select city,winner,team1,team2 from ipl.csv where city='Bangalore' order by winner
 - select winner, count(*) from ipl.csv group by winner;
 - select city, sum(win_by_runs) from ipl.csv group by city
 - select count(city), sum(win_by_runs), min(season), max(win_by_wickets) from ipl.csv
 - Finally store the filtered data in JSON file.

`Note : Once you have cloned boilerplate from the given gitlab URL, import the project into eclipse and try to run your test cases. 
Your project's test cases will show compile time error for methods, as you have not written the complete code.`

### Expected solution

A JSON file containing the filtered result set.

### Following are the broad tasks:

- Read the query from the user
- parse the query
- forward the object of query parameter to CsvQueryProcessor
- filter out rows basis on the conditions mentioned in the where clause
- write the result set into a JSON file

### Project structure

The folders and files you see in this repositories, is how it is expected to be in projects, which are submitted for automated evaluation by Hobbes

	Project
	|
	├── resources 			                    // If project needs any data file, it can be found here/placed here, if data is huge they can be mounted, no need put it in your repository
	|
	├── com.stackroute.datamunger	            // all your java file will be stored in this package
	|	└── query
	|		└──parser
	|			└── AggregateFunction.java             // This class is used to store Aggregate Function
	|			└── QueryParameter.java                // This class contains the parameters and accessor/mutator methods of QueryParameter
	|			└── QueryParser.java                    // This class will parse the queryString and return an object of QueryParameter class
	|			└── Restriction.java	                // This class is for storing Restriction object
	|		└── DataSet.java 		                    // This class will be acting as the DataSet containing multiple rows
	|		└── DataTypeDefinitions.java                // This class contains methods to find the column data types
	|		└── Filter.java 		                    // This class contains methods to evaluate expressions
	|       └── GenericComparator.java                  // this class contains the implementation of the custom comparator which can work for all data types
	|		└── Header.java                             // This class implements the getHeader method to return a Header object which contains a String array for containing headers.
	|		└── Query.java                              // This class selects the appropriate processor based on the type of query
	|		└── Row.java                                //This class contains the row object as ColumnName/Value 
	|		└── RowDataTypeDefinitions.java             // This class will be used to store the column data types as columnIndex/DataType
	|	└── reader
	|		└── CsvAggregateQueryProcessor.java         // this is the CsvAggregateQueryProcessor class used for evaluating queries with aggregate functions without group by clause
	|		└── CsvGroupByQueryProcessor.java  // this is the CsvGroupByAggregateQueryProcessor class used for evaluating queries with aggregate functions and group by clause
	|		└── CsvOrderByQueryProcessor.java           // this is the CsvGroupByQueryProcessor class used for evaluating queries without aggregate functions but with group by clause
	|		└── CsvQueryProcessor.java                  // This class is used to read data from CSV file
	|		└── CsvWhereQueryProcessor.java             // This class will read from CSV file and process and return the resultSet based on Where clause 
	                                                        //Filter is user defined utility class where we defined the methods related to filter fields, filter records.
	|		└── QueryProcessingEngine.java              //abstract class containing three abstract methods that should be implemented in CsvQueryProcessor class
	|	└── test                                        // all your test cases are written using JUnit, these test cases can be run by selecting Run As -> JUnit Test 
	|	└── writer
	|		└── JsonWriter.java                         // This class writes the result in a JSON file
	|	└── DataMunger.java	                            // This is the main file, all your logic is written in this file only
	|
	├── .classpath			                            // This file is generated automatically while creating the project in eclipse
	├── .hobbes   			                    // Hobbes specific config options, such as type of evaluation schema, type of tech stack etc., Have saved a default values for convenience
	├── .project			                    // This is automatically generated by eclipse, if this file is removed your eclipse will not recognize this as your eclipse project. 
	├── pom.xml 			                    // This is a default file generated by maven, if this file is removed your project will not get recognised in hobbes.
	└── PROBLEM.md  		                    // This files describes the problem of the assignment/project, you can provide as much as information and clarification you want about the project in this file

> PS: All lint rule files are by default copied during the evaluation process, however if need to be customizing, you should copy from this repo and modify in your project repo


#### To use this as a boilerplate for your new project, you can follow these steps

1. Clone the base boilerplate in your local

	`git clone  https://gitlab-dev.stackroute.in/datamunger-java/step-7-Boilerplate.git`

2. Remove its remote or original reference

	`git remote rm origin`

3. Add your new repository reference as remote

	`git remote add origin ssh://git@gitlab-dev.stackroute.in:2222/yourusername/your-new-project-repo.git`

4. Commit and Push the project to git

	`git commit -a -m "Initial commit | or place your comments according to your need"`

	`git push -u origin master`

5. Check on the git repo online, if the files have been pushed


### Important instructions for Participants
> - We expect you to write the assignment on your own by following through the guidelines, learning plan, and the practice exercises
> - The code must not be plagirized, the mentors will randomly pick the submissions and may ask you to explain the solution
> - The code must be properly indented, code structure maintained as per the boilerplate and properly commented
> - Follow through the problem statement and stories shared with you

### Further Instructions on Release

*** Release 0.1.0 ***

- Right click on the Assignment select Run As -> Java Application to run your Assignment.
- Right click on the Assignment select Run As -> JUnit Test to run your Assignment.