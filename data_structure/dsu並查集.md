dsu並查集
==

模板
==
```cpp
void initialise(int n,int parent[]){
    for (int i=0;i<n;i++){
        parent[i]=i;
    }
}

int find(int x,int parent[]){
    if (parent[x]==x){
        return x;
    }
    else{
        return parent[x]=find(parent[x],parent);
    }
}

void merge (int x,int y,int parent[]){
    int x_root=find(x,parent);
    int y_root=find(y,parent);
    parent[x_root]=y_root;   
}
```

[洛谷:P3367 【模板】并查集](https://www.luogu.com.cn/problem/P3367)
```cpp
#pragma GCC optimize("Ofast")
#pragma GCC target("sse,sse2,sse3,ssse3,sse4,popcnt,abm,mmx,avx,avx2,fma")
#pragma GCC optimize("unroll-loops")
#include<bits/stdc++.h>
using namespace std;
#define int long long
#define endl '\n'
#define inf 2e18
#define maxn 100005
#define mod 1000000007


int parent[maxn]={0};
void initialise(int n){
    for (int i=0;i<n;i++){
        parent[i]=i;
    }
}

int find(int x){
    if (parent[x]==x){
        return x;
    }
    else{
        return parent[x]=find(parent[x]);
    }
}

void merge (int x,int y){
    int x_root=find(x);
    int y_root=find(y);
    parent[x_root]=y_root;   
}


signed main(){

    ios::sync_with_stdio(0);
    cin.tie(0);

    int n,m;
    cin>>n>>m;
    initialise(n);
    while(m--){
        int a,b,c;
        cin>>a>>b>>c;
        if(a==1){
           merge(b,c);
        }
        else{
            if(find(b)==find(c)){
                cout<<"Y"<<endl;
            }
            else{
                cout<<"N"<<endl;
            }
        }
    }
}
```
[洛谷:P1551 亲戚](https://www.luogu.com.cn/problem/P1551)
```cpp
#pragma GCC optimize("Ofast")
#pragma GCC target("sse,sse2,sse3,ssse3,sse4,popcnt,abm,mmx,avx,avx2,fma")
#pragma GCC optimize("unroll-loops")
#include<bits/stdc++.h>
using namespace std;
#define int long long
#define endl '\n'
#define inf 2e18
#define maxn 100005
#define mod 1000000007

int parent[maxn]={0};

void initialise(int n){
    for (int i=0;i<n;i++){
        parent[i]=i;
    }
}

int find(int x){
    if (parent[x]==x){
        return x;
    }
    else{
        return parent[x]=find(parent[x]);
    }
}

void merge (int x,int y){
    int x_root=find(x);
    int y_root=find(y);
    parent[x_root]=y_root;   
}


signed main(){

    ios::sync_with_stdio(0);
    cin.tie(0);

    int n,m,p;
    cin>>n>>m>>p;
    initialise(n);
    for(int i=0;i<m;i++){
        int a,b;
        cin>>a>>b;
        merge(a,b);
    }
    for(int i=0;i<p;i++){
        int a,b;
        cin>>a>>b;
        if(find(a)==find(b)){
            cout<<"Yes"<<endl;
        }
        else{
            cout<<"No"<<endl;
        }
    }
}
```

[D1. Mocha and Diana (Easy Version)](https://codeforces.com/problemset/problem/1559/D1)
```cpp
#include<bits/stdc++.h>
using namespace std;
#define int long long
#define endl '\n'
#define inf 2e18
#define maxn 10005
#define mod 1000000007

int tree1[maxn];
int tree2[maxn];

void initialise(int n,int vec[]){
    for (int i=0;i<n;i++){
        vec[i]=i;
    }
}

int find(int x,int vec[]){
    if (vec[x]==x){
        return x;
    }
    else{
        return vec[x]=find(vec[x],vec);
    }
}

void merge (int x,int y,int vec[]){
    int x_root=find(x,vec);
    int y_root=find(y,vec);
    vec[x_root]=y_root;   
}


signed main(){

    ios::sync_with_stdio(0);
    cin.tie(0);

    int n,m1,m2;
    cin>>n>>m1>>m2;
    initialise(n,tree1);
    initialise(n,tree2);
    while(m1--){
        int u,v;
        cin>>u>>v;
        merge(u,v,tree1);    
    }
    while(m2--){
        int u,v;
        cin>>u>>v;
        merge(u,v,tree2);
    }
    int ans=0;
    vector<vector<int>>ans_list;
    for(int i=1;i<=n;i++){
        for(int j=1;j<=n;j++){
            if(find(i,tree1)!=find(j,tree1) and find(i,tree2)!=find(j,tree2)){
                merge(i,j,tree1);
                merge(i,j,tree2);
                ans_list.push_back({i,j});
                ans++;
            }
        }
    }
    cout<<ans<<endl;
    for(auto it:ans_list){
        cout<<it[0]<<" "<<it[1]<<endl;
    }
}
```
 

其他類題
===
[leetcode:547. Number of Provinces](https://leetcode.com/problems/number-of-provinces/)

[zerojudge: d831: 畢業旅行](https://zerojudge.tw/ShowProblem?problemid=d831)

[zerojudge: d449: 垃圾信件](https://zerojudge.tw/ShowProblem?problemid=d449)

[zerojudge: c291: APCS 2017-0304-2小群體](https://zerojudge.tw/ShowProblem?problemid=c291)

[zerojudge:f677: FJCU_109_Winter_Day3_Lab1 並查集練習](https://zerojudge.tw/ShowProblem?problemid=f677)
