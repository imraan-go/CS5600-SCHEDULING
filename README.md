# Chapter 8

## Question 1

 python3 mlfq.py -j 2 -n 2 -m 10 -M 0 -c
Here is the list of inputs:
OPTIONS jobs 2
OPTIONS queues 2
OPTIONS allotments for queue  1 is   1
OPTIONS quantum length for queue  1 is  10
OPTIONS allotments for queue  0 is   1
OPTIONS quantum length for queue  0 is  10
OPTIONS boost 0
OPTIONS ioTime 5
OPTIONS stayAfterIO False
OPTIONS iobump False


For each job, three defining characteristics are given:
  startTime : at what time does the job enter the system
  runTime   : the total CPU time needed by the job to finish
  ioFreq    : every ioFreq time units, the job issues an I/O
              (the I/O takes ioTime units to complete)

Job List:
  Job  0: startTime   0 - runTime   8 - ioFreq   0
  Job  1: startTime   0 - runTime   4 - ioFreq   0


Execution Trace:

[ time 0 ] JOB BEGINS by JOB 0
[ time 0 ] JOB BEGINS by JOB 1
[ time 0 ] Run JOB 0 at PRIORITY 1 [ TICKS 9 ALLOT 1 TIME 7 (of 8) ]
[ time 1 ] Run JOB 0 at PRIORITY 1 [ TICKS 8 ALLOT 1 TIME 6 (of 8) ]
[ time 2 ] Run JOB 0 at PRIORITY 1 [ TICKS 7 ALLOT 1 TIME 5 (of 8) ]
[ time 3 ] Run JOB 0 at PRIORITY 1 [ TICKS 6 ALLOT 1 TIME 4 (of 8) ]
[ time 4 ] Run JOB 0 at PRIORITY 1 [ TICKS 5 ALLOT 1 TIME 3 (of 8) ]
[ time 5 ] Run JOB 0 at PRIORITY 1 [ TICKS 4 ALLOT 1 TIME 2 (of 8) ]
[ time 6 ] Run JOB 0 at PRIORITY 1 [ TICKS 3 ALLOT 1 TIME 1 (of 8) ]
[ time 7 ] Run JOB 0 at PRIORITY 1 [ TICKS 2 ALLOT 1 TIME 0 (of 8) ]
[ time 8 ] FINISHED JOB 0
[ time 8 ] Run JOB 1 at PRIORITY 1 [ TICKS 9 ALLOT 1 TIME 3 (of 4) ]
[ time 9 ] Run JOB 1 at PRIORITY 1 [ TICKS 8 ALLOT 1 TIME 2 (of 4) ]
[ time 10 ] Run JOB 1 at PRIORITY 1 [ TICKS 7 ALLOT 1 TIME 1 (of 4) ]
[ time 11 ] Run JOB 1 at PRIORITY 1 [ TICKS 6 ALLOT 1 TIME 0 (of 4) ]
[ time 12 ] FINISHED JOB 1

Final statistics:
  Job  0: startTime   0 - response   0 - turnaround   8
  Job  1: startTime   0 - response   8 - turnaround  12

  Avg  1: startTime n/a - response 4.00 - turnaround 10.00



## Question 2

To make it act like round robin, Use  1 queue and a shorter time slice like 2.


python3 mlfq.py -j 2 -n 1 -q 2 -m 10 -M 0 -c 
Here is the list of inputs:
OPTIONS jobs 2
OPTIONS queues 1
OPTIONS allotments for queue  0 is   1
OPTIONS quantum length for queue  0 is   2
OPTIONS boost 0
OPTIONS ioTime 5
OPTIONS stayAfterIO False
OPTIONS iobump False


For each job, three defining characteristics are given:
  startTime : at what time does the job enter the system
  runTime   : the total CPU time needed by the job to finish
  ioFreq    : every ioFreq time units, the job issues an I/O
              (the I/O takes ioTime units to complete)

Job List:
  Job  0: startTime   0 - runTime   8 - ioFreq   0
  Job  1: startTime   0 - runTime   4 - ioFreq   0


Execution Trace:

[ time 0 ] JOB BEGINS by JOB 0
[ time 0 ] JOB BEGINS by JOB 1
[ time 0 ] Run JOB 0 at PRIORITY 0 [ TICKS 1 ALLOT 1 TIME 7 (of 8) ]
[ time 1 ] Run JOB 0 at PRIORITY 0 [ TICKS 0 ALLOT 1 TIME 6 (of 8) ]
[ time 2 ] Run JOB 1 at PRIORITY 0 [ TICKS 1 ALLOT 1 TIME 3 (of 4) ]
[ time 3 ] Run JOB 1 at PRIORITY 0 [ TICKS 0 ALLOT 1 TIME 2 (of 4) ]
[ time 4 ] Run JOB 0 at PRIORITY 0 [ TICKS 1 ALLOT 1 TIME 5 (of 8) ]
[ time 5 ] Run JOB 0 at PRIORITY 0 [ TICKS 0 ALLOT 1 TIME 4 (of 8) ]
[ time 6 ] Run JOB 1 at PRIORITY 0 [ TICKS 1 ALLOT 1 TIME 1 (of 4) ]
[ time 7 ] Run JOB 1 at PRIORITY 0 [ TICKS 0 ALLOT 1 TIME 0 (of 4) ]
[ time 8 ] FINISHED JOB 1
[ time 8 ] Run JOB 0 at PRIORITY 0 [ TICKS 1 ALLOT 1 TIME 3 (of 8) ]
[ time 9 ] Run JOB 0 at PRIORITY 0 [ TICKS 0 ALLOT 1 TIME 2 (of 8) ]
[ time 10 ] Run JOB 0 at PRIORITY 0 [ TICKS 1 ALLOT 1 TIME 1 (of 8) ]
[ time 11 ] Run JOB 0 at PRIORITY 0 [ TICKS 0 ALLOT 1 TIME 0 (of 8) ]
[ time 12 ] FINISHED JOB 0

Final statistics:
  Job  0: startTime   0 - response   0 - turnaround  12
  Job  1: startTime   0 - response   2 - turnaround   8

  Avg  1: startTime n/a - response 1.00 - turnaround 10.00



## Question 4

python3 mlfq.py -j 2  -S  -m 10 -l 0,100,9:0,100,9 -c  
Here is the list of inputs:
OPTIONS jobs 2
OPTIONS queues 3
OPTIONS allotments for queue  2 is   1
OPTIONS quantum length for queue  2 is  10
OPTIONS allotments for queue  1 is   1
OPTIONS quantum length for queue  1 is  10
OPTIONS allotments for queue  0 is   1
OPTIONS quantum length for queue  0 is  10
OPTIONS boost 0
OPTIONS ioTime 5
OPTIONS stayAfterIO True
OPTIONS iobump False


For each job, three defining characteristics are given:
  startTime : at what time does the job enter the system
  runTime   : the total CPU time needed by the job to finish
  ioFreq    : every ioFreq time units, the job issues an I/O
              (the I/O takes ioTime units to complete)

Job List:
  Job  0: startTime   0 - runTime 100 - ioFreq   9
  Job  1: startTime   0 - runTime 100 - ioFreq   9


Execution Trace:

