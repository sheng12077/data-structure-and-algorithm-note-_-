#stack

<img width="335" alt="stack001" src="https://user-images.githubusercontent.com/86102390/129564369-75c59b78-47bb-44e6-8a02-57c5d7f25969.png"><img width="334" alt="stack002" src="https://user-images.githubusercontent.com/86102390/129564770-205f6b2f-5dc5-4727-a889-ceffffa0e4d3.png">


```cpp
#include<bits/stdc++.h>
using namespace std;

int F(long long x){
    return (2*x-3);     
}

int G(long long x,long long y){
    return (2*x+y-7);
}

int H(long long x,long long y,long long z){
    return (3*x-2*y+z);
}

signed main(){

    ios::sync_with_stdio(0);
    cin.tie(0);
    cout.tie(0);

    vector<string> vec;
    stack<long long>stk;
    
    string s;
    while(cin>>s){
        vec.push_back(s);
    }
    int n=vec.size();
    for (int i=n-1;i>-1;i--){
        if (vec[i]=="f"){
            int a;
            a=stk.top();
            stk.pop();
            stk.push(F(a));
        }
        else if (vec[i]=="g"){
            int a,b;
            a=stk.top();
            stk.pop();
            b=stk.top();
            stk.pop();
            stk.push(G(a,b));
        }
        else if(vec[i]=="h"){
            int a,b,c;
            a=stk.top();
            stk.pop();
            b=stk.top();
            stk.pop();
            c=stk.top();
            stk.pop();
            stk.push(H(a,b,c));
        }
        else{
            int tmp;
            tmp=stoi(vec[i]);
            stk.push(tmp);
        }
    }
    cout<<stk.top()<<"\n";
}
```
