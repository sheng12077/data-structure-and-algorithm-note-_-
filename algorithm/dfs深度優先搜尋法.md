dfs深度優先搜尋法
=====
[codeforces:893C](https://codeforces.com/problemset/problem/893/C)(AC 124ms 130500270)
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
[codeforces:115A](https://codeforces.com/problemset/problem/115/A)(AC )
```cpp
#include<bits/stdc++.h>
using namespace std;
#define int long long
#define endl "\n"

vector<int>graph[2005];
bool vis[2005];
int height[2005];
int MaxHeight=1;  
vector<int>roots;             //存根，把所有根丟下去搜

void dfs(int pos){
    vis[pos]=1;
    stack<int>stk;
    stk.push(pos);
    while(!stk.empty()){
        int parent=stk.top();
        stk.pop();
        for(auto child:graph[parent]){
            if(!vis[child]){                        //沒走過
                vis[child]=1;                       //改成已走訪 
                height[child]=height[parent]+1;     //父節點的高度+1
                MaxHeight=max(MaxHeight,height[child]);
                stk.push(child);                    //丟下去繼續搜
            }
        }
    }
    return;
}

signed  main(){

    ios::sync_with_stdio(0);
    cin.tie(0);
    
    int n;
    cin>>n;
    for(int i=0;i<n;i++){
        int a;
        cin>>a;
        if(a!=-1){
            graph[a-1].push_back(i);       //轉0-base
        }
        else{
            roots.push_back(i);
        }
    }
    memset(vis,0,sizeof(vis));
    memset(height,0,sizeof(height));
    for(auto root:roots){               //把所有根丟下去搜
        height[root]=1;
        dfs(root);
    }
    cout<<MaxHeight;
}
```