[ time 0 ] JOB BEGINS by JOB 0
[ time 0 ] JOB BEGINS by JOB 1
[ time 0 ] Run JOB 0 at PRIORITY 2 [ TICKS 9 ALLOT 1 TIME 99 (of 100) ]
[ time 1 ] Run JOB 0 at PRIORITY 2 [ TICKS 8 ALLOT 1 TIME 98 (of 100) ]
[ time 2 ] Run JOB 0 at PRIORITY 2 [ TICKS 7 ALLOT 1 TIME 97 (of 100) ]
[ time 3 ] Run JOB 0 at PRIORITY 2 [ TICKS 6 ALLOT 1 TIME 96 (of 100) ]
[ time 4 ] Run JOB 0 at PRIORITY 2 [ TICKS 5 ALLOT 1 TIME 95 (of 100) ]
[ time 5 ] Run JOB 0 at PRIORITY 2 [ TICKS 4 ALLOT 1 TIME 94 (of 100) ]
[ time 6 ] Run JOB 0 at PRIORITY 2 [ TICKS 3 ALLOT 1 TIME 93 (of 100) ]
[ time 7 ] Run JOB 0 at PRIORITY 2 [ TICKS 2 ALLOT 1 TIME 92 (of 100) ]
[ time 8 ] Run JOB 0 at PRIORITY 2 [ TICKS 1 ALLOT 1 TIME 91 (of 100) ]
[ time 9 ] IO_START by JOB 0
IO DONE
[ time 9 ] Run JOB 1 at PRIORITY 2 [ TICKS 9 ALLOT 1 TIME 99 (of 100) ]
[ time 10 ] Run JOB 1 at PRIORITY 2 [ TICKS 8 ALLOT 1 TIME 98 (of 100) ]
[ time 11 ] Run JOB 1 at PRIORITY 2 [ TICKS 7 ALLOT 1 TIME 97 (of 100) ]
[ time 12 ] Run JOB 1 at PRIORITY 2 [ TICKS 6 ALLOT 1 TIME 96 (of 100) ]
[ time 13 ] Run JOB 1 at PRIORITY 2 [ TICKS 5 ALLOT 1 TIME 95 (of 100) ]
[ time 14 ] IO_DONE by JOB 0
[ time 14 ] Run JOB 1 at PRIORITY 2 [ TICKS 4 ALLOT 1 TIME 94 (of 100) ]
[ time 15 ] Run JOB 1 at PRIORITY 2 [ TICKS 3 ALLOT 1 TIME 93 (of 100) ]
[ time 16 ] Run JOB 1 at PRIORITY 2 [ TICKS 2 ALLOT 1 TIME 92 (of 100) ]
[ time 17 ] Run JOB 1 at PRIORITY 2 [ TICKS 1 ALLOT 1 TIME 91 (of 100) ]
[ time 18 ] IO_START by JOB 1
IO DONE
[ time 18 ] Run JOB 0 at PRIORITY 2 [ TICKS 9 ALLOT 1 TIME 90 (of 100) ]
[ time 19 ] Run JOB 0 at PRIORITY 2 [ TICKS 8 ALLOT 1 TIME 89 (of 100) ]
[ time 20 ] Run JOB 0 at PRIORITY 2 [ TICKS 7 ALLOT 1 TIME 88 (of 100) ]
[ time 21 ] Run JOB 0 at PRIORITY 2 [ TICKS 6 ALLOT 1 TIME 87 (of 100) ]
[ time 22 ] Run JOB 0 at PRIORITY 2 [ TICKS 5 ALLOT 1 TIME 86 (of 100) ]
[ time 23 ] IO_DONE by JOB 1
[ time 23 ] Run JOB 0 at PRIORITY 2 [ TICKS 4 ALLOT 1 TIME 85 (of 100) ]
[ time 24 ] Run JOB 0 at PRIORITY 2 [ TICKS 3 ALLOT 1 TIME 84 (of 100) ]
[ time 25 ] Run JOB 0 at PRIORITY 2 [ TICKS 2 ALLOT 1 TIME 83 (of 100) ]
[ time 26 ] Run JOB 0 at PRIORITY 2 [ TICKS 1 ALLOT 1 TIME 82 (of 100) ]
[ time 27 ] IO_START by JOB 0
IO DONE
[ time 27 ] Run JOB 1 at PRIORITY 2 [ TICKS 9 ALLOT 1 TIME 90 (of 100) ]
[ time 28 ] Run JOB 1 at PRIORITY 2 [ TICKS 8 ALLOT 1 TIME 89 (of 100) ]
[ time 29 ] Run JOB 1 at PRIORITY 2 [ TICKS 7 ALLOT 1 TIME 88 (of 100) ]
[ time 30 ] Run JOB 1 at PRIORITY 2 [ TICKS 6 ALLOT 1 TIME 87 (of 100) ]
[ time 31 ] Run JOB 1 at PRIORITY 2 [ TICKS 5 ALLOT 1 TIME 86 (of 100) ]
[ time 32 ] IO_DONE by JOB 0
[ time 32 ] Run JOB 1 at PRIORITY 2 [ TICKS 4 ALLOT 1 TIME 85 (of 100) ]
[ time 33 ] Run JOB 1 at PRIORITY 2 [ TICKS 3 ALLOT 1 TIME 84 (of 100) ]
[ time 34 ] Run JOB 1 at PRIORITY 2 [ TICKS 2 ALLOT 1 TIME 83 (of 100) ]
[ time 35 ] Run JOB 1 at PRIORITY 2 [ TICKS 1 ALLOT 1 TIME 82 (of 100) ]
[ time 36 ] IO_START by JOB 1
IO DONE
[ time 36 ] Run JOB 0 at PRIORITY 2 [ TICKS 9 ALLOT 1 TIME 81 (of 100) ]
[ time 37 ] Run JOB 0 at PRIORITY 2 [ TICKS 8 ALLOT 1 TIME 80 (of 100) ]
[ time 38 ] Run JOB 0 at PRIORITY 2 [ TICKS 7 ALLOT 1 TIME 79 (of 100) ]
[ time 39 ] Run JOB 0 at PRIORITY 2 [ TICKS 6 ALLOT 1 TIME 78 (of 100) ]
[ time 40 ] Run JOB 0 at PRIORITY 2 [ TICKS 5 ALLOT 1 TIME 77 (of 100) ]
[ time 41 ] IO_DONE by JOB 1
[ time 41 ] Run JOB 0 at PRIORITY 2 [ TICKS 4 ALLOT 1 TIME 76 (of 100) ]
[ time 42 ] Run JOB 0 at PRIORITY 2 [ TICKS 3 ALLOT 1 TIME 75 (of 100) ]
[ time 43 ] Run JOB 0 at PRIORITY 2 [ TICKS 2 ALLOT 1 TIME 74 (of 100) ]
[ time 44 ] Run JOB 0 at PRIORITY 2 [ TICKS 1 ALLOT 1 TIME 73 (of 100) ]
[ time 45 ] IO_START by JOB 0
IO DONE
[ time 45 ] Run JOB 1 at PRIORITY 2 [ TICKS 9 ALLOT 1 TIME 81 (of 100) ]
[ time 46 ] Run JOB 1 at PRIORITY 2 [ TICKS 8 ALLOT 1 TIME 80 (of 100) ]
[ time 47 ] Run JOB 1 at PRIORITY 2 [ TICKS 7 ALLOT 1 TIME 79 (of 100) ]
[ time 48 ] Run JOB 1 at PRIORITY 2 [ TICKS 6 ALLOT 1 TIME 78 (of 100) ]
[ time 49 ] Run JOB 1 at PRIORITY 2 [ TICKS 5 ALLOT 1 TIME 77 (of 100) ]
[ time 50 ] IO_DONE by JOB 0
[ time 50 ] Run JOB 1 at PRIORITY 2 [ TICKS 4 ALLOT 1 TIME 76 (of 100) ]
[ time 51 ] Run JOB 1 at PRIORITY 2 [ TICKS 3 ALLOT 1 TIME 75 (of 100) ]
[ time 52 ] Run JOB 1 at PRIORITY 2 [ TICKS 2 ALLOT 1 TIME 74 (of 100) ]
[ time 53 ] Run JOB 1 at PRIORITY 2 [ TICKS 1 ALLOT 1 TIME 73 (of 100) ]
[ time 54 ] IO_START by JOB 1
IO DONE
[ time 54 ] Run JOB 0 at PRIORITY 2 [ TICKS 9 ALLOT 1 TIME 72 (of 100) ]
[ time 55 ] Run JOB 0 at PRIORITY 2 [ TICKS 8 ALLOT 1 TIME 71 (of 100) ]
[ time 56 ] Run JOB 0 at PRIORITY 2 [ TICKS 7 ALLOT 1 TIME 70 (of 100) ]
[ time 57 ] Run JOB 0 at PRIORITY 2 [ TICKS 6 ALLOT 1 TIME 69 (of 100) ]
[ time 58 ] Run JOB 0 at PRIORITY 2 [ TICKS 5 ALLOT 1 TIME 68 (of 100) ]
[ time 59 ] IO_DONE by JOB 1
[ time 59 ] Run JOB 0 at PRIORITY 2 [ TICKS 4 ALLOT 1 TIME 67 (of 100) ]
[ time 60 ] Run JOB 0 at PRIORITY 2 [ TICKS 3 ALLOT 1 TIME 66 (of 100) ]
[ time 61 ] Run JOB 0 at PRIORITY 2 [ TICKS 2 ALLOT 1 TIME 65 (of 100) ]
[ time 62 ] Run JOB 0 at PRIORITY 2 [ TICKS 1 ALLOT 1 TIME 64 (of 100) ]
[ time 63 ] IO_START by JOB 0
IO DONE
[ time 63 ] Run JOB 1 at PRIORITY 2 [ TICKS 9 ALLOT 1 TIME 72 (of 100) ]
[ time 64 ] Run JOB 1 at PRIORITY 2 [ TICKS 8 ALLOT 1 TIME 71 (of 100) ]
[ time 65 ] Run JOB 1 at PRIORITY 2 [ TICKS 7 ALLOT 1 TIME 70 (of 100) ]
[ time 66 ] Run JOB 1 at PRIORITY 2 [ TICKS 6 ALLOT 1 TIME 69 (of 100) ]
[ time 67 ] Run JOB 1 at PRIORITY 2 [ TICKS 5 ALLOT 1 TIME 68 (of 100) ]
[ time 68 ] IO_DONE by JOB 0
[ time 68 ] Run JOB 1 at PRIORITY 2 [ TICKS 4 ALLOT 1 TIME 67 (of 100) ]
[ time 69 ] Run JOB 1 at PRIORITY 2 [ TICKS 3 ALLOT 1 TIME 66 (of 100) ]
[ time 70 ] Run JOB 1 at PRIORITY 2 [ TICKS 2 ALLOT 1 TIME 65 (of 100) ]
[ time 71 ] Run JOB 1 at PRIORITY 2 [ TICKS 1 ALLOT 1 TIME 64 (of 100) ]
[ time 72 ] IO_START by JOB 1
IO DONE
[ time 72 ] Run JOB 0 at PRIORITY 2 [ TICKS 9 ALLOT 1 TIME 63 (of 100) ]
[ time 73 ] Run JOB 0 at PRIORITY 2 [ TICKS 8 ALLOT 1 TIME 62 (of 100) ]
[ time 74 ] Run JOB 0 at PRIORITY 2 [ TICKS 7 ALLOT 1 TIME 61 (of 100) ]
[ time 75 ] Run JOB 0 at PRIORITY 2 [ TICKS 6 ALLOT 1 TIME 60 (of 100) ]
[ time 76 ] Run JOB 0 at PRIORITY 2 [ TICKS 5 ALLOT 1 TIME 59 (of 100) ]
[ time 77 ] IO_DONE by JOB 1
[ time 77 ] Run JOB 0 at PRIORITY 2 [ TICKS 4 ALLOT 1 TIME 58 (of 100) ]
[ time 78 ] Run JOB 0 at PRIORITY 2 [ TICKS 3 ALLOT 1 TIME 57 (of 100) ]
[ time 79 ] Run JOB 0 at PRIORITY 2 [ TICKS 2 ALLOT 1 TIME 56 (of 100) ]
[ time 80 ] Run JOB 0 at PRIORITY 2 [ TICKS 1 ALLOT 1 TIME 55 (of 100) ]
[ time 81 ] IO_START by JOB 0
IO DONE
[ time 81 ] Run JOB 1 at PRIORITY 2 [ TICKS 9 ALLOT 1 TIME 63 (of 100) ]
[ time 82 ] Run JOB 1 at PRIORITY 2 [ TICKS 8 ALLOT 1 TIME 62 (of 100) ]
[ time 83 ] Run JOB 1 at PRIORITY 2 [ TICKS 7 ALLOT 1 TIME 61 (of 100) ]
[ time 84 ] Run JOB 1 at PRIORITY 2 [ TICKS 6 ALLOT 1 TIME 60 (of 100) ]
[ time 85 ] Run JOB 1 at PRIORITY 2 [ TICKS 5 ALLOT 1 TIME 59 (of 100) ]
[ time 86 ] IO_DONE by JOB 0
[ time 86 ] Run JOB 1 at PRIORITY 2 [ TICKS 4 ALLOT 1 TIME 58 (of 100) ]
[ time 87 ] Run JOB 1 at PRIORITY 2 [ TICKS 3 ALLOT 1 TIME 57 (of 100) ]
[ time 88 ] Run JOB 1 at PRIORITY 2 [ TICKS 2 ALLOT 1 TIME 56 (of 100) ]
[ time 89 ] Run JOB 1 at PRIORITY 2 [ TICKS 1 ALLOT 1 TIME 55 (of 100) ]
[ time 90 ] IO_START by JOB 1
IO DONE
[ time 90 ] Run JOB 0 at PRIORITY 2 [ TICKS 9 ALLOT 1 TIME 54 (of 100) ]
[ time 91 ] Run JOB 0 at PRIORITY 2 [ TICKS 8 ALLOT 1 TIME 53 (of 100) ]
[ time 92 ] Run JOB 0 at PRIORITY 2 [ TICKS 7 ALLOT 1 TIME 52 (of 100) ]
[ time 93 ] Run JOB 0 at PRIORITY 2 [ TICKS 6 ALLOT 1 TIME 51 (of 100) ]
[ time 94 ] Run JOB 0 at PRIORITY 2 [ TICKS 5 ALLOT 1 TIME 50 (of 100) ]
[ time 95 ] IO_DONE by JOB 1
[ time 95 ] Run JOB 0 at PRIORITY 2 [ TICKS 4 ALLOT 1 TIME 49 (of 100) ]
[ time 96 ] Run JOB 0 at PRIORITY 2 [ TICKS 3 ALLOT 1 TIME 48 (of 100) ]
[ time 97 ] Run JOB 0 at PRIORITY 2 [ TICKS 2 ALLOT 1 TIME 47 (of 100) ]
[ time 98 ] Run JOB 0 at PRIORITY 2 [ TICKS 1 ALLOT 1 TIME 46 (of 100) ]
[ time 99 ] IO_START by JOB 0
IO DONE
[ time 99 ] Run JOB 1 at PRIORITY 2 [ TICKS 9 ALLOT 1 TIME 54 (of 100) ]
[ time 100 ] Run JOB 1 at PRIORITY 2 [ TICKS 8 ALLOT 1 TIME 53 (of 100) ]
[ time 101 ] Run JOB 1 at PRIORITY 2 [ TICKS 7 ALLOT 1 TIME 52 (of 100) ]
[ time 102 ] Run JOB 1 at PRIORITY 2 [ TICKS 6 ALLOT 1 TIME 51 (of 100) ]
[ time 103 ] Run JOB 1 at PRIORITY 2 [ TICKS 5 ALLOT 1 TIME 50 (of 100) ]
[ time 104 ] IO_DONE by JOB 0
[ time 104 ] Run JOB 1 at PRIORITY 2 [ TICKS 4 ALLOT 1 TIME 49 (of 100) ]
[ time 105 ] Run JOB 1 at PRIORITY 2 [ TICKS 3 ALLOT 1 TIME 48 (of 100) ]
[ time 106 ] Run JOB 1 at PRIORITY 2 [ TICKS 2 ALLOT 1 TIME 47 (of 100) ]
[ time 107 ] Run JOB 1 at PRIORITY 2 [ TICKS 1 ALLOT 1 TIME 46 (of 100) ]
[ time 108 ] IO_START by JOB 1
IO DONE
[ time 108 ] Run JOB 0 at PRIORITY 2 [ TICKS 9 ALLOT 1 TIME 45 (of 100) ]
[ time 109 ] Run JOB 0 at PRIORITY 2 [ TICKS 8 ALLOT 1 TIME 44 (of 100) ]
[ time 110 ] Run JOB 0 at PRIORITY 2 [ TICKS 7 ALLOT 1 TIME 43 (of 100) ]
[ time 111 ] Run JOB 0 at PRIORITY 2 [ TICKS 6 ALLOT 1 TIME 42 (of 100) ]
[ time 112 ] Run JOB 0 at PRIORITY 2 [ TICKS 5 ALLOT 1 TIME 41 (of 100) ]
[ time 113 ] IO_DONE by JOB 1
[ time 113 ] Run JOB 0 at PRIORITY 2 [ TICKS 4 ALLOT 1 TIME 40 (of 100) ]
[ time 114 ] Run JOB 0 at PRIORITY 2 [ TICKS 3 ALLOT 1 TIME 39 (of 100) ]
[ time 115 ] Run JOB 0 at PRIORITY 2 [ TICKS 2 ALLOT 1 TIME 38 (of 100) ]
[ time 116 ] Run JOB 0 at PRIORITY 2 [ TICKS 1 ALLOT 1 TIME 37 (of 100) ]
[ time 117 ] IO_START by JOB 0
IO DONE
[ time 117 ] Run JOB 1 at PRIORITY 2 [ TICKS 9 ALLOT 1 TIME 45 (of 100) ]
[ time 118 ] Run JOB 1 at PRIORITY 2 [ TICKS 8 ALLOT 1 TIME 44 (of 100) ]
[ time 119 ] Run JOB 1 at PRIORITY 2 [ TICKS 7 ALLOT 1 TIME 43 (of 100) ]
[ time 120 ] Run JOB 1 at PRIORITY 2 [ TICKS 6 ALLOT 1 TIME 42 (of 100) ]
[ time 121 ] Run JOB 1 at PRIORITY 2 [ TICKS 5 ALLOT 1 TIME 41 (of 100) ]
[ time 122 ] IO_DONE by JOB 0
[ time 122 ] Run JOB 1 at PRIORITY 2 [ TICKS 4 ALLOT 1 TIME 40 (of 100) ]
[ time 123 ] Run JOB 1 at PRIORITY 2 [ TICKS 3 ALLOT 1 TIME 39 (of 100) ]
[ time 124 ] Run JOB 1 at PRIORITY 2 [ TICKS 2 ALLOT 1 TIME 38 (of 100) ]
[ time 125 ] Run JOB 1 at PRIORITY 2 [ TICKS 1 ALLOT 1 TIME 37 (of 100) ]
[ time 126 ] IO_START by JOB 1
IO DONE
[ time 126 ] Run JOB 0 at PRIORITY 2 [ TICKS 9 ALLOT 1 TIME 36 (of 100) ]
[ time 127 ] Run JOB 0 at PRIORITY 2 [ TICKS 8 ALLOT 1 TIME 35 (of 100) ]
[ time 128 ] Run JOB 0 at PRIORITY 2 [ TICKS 7 ALLOT 1 TIME 34 (of 100) ]
[ time 129 ] Run JOB 0 at PRIORITY 2 [ TICKS 6 ALLOT 1 TIME 33 (of 100) ]
[ time 130 ] Run JOB 0 at PRIORITY 2 [ TICKS 5 ALLOT 1 TIME 32 (of 100) ]
[ time 131 ] IO_DONE by JOB 1
[ time 131 ] Run JOB 0 at PRIORITY 2 [ TICKS 4 ALLOT 1 TIME 31 (of 100) ]
[ time 132 ] Run JOB 0 at PRIORITY 2 [ TICKS 3 ALLOT 1 TIME 30 (of 100) ]
[ time 133 ] Run JOB 0 at PRIORITY 2 [ TICKS 2 ALLOT 1 TIME 29 (of 100) ]
[ time 134 ] Run JOB 0 at PRIORITY 2 [ TICKS 1 ALLOT 1 TIME 28 (of 100) ]
[ time 135 ] IO_START by JOB 0
IO DONE
[ time 135 ] Run JOB 1 at PRIORITY 2 [ TICKS 9 ALLOT 1 TIME 36 (of 100) ]
[ time 136 ] Run JOB 1 at PRIORITY 2 [ TICKS 8 ALLOT 1 TIME 35 (of 100) ]
[ time 137 ] Run JOB 1 at PRIORITY 2 [ TICKS 7 ALLOT 1 TIME 34 (of 100) ]
[ time 138 ] Run JOB 1 at PRIORITY 2 [ TICKS 6 ALLOT 1 TIME 33 (of 100) ]
[ time 139 ] Run JOB 1 at PRIORITY 2 [ TICKS 5 ALLOT 1 TIME 32 (of 100) ]
[ time 140 ] IO_DONE by JOB 0
[ time 140 ] Run JOB 1 at PRIORITY 2 [ TICKS 4 ALLOT 1 TIME 31 (of 100) ]
[ time 141 ] Run JOB 1 at PRIORITY 2 [ TICKS 3 ALLOT 1 TIME 30 (of 100) ]
[ time 142 ] Run JOB 1 at PRIORITY 2 [ TICKS 2 ALLOT 1 TIME 29 (of 100) ]
[ time 143 ] Run JOB 1 at PRIORITY 2 [ TICKS 1 ALLOT 1 TIME 28 (of 100) ]
[ time 144 ] IO_START by JOB 1
IO DONE
[ time 144 ] Run JOB 0 at PRIORITY 2 [ TICKS 9 ALLOT 1 TIME 27 (of 100) ]
[ time 145 ] Run JOB 0 at PRIORITY 2 [ TICKS 8 ALLOT 1 TIME 26 (of 100) ]
[ time 146 ] Run JOB 0 at PRIORITY 2 [ TICKS 7 ALLOT 1 TIME 25 (of 100) ]
[ time 147 ] Run JOB 0 at PRIORITY 2 [ TICKS 6 ALLOT 1 TIME 24 (of 100) ]
[ time 148 ] Run JOB 0 at PRIORITY 2 [ TICKS 5 ALLOT 1 TIME 23 (of 100) ]
[ time 149 ] IO_DONE by JOB 1
[ time 149 ] Run JOB 0 at PRIORITY 2 [ TICKS 4 ALLOT 1 TIME 22 (of 100) ]
[ time 150 ] Run JOB 0 at PRIORITY 2 [ TICKS 3 ALLOT 1 TIME 21 (of 100) ]
[ time 151 ] Run JOB 0 at PRIORITY 2 [ TICKS 2 ALLOT 1 TIME 20 (of 100) ]
[ time 152 ] Run JOB 0 at PRIORITY 2 [ TICKS 1 ALLOT 1 TIME 19 (of 100) ]
[ time 153 ] IO_START by JOB 0
IO DONE
[ time 153 ] Run JOB 1 at PRIORITY 2 [ TICKS 9 ALLOT 1 TIME 27 (of 100) ]
[ time 154 ] Run JOB 1 at PRIORITY 2 [ TICKS 8 ALLOT 1 TIME 26 (of 100) ]
[ time 155 ] Run JOB 1 at PRIORITY 2 [ TICKS 7 ALLOT 1 TIME 25 (of 100) ]
[ time 156 ] Run JOB 1 at PRIORITY 2 [ TICKS 6 ALLOT 1 TIME 24 (of 100) ]
[ time 157 ] Run JOB 1 at PRIORITY 2 [ TICKS 5 ALLOT 1 TIME 23 (of 100) ]
[ time 158 ] IO_DONE by JOB 0
[ time 158 ] Run JOB 1 at PRIORITY 2 [ TICKS 4 ALLOT 1 TIME 22 (of 100) ]
[ time 159 ] Run JOB 1 at PRIORITY 2 [ TICKS 3 ALLOT 1 TIME 21 (of 100) ]
[ time 160 ] Run JOB 1 at PRIORITY 2 [ TICKS 2 ALLOT 1 TIME 20 (of 100) ]
[ time 161 ] Run JOB 1 at PRIORITY 2 [ TICKS 1 ALLOT 1 TIME 19 (of 100) ]
[ time 162 ] IO_START by JOB 1
IO DONE
[ time 162 ] Run JOB 0 at PRIORITY 2 [ TICKS 9 ALLOT 1 TIME 18 (of 100) ]
[ time 163 ] Run JOB 0 at PRIORITY 2 [ TICKS 8 ALLOT 1 TIME 17 (of 100) ]
[ time 164 ] Run JOB 0 at PRIORITY 2 [ TICKS 7 ALLOT 1 TIME 16 (of 100) ]
[ time 165 ] Run JOB 0 at PRIORITY 2 [ TICKS 6 ALLOT 1 TIME 15 (of 100) ]
[ time 166 ] Run JOB 0 at PRIORITY 2 [ TICKS 5 ALLOT 1 TIME 14 (of 100) ]
[ time 167 ] IO_DONE by JOB 1
[ time 167 ] Run JOB 0 at PRIORITY 2 [ TICKS 4 ALLOT 1 TIME 13 (of 100) ]
[ time 168 ] Run JOB 0 at PRIORITY 2 [ TICKS 3 ALLOT 1 TIME 12 (of 100) ]
[ time 169 ] Run JOB 0 at PRIORITY 2 [ TICKS 2 ALLOT 1 TIME 11 (of 100) ]
[ time 170 ] Run JOB 0 at PRIORITY 2 [ TICKS 1 ALLOT 1 TIME 10 (of 100) ]
[ time 171 ] IO_START by JOB 0
IO DONE
[ time 171 ] Run JOB 1 at PRIORITY 2 [ TICKS 9 ALLOT 1 TIME 18 (of 100) ]
[ time 172 ] Run JOB 1 at PRIORITY 2 [ TICKS 8 ALLOT 1 TIME 17 (of 100) ]
[ time 173 ] Run JOB 1 at PRIORITY 2 [ TICKS 7 ALLOT 1 TIME 16 (of 100) ]
[ time 174 ] Run JOB 1 at PRIORITY 2 [ TICKS 6 ALLOT 1 TIME 15 (of 100) ]
[ time 175 ] Run JOB 1 at PRIORITY 2 [ TICKS 5 ALLOT 1 TIME 14 (of 100) ]
[ time 176 ] IO_DONE by JOB 0
[ time 176 ] Run JOB 1 at PRIORITY 2 [ TICKS 4 ALLOT 1 TIME 13 (of 100) ]
[ time 177 ] Run JOB 1 at PRIORITY 2 [ TICKS 3 ALLOT 1 TIME 12 (of 100) ]
[ time 178 ] Run JOB 1 at PRIORITY 2 [ TICKS 2 ALLOT 1 TIME 11 (of 100) ]
[ time 179 ] Run JOB 1 at PRIORITY 2 [ TICKS 1 ALLOT 1 TIME 10 (of 100) ]
[ time 180 ] IO_START by JOB 1
IO DONE
[ time 180 ] Run JOB 0 at PRIORITY 2 [ TICKS 9 ALLOT 1 TIME 9 (of 100) ]
[ time 181 ] Run JOB 0 at PRIORITY 2 [ TICKS 8 ALLOT 1 TIME 8 (of 100) ]
[ time 182 ] Run JOB 0 at PRIORITY 2 [ TICKS 7 ALLOT 1 TIME 7 (of 100) ]
[ time 183 ] Run JOB 0 at PRIORITY 2 [ TICKS 6 ALLOT 1 TIME 6 (of 100) ]
[ time 184 ] Run JOB 0 at PRIORITY 2 [ TICKS 5 ALLOT 1 TIME 5 (of 100) ]
[ time 185 ] IO_DONE by JOB 1
[ time 185 ] Run JOB 0 at PRIORITY 2 [ TICKS 4 ALLOT 1 TIME 4 (of 100) ]
[ time 186 ] Run JOB 0 at PRIORITY 2 [ TICKS 3 ALLOT 1 TIME 3 (of 100) ]
[ time 187 ] Run JOB 0 at PRIORITY 2 [ TICKS 2 ALLOT 1 TIME 2 (of 100) ]
[ time 188 ] Run JOB 0 at PRIORITY 2 [ TICKS 1 ALLOT 1 TIME 1 (of 100) ]
[ time 189 ] IO_START by JOB 0
IO DONE
[ time 189 ] Run JOB 1 at PRIORITY 2 [ TICKS 9 ALLOT 1 TIME 9 (of 100) ]
[ time 190 ] Run JOB 1 at PRIORITY 2 [ TICKS 8 ALLOT 1 TIME 8 (of 100) ]
[ time 191 ] Run JOB 1 at PRIORITY 2 [ TICKS 7 ALLOT 1 TIME 7 (of 100) ]
[ time 192 ] Run JOB 1 at PRIORITY 2 [ TICKS 6 ALLOT 1 TIME 6 (of 100) ]
[ time 193 ] Run JOB 1 at PRIORITY 2 [ TICKS 5 ALLOT 1 TIME 5 (of 100) ]
[ time 194 ] IO_DONE by JOB 0
[ time 194 ] Run JOB 1 at PRIORITY 2 [ TICKS 4 ALLOT 1 TIME 4 (of 100) ]
[ time 195 ] Run JOB 1 at PRIORITY 2 [ TICKS 3 ALLOT 1 TIME 3 (of 100) ]
[ time 196 ] Run JOB 1 at PRIORITY 2 [ TICKS 2 ALLOT 1 TIME 2 (of 100) ]
[ time 197 ] Run JOB 1 at PRIORITY 2 [ TICKS 1 ALLOT 1 TIME 1 (of 100) ]
[ time 198 ] IO_START by JOB 1
IO DONE
[ time 198 ] Run JOB 0 at PRIORITY 2 [ TICKS 9 ALLOT 1 TIME 0 (of 100) ]
[ time 199 ] FINISHED JOB 0
[ time 199 ] IDLE
[ time 200 ] IDLE
[ time 201 ] IDLE
[ time 202 ] IDLE
[ time 203 ] IO_DONE by JOB 1
[ time 203 ] Run JOB 1 at PRIORITY 2 [ TICKS 9 ALLOT 1 TIME 0 (of 100) ]
[ time 204 ] FINISHED JOB 1

