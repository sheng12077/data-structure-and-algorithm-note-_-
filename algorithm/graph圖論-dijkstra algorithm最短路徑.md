dijkstra algorithm最短路徑
=====



[zerojudge:PD.紅血球的快遞任務](https://zerojudge.tw/ShowProblem?problemid=g422)AC(80ms, 9.1MB)
```cpp
#include<bits/stdc++.h>
using namespace std;
#define int long long
#define endl "\n"
#define inf 1e9
#define maxn 100005

int dis[maxn];
bool gone[maxn]={false};
vector<pair<int,int>>vec[maxn];
priority_queue<pair<int,int>,vector<pair<int,int>>,greater<pair<int,int>>>pq;
int n,m,b;
int x,y,w;

signed main(){

    ios::sync_with_stdio(0);
    cin.tie(0);

    cin>>n>>m>>b;

    //initialize
    for(int i=0;i<n;i++){
        dis[i]=inf;
    }
    dis[0]=0;

    //建圖  
    for(int i=0;i<m;i++){
        cin>>x>>y>>w;
        vec[x].push_back({y,w});
        vec[y].push_back({x,w});
    }
    
    //dijkstra
    pq.push({0,0});
    while(!pq.empty()){
        auto now=pq.top();
        pq.pop();
        int v=now.second;
        if(gone[v]){
            continue;                    //走過就跳過
        }
        gone[v]=true;                    //標記成已經走訪過
        for(auto next:vec[v]){           //找跟這點相鄰的
            int u=next.first;            
            int k=next.second;           
            if(dis[u]>dis[v]+k){
                dis[u]=dis[v]+k;
                pq.push({dis[u],u});
            }
        }
    }
    cout<<dis[b];
}
//g422
```
