#stack

<img width="335" alt="stack001" src="https://user-images.githubusercontent.com/86102390/129564369-75c59b78-47bb-44e6-8a02-57c5d7f25969.png">
fuck
<img width="334" alt="stack002" src="https://user-images.githubusercontent.com/86102390/129564881-66e47647-7f3f-4e15-999d-7859d140c787.png">
fuck
<img width="331" alt="stack003" src="https://user-images.githubusercontent.com/86102390/129565468-ffccbfc0-5f38-47e2-8c51-41c0c76e0c03.png">
fuck
<img width="329" alt="stack004" src="https://user-images.githubusercontent.com/86102390/129565490-e1026ea4-1af1-4491-9461-086810053681.png">
fuck
<img width="332" alt="stack005" src="https://user-images.githubusercontent.com/86102390/129565502-7eb08ece-356e-429c-8972-40ffdd2f8fca.png">
fuck
<img width="332" alt="stack006" src="https://user-images.githubusercontent.com/86102390/129565931-410f46e3-b66a-4da1-8f00-3d27cb2c3463.png">
fuck
<img width="329" alt="stack007" src="https://user-images.githubusercontent.com/86102390/129565958-8d54b24d-69db-45e6-b3ef-9a37e5e04bf1.png">




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
