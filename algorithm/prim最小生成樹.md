
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
[tioj:1211 . 圖論 之 最小生成樹](https://tioj.ck.tp.edu.tw/problems/1211)(AC 29ms)

```cpp
//dijkstra model
#include<bits/stdc++.h>
using namespace std;
#define int long long
#define endl "\n"
#define inf 1e9
#define maxn 10005    

vector<pair<int,int>>graph[maxn];
int dis[maxn];
bool visited[maxn]={false};
priority_queue<pair<int,int>,vector<pair<int,int>>,greater<pair<int,int>>>pq;

signed main(){

    ios::sync_with_stdio(0);
    cin.tie(0);

    int n,m;
    while(cin>>n>>m and n!=0 and m!=0){

        //init
        memset(dis,0x3f,sizeof(dis));
        memset(visited,false,sizeof(visited));
        for(int i=0;i<=n;i++){
            graph[i].clear();
        }
        
        dis[1]=0;
        for(int i=1;i<=m;i++){
            int a,b,w;
            cin>>a>>b>>w;
            graph[a].push_back({b,w});
            graph[b].push_back({a,w});
        }

        //prim
        pq.push({0,1});
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
                if(dis[u]>k){
                    dis[u]=k;
                    pq.push({dis[u],u});
                }
            }
        }
        int cnt=0;
        bool flag=true;
        for(int i=1;i<=n;i++){
            if(dis[i]<inf){
                cnt+=dis[i];
            }
            else{
                flag=false;
            }
        }
        cout<<(flag?cnt:-1)<<endl;
    }
}
```
類題
[zerojudge:a129: 最小生成樹](https://zerojudge.tw/ShowProblem?problemid=a129)

[洛谷:P3366 【模板】最小生成树](https://www.luogu.com.cn/problem/P3366)

[zerojudge:d909: 公路局長好煩惱！？](https://zerojudge.tw/ShowProblem?problemid=d909)

[洛谷:P1111 修复公路](https://www.luogu.com.cn/problem/P1111)
