#include<stdio.h>

int main()

{

      int count,n,time,read,flag=0,time_quantum;
      
      int wait_time=0,turnaround_time=0,a_t[10],b_t[10],r_t[10];
      
      printf("Enter Total Number of Process or Processes:\t");
      
      scanf("%d",&n);
      
      read=n;
      
      for(count=0;count<n;count++)
      
        {
           printf("Enter Arrival Time and Burst Time for Process Process Number %d :",count+1);
           
            scanf("%d",&a_t[count]);//Arrival Time
            
            scanf("%d",&b_t[count]);//Burst Time
            
            r_t[count]=b_t[count];
            
            
        }

       printf("\nEnter the Time Quantum:  \t");
       scanf("%d",&time_quantum);
       printf("\n\nProcess\t|Turnaround Time|Waiting Time\n\n");
       for(time=0,count=0;read!=0;)
          {
             if(r_t[count]<=time_quantum && r_t[count]>0)
                {
                   time+=r_t[count];
                   r_t[count]=0;
                   flag=1;
                 }

             else if(r_t[count]>0)
                {
                   r_t[count]-=time_quantum;
                   time+=time_quantum;
                }
             if(r_t[count]==0 && flag==1)
                {
                    read--;
                    printf("P[%d]\t|\t%d\t|\t%d\n",count+1,time-a_t[count],time-a_t[count]-b_t[count]);
                    wait_time+=time-a_t[count]-b_t[count];
                    turnaround_time+=time-a_t[count];
                     flag=0;
                 }
              if(count==n-1)
              count=0;
              else if(a_t[count+1]<=time)
              count++;
              else
              count=0;
             }
      printf("\nAverage Waiting Time =   %f\n",wait_time*1.0/n);
      printf("Average Turnaround Time = %f\n\n",turnaround_time*1.0/n);
      return 0;

}
