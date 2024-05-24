# redis_7.2.5-for-WIndows

A compiled version of Redis 7.2.5 that can run on Windows is available.

I have compiled the Redis 7.2.5 version for Windows using the source code downloaded from the official website.Because the compilation process can be prone to various bugs and cumbersome, I have decided to upload it to GitHub to facilitate everyone's download of the precompiled Redis version that can be executed directly on Windows.

Here's a brief description of potential bugs you may encounter during the process you described (compiling Redis on Windows) that may not have readily available solutions online:  
&nbsp;&nbsp;&nbsp;&nbsp;1.Missing files in the "deps" folder after running "make && make install":  
&nbsp;&nbsp;&nbsp;&nbsp;Solution: Enter the "deps" folder in Cygwin and execute commands like "make lua hiredis fpconv hdr_histogram" (or more, depending on the error message) to build the necessary dependencies. Once completed, return to the "src" directory and run "make && make install" again.  
&nbsp;&nbsp;&nbsp;&nbsp;2.Error in "sds.c" file related to "array subscript has type 'char'":  
&nbsp;&nbsp;&nbsp;&nbsp;Error message: "error: array subscript has type ‘char’ [-Werror=char-subscripts]"  
&nbsp;&nbsp;&nbsp;&nbsp;Solution: Locate the "sds.c" file and modify the line "if (isprint(*p))" to "if (isprint((int)*p))". This change ensures proper handling of the character type, resolving the error. After making the modification, proceed with compiling and you should see a successful outcome with the appearance of the executable files.  