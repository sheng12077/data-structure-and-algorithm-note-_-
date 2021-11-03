
[AP325:d098: P-7-12. 最小生成樹 (*)](https://judge.tcirc.tw/ShowProblem?problemid=d098)
```cpp
//dijkstra model
#include<bits/stdc++.h>
using namespace std;
#define int long long
#define endl "\n"
#define inf 1e9
#define maxn 100005

vector<pair<int,int>>graph[maxn];
int dis[maxn];
bool visited[maxn]={false};
priority_queue<pair<int,int>,vector<pair<int,int>>,greater<pair<int,int>>>pq;

signed main(){

    ios::sync_with_stdio(0);
    cin.tie(0);

    int n,m;
    cin>>n>>m;
    for(int i=0;i<m;i++){
        int a,b,w;
        cin>>a>>b>>w;
        graph[a].push_back({b,w});
        graph[b].push_back({a,w});
    }

    memset(dis,0x3f,sizeof(dis));
    dis[0]=0;

    pq.push({0,0});
    while(!pq.empty()){
        auto now=pq.top();
        pq.pop();
        int v=now.second;
        if(visited[v]){
            continue;
        }
        visited[v]=true;
        for(auto next:graph[v]){
            int u=next.first;
            int k=next.second;
            if(visited[u]){
                continue;
            }
            if(k<dis[u]){
                dis[u]=k;   
                pq.push({dis[u],u});
            }
        }
    }
    int cnt=0;
    bool flag=true;
    for(int i=0;i<n;i++){
        if(dis[i]<inf){
            cnt+=dis[i];
        }
        else{
            flag=false;
        }
    }
    cout<<(flag?cnt:-1);
}
```
