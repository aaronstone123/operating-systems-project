[ Sleeping-TA-Problem question number 14]

14. A university computer science department has a teaching assistant (TA) whohelps undergraduate students with their programming assignments duringregular office hours. The TA’s office is rather small and has room for only onedesk with a chair and computer. There are three chairs in the hallway outsidethe office where students can sit and wait if the TA is currently helping anotherstudent. When there are no students who need help during office hours, the TA sits at the desk and takes a nap. If a student arrives during office hoursand finds the TA sleeping, the student must awaken the TA to ask for help. If astudent arrives and finds the TA currently helping another student, the student sits on one of the chairs in the hallway and waits. If no chairs are available, thestudent will come back at a later time. Using POSIX threads, mutex locks, and semaphores, implement a solutionthat coordinates the activities of the TA and the students.


[Solution]

Using Pthreads, n students are created. Each student, as well as the TA, run as a separate thread. Student threads alternate between programming for a period of time and seeking help from the TA. If the TA is available, they obtain help. Otherwise, they either sit in a chair in the hallway, or if no chairs are available, resume programming and seek help at a later time. If a student arrives and notices that the TA is sleeping, the student notifies the TA using a semaphore. When the TA finishes helping a student, the TA checks to see if there are students waiting for help in the hallway. If so, the TA helps each of these students in turn. If no students are present, the TA returns to napping.

The TA and each student thread print their state and threadID (student number).

The program can take 0 or 1 command line parameters. The number of students present can be specified as a command line parameter. If this parameter is not included, the number of students defaults to 5.

## To Run
* Navigate to the Sleeping-TA-Problem directory.
* From the command line, run make or make all.
* From the command line, run ./sleepingTA (if specifying the number of students present, include that integer as a parameter).
* Results will print to console.
* Press Ctrl-C to exit the program.
