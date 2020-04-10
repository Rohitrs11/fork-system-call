#include<stdio.h>  //header file for all operations
#include<unistd.h>
#include<sys/types.h>  //header file for pid_t
#include<sys/wait.h>  //header file for wait function
int main()
{
int i, num;   //for declaring variables
pid_t pid;    //declaring data type for process
printf("ENTER A NUMBER:\n");  //user defined entry for the number
sacnf("%d",&num);  //input entered by the user
if(num<0) //for checking number should not be smaller than 0
printf("ENTER A POSITIVE NUMBER:\n");  
else
{
pid=fork();  //used for generation of a new procees that is child process
if(pid==0)
{
printf("CHILD PROCESS IS RUNNING...\n\n");
printf("OUTPUT: ");
while(num>0)  //for checking that entered number should be greater than 0
{
printf("%d"," ",num);  //this for printing the integer values
num=num/2;   
}
printf("\n\n CHILD PROCESS IS COMPLETE\n");
}
else
{
printf("PARENT IS WAITING FOR THE CHILD TO COMPLETE.......\n"); //if the child process still runs then it shows this statement.
wait(NULL); //waiting untill the process is complete
printf("PARENT PROCESS IS COMPLETE \n");  //after the termination of the process it prints this statement.
}

}
return 0;  //it returns after successful execution
}
