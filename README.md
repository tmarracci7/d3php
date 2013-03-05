d3php
=====

Interface for PHP to D3 database

Use native php to access your D3 data. Uses a *nix bridge called d3pipe that is included in the project.

In a nutshell, d3pipe is a multithreaded, multiprocess daemon running on the *nix box where your D3 7+ server resides.
d3pipe has been compiled and is currently working on D3/AIX 7.4 and 9.0 and D3/Linux 7.4.  Other implementations
will need to be tested. 

The php module was developed on PHP/5.3.2 but should be tested on other versions for completeness.

Use the module like you would mysql or any of the other database extensions available for PHP. That is, 
connect, login, execute your queries, and close.

Functions currently included are:

d3_connect - connect to a server on a specific part running d3pipe
d3_login - login to the aforementioned connection and connect to a D3 database
d3_close - close a connection
d3_status - report back the connection and login status
d3_open - open a D3 file
d3_open_dict - open a D3 dictionary
d3_matparse - create a php array out of a D3 array
d3_matbuild - build a D3 string out of a php array
d3_read - read a D3 record
d3_readu - read a D3 record and lock it. because web is stateful, locks will not survive between pages
d3_write - write a D3 record
d3_matread - read a D3 record into a php array
d3_matwrite - write a php array to a D3 record
d3_delete - delete a D3 record
d3_readv - read an attribute from a D3 file
d3_writev - write to an attribute in a D3 file
d3_select - select a D3 file
d3_eof - determine if the aforementioned select is at the end
d3_readnext - get the next id from a D3 select list
d3_dcount - count delimiters. if parameter is an array, return the number of entries
d3_date - capture the current julian date - uses the php server, not the pick server to get this
d3_time - capture the current time in seconds since midnight - again not from the D3 server but from php server
d3_oconv - perform output conversion. many conversions are done by the extension and not by the server
d3_iconv - perform input conversion. optimized to reduce traffic to the D3 server
d3_match - perform a pattern match
d3_print - print text presumably to a print job
d3_printer - turn D3 printer on and off
d3_execute - execute a D3 TCL command. capture output to a variable
d3_system - perform a special D3 system function - see D3 documentation for parameters
d3_call - perform a Flash/Basic D3 call. Can send up to 16 parameters all passed by reference
d3_query - perform a simple SQL-like command. only SELECT is supported and uses dictionary words and files found in D3
           no joins are supported - used D3 dictionary words judiciously to perform complex selects
d3_num_rows - number of rows return by a query
d3_num_fields - number of fields return by a query
d3_fetch_row - fetch the next row as a PHP array from a query
d3_locate - locate text in a PHP array. if the array is sorted, uses binary search for quick locations
d3_sort - sort a PHP array with quicksort
d3_heapsort - sort a PHP array with heapsort
d3_del - delete a cell from a PHP array and adjust the cells
d3_ins - insert data before a cell in a PHP array

PHP arrays can only be numbered (no associative arrays are supported) and are 1-based, like D3 arrays. They can be
3 dimensional and maintain syncronicity with D3 arrays (ie simulates AM, VM, and SVM constructs).  The routines that
operate on arrays all assume this constraint.
