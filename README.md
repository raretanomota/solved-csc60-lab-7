Download Link: https://assignmentchef.com/product/solved-csc60-lab-7
<br>
<strong><u>Problem.</u></strong>  Write a program that uses structures and pointers.  You will have to write two functions:  <strong>get_stats</strong>, and <strong>get_median</strong>.




<ul>

 <li>First in lab7.c, you need to declare a structure type <strong>driver_t</strong>.

  <ul>

   <li>named my structure <strong>driver_t</strong> and its 4 parts are:          a character array <strong>name</strong> that is 21 in length, (comes from the data file)            a double array of <strong>tries</strong> that has a length of TRIES, (comes from the data file)</li>

  </ul></li>

</ul>

a double named <strong>best_time</strong>,  (value computed by program)              a double named <strong>deviation</strong>, (value computed by program).




<table width="371">

 <tbody>

  <tr>

   <td width="57">Name</td>

   <td width="52"><strong>Try 0 </strong></td>

   <td width="51"><strong>Try 1 </strong></td>

   <td width="52"><strong>Try 2 </strong></td>

   <td width="81">Best Time</td>

   <td width="79">Deviation</td>

  </tr>

 </tbody>

</table>




Array




<ul>

 <li>Next in lab7.c, you need to declare a structure type: <strong>stats_t</strong>.

  <ul>

   <li>named my structure <strong>stats_t</strong> and its 4 parts are:</li>

  </ul></li>

</ul>

four variables, all type double, named <strong>best_average</strong>, <strong>fast_time</strong>, <strong>slow_time</strong>, and <strong>median</strong>.




<ul>

 <li>Write the function <strong>get_stats</strong>. This function will figure the driver’s best time, the track slow time and fast time, the average of the driver’s best times, and the driver’s deviation from the fast time. The prototype is:</li>

</ul>




void get_stats(driver_t driver_list[NRACERS],       /* in &amp; out */

stats_t *race_stats );                        /* in &amp; out */




<ul>

 <li>Write the function <strong>get_median</strong>. It will find the mid best time from the sorted list of best times. Examples of computing median are on the top of page 4. The prototype for <strong>get_median</strong> is:</li>

</ul>




void get_median(driver_t driver_list[NRACERS],  stats_t *race_stats );




<ul>

 <li>You will be provided a test driver program that needs ALMOST NO changing, only ADDing. You will only need to <strong>add</strong> the two structures and the two functions as above.</li>

</ul>

