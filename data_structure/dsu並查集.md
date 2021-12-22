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
 

其他類題
===
[leetcode:547. Number of Provinces](https://leetcode.com/problems/number-of-provinces/)

[zerojudge: d831: 畢業旅行](https://zerojudge.tw/ShowProblem?problemid=d831)

[zerojudge: d449: 垃圾信件](https://zerojudge.tw/ShowProblem?problemid=d449)

[zerojudge: c291: APCS 2017-0304-2小群體](https://zerojudge.tw/ShowProblem?problemid=c291)

[zerojudge:f677: FJCU_109_Winter_Day3_Lab1 並查集練習](https://zerojudge.tw/ShowProblem?problemid=f677)
