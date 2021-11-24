This lab is a 2 week lab

It is worth 200 points ( all previous were worth 100)

You may work in a team of 2 people (this is common in the industry and is called "pair programming") and submit the same code from both members. If you do, you must submit a comment on Canvas stating the members of your team. Your code should also mention this in a comment.

You may also choose to work by yourself but no extra credit will be given if you do.

.
Well...we're taking another trip with our parents and all of our electronic devices are out of power, so we need to go "old school" to kill some time to get over the boredom.

Hey, let's sing 100 bottles of beer on the wall!!!!!!!!!!!!!!!
You know....
100 bottles of beer on the wall, 100 bottles of beer
if one of those bottles just happens to fall
99 bottles of beer on the wall
<continue until there are no bottles left, then complete the song with the last line which has no number>
NO MORE BOTTLES OF BEER ON THE WALL

.

Ok...so this is what we're going to do.

.
Write some code and call it lab7_1.c
- compile it into a file called lab7_1
- this code will accept a number on the command line, as an argument from which you will count down from
- if no argument is entered on the command line respond to the user with a "Usage" statement showing that the command requires an argument of a number between 1 and 100 and exit the program with an exit status of 1
- it will check to see what you entered was a number between 1 and 100. if the number is not between 1 and 100 please exit the program with exit status 99
- lab7_1 will start a loop based on the number of bottles of beer you began with
- the code should open up a text file called bottlesofbeer.txt which will contain the text...
bottles of beer on the wall
bottles of beer
- it will print the beer bottle number, followed by each line of text from bottlesofbeer.txt all on the same line of output
EXAMPLE: 99 bottles of beer on the wall, 99 bottles of beer
- lab7_1 should NOT close the file bottlesofbeer.txt
- at this point lab7_1 should fork a new process
- it then will do a corresponding exec to call lab7_2 (specifications are below) and pass the beer bottle number to it
- lab7_1 will wait until lab7_2 is complete

.

Write some code and call it lab7_2.c then compile it to a file called lab7_2
- lab7_2 will open a file called happenstofall.txt which will contain the text...
if one of those bottles just happens to fall
- lab7_2 will read the file and print the contents (please note that we are not printing the bottle number, just the text in the file).
EXAMPLE: if one of those bottles just happens to fall
- lab7_2 should now close the file happenstofall.txt
- at this point lab7_2 should fork a new process
- it then will do a corresponding exec to call lab7_3 (specifications are below) and pass the present beer bottle number to it
- lab7_2 will wait until lab7_3 is complete

.

Write some code and call it lab7_3.c and then compile it to a file called lab7_3
- lab7_3 will then open a file called remaining.txt which will contain the text...
bottles of beer on the wall
- lab7_3 will decrement the present beer bottle number passed to it by lab7_2 and print it, followed by the contents of the file remaining.txt on the same line of output
EXAMPLE: 98 bottles of beer on the wall
- lab7_3 will close the file remaining.txt

.

At this point 
- lab7_3 will now terminate
- because lab7_2 was waiting for lab7_3 to terminate, lab7_2 will now terminate, passing control back to lab7_1
- lab7_1 will pause for 1 second
- lab7_1 will then continue its loop with the next beer bottle in the descending sequence and the processes above will repeat.
- Once the beer bottle number becomes 0, the loop is complete and then then lab7_1 will print the last line which is a literal (not read from a file).
EXAMPLE: NO MORE BOTTLES OF BEER ON THE WALL
- then close the file bottlesofbeer.txt

.

The entire process is done.

.

Other REQUIREMENTS:
*before each line of output, have each of the processes print out its PID and PPID and the file descriptor of the file it just opened (on a single line) before the requested output line (the lyrics)

*The entire process should not only output to STDOUT but also to a file called beer.out which should show everything that was sent to STDOUT. Since this file is used by all 3 processes it should be opened, written to and closed before any forking of new processes happens in each of the programs.

*beer.out will be referenced throughout the process. after the final line is written to the file change the permissions of beer.out to 600 ( - rw- --- --- ). This step should be done in lab7_1.c

*submit lab7_1.c, lab7_2.c, lab7_3.c and your beer.out to Canvas for grading (we do not need the txt files...we will use our own)

.

HINTS:

*check out mother.c and daughter.c regarding examples of forking and execing processes

*check out fstuff.c for examples of opening, closing, reading from and writing to files

*all this code was covered in class and the specific videos containing them can be reviewed if you think you need to get a refresher.

* those code samples can be found in our dropbox /var/tmp/FA2021_CSIT231/