Final statistics:
  Job  0: startTime   0 - response   0 - turnaround 199
  Job  1: startTime   0 - response   9 - turnaround 204

  Avg  1: startTime n/a - response 4.50 - turnaround 201.50



## Question 5

python3 mlfq.py -j 2 -Q 10,40 -S  -m 10 -l 0,100,0:0,100,0 -B 2 -c  
Here is the list of inputs:
OPTIONS jobs 2
OPTIONS queues 2
OPTIONS allotments for queue  1 is   1
OPTIONS quantum length for queue  1 is  10
OPTIONS allotments for queue  0 is   1
OPTIONS quantum length for queue  0 is  40
OPTIONS boost 2
OPTIONS ioTime 5
OPTIONS stayAfterIO True
OPTIONS iobump False


For each job, three defining characteristics are given:
  startTime : at what time does the job enter the system
  runTime   : the total CPU time needed by the job to finish
  ioFreq    : every ioFreq time units, the job issues an I/O
              (the I/O takes ioTime units to complete)

Job List:
  Job  0: startTime   0 - runTime 100 - ioFreq   0
  Job  1: startTime   0 - runTime 100 - ioFreq   0


Execution Trace:

[ time 0 ] JOB BEGINS by JOB 0
[ time 0 ] JOB BEGINS by JOB 1
[ time 0 ] Run JOB 0 at PRIORITY 1 [ TICKS 9 ALLOT 1 TIME 99 (of 100) ]
[ time 1 ] Run JOB 0 at PRIORITY 1 [ TICKS 8 ALLOT 1 TIME 98 (of 100) ]
[ time 2 ] BOOST ( every 2 )
[ time 2 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 97 (of 100) ]
[ time 3 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 99 (of 100) ]
[ time 4 ] BOOST ( every 2 )
[ time 4 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 96 (of 100) ]
[ time 5 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 98 (of 100) ]
[ time 6 ] BOOST ( every 2 )
[ time 6 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 95 (of 100) ]
[ time 7 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 97 (of 100) ]
[ time 8 ] BOOST ( every 2 )
[ time 8 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 94 (of 100) ]
[ time 9 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 96 (of 100) ]
[ time 10 ] BOOST ( every 2 )
[ time 10 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 93 (of 100) ]
[ time 11 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 95 (of 100) ]
[ time 12 ] BOOST ( every 2 )
[ time 12 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 92 (of 100) ]
[ time 13 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 94 (of 100) ]
[ time 14 ] BOOST ( every 2 )
[ time 14 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 91 (of 100) ]
[ time 15 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 93 (of 100) ]
[ time 16 ] BOOST ( every 2 )
[ time 16 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 90 (of 100) ]
[ time 17 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 92 (of 100) ]
[ time 18 ] BOOST ( every 2 )
[ time 18 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 89 (of 100) ]
[ time 19 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 91 (of 100) ]
[ time 20 ] BOOST ( every 2 )
[ time 20 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 88 (of 100) ]
[ time 21 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 90 (of 100) ]
[ time 22 ] BOOST ( every 2 )
[ time 22 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 87 (of 100) ]
[ time 23 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 89 (of 100) ]
[ time 24 ] BOOST ( every 2 )
[ time 24 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 86 (of 100) ]
[ time 25 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 88 (of 100) ]
[ time 26 ] BOOST ( every 2 )
[ time 26 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 85 (of 100) ]
[ time 27 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 87 (of 100) ]
[ time 28 ] BOOST ( every 2 )
[ time 28 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 84 (of 100) ]
[ time 29 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 86 (of 100) ]
[ time 30 ] BOOST ( every 2 )
[ time 30 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 83 (of 100) ]
[ time 31 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 85 (of 100) ]
[ time 32 ] BOOST ( every 2 )
[ time 32 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 82 (of 100) ]
[ time 33 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 84 (of 100) ]
[ time 34 ] BOOST ( every 2 )
[ time 34 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 81 (of 100) ]
[ time 35 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 83 (of 100) ]
[ time 36 ] BOOST ( every 2 )
[ time 36 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 80 (of 100) ]
[ time 37 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 82 (of 100) ]
[ time 38 ] BOOST ( every 2 )
[ time 38 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 79 (of 100) ]
[ time 39 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 81 (of 100) ]
[ time 40 ] BOOST ( every 2 )
[ time 40 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 78 (of 100) ]
[ time 41 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 80 (of 100) ]
[ time 42 ] BOOST ( every 2 )
[ time 42 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 77 (of 100) ]
[ time 43 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 79 (of 100) ]
[ time 44 ] BOOST ( every 2 )
[ time 44 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 76 (of 100) ]
[ time 45 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 78 (of 100) ]
[ time 46 ] BOOST ( every 2 )
[ time 46 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 75 (of 100) ]
[ time 47 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 77 (of 100) ]
[ time 48 ] BOOST ( every 2 )
[ time 48 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 74 (of 100) ]
[ time 49 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 76 (of 100) ]
[ time 50 ] BOOST ( every 2 )
[ time 50 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 73 (of 100) ]
[ time 51 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 75 (of 100) ]
[ time 52 ] BOOST ( every 2 )
[ time 52 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 72 (of 100) ]
[ time 53 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 74 (of 100) ]
[ time 54 ] BOOST ( every 2 )
[ time 54 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 71 (of 100) ]
[ time 55 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 73 (of 100) ]
[ time 56 ] BOOST ( every 2 )
[ time 56 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 70 (of 100) ]
[ time 57 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 72 (of 100) ]
[ time 58 ] BOOST ( every 2 )
[ time 58 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 69 (of 100) ]
[ time 59 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 71 (of 100) ]
[ time 60 ] BOOST ( every 2 )
[ time 60 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 68 (of 100) ]
[ time 61 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 70 (of 100) ]
[ time 62 ] BOOST ( every 2 )
[ time 62 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 67 (of 100) ]
[ time 63 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 69 (of 100) ]
[ time 64 ] BOOST ( every 2 )
[ time 64 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 66 (of 100) ]
[ time 65 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 68 (of 100) ]
[ time 66 ] BOOST ( every 2 )
[ time 66 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 65 (of 100) ]
[ time 67 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 67 (of 100) ]
[ time 68 ] BOOST ( every 2 )
[ time 68 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 64 (of 100) ]
[ time 69 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 66 (of 100) ]
[ time 70 ] BOOST ( every 2 )
[ time 70 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 63 (of 100) ]
[ time 71 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 65 (of 100) ]
[ time 72 ] BOOST ( every 2 )
[ time 72 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 62 (of 100) ]
[ time 73 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 64 (of 100) ]
[ time 74 ] BOOST ( every 2 )
[ time 74 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 61 (of 100) ]
[ time 75 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 63 (of 100) ]
[ time 76 ] BOOST ( every 2 )
[ time 76 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 60 (of 100) ]
[ time 77 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 62 (of 100) ]
[ time 78 ] BOOST ( every 2 )
[ time 78 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 59 (of 100) ]
[ time 79 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 61 (of 100) ]
[ time 80 ] BOOST ( every 2 )
[ time 80 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 58 (of 100) ]
[ time 81 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 60 (of 100) ]
[ time 82 ] BOOST ( every 2 )
[ time 82 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 57 (of 100) ]
[ time 83 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 59 (of 100) ]
[ time 84 ] BOOST ( every 2 )
[ time 84 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 56 (of 100) ]
[ time 85 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 58 (of 100) ]
[ time 86 ] BOOST ( every 2 )
[ time 86 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 55 (of 100) ]
[ time 87 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 57 (of 100) ]
[ time 88 ] BOOST ( every 2 )
[ time 88 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 54 (of 100) ]
[ time 89 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 56 (of 100) ]
[ time 90 ] BOOST ( every 2 )
[ time 90 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 53 (of 100) ]
[ time 91 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 55 (of 100) ]
[ time 92 ] BOOST ( every 2 )
[ time 92 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 52 (of 100) ]
[ time 93 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 54 (of 100) ]
[ time 94 ] BOOST ( every 2 )
[ time 94 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 51 (of 100) ]
[ time 95 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 53 (of 100) ]
[ time 96 ] BOOST ( every 2 )
[ time 96 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 50 (of 100) ]
[ time 97 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 52 (of 100) ]
[ time 98 ] BOOST ( every 2 )
[ time 98 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 49 (of 100) ]
[ time 99 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 51 (of 100) ]
[ time 100 ] BOOST ( every 2 )
[ time 100 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 48 (of 100) ]
[ time 101 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 50 (of 100) ]
[ time 102 ] BOOST ( every 2 )
[ time 102 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 47 (of 100) ]
[ time 103 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 49 (of 100) ]
[ time 104 ] BOOST ( every 2 )
[ time 104 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 46 (of 100) ]
[ time 105 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 48 (of 100) ]
[ time 106 ] BOOST ( every 2 )
[ time 106 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 45 (of 100) ]
[ time 107 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 47 (of 100) ]
[ time 108 ] BOOST ( every 2 )
[ time 108 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 44 (of 100) ]
[ time 109 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 46 (of 100) ]
[ time 110 ] BOOST ( every 2 )
[ time 110 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 43 (of 100) ]
[ time 111 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 45 (of 100) ]
[ time 112 ] BOOST ( every 2 )
[ time 112 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 42 (of 100) ]
[ time 113 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 44 (of 100) ]
[ time 114 ] BOOST ( every 2 )
[ time 114 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 41 (of 100) ]
[ time 115 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 43 (of 100) ]
[ time 116 ] BOOST ( every 2 )
[ time 116 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 40 (of 100) ]
[ time 117 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 42 (of 100) ]
[ time 118 ] BOOST ( every 2 )
[ time 118 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 39 (of 100) ]
[ time 119 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 41 (of 100) ]
[ time 120 ] BOOST ( every 2 )
[ time 120 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 38 (of 100) ]
[ time 121 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 40 (of 100) ]
[ time 122 ] BOOST ( every 2 )
[ time 122 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 37 (of 100) ]
[ time 123 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 39 (of 100) ]
[ time 124 ] BOOST ( every 2 )
[ time 124 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 36 (of 100) ]
[ time 125 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 38 (of 100) ]
[ time 126 ] BOOST ( every 2 )
[ time 126 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 35 (of 100) ]
[ time 127 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 37 (of 100) ]
[ time 128 ] BOOST ( every 2 )
[ time 128 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 34 (of 100) ]
[ time 129 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 36 (of 100) ]
[ time 130 ] BOOST ( every 2 )
[ time 130 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 33 (of 100) ]
[ time 131 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 35 (of 100) ]
[ time 132 ] BOOST ( every 2 )
[ time 132 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 32 (of 100) ]
[ time 133 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 34 (of 100) ]
[ time 134 ] BOOST ( every 2 )
[ time 134 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 31 (of 100) ]
[ time 135 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 33 (of 100) ]
[ time 136 ] BOOST ( every 2 )
[ time 136 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 30 (of 100) ]
[ time 137 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 32 (of 100) ]
[ time 138 ] BOOST ( every 2 )
[ time 138 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 29 (of 100) ]
[ time 139 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 31 (of 100) ]
[ time 140 ] BOOST ( every 2 )
[ time 140 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 28 (of 100) ]
[ time 141 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 30 (of 100) ]
[ time 142 ] BOOST ( every 2 )
[ time 142 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 27 (of 100) ]
[ time 143 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 29 (of 100) ]
[ time 144 ] BOOST ( every 2 )
[ time 144 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 26 (of 100) ]
[ time 145 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 28 (of 100) ]
[ time 146 ] BOOST ( every 2 )
[ time 146 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 25 (of 100) ]
[ time 147 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 27 (of 100) ]
[ time 148 ] BOOST ( every 2 )
[ time 148 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 24 (of 100) ]
[ time 149 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 26 (of 100) ]
[ time 150 ] BOOST ( every 2 )
[ time 150 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 23 (of 100) ]
[ time 151 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 25 (of 100) ]
[ time 152 ] BOOST ( every 2 )
[ time 152 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 22 (of 100) ]
[ time 153 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 24 (of 100) ]
[ time 154 ] BOOST ( every 2 )
[ time 154 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 21 (of 100) ]
[ time 155 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 23 (of 100) ]
[ time 156 ] BOOST ( every 2 )
[ time 156 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 20 (of 100) ]
[ time 157 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 22 (of 100) ]
[ time 158 ] BOOST ( every 2 )
[ time 158 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 19 (of 100) ]
[ time 159 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 21 (of 100) ]
[ time 160 ] BOOST ( every 2 )
[ time 160 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 18 (of 100) ]
[ time 161 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 20 (of 100) ]
[ time 162 ] BOOST ( every 2 )
[ time 162 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 17 (of 100) ]
[ time 163 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 19 (of 100) ]
[ time 164 ] BOOST ( every 2 )
[ time 164 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 16 (of 100) ]
[ time 165 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 18 (of 100) ]
[ time 166 ] BOOST ( every 2 )
[ time 166 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 15 (of 100) ]
[ time 167 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 17 (of 100) ]
[ time 168 ] BOOST ( every 2 )
[ time 168 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 14 (of 100) ]
[ time 169 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 16 (of 100) ]
[ time 170 ] BOOST ( every 2 )
[ time 170 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 13 (of 100) ]
[ time 171 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 15 (of 100) ]
[ time 172 ] BOOST ( every 2 )
[ time 172 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 12 (of 100) ]
[ time 173 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 14 (of 100) ]
[ time 174 ] BOOST ( every 2 )
[ time 174 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 11 (of 100) ]
[ time 175 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 13 (of 100) ]
[ time 176 ] BOOST ( every 2 )
[ time 176 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 10 (of 100) ]
[ time 177 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 12 (of 100) ]
[ time 178 ] BOOST ( every 2 )
[ time 178 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 9 (of 100) ]
[ time 179 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 11 (of 100) ]
[ time 180 ] BOOST ( every 2 )
[ time 180 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 8 (of 100) ]
[ time 181 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 10 (of 100) ]
[ time 182 ] BOOST ( every 2 )
[ time 182 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 7 (of 100) ]
[ time 183 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 9 (of 100) ]
[ time 184 ] BOOST ( every 2 )
[ time 184 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 6 (of 100) ]
[ time 185 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 8 (of 100) ]
[ time 186 ] BOOST ( every 2 )
[ time 186 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 5 (of 100) ]
[ time 187 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 7 (of 100) ]
[ time 188 ] BOOST ( every 2 )
[ time 188 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 4 (of 100) ]
[ time 189 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 6 (of 100) ]
[ time 190 ] BOOST ( every 2 )
[ time 190 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 3 (of 100) ]
[ time 191 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 5 (of 100) ]
[ time 192 ] BOOST ( every 2 )
[ time 192 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 2 (of 100) ]
[ time 193 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 4 (of 100) ]
[ time 194 ] BOOST ( every 2 )
[ time 194 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 1 (of 100) ]
[ time 195 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 3 (of 100) ]
[ time 196 ] BOOST ( every 2 )
[ time 196 ] Run JOB 0 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 0 (of 100) ]
[ time 197 ] FINISHED JOB 0
[ time 197 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 2 (of 100) ]
[ time 198 ] BOOST ( every 2 )
[ time 198 ] Run JOB 1 at PRIORITY 1 [ TICKS 0 ALLOT 1 TIME 1 (of 100) ]
[ time 199 ] Run JOB 1 at PRIORITY 0 [ TICKS 39 ALLOT 1 TIME 0 (of 100) ]
[ time 200 ] FINISHED JOB 1