You will need to shift the comment marks ( // ) on the four #define statements: two for the          data file, two for the NRACERS







<strong><u>Input/Output Description</u></strong>:

The program <u>input</u> is a set of driver’s names and their three tries on the race track in one file.  The race times are type double.  Each record/line of the file has a student name and three times.




The first line from the sample data file is:

Jay Johnson               4.100       5.300       6.700




The <u>output</u> is printed to <strong>lab7.out</strong> as shown in the sample output.

<strong> </strong>

<strong> </strong>

<strong><u>Algorithm Development – Pseudo code</u></strong>:

/*————————————————————-*/

main

/* <strong>This function already exists.</strong> */    out_file = open_out_file ();                      get_data(IN_FILENAME, driver_list);                 get_stats(driver_list, &amp;race_stats);                do_sort(driver_list);                               get_median(driver_list, &amp;race_stats);               print_all(out_file, driver_list, &amp;race_stats);




/*————————————————————-*/

FILE * open_out_file(void)

/* <strong>This function already exists.</strong> */

/* Opens the output file */




/*————————————————————-*/ void get_data (char *filename,                   /* input  */                             driver_t driver_list[NRACERS] );  /* output */




/* <strong>This function already exists</strong>. */

/*It opens the data file and reads it into the appropriate places. */




/*————————————————————-*/

void print_all(FILE * out_file,

driver_t driver_list[NRACERS] ,

stats_t *race_stats )




<strong>/* This function already exists. */ </strong>




/*————————————————————-*/ void do_sort(student_t student_list[NSTUDENTS])




/* <strong>This function already exists.</strong> */




/*————————————————————-*/










è more on next page




/*————————————————————-*/

/*     <strong>THIS IS A SUB-FUNCTION THAT YOU HAVE TO WRITE</strong>  */ void get_stats( driver_t driver_list[NRACERS],     /* in &amp; out */

stats_t *race_stats )                      /* in &amp; out */




Zero out the best_average  (HINT: use the -&gt; notation)    Set the slow_time to the first driver’s first try.    Set the fast_time to the first driver’s first try.




loop from d=zero to &lt; NRACERS increment by one

{

zero out the driver_list[d].deviation               set the driver’s best time to the driver’s first time                  loop from t=zero to t&lt; TRIES increment by one

{

figure the driver’s best time

find the fastest and slowest track time

}

add the driver’s best time into the running total of best times

}

compute the average of the best times




loop from d=zero to &lt; NRACERS increment by one

{

figure the driver’s deviation from the <strong>fast_time</strong>(the fastest all-over time)

(deviation is fast time minus driver’s best time)

}

return




/*————————————————————-*/

/*  <strong>THIS IS A SUB-FUNCTION THAT YOU HAVE TO WRITE</strong> */ void get_median(driver_t driver_list[NRACERS],

stats_t *race_stats )




zero out the median.      calculate the mid point (divide NRACERS by two)      if the number of racers is odd then

set the median to the mid average      else

set the median to the average of the two numbers(averages) on                       each side of the median. [mid] &amp; [mid-1]. NO integer division.




/*————————————————————-*/




è <strong>Examples of Median on next page. </strong>

<strong><u>NOTES on the median</u></strong>:

The median is the value in the middle of a group of values, assuming that the values are sorted.  If there is an odd number of values, the median is the value in the middle.  If there is an even number of values, the median is the average of the values in the two middle positions.

EXAMPLES:

<ul>

 <li>The median of values {1, 6, <strong>18</strong>, 39, 86} is the middle value, or 18.</li>

 <li>The median of values {1, 6, <strong>18, 39</strong>, 86, 91} is the average of the two middle values, or (18 + 39)/2 or 28.5.</li>

</ul>




<strong><u>Sample Data</u></strong>:

This is the sample data example.  It does not match the lab7.dat file in length <strong>or</strong> in value!




<u>SAMPLE DATA</u>:

Jay Johnson               4.100       5.300       6.700         Missy Monroe              1.000       2.000       3.500

Ned Niner                 3.800       7.000       5.500

Lenny Loop                2.200       3.400       4.600

<strong> <u>Sample Output</u></strong><strong>: </strong>




Your Name.  Lab 7 output.




Track Results




Drivers                  Try 1       Try 2       Try 3      Best Time   Deviation

——————–   ———   ———   ———   ———-   ———

Missy Monroe              1.000       2.000       3.500        1.000       0.000

Lenny Loop                2.200       3.400       4.600        2.200      -1.200

Ned Niner                 3.800       7.000       5.500        3.800      -2.800 Jay Johnson               4.100       5.300       6.700        4.100      -3.100







The average of best times =    2.775




The track fast time       =    1.000




The track slow time       =    7.000




The median of best times  =    3.000







<strong><u>Using the Sample Data:</u> </strong>

To use the sample date, you need to make changes:

These lines are currently set to access the sample file.<em>  Move the comment symbols (//) from one line to another to shift the use of files.  </em>

<strong>//#define IN_FILENAME “lab7.dat” </strong>

<strong>#define IN_FILENAME “lab7sample.dat” </strong>




The final data file has a length of 10, the sample file has a length of 4. <em>Move the comment symbols (//) from one line to another to shift the use of files.   </em>

<strong>//#define NRACERS 10            </strong>

<strong>#define NRACERS 4 </strong>

<strong> </strong>

à<strong> more on next page  </strong>

<strong><u>Files To Copy</u></strong>:

Type:  <strong>cp  -R  /gaia/home/faculty/bielr/files_csc60/lab7  . </strong>

Spaces needed:  (1) After the <strong>cp                                                      <em>↑</em></strong><em> Don’t miss the space &amp; dot.</em>

<ul>

 <li>After the <strong>-R</strong></li>

 <li>After the directory name at the end &amp; before the dot.</li>

</ul>




After the files are in your account and you are still in <strong>csc60</strong>,

you need to type: <strong>chmod 755 lab7 </strong>

This will give permissions to the directory.

Next move into lab7 directory by typing:  <strong>cd lab7 </strong>

After the files are in your account, you need to type: <strong>chmod  644  lab7* </strong>This will give permissions to the files.

Your new lab7 directory should now contain:  lab7.c, lab7.dat, lab7sample.dat




<strong><u>PREPARE YOUR FILE FOR GRADING:</u> </strong>Make sure your program has been:

<ul>

 <li>corrected to use <strong>dat</strong></li>

 <li>corrected to use the proper value for <strong>NRACERS</strong>  has been re-complied.</li>

</ul>




When all is well and correct,

Type:  <strong>script StudentName_lab7.txt  </strong>[Script will keep a log of your session.]

Type:  <strong>a.out</strong> or <strong>lab7</strong>     to run the program to show the output of the program

(or <u>whatever name</u> you used for the executable)

Type:  <strong>cat lab7.out      </strong>to see the output of your program

Type:  <strong>exit</strong>                    to leave the script session




<strong> </strong>

<strong><u>Turn in your completed session:</u> </strong>

Go to Canvas and turn in (no zip files):

<ol>

 <li>c</li>

 <li>your script session (StudentName_lab7.txt)</li>

</ol>





