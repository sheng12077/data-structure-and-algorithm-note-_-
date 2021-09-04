dsu並查集
==

[zerojudge: a445: 新手訓練系列- 我的朋友很少](https://zerojudge.tw/ShowProblem?problemid=a445)AC (49ms, 452KB)
```cpp
#include<bits/stdc++.h>
using namespace std;

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


signed main(){

    ios::sync_with_stdio(0);
    cin.tie(0);
    cout.tie(0);

    int n,m,q;                
    cin>>n>>m>>q;
    int parent[10005]={0};
    initialise(n,parent);
    int edges[m][2];
    for (int i=0;i<m;i++){
        cin>>edges[i][0]>>edges[i][1];
        merge(edges[i][0],edges[i][1],parent);
    }
    while(q--){
        int a,b;
        cin>>a>>b;
        if (find(a,parent)==find(b,parent)){
            cout<<":)"<<"\n";
        }
        else{
            cout<<":("<<"\n";
        }
    }
}
```


[zerojudge:f677: FJCU_109_Winter_Day3_Lab1 並查集練習](https://zerojudge.tw/ShowProblem?problemid=f677)	AC (3ms, 740KB)

```cpp
#include<bits/stdc++.h>
using namespace std;

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

signed main(){
    
    ios::sync_with_stdio(0);
    cin.tie(0);
    cout.tie(0);

    int n,m;
    cin>>n>>m;
    int parent[100000]={0};
    int edges[m][2];
    initialise(n,parent);
    for(int i=0;i<m;i++){
        cin>>edges[i][0]>>edges[i][1];
        merge(edges[i][0],edges[i][1],parent);
    }
    int ans=0;
    for (int i=0;i<n;i++){
        if(find(0,parent)==find(i,parent)){
            ans++;
        }
    }
    cout<<ans;
}
```

[zerojudge: c291: APCS 2017-0304-2小群體](https://zerojudge.tw/ShowProblem?problemid=c291)AC (10ms, 920KB)

```cpp
#include<bits/stdc++.h>
using namespace std;

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

signed main(){
    ios::sync_with_stdio(0);
    cin.tie(0);
    cout.tie(0);
    int n;
    cin>>n;
    int parent[50001];
    initialise(n,parent);
    int edges[n][2];
    for (int i=0;i<n;i++){
        int k;
        cin>>k;
        edges[i][0]=i;
        edges[i][1]=k;
        merge(edges[i][0],edges[i][1],parent);
    }
    int ans=0;
    for (int i=0;i<n;i++){
        if(find(i,parent)==i){
            ans++;
        }
    }
    cout<<ans;
}
```
 

其他類題
===
[leetcode:547. Number of Provinces](https://leetcode.com/problems/number-of-provinces/)

[zerojudge: d831: 畢業旅行](https://zerojudge.tw/ShowProblem?problemid=d831)

[zerojudge: d449: 垃圾信件](https://zerojudge.tw/ShowProblem?problemid=d449)