Final statistics:
  Job  0: startTime   0 - response   0 - turnaround 197
  Job  1: startTime   0 - response   3 - turnaround 200

  Avg  1: startTime n/a - response 1.50 - turnaround 198.50




## Question 6
python3 mlfq.py -j 5 -Q 10,40 -S  -m 10 -I  -c

With -I flag, turnaround time decreases but the response time increases.




# Chapter 9


## Question 1


python3 lottery.py -j 3 -s 1 -c
ARG jlist 
ARG jobs 3
ARG maxlen 10
ARG maxticket 100
ARG quantum 1
ARG seed 1

Here is the job list, with the run time of each job: 
  Job 0 ( length = 1, tickets = 84 )
  Job 1 ( length = 7, tickets = 25 )
  Job 2 ( length = 4, tickets = 44 )


** Solutions **

Random 651593 -> Winning ticket 119 (of 153) -> Run 2
  Jobs:
 (  job:0 timeleft:1 tix:84 )  (  job:1 timeleft:7 tix:25 )  (* job:2 timeleft:4 tix:44 ) 
Random 788724 -> Winning ticket 9 (of 153) -> Run 0
  Jobs:
 (* job:0 timeleft:1 tix:84 )  (  job:1 timeleft:7 tix:25 )  (  job:2 timeleft:3 tix:44 ) 
