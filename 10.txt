#include<bits/stdc++.h>
using namespace std;
#define ll long long int
int main()
{
    ll t,i,j,k,l,n,m;
    cin>>n>>m;
    priority_queue<pair<ll,ll>>p;
    ll a[n+3];
    unordered_map<ll,ll>h;
    for(i=0;i<n;i++)
        cin>>a[i];
    for(i=0;i<n;i++)
    {
        //cin>>a[i];
        h[a[i]]++;
        p.push({h[a[i]],a[i]});
        cout<<p.top().second<<" "<<p.top().first<<endl;
    }
    return 0;
}