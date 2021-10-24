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
    
    pq.push({0,0});
    while(!pq.empty()){
        auto now=pq.top();
        pq.pop();
        if(dis[now.second]!=now.first){
            continue;
        }
        for(auto next:vec[now.second]){
            if(dis[next.first]>now.first+next.second){
                dis[next.first]=now.first+next.second;
                pq.push({dis[next.first],next.first});
            }
        }
    }
    cout<<dis[b];
}
//g422
```