--> JOB 0 DONE at time 2
Random 93859 -> Winning ticket 19 (of 69) -> Run 1
  Jobs:
 (  job:0 timeleft:0 tix:--- )  (* job:1 timeleft:7 tix:25 )  (  job:2 timeleft:3 tix:44 ) 
Random 28347 -> Winning ticket 57 (of 69) -> Run 2
  Jobs:
 (  job:0 timeleft:0 tix:--- )  (  job:1 timeleft:6 tix:25 )  (* job:2 timeleft:3 tix:44 ) 
Random 835765 -> Winning ticket 37 (of 69) -> Run 2
  Jobs:
 (  job:0 timeleft:0 tix:--- )  (  job:1 timeleft:6 tix:25 )  (* job:2 timeleft:2 tix:44 ) 
Random 432767 -> Winning ticket 68 (of 69) -> Run 2
  Jobs:
 (  job:0 timeleft:0 tix:--- )  (  job:1 timeleft:6 tix:25 )  (* job:2 timeleft:1 tix:44 ) 
--> JOB 2 DONE at time 6
Random 762280 -> Winning ticket 5 (of 25) -> Run 1
  Jobs:
 (  job:0 timeleft:0 tix:--- )  (* job:1 timeleft:6 tix:25 )  (  job:2 timeleft:0 tix:--- ) 
