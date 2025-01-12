# streaming-02-multiple-processes

> Multiple processes accessing a shared resource concurrently

## Oveview

This example starts up a shared database and three different processes.

The processes represent multiple users, or locations, or programs 
hitting a shared database at the same time. 

## Prerequisite

Complete the setup at [streaming-01-getting-started](https://github.com/denisecase/streaming-01-getting-started).

## About

Execute about.py to generate some useful information.

## First Run

Executing multiple_processes.py script.

Read the output. Read the code. 
Try to figure out what's going on. 

1. What libraries did we import?
    sqlite3, time, multiprocessing, os, datetime, platform, sys
1. Where do we set the task_duration?
    variable task_duration
1. How many functions are defined? 
    7
1. What are the function names? 
    create_table, drop_table, insert_pet, process_one, process_two, process_three, recreate_database
1. In general, what does each function do? 
    create_table: creates a table names pets; drop_table: drops a table names pets; insert_pet: inserts a record in the pets table; process_one,    process_two, and process_three, insert_pet, adding specific pet information; recreate_database: drops and creates the pets table
1. Where does the execution begin?
    with "if name == "main":"
1. How many processes do we start?
    3
1. How many records does each process insert?
    2

In this first run, we start 3 processes, 
each inserting 2 records into a shared database 
(for a total of 6 records inserted.)

In each case, the process gets a connection to the database, 
and a cursor to execute SQL statements.
They insert a record, and get out of the database quickly.

In general, we're successful and six new records get inserted. 

## Second Run

For the second run, modify the task_duration to make each task take 3 seconds. Run it again. 
With the longer tasks, we now get into trouble - 
one process will have the database open and be working on it - 
then when another process tries to do the same, it can't and 
we end up with an error. 

## Document Results After Each Run

To clear the terminal, in the terminal window, type clear and hit enter or return. 

`clear`

To document results, clear the terminal, run the script, and paste all of the terminal contents into the output file.

Use out0.txt to document the first run. 

Use out3.txt to document the second run.

## Select All, Copy, Paste

On Windows the select all, copy, paste hotkeys are:

- CTRL a 
- CTRL c 
- CTRL v 

On a Mac the select all, copy, paste hotkeys are:

- Command a
- Command c
- Command v

Detailed copy/paste instructions (as needed)

1. To use these keys to transfer your output into a file, 
clear the terminal, run the script, then click in the terminal to make it active.
1. To select all terminal content, hold CTRL and the 'a' key together. 
1. To copy the selected content, hold CTRL and the 'c' key together. 
1. To paste, open the destination file (e.g. out0.py) for editing.
1. Click somewhere in the destination file to make it the active window.
1. Now hit CTRL a (both together) to select all of the destination file.
1. Hit CTRL v (both together) to paste the content from your clipboard.

Do a web search to find helpful videos on anything that seems confusing. 

## Reading Error Messages

Python has pretty helpful error messages. 
When you get an error, read them carefully. 

- What error do you get?  AttributeError line 126
- Can you tell what line it was executing when it failed?
  AttributeError line 126

## Database Is Locked Error

Do a web search on the sqlite3 'database is locked' error.

- What do you learn? Locked error occurs while performing two operations on a database at the same detail and connection or two users are running transactions on the same table,
- Once a process fails, it crashes the main process and everything stops. 

## Deadlock

Deadlock is a special kind of locking issue where a proces 
is waiting on a resource or process, that is waiting also. 

Rather than crashing, a system in deadlock may wait indefinitely, 
with no process able to move forward and make progress.

## Learn More

Check out Wikipedia's article on deadlock and other sources to learn how to prevent and avoid locking issues in concurrent processes.  Reference suggest when a deadlock scenario exists, set a new super-thread and follow that logic.

UDP datagrams vs TCP protocol https://www.spiceworks.com/tech/networking/articles/tcp-vs-udp/#:~:text=Transmission%20control%20protocol%20(TCP)%20drives,are%20crucial%20to%20internet%20operations
Some contrasts
1.TCP is connection oriented while UDP is connectionless
2. TCP leverages more error-checking mechanisms than UDP
3. TCP sends data in a particular sequence, whereas there is no fixed order for UDP protocol
4. UDP is faster and more efficient than TCP 
5. Unlike UDP, TCP cannot be used for multicast or broadcast services 
6.  TCP leverages flow control, while UDP does not
7. UDP does not control congestion, whereas TCP implements congestion avoidance algorithms 
8. TCP is more reliable than UDP 
9. The TCP header is different from the UDP header 
10. UDP is suitable for live and real-time data transmission, which TCP cannot support 


