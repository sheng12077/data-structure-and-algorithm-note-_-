#huhuh

Stack-中文叫作堆疊

先稍微解釋一下這是什麼概念
原理的話先不要因為我不知道
因為我只知道怎麼用==

stack就像疊積木的感覺
一層一層疊上去
夠白話了吧

先來介紹基本的概念
<img width="335" alt="stack001" src="https://user-images.githubusercontent.com/86102390/129564369-75c59b78-47bb-44e6-8a02-57c5d7f25969.png">

<img width="334" alt="stack002" src="https://user-images.githubusercontent.com/86102390/129564881-66e47647-7f3f-4e15-999d-7859d140c787.png">

<img width="331" alt="stack003" src="https://user-images.githubusercontent.com/86102390/129565468-ffccbfc0-5f38-47e2-8c51-41c0c76e0c03.png">

<img width="329" alt="stack004" src="https://user-images.githubusercontent.com/86102390/129565490-e1026ea4-1af1-4491-9461-086810053681.png">

<img width="332" alt="stack005" src="https://user-images.githubusercontent.com/86102390/129565502-7eb08ece-356e-429c-8972-40ffdd2f8fca.png">

<img width="332" alt="stack006" src="https://user-images.githubusercontent.com/86102390/129565931-410f46e3-b66a-4da1-8f00-3d27cb2c3463.png">

<img width="329" alt="stack007" src="https://user-images.githubusercontent.com/86102390/129565958-8d54b24d-69db-45e6-b3ef-9a37e5e04bf1.png">

<img width="349" alt="stack008" src="https://user-images.githubusercontent.com/86102390/129567108-37503f6a-8024-4a15-a3b6-cf6c7682b618.png">

<img width="331" alt="stack009" src="https://user-images.githubusercontent.com/86102390/129567119-28278347-b36b-4406-956d-1f74eeaf51a4.png">

<img width="326" alt="stack010" src="https://user-images.githubusercontent.com/86102390/129567124-f799c917-94d2-4186-a41a-6b2a695ae4ed.png">

<img width="326" alt="stack011" src="https://user-images.githubusercontent.com/86102390/129567127-e5a77232-0ca0-4405-bf58-26b79b489ec7.png">

<img width="322" alt="stack012" src="https://user-images.githubusercontent.com/86102390/129567151-2b0483c5-550f-4a13-9487-60ab738a3ffe.png">

<img width="335" alt="stack001" src="https://user-images.githubusercontent.com/86102390/129567244-6f04efb4-ea16-4a29-9811-9e4a1cacc598.png">
b923: stack 堆疊的模板題:
https://zerojudge.tw/ShowProblem?problemid=b923
AC (3ms, 316KB)

```cpp
#include<bits/stdc++.h>
#include<utility>
using namespace std;

stack <int> stk1;
int n,operation,inputval;

signed main(){
    cin>>n;
    for (int i=1;i<=n;i++){
        cin>>operation;
        if (operation==1){
            stk1.pop();
        }
        else if (operation==2){
            cout<<stk1.top()<<endl;
        }
        else{
            cin>>inputval;
            stk1.push(inputval);
        }
    }
}
//b923
```

f640: 函數運算式求值:
https://zerojudge.tw/ShowProblem?problemid=f640
AC (3ms, 392KB)

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