Random 2106 -> Winning ticket 6 (of 25) -> Run 1
  Jobs:
 (  job:0 timeleft:0 tix:--- )  (* job:1 timeleft:5 tix:25 )  (  job:2 timeleft:0 tix:--- ) 
Random 445387 -> Winning ticket 12 (of 25) -> Run 1
  Jobs:
 (  job:0 timeleft:0 tix:--- )  (* job:1 timeleft:4 tix:25 )  (  job:2 timeleft:0 tix:--- ) 
Random 721540 -> Winning ticket 15 (of 25) -> Run 1
  Jobs:
 (  job:0 timeleft:0 tix:--- )  (* job:1 timeleft:3 tix:25 )  (  job:2 timeleft:0 tix:--- ) 
Random 228762 -> Winning ticket 12 (of 25) -> Run 1
  Jobs:
 (  job:0 timeleft:0 tix:--- )  (* job:1 timeleft:2 tix:25 )  (  job:2 timeleft:0 tix:--- ) 
Random 945271 -> Winning ticket 21 (of 25) -> Run 1
  Jobs:
 (  job:0 timeleft:0 tix:--- )  (* job:1 timeleft:1 tix:25 )  (  job:2 timeleft:0 tix:--- ) 
--> JOB 1 DONE at time 12

➜  CS5600-SCHEDULING git:(main) ✗ python3 lottery.py -j 3 -s 2 -c
ARG jlist 
ARG jobs 3
ARG maxlen 10
ARG maxticket 100
ARG quantum 1
ARG seed 2

