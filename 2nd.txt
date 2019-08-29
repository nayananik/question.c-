#include<stdio.h>
 
void main()
{
int n;
scanf("%d",&n);
int a[n],count=0;
for(int i=0;i<n;i++)
scanf("%d",&a[i]);
for(int i=0;i<n-1;i++)
{
count = n-1-i;
for(int j=i+1;j<n;j++)
{
if(a[i]>=a[j]) count=count - 1;
else break;
}
if(count == 0)
printf("%d ",a[i]);
}
printf("%d",a[n-1]);
}