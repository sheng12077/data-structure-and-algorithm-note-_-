dfs深度優先搜尋法
=====
[codeforces:893C](https://codeforces.com/problemset/problem/893/C)
```cpp
#include<bits/stdc++.h>
using namespace std;
#define int long long
#define endl "\n"

int n,m;
int graph[100005];
vector<int>edges[100005];
bool vis[100005];

int dfs(int v){
    int mn=graph[v];
    vis[v]=1;
    for(auto i:edges[v]){
        if(!vis[i]){
            mn=min(mn,dfs(i));        //找到此子圖上值最小(賄絡代價)最低者
        }
    }
    return mn;  
}

signed  main(){

    ios::sync_with_stdio(0);
    cin.tie(0);

    cin>>n>>m;
    for(int i=0;i<n;i++){
        cin>>graph[i];
    }
    for(int i=0;i<m;i++){
        int a,b;
        cin>>a>>b;
        a--;
        b--;
        edges[a].push_back(b);          
        edges[b].push_back(a);
    }
    int ans=0;
    for(int i=0;i<n;i++){
        if(!vis[i]){
            ans+=dfs(i);
        }
    }
    cout<<ans;
}
```