Here is the job list, with the run time of each job: 
  Job 0 ( length = 9, tickets = 94 )
  Job 1 ( length = 8, tickets = 73 )
  Job 2 ( length = 6, tickets = 30 )


** Solutions **

Random 605944 -> Winning ticket 169 (of 197) -> Run 2
  Jobs:
 (  job:0 timeleft:9 tix:94 )  (  job:1 timeleft:8 tix:73 )  (* job:2 timeleft:6 tix:30 ) 
Random 606802 -> Winning ticket 42 (of 197) -> Run 0
  Jobs:
 (* job:0 timeleft:9 tix:94 )  (  job:1 timeleft:8 tix:73 )  (  job:2 timeleft:5 tix:30 ) 
Random 581204 -> Winning ticket 54 (of 197) -> Run 0
  Jobs:
 (* job:0 timeleft:8 tix:94 )  (  job:1 timeleft:8 tix:73 )  (  job:2 timeleft:5 tix:30 ) 
Random 158383 -> Winning ticket 192 (of 197) -> Run 2
  Jobs:
 (  job:0 timeleft:7 tix:94 )  (  job:1 timeleft:8 tix:73 )  (* job:2 timeleft:5 tix:30 ) 
Random 430670 -> Winning ticket 28 (of 197) -> Run 0
  Jobs:
 (* job:0 timeleft:7 tix:94 )  (  job:1 timeleft:8 tix:73 )  (  job:2 timeleft:4 tix:30 ) 
Random 393532 -> Winning ticket 123 (of 197) -> Run 1
  Jobs:
 (  job:0 timeleft:6 tix:94 )  (* job:1 timeleft:8 tix:73 )  (  job:2 timeleft:4 tix:30 ) 
Random 723012 -> Winning ticket 22 (of 197) -> Run 0
  Jobs:
 (* job:0 timeleft:6 tix:94 )  (  job:1 timeleft:7 tix:73 )  (  job:2 timeleft:4 tix:30 ) 
Random 994820 -> Winning ticket 167 (of 197) -> Run 2
  Jobs:
 (  job:0 timeleft:5 tix:94 )  (  job:1 timeleft:7 tix:73 )  (* job:2 timeleft:4 tix:30 ) 
Random 949396 -> Winning ticket 53 (of 197) -> Run 0
  Jobs:
 (* job:0 timeleft:5 tix:94 )  (  job:1 timeleft:7 tix:73 )  (  job:2 timeleft:3 tix:30 ) 
Random 544177 -> Winning ticket 63 (of 197) -> Run 0
  Jobs:
 (* job:0 timeleft:4 tix:94 )  (  job:1 timeleft:7 tix:73 )  (  job:2 timeleft:3 tix:30 ) 
Random 444854 -> Winning ticket 28 (of 197) -> Run 0
  Jobs:
 (* job:0 timeleft:3 tix:94 )  (  job:1 timeleft:7 tix:73 )  (  job:2 timeleft:3 tix:30 ) 
Random 268241 -> Winning ticket 124 (of 197) -> Run 1
  Jobs:
 (  job:0 timeleft:2 tix:94 )  (* job:1 timeleft:7 tix:73 )  (  job:2 timeleft:3 tix:30 ) 
Random 35924 -> Winning ticket 70 (of 197) -> Run 0
  Jobs:
 (* job:0 timeleft:2 tix:94 )  (  job:1 timeleft:6 tix:73 )  (  job:2 timeleft:3 tix:30 ) 
Random 27444 -> Winning ticket 61 (of 197) -> Run 0
  Jobs:
 (* job:0 timeleft:1 tix:94 )  (  job:1 timeleft:6 tix:73 )  (  job:2 timeleft:3 tix:30 ) 
--> JOB 0 DONE at time 14
Random 464894 -> Winning ticket 55 (of 103) -> Run 1
  Jobs:
 (  job:0 timeleft:0 tix:--- )  (* job:1 timeleft:6 tix:73 )  (  job:2 timeleft:3 tix:30 ) 
Random 318465 -> Winning ticket 92 (of 103) -> Run 2
  Jobs:
 (  job:0 timeleft:0 tix:--- )  (  job:1 timeleft:5 tix:73 )  (* job:2 timeleft:3 tix:30 ) 
Random 380015 -> Winning ticket 48 (of 103) -> Run 1
  Jobs:
 (  job:0 timeleft:0 tix:--- )  (* job:1 timeleft:5 tix:73 )  (  job:2 timeleft:2 tix:30 ) 
Random 891790 -> Winning ticket 16 (of 103) -> Run 1
  Jobs:
 (  job:0 timeleft:0 tix:--- )  (* job:1 timeleft:4 tix:73 )  (  job:2 timeleft:2 tix:30 ) 
Random 525753 -> Winning ticket 41 (of 103) -> Run 1
  Jobs:
 (  job:0 timeleft:0 tix:--- )  (* job:1 timeleft:3 tix:73 )  (  job:2 timeleft:2 tix:30 ) 
