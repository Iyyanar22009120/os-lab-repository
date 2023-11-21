# os-lab-repository

# OS EX.4-LINUX-COMMANDS
## AIM:
To study and execute basic UNIX commands.

## Software requirements:
Linux operating system.

## COMMAND 1: ls - List Files and Directories
```
Syntax: 
	ls [options] [directory]
Code: 
	ls -l /home/user
Output: 
	List of files and directories in /home/user with details.
```
## COMMAND 2: cd - Change Directory
```
Syntax: 
	cd [directory]
Code: 
	cd /var/www
Output: 
	Change to the /var/www directory.
```
## COMMAND 3: pwd - Print Working Directory
```
Syntax: 
	pwd
Code: 
	pwd
Output: 
	/home/user (prints the current working directory).
```
## COMMAND 4: mkdir - Create Directory
```
Syntax: 
	mkdir [directory]
Code: 
	mkdir my_directory
Output:	
	Creates a new directory named my_directory.
```
## COMMAND 5: touch - Create Empty File
```
Syntax: 
	touch [filename]
Code: 
	touch newfile.txt
Output: 
	Creates a new empty file named newfile.txt.
```
## COMMAND 6: cp - Copy Files and Directories
```
Syntax: 
	cp [options] source destination
Code: 
	cp file.txt /backup/
Output: 
	Copies file.txt to the /backup/ directory.
```
## COMMAND 7: mv - Move/Rename Files and Directories
```
Syntax: 
	mv [options] source destination
Code: 
	mv oldfile.txt newfile.txt
Output: 
	Renames oldfile.txt to newfile.txt.
```
## COMMAND 8: rm - Remove Files and Directories
```
Syntax: 
	rm [options] [file/directory]
Code: 
	rm file.txt
Output: 
	Deletes file.txt.
```
## COMMAND 9: cat - Concatenate and Display File Content
```
Syntax: 
	cat [filename]
Code: 
	cat file.txt
Output: 
	Displays the content of file.txt.
```
## COMMAND 10: more - View File Content Page by Page
```
Syntax: 
	more [filename]
Code: 
	more longfile.txt
Output: 
	Allows you to view the content of longfile.txt one page at a time.
```
## COMMAND 11: less - View File Content with Navigation
```
Syntax: 
	less [filename]
Code: 
	less largefile.txt
Output: 
	Displays largefile.txt with navigation capabilities.
```
## COMMAND 12: head - Display Top Lines of a File
```
Syntax: 
	head [options] [filename]
Code: 
	head -n 5 file.txt
Output: 
	Shows the first 5 lines of file.txt.
```
## COMMAND 13: tail - Display Bottom Lines of a File
```
Syntax: 
	tail [options] [filename]
Code: 
	tail -n 10 file.log
Output: 
	Shows the last 10 lines of file.log.
```
## COMMAND 14: grep - Search Text in Files
```
Syntax: 
	grep [options] 'pattern' [file(s)]
Code: 
	grep 'keyword' file.txt
Output: 
	Lists lines containing 'keyword' in file.txt.
```
## COMMAND 15: find - Search for Files and Directories
```
Syntax:
	find [path] [expression]
Code: 
	find /home/user -name '*.txt'
Output: 
	Finds all .txt files under /home/user.
```
## COMMAND 16: chmod - Change File Permissions
```
Syntax: 
	chmod [options] permissions file(s)
Code: 
	chmod 644 file.txt
Output: 
	Sets read and write permissions for the owner and read-only permissions for others on file.txt.
```
## COMMAND 17: chown - Change File Ownership
```
Syntax: 
	chown [options] user:group file(s)
Code: 
	chown user:group file.txt
Output: 
	Changes the owner and group of file.txt.
```
## COMMAND 18: tar - Archive and Compress Files
```
Syntax: 
	tar [options] [file(s)]
Code: 
	tar -cvzf archive.tar.gz dir/
Output: 
	Creates a compressed archive of the dir/ directory.
```
## COMMAND 19: df - Display Disk Space Usage
```
Syntax: 
	df [options] [filesystem(s)]
Code: 
	df -h
Output: 
	Shows disk space usage in a human-readable format.
```
## COMMAND 20: du - Display Directory Space Usage
```
Syntax: 
	du [options] [directory]
Code: 
	du -sh /var
Output: 
	Displays the total size of the /var directory in a human-readable format.
```
## COMMAND 21: ps - Display Process Status
```
Syntax: 
	ps [options]
Code: 
	ps aux
Output: 
	Lists running processes with details.
```
## COMMAND 22: kill - Terminate Processes
```
Syntax: 
	kill [signal] [PID]
Code: 
	kill -9 1234
Output: 
	Sends a SIGKILL signal to process with PID 1234.
```
## COMMAND 23: ssh - Secure Shell
```
Syntax: 
	ssh [user@]hostname
Code: 
	ssh user@remote-server
Output: 
	Establishes a secure remote connection to remote-server.
```
## COMMAND 24: scp - Securely Copy Files Over SSH
```
Syntax:
	scp [options] source destination
Code: 
	scp file.txt user@remote-server:/path/
Output: 
	Copies file.txt to a remote server over SSH.
```
## COMMAND 25: wget - Download Files from the Internet
```
Syntax: 
	wget [options] [URL]
Code: 
	wget https://example.com/file.zip
Output: 
	Downloads file.zip from the specified URL.
```
## RESULT:
Thus basic UNIX commands are studied and executed.

 # EX.5-IMPLEMENTATION-OF-CPU-SCHEDULING-ALGORITHMS
# FIRST COME FIRST SERVE SCHEDULING
 
## AIM:
To implement First-Come-First-Serve (FCFS) Scheduling

## ALGORITHM:

1. Start the process
2. Get the number of processes to be inserted
3. Get the value for burst time of each process from the user
4. Having allocated the burst time(bt) for individual processes , Start with the first
process from its initial position let other process to be in queue
5. Calculate the waiting time(wt) and turnaround time(tat) as
6. Wt(pi) = wt(pi-1) + tat(pi-1) (i.e. wt of current process = wt of previous process + tat of
previous process)
7. tat(pi) = wt(pi) + bt(pi) (i.e. tat of current process = wt of current process + bt of
current process)
8. Calculate the total and average waiting time and turnaround time
9. Display the values
10. Stop the process



