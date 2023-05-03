Download Link: https://assignmentchef.com/product/solved-cs-3423-systems-programming-asignment-1
<br>
Shell Scripting




For this assignment, you will use <strong>bash </strong>create a simple course catalog for administrators to update the details of each course offered by their department. The system will store basic information about each course, allowing the user to create, read, update, and delete them.

This assignment requires only the utilities used so far in the lecture notes. <strong>Do not </strong>use sed, awk, or any programming languages or utilities not yet covered in the lecture notes.

<strong>Tip: </strong>Filenames in the native Linux filesystem are case-sensitive. Thus, without proper consideration, a course whose associated filename was created as <sub>cs3423.crs </sub>(based on lowercase input given for the course’s department code the time of its creation) will not also be associated with the file <sub>CS3423.crs</sub>. This is not desirable behavior, however, as user’s may unexpectedly enter either uppercase or lowercase department codes when using your script.

Therefore, you may utilize a <strong>bash </strong>feature (known as “case modification” parameter expansion) that enables you to easily convert the contents of a variable to its uppercase equivalent. For example, this feature can be utilized to produce the capitalized contents of the variable containing a department code by simply writing <sub>${dept_codeˆˆ} </sub>instead of <sub>$dept_code </sub>when building the filename you will use for a particular course.

<strong>Tip: </strong>Note, that when prompted to enter a department code and course number, you should enter these values as <em>two separate tokens separated by a space</em>. Otherwise, it would be necessary to perform complex token-splitting to separate these values, which is outside the scope of this assignment. For example, when prompting the user:

<strong>Enter a department code and course number: </strong>You should enter “cs 3423”, <strong>not </strong>“cs3423”!

<h1>Storing Course Information</h1>

Course information will be stored in text files.

<ol>

 <li>Files will be stored inside a directory called <strong><sub>data </sub></strong>within the same directory as your script.</li>

 <li>Each file will be named based on the combination of a department code and a course number, which consists of <strong>two or three </strong>letters followed by an integer with exactly <strong>four </strong>digits, followed by the extension <strong><sub>.crs </sub></strong>(notice that the text file does not end in <strong><sub>.txt</sub></strong>. Does that need to be accounted for?).</li>

 <li>A course file consists of <em>exactly </em>five lines:

  <ul>

   <li>dept_code (two or three letter abbreviation) dept_name (string with <strong>probable whitespace</strong>)</li>

   <li>course_name (string with <strong>probable whitespace</strong>)</li>

   <li>course_sched (string consisting precisely of either “MWF” or “TH”) course_start (string with <strong>no whitespace</strong>) course_end (string with <strong>no whitespace</strong>)</li>

   <li>course_hours (credit hours, unsigned integer)</li>

   <li>course_size (enrolled students, unsigned integer)</li>

  </ul></li>

</ol>

* Department names may contain whitespace. You should account for names with multiple tokens (e.g., “ESL English as a Second Language” =<em><sub>⇒ </sub></em>dept_code = “ESL”, and dept_name = “English as a Second Language”)

<ol start="4">

 <li>Example file named <strong><sub>crs</sub></strong></li>

</ol>

ESL English as a Second Language

Literacy in a Second Language MWF 8/26/19 12/13/19

3

52

<h1>Script Execution</h1>

When the script is run, the following should occur. <strong>All script output should appear exactly as it appears below.</strong>

<ol>

 <li>Upon running your script, the user should be presented with the following menu:</li>

</ol>

<strong>Enter one of the following actions or press CTRL-D to exit.</strong>

<strong>C – create a new course record</strong>

<strong>R – read an existing course record</strong>

<strong>U – update an existing course record D – delete an existing course record</strong>

<strong>E – update enrolled student count of existing course</strong>

<strong>T – show total course count</strong>

<ol start="2">

 <li>The user then enters a one-character action (upper or lowercase), leading to one of the following.</li>

</ol>

<ul>

 <li><strong><sub>C</sub></strong>: a course is created</li>

</ul>

(a) From the terminal, read the following one at a time:

<ol>

 <li>Department code (two-to-three character string)</li>

 <li>Department name (string possibly containing whitespace)</li>

</ol>

<ul>

 <li>Course number (integer) iv. Course name (string possibly containing whitespace)</li>

</ul>

<ol>

 <li>Course schedule (string <em>∈{</em>MWF<em>,</em>TH<em>}</em>)</li>

 <li>Course start date (string with slashes) vii. Course end date (string with slashes) viii. Course credit hours (unsigned integer)</li>

 <li>Initial course enrollment (unsigned integer)</li>

</ol>

<ul>

 <li>Using the values entered by the user, create a new file in the <strong><sub>data </sub></strong>folder based on the instructions above.</li>

 <li>Update <strong><sub>data/queries.log </sub></strong>by adding the following line:</li>

</ul>

<h2>[date] CREATED: dept_code course_num course_name</h2>

where <em>date </em>is the output from the <strong><sub>date </sub></strong>command and <em>dept_code</em>, <em>course_num</em>, and <em>course_name </em>are the corresponding values.

(d) If the course already exists, print the following error and continue with the script.

The script should accept all seven inputs <em>before </em>checking if the record exists.

<strong>ERROR: course already exists</strong>

<ul>

 <li><strong><sub>R</sub></strong>: read an existing course’s information</li>

 <li>Prompt the user for a course department and course number: (e.g., “<sub>cs 3423</sub>”)</li>

</ul>

<strong>Enter a department code and course number:</strong>

<ul>

 <li>Search for the specified course using the provided department and number (e.g., “<sub>cs</sub></li>

</ul>

3423”).

<ul>

 <li>Print the course information in the following format:</li>

</ul>

<h2>Course department: dept_code dept_name</h2>

<strong>Course number: <em>course_num</em></strong>

<strong>Course name: <em>course_name</em></strong>

<strong>Scheduled days: <em>course_sched</em></strong>

<strong>Course start: <em>course_start</em></strong>

<strong>Course end: <em>course_end</em></strong>

<strong>Credit hours: <em>course_hours</em></strong>

<strong>Enrolled Students: <em>course_size</em></strong>

(d) If the course is not found, print the following error instead and continue with the script.

<strong>ERROR: course not found</strong>

<ul>

 <li><strong><sub>U</sub></strong>: update an existing course record</li>

 <li>Prompt the user for the following one at a time:

  <ol>

   <li>Department code (two-to-three character string)</li>

   <li>Department name (string possibly containing whitespace)</li>

  </ol></li>

</ul>

<ul>

 <li>Course number (integer) iv. Course name (string possibly containing whitespace)</li>

</ul>

<ol>

 <li>Course meeting days (string <em>∈{</em>MWF<em>,</em>TH<em>}</em>)</li>

 <li>Course start date (string with slashes) vii. Course end date (string with slashes) viii. Course credit hours (unsigned integer)</li>

 <li>Course enrollment (unsigned integer)</li>

</ol>

<ul>

 <li>Search for the specified course using the course department and course number (e.g.,</li>

</ul>

“cs 3423”).

<ul>

 <li>Update each of the corresponding fields based on the user input. <strong>If the user input is blank for a particular field, keep the original value from the file.</strong></li>

 <li>Update <strong><sub>data/queries.log </sub></strong>by adding the following line:</li>

</ul>

<h2>[date] UPDATED: dept_code course_num course_name</h2>

where <em>date </em>is the output from the <strong><sub>date </sub></strong>command and <em>dept_code</em>, <em>course_num</em>, and <em>course_name </em>are the corresponding values.

(e) If the course is not found, print the following error and continue with the script. The script should accept all nine inputs <em>before </em>checking if the record exists.

<strong>ERROR: course not found</strong>

<ul>

 <li><strong><sub>D</sub></strong>: delete an existing course</li>

 <li>Prompt the user for a string representing the course department and number (e.g.,</li>

</ul>

“cs 3423”):

<strong>Enter a course department code and number:</strong>