Random 560510 -> Winning ticket 87 (of 103) -> Run 2
  Jobs:
 (  job:0 timeleft:0 tix:--- )  (  job:1 timeleft:2 tix:73 )  (* job:2 timeleft:2 tix:30 ) 
Random 236123 -> Winning ticket 47 (of 103) -> Run 1
  Jobs:
 (  job:0 timeleft:0 tix:--- )  (* job:1 timeleft:2 tix:73 )  (  job:2 timeleft:1 tix:30 ) 
Random 23858 -> Winning ticket 65 (of 103) -> Run 1
  Jobs:
 (  job:0 timeleft:0 tix:--- )  (* job:1 timeleft:1 tix:73 )  (  job:2 timeleft:1 tix:30 ) 
--> JOB 1 DONE at time 22
Random 325143 -> Winning ticket 3 (of 30) -> Run 2
  Jobs:
 (  job:0 timeleft:0 tix:--- )  (  job:1 timeleft:0 tix:--- )  (* job:2 timeleft:1 tix:30 ) 
--> JOB 2 DONE at time 23

➜  CS5600-SCHEDULING git:(main) ✗ python3 lottery.py -j 3 -s 3 -c
ARG jlist 
ARG jobs 3
ARG maxlen 10
ARG maxticket 100
ARG quantum 1
ARG seed 3

Here is the job list, with the run time of each job: 
  Job 0 ( length = 2, tickets = 54 )
  Job 1 ( length = 3, tickets = 60 )
  Job 2 ( length = 6, tickets = 6 )


** Solutions **

Random 13168 -> Winning ticket 88 (of 120) -> Run 1
  Jobs:
 (  job:0 timeleft:2 tix:54 )  (* job:1 timeleft:3 tix:60 )  (  job:2 timeleft:6 tix:6 ) 
Random 837469 -> Winning ticket 109 (of 120) -> Run 1
  Jobs:
 (  job:0 timeleft:2 tix:54 )  (* job:1 timeleft:2 tix:60 )  (  job:2 timeleft:6 tix:6 ) 
Random 259354 -> Winning ticket 34 (of 120) -> Run 0
  Jobs:
 (* job:0 timeleft:2 tix:54 )  (  job:1 timeleft:1 tix:60 )  (  job:2 timeleft:6 tix:6 ) 
Random 234331 -> Winning ticket 91 (of 120) -> Run 1
  Jobs:
 (  job:0 timeleft:1 tix:54 )  (* job:1 timeleft:1 tix:60 )  (  job:2 timeleft:6 tix:6 ) 
--> JOB 1 DONE at time 4
Random 995645 -> Winning ticket 5 (of 60) -> Run 0
  Jobs:
 (* job:0 timeleft:1 tix:54 )  (  job:1 timeleft:0 tix:--- )  (  job:2 timeleft:6 tix:6 ) 
--> JOB 0 DONE at time 5
Random 470263 -> Winning ticket 1 (of 6) -> Run 2
  Jobs:
 (  job:0 timeleft:0 tix:--- )  (  job:1 timeleft:0 tix:--- )  (* job:2 timeleft:6 tix:6 ) 
Random 836462 -> Winning ticket 2 (of 6) -> Run 2
  Jobs:
 (  job:0 timeleft:0 tix:--- )  (  job:1 timeleft:0 tix:--- )  (* job:2 timeleft:5 tix:6 ) 
Random 476353 -> Winning ticket 1 (of 6) -> Run 2
  Jobs:
 (  job:0 timeleft:0 tix:--- )  (  job:1 timeleft:0 tix:--- )  (* job:2 timeleft:4 tix:6 ) 
Random 639068 -> Winning ticket 2 (of 6) -> Run 2
  Jobs:
 (  job:0 timeleft:0 tix:--- )  (  job:1 timeleft:0 tix:--- )  (* job:2 timeleft:3 tix:6 ) 
Random 150616 -> Winning ticket 4 (of 6) -> Run 2
  Jobs:
 (  job:0 timeleft:0 tix:--- )  (  job:1 timeleft:0 tix:--- )  (* job:2 timeleft:2 tix:6 ) 
Random 634861 -> Winning ticket 1 (of 6) -> Run 2
  Jobs:
 (  job:0 timeleft:0 tix:--- )  (  job:1 timeleft:0 tix:--- )  (* job:2 timeleft:1 tix:6 ) 
--> JOB 2 DONE at time 11




## Question 2

 python3 lottery.py -l  10:1,10:100 -c
ARG jlist 10:1,10:100
ARG jobs 3
ARG maxlen 10
ARG maxticket 100
ARG quantum 1
ARG seed 0

Here is the job list, with the run time of each job: 
  Job 0 ( length = 10, tickets = 1 )
  Job 1 ( length = 10, tickets = 100 )


** Solutions **

Random 844422 -> Winning ticket 62 (of 101) -> Run 1
  Jobs:
 (  job:0 timeleft:10 tix:1 )  (* job:1 timeleft:10 tix:100 ) 
Random 757955 -> Winning ticket 51 (of 101) -> Run 1
  Jobs:
 (  job:0 timeleft:10 tix:1 )  (* job:1 timeleft:9 tix:100 ) 
Random 420572 -> Winning ticket 8 (of 101) -> Run 1
  Jobs:
 (  job:0 timeleft:10 tix:1 )  (* job:1 timeleft:8 tix:100 ) 
Random 258917 -> Winning ticket 54 (of 101) -> Run 1
  Jobs:
 (  job:0 timeleft:10 tix:1 )  (* job:1 timeleft:7 tix:100 ) 
Random 511275 -> Winning ticket 13 (of 101) -> Run 1
  Jobs:
 (  job:0 timeleft:10 tix:1 )  (* job:1 timeleft:6 tix:100 ) 
Random 404934 -> Winning ticket 25 (of 101) -> Run 1
  Jobs:
 (  job:0 timeleft:10 tix:1 )  (* job:1 timeleft:5 tix:100 ) 
Random 783799 -> Winning ticket 39 (of 101) -> Run 1
  Jobs:
 (  job:0 timeleft:10 tix:1 )  (* job:1 timeleft:4 tix:100 ) 
Random 303313 -> Winning ticket 10 (of 101) -> Run 1
  Jobs:
 (  job:0 timeleft:10 tix:1 )  (* job:1 timeleft:3 tix:100 ) 
Random 476597 -> Winning ticket 79 (of 101) -> Run 1
  Jobs:
 (  job:0 timeleft:10 tix:1 )  (* job:1 timeleft:2 tix:100 ) 
Random 583382 -> Winning ticket 6 (of 101) -> Run 1
  Jobs:
 (  job:0 timeleft:10 tix:1 )  (* job:1 timeleft:1 tix:100 ) 
--> JOB 1 DONE at time 10
Random 908113 -> Winning ticket 0 (of 1) -> Run 0
  Jobs:
 (* job:0 timeleft:10 tix:1 )  (  job:1 timeleft:0 tix:--- ) 
Random 504687 -> Winning ticket 0 (of 1) -> Run 0
  Jobs:
 (* job:0 timeleft:9 tix:1 )  (  job:1 timeleft:0 tix:--- ) 
Random 281838 -> Winning ticket 0 (of 1) -> Run 0
  Jobs:
 (* job:0 timeleft:8 tix:1 )  (  job:1 timeleft:0 tix:--- ) 
Random 755804 -> Winning ticket 0 (of 1) -> Run 0
  Jobs:
 (* job:0 timeleft:7 tix:1 )  (  job:1 timeleft:0 tix:--- ) 
Random 618369 -> Winning ticket 0 (of 1) -> Run 0
  Jobs:
 (* job:0 timeleft:6 tix:1 )  (  job:1 timeleft:0 tix:--- ) 
Random 250506 -> Winning ticket 0 (of 1) -> Run 0
  Jobs:
 (* job:0 timeleft:5 tix:1 )  (  job:1 timeleft:0 tix:--- ) 
Random 909747 -> Winning ticket 0 (of 1) -> Run 0
  Jobs:
 (* job:0 timeleft:4 tix:1 )  (  job:1 timeleft:0 tix:--- ) 
Random 982786 -> Winning ticket 0 (of 1) -> Run 0
  Jobs:
 (* job:0 timeleft:3 tix:1 )  (  job:1 timeleft:0 tix:--- ) 
Random 810218 -> Winning ticket 0 (of 1) -> Run 0
  Jobs:
 (* job:0 timeleft:2 tix:1 )  (  job:1 timeleft:0 tix:--- ) 
Random 902166 -> Winning ticket 0 (of 1) -> Run 0
  Jobs:
 (* job:0 timeleft:1 tix:1 )  (  job:1 timeleft:0 tix:--- ) 
--> JOB 0 DONE at time 20


Chances are 0 to none that job 0 will run before job 1. In such scenario, lottery scheduling starves the lowest ticket job


## Question 3

Unfairness is relativyly high at first. Unfairness reduces overtime.


## Question 4
Shorter qunatum increases fairness