## PROGRAM:
```C
#include<stdio.h>
int main()
{
	int bt[20],p[20],wt[20],tat[20],i,j,n,total=0,pos,temp; float
	avg_wt,avg_tat;
	printf("Enter number of process:");
	scanf("%d",&n);
	printf("\nEnter Burst Time:\n");
	for(i=0;i<n;i++)
	{
		printf("p % d:",i+1);
		scanf("%d",&bt[i]);
		p[i]=i+1; //contains process number
	}
	wt[0]=0; //waiting time for first process will be zero
	//calculate waiting time
	for(i=1;i<n;i++)
	{
		wt[i]=0;
		for(j=0;j<i;j++)
		wt[i]+=bt[j];
		total+=wt[i];
	}
	avg_wt=(float)total/n; //average waiting time
	total=0;
	printf("\nProcess\t Burst Time \tWaiting Time\tTurnaround Time");
	for(i=0;i<n;i++)
	{
		tat[i]=bt[i]+wt[i]; //calculate turnaround time
		total+=tat[i];
		printf("\np%d\t\t %d\t\t %d\t\t\t%d",p[i],bt[i],wt[i],tat[i]);
	}
	avg_tat=(float)total/n; //average turnaround time
	printf("\n\nAverage Waiting Time=%f",avg_wt);
	printf("\nAverage Turnaround Time=%f\n",avg_tat);
}

```