<ul>

 <li>Delete the specified course’s file.</li>

 <li>Update <strong><sub>data/queries.log </sub></strong>by adding the following line:</li>

</ul>

<h2>[date] DELETED: dept_code course_num course_name</h2>

where <em>date </em>is the output from the <strong><sub>date </sub></strong>command and <em>dept_code</em>, <em>course_num</em>, and <em>course_name </em>are the corresponding values.

<ul>

 <li>Print the following message to stdout with the course’s number: <strong><em>course number </em></strong><strong>was successfully deleted.</strong></li>

 <li>If the course is not found, print the following error instead and continue with the script.</li>

</ul>

<strong>ERROR: course not found</strong>

<ul>

 <li><strong><sub>E</sub></strong>: update the number of enrolled students for an existing course</li>

 <li>Prompt the user for a string representing the course department and number (e.g.,</li>

</ul>

“cs 3423”):

<strong>Enter a course department code and number:</strong>

<ul>

 <li>Prompt the user for an enrollment change amount (e.g., entering a value of <sub>3 </sub>would represent enrolling three new students in the class, while <sub>-2 </sub>would reflect two students having dropped the course):</li>

</ul>

<strong>Enter an enrollment change amount:</strong>

<ul>

 <li>Search for the specified course using the course number.</li>

 <li>Update the course record by adding the new enrollment count to the course’s current enrollment count. <strong>Negative values are allowed. </strong>(i.e., students could drop the class).</li>

 <li>Update <strong><sub>data/queries.log </sub></strong>by adding the following line:</li>

</ul>

<h2>[date] ENROLLMENT: dept_code course_num course_name changed by change_amt</h2>

where <em>date </em>is the output from the <strong><sub>date </sub></strong>command and <em>dept_code</em>, <em>course_num</em>, <em>course_name</em>, and <em>change_amt </em>are the corresponding values.

(f) If the course record is not found, print the following error and continue with the script. The script should accept the enrollment change amount <em>before </em>checking if the record exists.

<strong>ERROR: course not found</strong>

<ul>

 <li><strong><sub>T</sub></strong>: print the total number of course records</li>

</ul>

(a) Print the total number of <strong><sub>.crs </sub></strong>files within the <strong><sub>data </sub></strong>directory:

<strong>Total course records: <em>total </em></strong>where <em>total </em>is the total <strong><sub>.crs </sub></strong>files.

<ul>

 <li>If an invalid character is entered, print the following error and continue with the script.</li>

</ul>

<strong>ERROR: invalid option</strong>

<ol start="3">

 <li>After an action is completed, display the menu again. This should go on indefinitely until <strong>CTRL-D </strong>or the end of a file is reached.</li>

</ol>

<h1>Assignment Data</h1>

An initial data set can be found in <strong>/usr/local/courses/ssilvestro/cs3423/Fall19/assign1</strong>. Copy this to your own assignment’s directory.

<h1>Script Files</h1>

Your program should consist of seven bash files with the following names (case sensitive):

<ul>

 <li><strong><sub>bash </sub></strong>– the main file which is initially invoked</li>

 <li><strong><sub>bash </sub></strong>– logic for the create option</li>

 <li><strong><sub>bash </sub></strong>– logic for the read option</li>

 <li><strong><sub>bash </sub></strong>– logic for the update option</li>

 <li><strong><sub>bash </sub></strong>– logic for the delete option</li>

 <li><strong><sub>bash </sub></strong>– logic for the update enrollment option</li>

 <li><strong><sub>bash </sub></strong>– logic for the total option</li>

</ul>

<h1>Verifying Your Program</h1>

Your program must work with the input provided in <strong><sub>a1Input.txt</sub></strong>. To test it:

<ol>

 <li>Verify that your assignment folder has a <strong><sub>data </sub></strong>directory with the initial data set.</li>

 <li>Execute your script and <strong>redirect </strong><strong><sub>txt </sub></strong>into it. You should not be copying or typing the contents of <strong><sub>a1Input.txt </sub></strong>into your terminal. Redirection must work.</li>

 <li>Verify that the output and files are as expected.</li>

</ol>


