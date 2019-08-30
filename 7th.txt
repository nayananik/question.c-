#include <stdio.h>
#include <stdlib.h>
typedef struct
{
    int data;
    struct node*next;
}node;
node*createlink(int num,node*ptr)
{
    node*temp=(node*)malloc(sizeof(node));
    temp->data=num;
    temp->next=NULL;
    if(ptr==NULL)
        return temp;
    else
    {
        ptr->next=temp;
        return temp;
    }
}
int dfs(node**a,int pre,int sv,int ch,int max,int*pos,int*deg,int start)
{
    node*temp=a[sv];
    if(deg[sv]==1 && sv!=start)
    {
        if(ch>max)
        {
            max=ch;
            *pos=sv;
        }
        return max;
    }
    while(temp)
    {
        if(temp->data!=pre)
            max=dfs(a,sv,temp->data,ch+1,max,pos,deg,start);
        temp=temp->next;
    }
    return max;
}
int main()
{
    int n,i,u,v;
    scanf("%d",&n);
    node**a=(node**)malloc((n+1)*sizeof(node*));
    node**ptr=(node**)malloc((n+1)*sizeof(node*));
    int*deg=(int*)calloc(n+1,sizeof(int));
    for(i=1;i<=n;i++)
    {
        a[i]=NULL;
        ptr[i]=NULL;
    }
    for(i=0;i<n-1;i++)
    {
        scanf("%d%d",&u,&v);
        deg[u]++;
        deg[v]++;
        ptr[u]=createlink(v,ptr[u]);
        if(a[u]==NULL)
            a[u]=ptr[u];
        ptr[v]=createlink(u,ptr[v]);
        if(a[v]==NULL)
            a[v]=ptr[v];
    }
    for(i=1;i<=n;i++)
    {
        if(deg[i]==1)
            break;
    }
    int pos,pos1;
    dfs(a,0,i,0,-1,&pos,deg,i);
    dfs(a,0,pos,0,-1,&pos1,deg,pos);
    printf("%d %d",pos,pos1);
    return 0;
}