## OUTPUT:
![WhatsApp Image 2023-10-05 at 00 51 35_ac3f727a](https://github.com/Jayabharathi3/EX.5-IMPLEMENTATION-OF-CPU-SCHEDULING-ALGORITHMS/assets/120367796/ebea4825-8bee-409f-a16c-639496fd9faa)


## RESULT: 
First-Come-First-Serve Scheduling is implemented successfully.


# SHORTEST JOB FIRST  PREEMPTIVE SCHEDULING

## AIM:
To implement Shortest Job First (SJF) Preemptive Scheduling

## ALGORITHM:

1. Start the process
2. Get the number of processes to be inserted
3. Sort the processes according to the burst tiine and allocate the one with shortest burst to
execute first
4. If two process have same burst length then FCFS scheduling algorithm is used
5. Calculate the total and average waiting time and turn around time
6. Display the values
7. Stop the process



## PROGRAM:
```C

#include <stdio.h>
  
int main() 
{
      int arrival_time[10], burst_time[10], temp[10];
      int i, smallest, count = 0, time, limit;
      double wait_time = 0, turnaround_time = 0, end;
      float average_waiting_time, average_turnaround_time;
      printf("nEnter the Total Number of Processes:t");
      scanf("%d", &limit); 
      printf("nEnter Details of %d Processesn", limit);
      for(i = 0; i < limit; i++)
      {
            printf("nEnter Arrival Time:t");
            scanf("%d", &arrival_time[i]);
            printf("Enter Burst Time:t");
            scanf("%d", &burst_time[i]); 
            temp[i] = burst_time[i];
      }
      burst_time[9] = 9999;  
      for(time = 0; count != limit; time++)
      {
            smallest = 9;
            for(i = 0; i < limit; i++)
            {
                  if(arrival_time[i] <= time && burst_time[i] < burst_time[smallest] && burst_time[i] > 0)
                  {
                        smallest = i;
                  }
            }
            burst_time[smallest]--;
            if(burst_time[smallest] == 0)
            {
                  count++;
                  end = time + 1;
                  wait_time = wait_time + end - arrival_time[smallest] - temp[smallest];
                  turnaround_time = turnaround_time + end - arrival_time[smallest];
            }
      }
      average_waiting_time = wait_time / limit; 
      average_turnaround_time = turnaround_time / limit;
      printf("nnAverage Waiting Time:t%lfn", average_waiting_time);
      printf("Average Turnaround Time:t%lfn", average_turnaround_time);
      return 0;
}

```


## OUTPUT:

![image](https://github.com/Jayabharathi3/EX.5-IMPLEMENTATION-OF-CPU-SCHEDULING-ALGORITHMS/assets/120367796/a2c7aeac-d6f7-4594-810a-8cea3bf0628a)



## RESULT:
Shortest Job First (SJF) preemptive scheduling is implemented successfully.

# SHORTEST JOB FIRST NON - PREEMPTIVE SCHEDULING
## AIM:
To implement Shortest Job First (SJF) Non-Preemptive Scheduling

## ALGORITHM:

1. Start the process
2. Get the number of processes to be inserted
3. Get the corresponding priority of processes
4. Sort the processes according to the priority and allocate the one with highest priority
to execute first
5. If two process have same priority then FCFS scheduling algorithm is used
6. Calculate the total and average waiting time and turnaround time
7. Display the values
8. Stop the process



## PROGRAM:
```C

#include<stdio.h>
 int main()
{
    int bt[20],p[20],wt[20],tat[20],i,j,n,total=0,pos,temp;
    float avg_wt,avg_tat;
    printf("Enter number of process:");
    scanf("%d",&n);
  
    printf("\nEnter Burst Time:");
    for(i=0;i<n;i++)
    {
        printf("\np%d:",i+1);
        scanf("%d",&bt[i]);
        p[i]=i+1;         
    }
  
   //sorting of burst times
    for(i=0;i<n;i++)
    {
        pos=i;
        for(j=i+1;j<n;j++)
        {
            if(bt[j]<bt[pos])
                pos=j;
        }
  
        temp=bt[i];
        bt[i]=bt[pos];
        bt[pos]=temp;
  
        temp=p[i];
        p[i]=p[pos];
        p[pos]=temp;
    }
   
    wt[0]=0;            
  
   
    for(i=1;i<n;i++)
    {
        wt[i]=0;
        for(j=0;j<i;j++)
            wt[i]+=bt[j];
  
        total+=wt[i];
    }
  
    avg_wt=(float)total/n;      
    total=0;
  
    printf("\nProcess    Burst Time    Waiting Time   Turn around Time"); 
    for(i=0;i<n;i++)
    {
        tat[i]=bt[i]+wt[i];   
        total+=tat[i];
        printf("\n%d   %d   %d   %d",p[i],bt[i],wt[i],tat[i]);
    }
  
    avg_tat=(float)total/n;    
    printf("\nAverage Waiting Time=%f",avg_wt);
    printf("\nAverage Turnaround Time=%f",avg_tat);
}
```


## OUTPUT:
![image](https://github.com/Jayabharathi3/EX.5-IMPLEMENTATION-OF-CPU-SCHEDULING-ALGORITHMS/assets/120367796/572eb999-78e6-4cf2-9236-9d559f2e46f7)


## RESULT:
Shortest Job First (SJF) Non-preemptive scheduling is implemented successfully.


# ROUND ROBIN SCHEDULING

## AIM:
To implement Round Robin (RR) Scheduling

## ALGORITHM:

1. Start the process
2. Get the number of elements to be inserted
3. Get the value for burst time for individual processes
4. Get the value for time quantum
5. Make the CPU scheduler go around the ready queue allocating CPU to each process
for the time interval specified
6. Make the CPU scheduler pick the first process and set time to interrupt after quantum.
And after it's expiry dispatch the process
7. If the process has burst time less than the time quantum then the process is released by
the CPU
8. If the process has burst time greater than time quantum then it is interrupted by the OS
and the process is put to the tail of ready queue and the schedule selects next
process from head of the queue
9. Calculate the total and average waiting time and turnaround time
10. Display the results


## PROGRAM:
```C

#include<stdio.h>
int main()
{
    int st[10],bt[10],wt[10],tat[10],n,tq; 
    int i,count=0,swt=0,stat=0,temp,sq=0;
    float awt,atat;
    printf("Enter the number of processes :");
    scanf("%d",&n);
    printf("\nEnter the burst time of each process: ");
    for(i=0;i<n;i++)
    {
        printf("\np%d",i+1);
        scanf("%d",&bt[i]);
        st[i]=bt[i];
        
    }
    printf("\nenter the time quantum");
    scanf("%d",&tq);
    while(1)
    {
        for(i=0,count=0;i<n;i++)
        {
            temp=tq;
            if(st[i]==0)
            {
                count++;
                continue;
                
            }
            if(st[i]>tq)
            st[i]=st[i]-tq;
            else
            if(st[i]>=0)
            {
                temp=st[i];
                st[i]=0;
                
            }
            sq=sq+temp;
            tat[i]=sq;
            
        }
        if(n==count)
        break;
        
    }
    for(i=0;i<n;i++)
    {
        wt[i]=tat[i]-bt[i];
        swt=swt+wt[i];
        stat=stat+tat[i];
        
    }
    awt=(float)swt/n;
    atat=(float)stat/n;
    printf("\nprocess no\t burst time\t waiting time\t turnaround time\n");
    for(i=0;i<n;i++)
    printf("\n%d\t\t %d\t\t %d\t\t %d\n",i+1,bt[i],wt[i],tat[i]); 
    printf("\nAverage waiting time=%f\nAverage turn around time=%f",awt,atat);
}

```


OUTPUT:

![image](https://github.com/Jayabharathi3/EX.5-IMPLEMENTATION-OF-CPU-SCHEDULING-ALGORITHMS/assets/120367796/012fad3b-d043-4651-ad22-8a4b0350ef36)



RESULT: Round Robin (RR) Scheduling is implemented successfully.


# PRIORITY PREEMPTIVE SCHEDULING

## AIM: 
 To implement Priority Preemptive Scheduling

## ALGORITHM:
1. Start the process
2. Get the number of processes to be inserted
3. Get the corresponding priority of processes
4. Sort the processes according to the priority and allocate the one with highest priority
to execute first
5. If two process have same priority then FCFS scheduling algorithm is used
6. Calculate the total and average waiting time and turnaround time
7. Display the values
8. Stop the process

## PROGRAM:

```C
#include<stdio.h>
struct process
{
    int WT,AT,BT,TAT,PT;
};

struct process a[10];

int main()
{
    int n,temp[10],t,count=0,short_p;
    float total_WT=0,total_TAT=0,Avg_WT,Avg_TAT;
    printf("Enter the number of the process\n");
    scanf("%d",&n);
    printf("Enter the arrival time , burst time and priority of the process\n");
    printf("AT BT PT\n");
    for(int i=0;i<n;i++)
    {
        scanf("%d%d%d",&a[i].AT,&a[i].BT,&a[i].PT);
        
        // copying the burst time in
        // a temp array fot futher use
        temp[i]=a[i].BT;
    }
    
    // we initialize the burst time
    // of a process with maximum 
    a[9].PT=10000;
    
    for(t=0;count!=n;t++)
    {
        short_p=9;
        for(int i=0;i<n;i++)
        {
            if(a[short_p].PT>a[i].PT && a[i].AT<=t && a[i].BT>0)
            {
                short_p=i;
            }
        }
        
        a[short_p].BT=a[short_p].BT-1;
        
        // if any process is completed
        if(a[short_p].BT==0)
        {
            // one process is completed
            // so count increases by 1
            count++;
            a[short_p].WT=t+1-a[short_p].AT-temp[short_p];
            a[short_p].TAT=t+1-a[short_p].AT;
            
            // total calculation
            total_WT=total_WT+a[short_p].WT;
            total_TAT=total_TAT+a[short_p].TAT;
            
        }
    }
    
    Avg_WT=total_WT/n;
    Avg_TAT=total_TAT/n;
    
    // printing of the answer
    printf("ID WT TAT\n");
    for(int i=0;i<n;i++)
    {
        printf("%d %d\t%d\n",i+1,a[i].WT,a[i].TAT);
    }
    
    printf("Avg waiting time of the process  is %f\n",Avg_WT);
    printf("Avg turn around time of the process is %f\n",Avg_TAT);
    
    return 0;
}

```

## OUTPUT:

![image](https://github.com/Jayabharathi3/EX.5-IMPLEMENTATION-OF-CPU-SCHEDULING-ALGORITHMS/assets/120367796/97ea080d-abf0-4323-b96d-aa7b7abfe0fc)


## RESULT: Priority Preemptive scheduling is implemented successfully.


# PRIORITY NON - PREEMPTIVE SCHEDULING
## AIM:
To implement Priority Non-Preemptive Scheduling

## ALGORITHM:
1. Start the process
2. Get the number of processes to be inserted
3. Get the corresponding priority of processes
4. Sort the processes according to the priority and allocate the one with highest priority
to execute first
5. If two process have same priority then FCFS scheduling algorithm is used
6. Calculate the total and average waiting time and turnaround time
7. Display the values
8. Stop the process


## PROGRAM:
```C
#include<stdio.h>
 
int main()
{
    int bt[20],p[20],wt[20],tat[20],pr[20],i,j,n,total=0,pos,temp,avg_wt,avg_tat;
    printf("Enter Total Number of Process:");
    scanf("%d",&n);
 
    printf("\nEnter Burst Time and Priority\n");
    for(i=0;i<n;i++)
    {
        printf("\nP[%d]\n",i+1);
        printf("Burst Time:");
        scanf("%d",&bt[i]);
        printf("Priority:");
        scanf("%d",&pr[i]);
        p[i]=i+1;           
    }
 
    //sorting burst time, priority and process number in ascending order using selection sort
    for(i=0;i<n;i++)
    {
        pos=i;
        for(j=i+1;j<n;j++)
        {
            if(pr[j]<pr[pos])
                pos=j;
        }
 
        temp=pr[i];
        pr[i]=pr[pos];
        pr[pos]=temp;
 
        temp=bt[i];
        bt[i]=bt[pos];
        bt[pos]=temp;
 
        temp=p[i];
        p[i]=p[pos];
        p[pos]=temp;
    }
 
    wt[0]=0;	//waiting time for first process is zero
 
    //calculate waiting time
    for(i=1;i<n;i++)
    {
        wt[i]=0;
        for(j=0;j<i;j++)
            wt[i]+=bt[j];
 
        total+=wt[i];
    }
 
    avg_wt=total/n;      //average waiting time
    total=0;
 
    printf("\nProcess\t    Burst Time    \tWaiting Time\tTurnaround Time");
    for(i=0;i<n;i++)
    {
        tat[i]=bt[i]+wt[i];     //calculate turnaround time
        total+=tat[i];
        printf("\nP[%d]\t\t  %d\t\t    %d\t\t\t%d",p[i],bt[i],wt[i],tat[i]);
    }
 
    avg_tat=total/n;     //average turnaround time
    printf("\n\nAverage Waiting Time=%d",avg_wt);
    printf("\nAverage Turnaround Time=%d\n",avg_tat);
 
	return 0;
}
```

## OUTPUT:

![image](https://github.com/Jayabharathi3/EX.5-IMPLEMENTATION-OF-CPU-SCHEDULING-ALGORITHMS/assets/120367796/64eb71af-05b2-4770-a6a1-0972742acc48)



## RESULT:
Priority Non-preemptive scheduling is implemented successfully.


# OS-EX.6-IMPLEMENTATION-OF-INTER-PROCESS-COMMUNICATION-USING-PIPE

## AIM:

Write C programs to illustrate IPC using pipes mechanisms

## ALGORITHM: IPC using pipes

Create a child process usingfork()

Create a simple pipe with C, we make use of the pipe() systemcall.

Create two file descriptor fd[0] is set up for reading, fd[1] isset up forwriting

Close the read end of parent process using close() and perform writeoperation

Close the write end of child process and performreading

Display thetext.

## PROGRAM:
```
#include <stdio.h>

int main()

{

int fd[2],child; char a[20];

printf("\n Enter the string:");

scanf("%s",a);

pipe(fd);

child=fork();

if(!child)

{

close(fd[0]);

write(fd[1],a,5); wait(0);

}

else

{

close(fd[1]);

read(fd[0],a,5); printf("The string received from pipe is: %s",a);

}

return 0;

}

```
## OUTPUT:

![Screenshot (121)](https://github.com/JAYAVARTHAN-P/OS-EX.6-IMPLEMENTATION-OF-INTER-PROCESS-COMMUNICATION-USING-PIPE/assets/121369281/55ca7ffc-e720-4a0f-b756-dda1066c1e6c)


## RESULT: 
Thus, IPC using pipes mechanisms is illustrated using c program successfully

# EX.7-IMPLEMENTATION-OF-SYSTEM-CALLS-READ-WRITE-FORK-OPEN-CLOSE

## AIM:
 C program using open, read, write, close , create , fork() system calls

## THEORY :

There are 5 basic system calls that Unix provides for file I/O.

**1.Create:**
Used to Create a new empty file
Syntax :int creat(char *filename, mode_t mode)
filename : name of the file which you want to create
mode : indicates permissions of new file.

**2. open:** 
Used to Open the file for reading, writing or both.
Syntax: int open(char *path, int flags [ , int mode ] );
Path : path to file which you want to use
flags : How you like to use
O_RDONLY: read only, O_WRONLY: write only, O_RDWR: read and write, O_CREAT: create
file if it doesn’t exist, O_EXCL: prevent creation if it already exists

**3. close:** 
Tells the operating system you are done with a file descriptor and Close the file which
pointed by fd.
Syntax: int close(int fd);fd :file
descriptor

**4. read:**
From the file indicated by the file descriptor fd, the read() function reads cnt bytes of input 
into the memory area indicated by buf. A successful read() updates the access time for thefile.
Syntax: int read(int fd, char *buf, int size);
fd: file descripter
buf: buffer to read data from
cnt: length of buffer

**5.write:**
Writes cnt bytes from buf to the file or socket associated with fd. cnt should not begreater
than INT_MAX (defined in the limits.h header file). If cnt is zero, write()simply returns 0without
attempting any other action.
Syntax: int write(int fd, char *buf, int size);fd: file
descripter
buf: buffer to write data to
cnt: length of buffer
*File descriptor is integer that uniquely identifies an open file of the process.


## ALGORITHM:

1. Star the program.
2. Open a file for O_RDWR for R/W,O_CREATE for creating a file ,O_TRUNC for truncate
a file.
3. Using getchar(), read the character and stored in the string[] array.
4. The string [] array is write into a file close it.
5. Then the first is opened for read only mode and read the characters and displayed it and
close the file.
6. Use Fork().
7. Stop the program.

## PROGRAM:
```C
#include<sys/stat.h> 
#include<stdio.h> 
#include<fcntl.h> 
#include<sys/types.h> 
int main() 
{ 
    int n,i=0; 
    int f1,f2; 
    char c,strin[100]; 
    f1=open("data",O_RDWR|O_CREAT|O_TRUNC); 
    while((c=getchar())!='\n') 
    { 
        strin[i++]=c; 
 
    } 
    strin[i]='\0'; 
    write(f1,strin,i); 
    close(f1); 
    f2=open("data",O_RDONLY); 
    read(f2,strin,0); 
    printf("\n%s\n",strin); 
    close(f2); 
    fork(); 
    return 0; 
 
}

```

## OUTPUT:
![image](https://github.com/Jayabharathi3/EX.7-IMPLEMENTATION-OF-SYSTEM-CALLS-READ-WRITE-FORK-OPEN-CLOSE/assets/120367796/d4cde5a3-128e-499e-8a7b-144694d881fb)



## RESULT:
   Thus, open, read, write, close , create , fork() system calls implemented successfully using c
program.

# OS-EX.8-IMPLEMENTATION-OF-BANKER-S-ALGORITHM

## AIM:
To implement the bankers Algorithm 
## ALGORITHM:
### Step 1: Initialize Data
* Set n to 5 (number of processes) and m to 3 (number of resource types).
* Initialize the alloc matrix with the allocation of resources to processes.
* Initialize the max matrix with the maximum demand of resources for each process.
* Initialize the avail list with the available resources.
* Initialize arrays f, ans, and ind to manage process states and safe sequence.
### Step 2: Initialize Flags and Need Matrix
* Initialize the array f to keep track of whether each process is finished (all initially set to 0).
* Create an empty matrix need to represent the resource needs of each process.
### Step 3: Calculate Need Matrix
* Calculate the need matrix by subtracting the alloc matrix from the max matrix for each process and resource.
### Step 4: Main Loop
* Loop k from 0 to 4 (5 iterations, one for each process).
* Inside the loop:
* Loop through each process i (0 to 4).
* Check if process i is not finished (f[i] == 0).
* Initialize flag to 0.
* Loop through each resource type j (0 to 2).
* Check if the resource need of process i for resource j exceeds the available resource avail[j].
* If it does, set flag to 1 and break out of the inner loop.
* If flag is still 0 (i.e., all resource needs are satisfied), add process i to the ans array and increment ind.
* Update the available resources by adding the allocated resources of process i to avail.
* Mark process i as finished by setting f[i] to 1.
### Step 5: Print the SAFE Sequence
* Print "Following is the SAFE Sequence" as a header.
* Loop through the processes in the ans array and print them as the safe sequence, separated by " -> ".
* Print the last process in the sequence.
## PROGRAM:
```
n = 5
m = 3

alloc = [[0, 1, 0 ],[ 2, 0, 0 ],
        [3, 0, 2 ],[2, 1, 1] ,[ 0, 0, 2]]

max = [[7, 5, 3 ],[3, 2, 2 ],
        [ 9, 0, 2 ],[2, 2, 2],[4, 3, 3]]

avail = [3, 3, 2]

f = [0]*n
ans = [0]*n
ind = 0

for k in range(n):
    f[k] = 0

need = [[ 0 for i in range(m)]for i in range(n)]
for i in range(n):
    for j in range(m):
        need[i][j] = max[i][j] - alloc[i][j]
y = 0
for k in range(5):
    for i in range(n):
        if (f[i] == 0):
            flag = 0
            for j in range(m):
                if (need[i][j] > avail[j]):
                    flag = 1
                    break

            if (flag == 0):
                ans[ind] = i
                ind += 1
                for y in range(m):
                    avail[y] += alloc[i][y]
                f[i] = 1

print("Following is the SAFE Sequence")

for i in range(n - 1):
    print(" P", ans[i], " ->", sep="", end="")
print(" P", ans[n - 1], sep="")

```
## OUTPUT:
![Screenshot (215)](https://github.com/Dhivya-bharathi88/OS-EX.8-IMPLEMENTATION-OF-BANKER-S-ALGORITHM/assets/128019999/c2d947b5-3fd7-4db4-9a9b-49bac06f872e)

## RESULT:
Thus the program for the bankers algorithm is implemented successfully.


 # EX.9 IMPLEMENTATION OF PAGING MEMORY MANAGEMENT

## AIM:

  To write a c program to implement Paging technique for memory management.


## ALGORITHM:

  1. Read all the necessary input from the keyboard.
  2. Pages - Logical memory is broken into fixed - sized blocks.
  3. Frames – Physical memory is broken into fixed – sized blocks.
  4. Calculate the physical address using the logical address
  5. Physical address = (Frame number * Frame size) + offset
  6. Display the physical address.
  7. Stop the process

## PROGRAM:
```
#include<stdio.h>
#include<conio.h>
int main()
{
int ms, ps, nop, np, rempages, i, j, x, y, pa, offset;
int s[10], fno[10][20];
printf("\nEnter the memory size -- ");
scanf("%d",&ms);
printf("\nEnter the page size -- ");
scanf("%d",&ps);
nop = ms/ps;
printf("\nThe no. of pages available in memory are -- %d ",nop);
printf("\nEnter number of processes -- ");
scanf("%d",&np);
rempages = nop;
for(i=1;i<=np;i++)
{
printf("\nEnter no. of pages required for p[%d]-- ",i);
scanf("%d",&s[i]);
if(s[i] >rempages)
{
printf("\nMemory is Full");
break;
}
rempages = rempages - s[i];
printf("\nEnter pagetable for p[%d] --- ",i);
for(j=0;j<s[i];j++)
scanf("%d",&fno[i][j]);
}
printf("\nEnter Logical Address to find Physical Address ");
printf("\nEnter process no. and page number and offset -- ");
scanf("%d %d %d",&x,&y, &offset);
if(x>np || y>=s[i] || offset>=ps)
printf("\nInvalid Process or Page Number or offset");
else
{ pa=fno[x][y]*ps+offset;
printf("\nThe Physical Address is -- %d",pa);
}
getch();
}
```
## OUTPUT:

![Screenshot (406)](https://github.com/Dhivya-bharathi88/OS-EX.9-IMPLEMENTATION-OF-PAGING---MEMORY-MANAGEMENT-/assets/128019999/cac10bc2-de23-4ee0-8ab9-9486504aa28d)


## RESULT:

  Thus the implementation of paging technique for memory management is executed successfully.
  
  
  # EX.10 IMPLEMENTATION OF PAGE REPLACEMENT ALGORITHMS

## AIM:
  To write a C program to implement Page Replacement technique using FIFO


## ALGORITHM:

1. Start the program.
2. Get the number of pages and their sequence from the user
3. Get the number of available page frames from the user.
4. In FIFO, on the basics of first in first out, replace the pages respectively, then
find number of page faults occurred.
5. Compare all frames with incoming page6. If the incoming page is already available in page frame, set the match flag to
indicate ‘no need of page replacement’.
7. If the incoming page is not available in all frames, then remove the page
which is loaded into the memory long back and give space for new incoming
page.
8. Increment the ‘number of Page faults counter
9. Print the number of page faults.
10. Stop the program.


## PROGRAM:
```
#include<stdio.h>
int main()
{
int i,j,n,a[50],frame[10],no,k,avail,count=0;
printf("\n ENTER THE NUMBER OF PAGES:\n");
scanf("%d",&n);
printf("\n ENTER THE PAGE NUMBER :\n");
for(i=1;i<=n;i++)
scanf("%d",&a[i]);
printf("\n ENTER THE NUMBER OF FRAMES :");
scanf("%d",&no);
for(i=0;i<no;i++)
frame[i]= -1;
j=0;
printf("\tRef string\t Page Frames\n");
for(i=1;i<=n;i++)
{
printf("%d\t\t\t",a[i]);
avail=0;
for(k=0;k<no;k++)
if(frame[k]==a[i])
avail=1;
if (avail==0)
{
frame[j]=a[i];
j=(j+1)%no;
count++;
for(k=0;k<no;k++)
printf("%d\t",frame[k]);
}
printf("\n");
}
printf("\nPage Fault Is %d",count);
return 0;
}
```

## OUTPUT:

![Screenshot (407)](https://github.com/Dhivya-bharathi88/OS-EX.10-IMPLEMENTATION-OF-PAGE-REPLACEMENT-ALGORITHMS/assets/128019999/3e059f35-b0e0-4b76-94c2-9a31c76ad42b)


## RESULT:

  Thus the implementation of FIFO page replacement is successfully executed.

# PAGE REPLACEMENT ALGORITHM (LRU)

## AIM:
  To write a C program to implement Page Replacement technique using LRU

## ALGORITHM:

1. Start the program
2. Get the number of pages and their sequence from theuser
3. Get the number of available page frames from theuser.
4. In LRU replace the page that has not been used for the longest period oftime.
5. Compare all frames with incoming page6. If the incoming page is already available in page frame, set the match flag to
indicate ‘no need of page replacement’.
7. If the incoming page is not available in all frames, then remove the page which
has not been used for the longest period oftime.
8. Increment the ‘number of Page faults’ counter
9. Print the number of page faults.
10. Stop the program.

## PROGRAM:
```
#include<stdio.h>
main()
{
int q[20],p[50],c=0,c1,d,f,i,j,k=0,n,r,t,b[20],c2[20];
printf("Enter no of pages: \n");
scanf("%d",&n);
printf("Enter the reference string: \n");
for(i=0;i<n;i++)
scanf("%d",&p[i]);
printf("Enter no of frames: \n");
scanf("%d",&f);
q[k]=p[k];
printf("\t\n\t %d\n",q[k]);
c++;
k++;
for(i=1;i<n;i++)
{
c1=0;
for(j=0;j<f;j++)
{
if(p[i]!=q[j])
c1++;
}
if(c1==f)
{
c++;
if(k<f)
{
q[k]=p[i];
k++;
for(j=0;j<k;j++)
printf("\t%d",q[j]);
printf("\n");
}
else
{
for(r=0;r<f;r++)
{
c2[r]=0;
for(j=i-1;j<n;j--)
{
if(q[r]!=p[j])
c2[r]++;
else
break;
}
}
for(r=0;r<f;r++)
b[r]=c2[r];
for(r=0;r<f;r++)
{
for(j=r;j<f;j++)
{
if(b[r]<b[j])
{
t=b[r];
b[r]=b[j];
b[j]=t;
}
}
}
for(r=0;r<f;r++)
{
if(c2[r]==b[0])
q[r]=p[i];
printf("\t%d",q[r]);
}
printf("\n");
}
}
}
printf("\nThe no of page faults is %d",c);
}
```
## OUTPUT:

![Screenshot (408)](https://github.com/Dhivya-bharathi88/OS-EX.10-IMPLEMENTATION-OF-PAGE-REPLACEMENT-ALGORITHMS/assets/128019999/fd48b7fa-1d07-4d29-b48e-58f50d0b439a)

## RESULT:

  Thus the implementation of LRU page replacement is successfully executed.

# PAGE REPLACEMENT ALGORITHM (OPR)

## AIM:

  To write a C program to implement Page Replacement technique using OPR
  
## ALGORITHM:

1. Start the program.
2. Take the input of pages as an array.
3. Look for the page allocated is present in near future, if no then replace that page
in the memory with new page,
4. If page already present increment hit, else increment miss.
5. Repeat till we reach the last element of the array.
6. Print the number of hits and misses.
7. Stop the program.

## PROGRAM:
```
#include<stdio.h>
int main()
{
int i,j,n,a[50],frame[10],no,k,avail,count=0;
printf("\n ENTER THE NUMBER OF PAGES:\n");
scanf("%d",&n);
printf("\n ENTER THE PAGE NUMBER :\n");
for(i=1;i<=n;i++)
scanf("%d",&a[i]);
printf("\n ENTER THE NUMBER OF FRAMES :");
scanf("%d",&no);
for(i=0;i<no;i++)
frame[i]= -1;
j=0;
printf("\tref string\t page frames\n");
for(i=1;i<=n;i++)
{
printf("%d\t\t",a[i]);
avail=0;
for(k=0;k<no;k++)
if(frame[k]==a[i])
avail=1;
if (avail==0)
{
frame[j]=a[i];
j=(j+1)%no;
count++;
for(k=0;k<no;k++)
printf("%d\t",frame[k]);
}
printf("\n");
}
printf("Page Fault Is %d",count);
return 0;
}
```
## OUTPUT:

![Screenshot (409)](https://github.com/Dhivya-bharathi88/OS-EX.10-IMPLEMENTATION-OF-PAGE-REPLACEMENT-ALGORITHMS/assets/128019999/89a6554c-05f1-4e3a-b5de-c3f9173da131)

## RESULT:

  Thus the implementation of OPR page replacement is successfully executed.

  # EX.11-IMPLEMENTATION-OF-DISK-SCHEDULING-ALGORITHMS
## FIRST COME FIRST SERVE

### AIM:
To write a program for the first come first serve method of disc scheduling.

### DESCRIPTION:
Disk scheduling is schedule I/O requests arriving for the disk.

It is important because: -

Multiple I/O requests may arrive by different processes and only one I/O request can be served at a time
by the disk controller. Thus other I/O requests need to wait in the waiting queue and need to be
scheduled.

Two or more request may be far from each other so can result in greater disk head movement.
Hard drives are one of the slowest parts of the computer system and thus need to be accessed in an
efficient manner

FCFS is the simplest of all the Disk Scheduling Algorithms. In FCFS, the requests are addressed in the
order they arrive in the disk queue.

### PROGRAM:
```

#include <stdio.h>
#include <stdlib.h>
int main()
{
int RQ[100],i,n,TotalHeadMoment=0,initial;
printf ("Enter the number of Requests\n");
scanf("%d",&n);
printf("Enter the Requests sequence\n");
for(i=0;i<n;i++)
scanf("%d",&RQ[i]);
printf("Enter initial head position\n");
scanf("%d",&initial);
for(i=0;i<n;i++)
{
TotalHeadMoment=TotalHeadMoment+abs(RQ[i]-initial);
initial=RQ[i];
}
printf("Total head moment is %d",TotalHeadMoment);
return 0;
}
```

### OUTPUT:
  
![Screenshot 2023-10-08 204204](https://github.com/Aishwarya-TM/OS-EX.11-IMPLEMENTATION-OF-DISK-SCHEDULING-ALGORITHMS/assets/127846109/a18fe07e-2e54-4400-9d7d-78e10d234555)

### RESULT:
Thus the implementation of the program for first come first serve disc scheduling has been
successfully executed.


## SHORTEST SEEK TIME FIRST

### AIM:
To write a program for the first come first serve method of disc scheduling.

### DESCRIPTION:
Shortest seek time first (SSTF) algorithm

Shortest seek time first (SSTF) algorithm selects the disk I/O request which requires the least disk arm
movement from its current position regardless of the direction. It reduces the total seek time as compared
to FCFS.

### PROGRAM:
```
#include<stdio.h>
#include<stdlib.h>
int main()
{
int RQ[100],i,n,TotalHeadMoment=0,initial,count=0;
printf("Enter the number of Requests\n");
scanf("%d",&n);
printf("Enter the Requests sequence\n");
for(i=0;i<n;i++)
scanf("%d",&RQ[i]);
printf("Enter initial head position\n");
scanf("%d",&initial);
while(count!=n)
{
int min=1000,d,index;
for(i=0;i<n;i++)
{
d=abs(RQ[i]-initial);
if(min>d)
{
min=d;
index=i;
}
}
TotalHeadMoment=TotalHeadMoment+min;
initial=RQ[index];
RQ[index]=1000;
count++;
}
printf("Total head movement is %d",TotalHeadMoment);
return 0;
}

```

### OUTPUT:

![Screenshot 2023-10-08 204225](https://github.com/Aishwarya-TM/OS-EX.11-IMPLEMENTATION-OF-DISK-SCHEDULING-ALGORITHMS/assets/127846109/52055641-f28c-4d32-ab7b-f50d08a6428a)


### RESULT:
Thus the implementation of the program for shortest seek time first disc scheduling has been
successfully executed.

## SCAN

### AIM:
To write a program for the first come first serve method of disc scheduling.

### DESCRIPTION:
SCAN

It is also called as Elevator Algorithm. In this algorithm, the disk arm moves into a particular direction
till the end, satisfying all the requests coming in its path, and then it turns backend moves in the reverse
direction satisfying requests coming in its path.

It works in the way an elevator works, elevator moves in a direction completely till the last floor of that
direction and then turns back.

### PROGRAM:
```
#include<stdio.h>
#include<stdlib.h>
int main()
{
int RQ[100],i,j,n,TotalHeadMoment=0,initial,size,move;
printf("Enter the number of Requests\n");
scanf("%d",&n);
printf("Enter the Requests sequence\n");
for(i=0;i<n;i++)
scanf("%d",&RQ[i]);
printf("Enter initial head position\n");
scanf("%d",&initial);
printf("Enter total disk size\n");
scanf("%d",&size);
printf("Enter the head movement direction for high 1 and for low 0\n");
scanf("%d",&move);
for(i=0;i<n;i++)
{
for(j=0;j<n-i-1;j++)
{
if(RQ[j]>RQ[j+1])
{
int temp;
temp=RQ[j];
RQ[j]=RQ[j+1];
RQ[j+1]=temp;
}
}
}
int index;
for(i=0;i<n;i++)
{
if(initial<RQ[i])
{
index=i;
break;
}
}
if(move==1)
{
for(i=index;i<n;i++)
{
TotalHeadMoment=TotalHeadMoment+abs(RQ[i]-initial);
initial=RQ[i];
}
// last movement for max size
TotalHeadMoment=TotalHeadMoment+abs(size-RQ[i-1]-1);
initial = size-1;
for(i=index-1;i>=0;i--)
{
TotalHeadMoment=TotalHeadMoment+abs(RQ[i]-initial);
initial=RQ[i];
}
}
else
{
for(i=index-1;i>=0;i--)
{
TotalHeadMoment=TotalHeadMoment+abs(RQ[i]-initial);
initial=RQ[i];
}
TotalHeadMoment=TotalHeadMoment+abs(RQ[i+1]-0);
initial =0;
for(i=index;i<n;i++)
{
TotalHeadMoment=TotalHeadMoment+abs(RQ[i]-initial);
initial=RQ[i];
}
}
printf("Total head movement is %d",TotalHeadMoment);
return 0;
}

```
### OUTPUT:

![Screenshot 2023-10-08 204237](https://github.com/Aishwarya-TM/OS-EX.11-IMPLEMENTATION-OF-DISK-SCHEDULING-ALGORITHMS/assets/127846109/722601de-9db8-4732-8e97-1ddc820d8392)

### RESULT:
Thus the implementation of the program for SCAN disc scheduling has been successfully executed.
## LOOK
### AIM:
To write a program for the first come first serve method of disc scheduling.

### DESCRIPTION:
Look

It is similar to the SCAN disk scheduling algorithm except for the difference that the disk arm in spite of
going to the end of the disk goes only to the last request to be serviced in front of the head and then
reverses its direction from there only. Thus, it prevents the extra delay which occurred due to unnecessary
traversal to the end of the disk.

### PROGRAM:
```
#include<stdio.h>
#include<stdlib.h>
int main()
{
int RQ[100],i,j,n,TotalHeadMoment=0,initial,size,move;
printf("Enter the number of Requests\n");
scanf("%d",&n);
printf("Enter the Requests sequence\n");
for(i=0;i<n;i++)
scanf("%d",&RQ[i]);
printf("Enter initial head position\n");
scanf("%d",&initial);
printf("Enter total disk size\n");
scanf("%d",&size);
printf("Enter the head movement direction for high 1 and for low 0\n");
scanf("%d",&move);
for(i=0;i<n;i++)
{
for(j=0;j<n-i-1;j++)
{
if(RQ[j]>RQ[j+1])
{
int temp;
temp=RQ[j];
RQ[j]=RQ[j+1];
RQ[j+1]=temp;
}
}
}
int index;
for(i=0;i<n;i++)
{
if(initial<RQ[i])
{
index=i;
break;
}
}
if(move==1)
{
for(i=index;i<n;i++)
{
TotalHeadMoment=TotalHeadMoment+abs(RQ[i]-initial);
initial=RQ[i];
}
for(i=index-1;i>=0;i--)
{
TotalHeadMoment=TotalHeadMoment+abs(RQ[i]-initial);
initial=RQ[i];
}
}
else
{
for(i=index-1;i>=0;i--)
{
TotalHeadMoment=TotalHeadMoment+abs(RQ[i]-initial);
initial=RQ[i];
}
for(i=index;i<n;i++)
{
TotalHeadMoment=TotalHeadMoment+abs(RQ[i]-initial);
initial=RQ[i];
}
}
printf("Total head movement is %d",TotalHeadMoment);
return 0;
}
```
### OUTPUT:

![Screenshot 2023-10-08 204253](https://github.com/Aishwarya-TM/OS-EX.11-IMPLEMENTATION-OF-DISK-SCHEDULING-ALGORITHMS/assets/127846109/5657aa8c-0ed7-4eaa-b207-4710836bbbb4)

### RESULT:
Thus the implementation of the program for LOOK disc scheduling has been successfully executed.


EX.12-IMPLEMENTATION-OF-FILE-ALLOCATION-METHODS
SEQUENTIAL ALLOCATION
AIM:
To implement file management using sequential list.

ALGORITHM:
Step 1: Start the program.

Step 2: Get the number of memory partition and their sizes.

Step 3: Get the number of processes and values of block size for each process.

Step 4: First fit algorithm searches all the entire memory block until a hole which is big enough is encountered. It allocates that memory block for the requesting process.

Step 5: Best-fit algorithm searches the memory blocks for the smallest hole which can be allocated to requesting process and allocates it.

Step 6: Worst fit algorithm searches the memory blocks for the largest hole and allocates it to the process.

Step 7: Analyses all the three memory management techniques and display the best algorithm which utilizes the memory resources effectively and efficiently.

Step 8: Stop the program.

PROGRAM:
#include < stdio.h>
#include<conio.h>
void main()
{
int f[50], i, st, len, j, c, k, count = 0;
clrscr();
for(i=0;i<50;i++)
f[i]=0;
printf("Files Allocated are : \n");
x: count=0;
printf(“Enter starting block and length of files: ”);
scanf("%d%d", &st,&len);
for(k=st;k<(st+len);k++)
if(f[k]==0)
count++;
if(len==count)
{
for(j=st;j<(st+len);j++)
if(f[j]==0)
{
f[j]=1;
printf("%d\t%d\n",j,f[j]);
}
if(j!=(st+len-1))
printf(” The file is allocated to disk\n");
}
else
printf(” The file is not allocated \n");
printf("Do you want to enter more file(Yes - 1/No - 0)");
scanf("%d", &c);
if(c==1)
goto x;
else
exit();
getch();
}
OUTPUT:
Screenshot 2023-10-09 095855

RESULT:
Thus, file management using sequential list is implemented successfully.

LINKED ALLOCATION
AIM:
To implement file management using Linked list.

DESCRIPTION:
➢Linked allocation solves all problems of contiguous allocation. With linked allocation, each file is a linked list of disk blocks; the disk blocks may be scattered anywhere on the disk. The directory contains a pointer to the first and last blocks of the file.

➢ Each block contains a pointer to the next block. These pointers are not made available to the user. Thus, if each block is 512 bytes, and a disk address (the pointer) requires 4 bytes, then the user sees blocks of 508bytes.

➢ To create a new file, we simply create a new entry in the directory. With linked allocation, each directory entry has a pointer to the first disk block of thefile.

➢ This pointer is initialized to nil (the end-of-list pointer value) to signify an empty file. The size field is also set to 0. A write to the file causes a free block to be found via the free-space-management system, and this new block is then written to, and is linked to the end of thefile.

➢ To read a file, we simply read blocks by following the pointers from block to block. There is no external fragmentation with linked allocation, and any free blockon the free-space list can be used to satisfy arequest.

➢ The size of a file does not need to be declared when that file is created. A file can continue to grow as long as free blocks areavailable.

➢ Consequently, it is never necessary to compact diskspace.

PROGRAM:
#include <stdio.h>
#include <conio.h>
#include <stdlib.h>
void recursivePart(int pages[]){
int st, len, k, c, j;
printf("Enter the index of the starting block and its length: ");
scanf("%d%d", &st, &len);
k = len;
if (pages[st] == 0){
for (j = st; j < (st + k); j++){
if (pages[j] == 0){
pages[j] = 1;
printf("%d ----- >%d\n", j, pages[j]);
}
else {
printf("The block %d is already allocated \n", j);
k++;
}
}
}
else
printf("The block %d is already allocated \n", st);
printf("Do you want to enter more files? \n");
printf("Enter 1 for Yes, Enter 0 for No: ");
scanf("%d", &c);
if (c==1)
recursivePart(pages);
else
exit(0);
return;
}
int main(){
int pages[50], p, a;
for (int i = 0; i < 50; i++)
pages[i] = 0;
printf("Enter the number of blocks already allocated: ");
scanf("%d", &p);
printf("Enter the blocks already allocated: ");
for (int i = 0; i < p; i++){
scanf("%d", &a);
pages[a] = 1;
}
recursivePart(pages);
getch();
return 0;
}
OUTPUT:
Screenshot 2023-10-09 095914

RESULT:
Thus, file management using Linked list is implemented successfully.

INDEXED ALLOCATION
AIM:
To implement file management using Indexed list.

DESCRIPTION:
➢ Indexed allocation brings all the block pointers together into onelocation: called the index block.

➢ Each file has its own index block, which is an array of disk-block addresses. The ith entry in the index block points to the ith block of thefile.

➢ The directory contains the address of the index block.

➢ To read the ith block, we use the pointer in the ith index-block entry to find and read the desiredblock.

➢ When the file is created, all pointers in the index block are set to nil. When the ith block is first written, a block is obtained from the free-space manager, and its address is put in the ith index-blockentry.

➢ Indexed allocation supports direct access, without suffering from external fragmentation, because any free block on the disk may satisfy a request for more space.

➢ If the index block is too small, however, it will not be able to hold enough pointers for a large file, and a mechanism will have to be available to deal with thisissue: Linked scheme: An index block is normally one disk block. Thus, it can be read and written directly by itself. To allow for large files, we may link together several index blocks.

Multilevel index: A variant of the linked representation is to use a first level index block to point to a set of second-level index blocks, which in turn point to the file blocks. To access a block, the operating system uses the first-level index to find a second-level index block, and that block to find the desired data block. This approach could be continued to a third or fourth level, depending on the desired maximum file size.

PROGRAM:
#include<stdio.h>
#include<conio.h>
#include<stdlib.h>
void main()
{
int f[50], index[50],i, n, st, len, j, c, k, ind,count=0;
clrscr();
for(i=0;i<50;i++)
f[i]=0;
x:printf("Enter the index block: ");
scanf("%d",&ind);
if(f[ind]!=1)
{
printf("Enter no of blocks needed and no of files for the index %d on the disk : \n", ind);
scanf("%d",&n);
}
else
{
printf("%d index is already allocated \n",ind);
goto x;
}
y: count=0;
for(i=0;i<n;i++)
{
scanf("%d", &index[i]);
if(f[index[i]]==0)
count++;
}
if(count==n)
{
for(j=0;j<n;j++)
f[index[j]]=1;
printf("Allocated\n");
printf("File Indexed\n");
for(k=0;k<n;k++)
printf("%d ------->%d : %d\n",ind,index[k],f[index[k]]);
}
else
{
printf("File in the index is already allocated \n");
printf("Enter another file indexed");
goto y;
}
printf("Do you want to enter more file(Yes - 1/No - 0)");
scanf("%d", &c);
if(c==1)
goto x;
else
exit(0);
getch();
}
OUTPUT:
Screenshot 2023-10-09 095933

RESULT;
Thus, file management using Indexed list is implemented successfully.
