# stack


Stack-中文叫作堆疊

隔壁國家叫這個堆栈

先稍微解釋一下這是什麼概念

原理的話先不要因為我不知道

因為我只知道怎麼用==

stack就像疊積木的感覺

一層一層疊上去

夠白話了吧

# 

堆疊

先進後出FILO也就是後進先出LIFO的特性

~~對，這是幹話~~

Stack的pop跟push之時間複雜度皆為常數，即O(1)

介紹完了，三句話而已

# 
這是一個stack

<img width="335" alt="stack001" src="https://user-images.githubusercontent.com/86102390/129564369-75c59b78-47bb-44e6-8a02-57c5d7f25969.png">

現在加入0這個元素進去stack

<img width="334" alt="stack002" src="https://user-images.githubusercontent.com/86102390/129564881-66e47647-7f3f-4e15-999d-7859d140c787.png">

Top變0這個元素了

<img width="331" alt="stack003" src="https://user-images.githubusercontent.com/86102390/129565468-ffccbfc0-5f38-47e2-8c51-41c0c76e0c03.png">

接著加入69這個元素

<img width="329" alt="stack004" src="https://user-images.githubusercontent.com/86102390/129565490-e1026ea4-1af1-4491-9461-086810053681.png">

Top再次改變

<img width="332" alt="stack005" src="https://user-images.githubusercontent.com/86102390/129565502-7eb08ece-356e-429c-8972-40ffdd2f8fca.png">

接著加入420這個元素

<img width="332" alt="stack006" src="https://user-images.githubusercontent.com/86102390/129565931-410f46e3-b66a-4da1-8f00-3d27cb2c3463.png">

Top再變

<img width="329" alt="stack007" src="https://user-images.githubusercontent.com/86102390/129565958-8d54b24d-69db-45e6-b3ef-9a37e5e04bf1.png">

接著pop頂端的元素

<img width="349" alt="stack008" src="https://user-images.githubusercontent.com/86102390/129567108-37503f6a-8024-4a15-a3b6-cf6c7682b618.png">

Top變69

<img width="331" alt="stack009" src="https://user-images.githubusercontent.com/86102390/129567119-28278347-b36b-4406-956d-1f74eeaf51a4.png">

再pop stack最頂的元素

<img width="326" alt="stack010" src="https://user-images.githubusercontent.com/86102390/129567124-f799c917-94d2-4186-a41a-6b2a695ae4ed.png">

Top變0

<img width="326" alt="stack011" src="https://user-images.githubusercontent.com/86102390/129567127-e5a77232-0ca0-4405-bf58-26b79b489ec7.png">

再pop一次頂端的元素

<img width="322" alt="stack012" src="https://user-images.githubusercontent.com/86102390/129567151-2b0483c5-550f-4a13-9487-60ab738a3ffe.png">

Stack空了

<img width="335" alt="stack001" src="https://user-images.githubusercontent.com/86102390/129567244-6f04efb4-ea16-4a29-9811-9e4a1cacc598.png">

# 然後是一些基礎語法
* 宣告
```cpp
#include<bits/stdc++.h>
#include<stack>                     //兩個都可以用，不過上面那個非常好用，懶的話用上面那個就對了

宣告方式
stack <資料型態> Stack的名稱 
                                    
stack<int>stk1;                     //   我這邊叫它stk1   它存的是int
stack<char>stk2;                    //   我這邊叫它stk2   這個存的是char       
stack<bool>stk3;
stack<long long>stk4;
.
.
.
諸如此類
```

接著stack的宣告的名稱全部叫stk

* .top()
```cpp
cout<<stk.top()<<endl;             //輸出stk最頂端的值
```

* .push()
```cpp
stk.push(x);                       //將資料放進stk中
```

* .pop()
```cpp
stk.pop();                         //沒有輸出值，只是把頂端元素拋棄(刪除)
```

* .size()
```cpp
cout<<stk.size()<<endl;            //輸出stk的大小(層數)
```

* .empty()
```cpp
cout<<stk.empty()<<endl;           //stk空的時候回傳true，有東西時回傳false
```


# 接著是簡單的題目，熟悉語法

b923: stack 堆疊的模板題:
https://zerojudge.tw/ShowProblem?problemid=b923
AC (3ms, 316KB)

```cpp
#include<bits/stdc++.h>
using namespace std;

stack <int> stk1;
int n,operation,inputval;                //n操作次數    operation操作編號   inputval加入的資料的值

signed main(){
    cin>>n;
    for (int i=1;i<=n;i++){              //執行n次
        cin>>operation;                  //輸入操作編號
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
這題會用到其他的資料結構，建議可以先去了解vector再來解這題

然後題解跟想法的話晚點再說

f640: 函數運算式求值:
https://zerojudge.tw/ShowProblem?problemid=f640
AC (3ms, 392KB)

```cpp
#include<bits/stdc++.h>
using namespace std;
                                                //開long long是怕int會爆，我沒看題目最大給多少反正我覺得會爆就直接開long long 這樣比較保險
int F(long long x){                             //F函式
    return (2*x-3);     
}

int G(long long x,long long y){                 //G函式
    return (2*x+y-7);
}

int H(long long x,long long y,long long z){     //H函式
    return (3*x-2*y+z);
}

signed main(){

    ios::sync_with_stdio(0);                    //cin cout 加速
    cin.tie(0);
    cout.tie(0);

    vector<string> vec;                         //vec 是存輸入的資料的，這邊全部先設定成string，如果是數字的string等等再轉成int就可以囉
    stack<long long>stk;                        //stk是存數字的，一樣直接開long long，我怕爆掉
    
    string s;
    while(cin>>s){                              //沒給輸入多少行，直接用while cin去輸入
        vec.push_back(s);
    }
    int n=vec.size();                           //其實這行好像沒必要寫==，但我懶的改
    for (int i=n-1;i>-1;i--){                   //從vec的後面讀回來   讀完整個vec，且次數是vec的大小
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
        else{                                    //不是f也不是g也不是h 那就是個數字，把這個數字string轉成int
            int tmp;                             //一個用來暫存資料的變數
            tmp=stoi(vec[i]);                    //stoi()可以把string轉int
            stk.push(tmp);
        }
    }
    cout<<stk.top()<<"\n";                       //整個迴圈跑外就剩下一個值在stk中，也就是答案
}
//f640
```

# 其他類題

TIOJ-1368-get high

https://tioj.ck.tp.edu.tw/problems/1368

uva-00514-Rails

https://onlinejudge.org/index.php?option=com_onlinejudge&Itemid=8&page=show_problem&problem=455

https://zerojudge.tw/ShowProblem?problemid=c123
 
