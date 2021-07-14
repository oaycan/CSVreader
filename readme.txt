
----------------------------------------
ReadMe File - Assignment1:Data Ingestion 
----------------------------------------

** Purpose of the Document **
-----------------------------
This readme file is prepared to explain the general structure and the functions of my python program that can parse CSV files.

** General Instructions **
--------------------------
I have prepared a single Jupyter file which includes codes for both Part1 and Part2 of the assignment. 

** General Explanation on the Algorithm **
--------------------------------------------------------------------
First, I have used lists to read lines of CSV files and then created a 2-d array to store the values and the header if available.

** General Structure of the Code ** 
-----------------------------------
  * Part-1 *
  ----------
  My custom CSV parser has one main function and two inner functions as below.

  Main Function: ** read_csv
      Main function is the one which we call when a file is intended to be read and parsed. We return two arrays which include our 
      data and header information respectively.
      This function can have 5 arguments as shown below:

      read_csv(filename, encoding="UTF-8-sig", header=0, read_only=False, time_column=None)

	* Function Argument Explanations:
		- filename: It takes the CSV file name with its full path
		- encoding: Filename encoding can be passed as an argument, default is "UTF-8-sig".
		- header: If the CSV file has a header, it can be identified by the parser by passing the row number of header,
		 	  default value is 0, and if no header in the file then None can be passed.
	        - read_only: It is passed with True for parser to only read but not parse(print) the file, default value is False
	        - time_column: It is used to indicate the time column when we want our parser to convert time data to datetime object format
	          ("0000-00-00 00:00:00"), and if the time data is not in a suitable form then it returns "invalid time". Default value is None

	Inner functions are as follows.

	* Inner Function-1: ** date_parser:
	This function is optional and can be opt when calling the main function with time_column argument as described in main function 
	section above. It basically checks if the date 	data is in a valid time format and if so it returns the data with its suitable 
	datetime object ("0000-00-00 00:00:00"), if not then it returns with "Invalid time"

	* Inner Function-2: ** split_lines:
	This function splits the lines in the file using the delimiter "," and creates a 2-d array with the data and optionally second 
	2-d array only with header information and returns both of them.

  * Part-2 *
  ----------
  In order to calculate the statistics on each CSV file, I wrote a function called "stats". This function reads each file without 
  Returning the outputs and uses numpy to calculate mean, max, min and std_dev and output them in a clear tabular format.

  I modified the file “indoor-temperature-1617.csv” by introducing an outlier on its “Temperature” field and saved it with a new name 
  as "indoor-temperature-1617-modified.csv". I replaced one value which was originally “23.93” with “2100.93” that we normally should
  not read as a value for indoor temperature from a sensor so basically the new value became an outlier.

  Afterwards, I called stats function again and calculated the new summary statistics on the modified CSV file.