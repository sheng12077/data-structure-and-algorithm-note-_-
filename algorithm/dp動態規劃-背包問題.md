背包問題
===

經典的背包問題有3種:

+ 01背包問題:
  每<font color="#f00">**種**</font>物品個數有<font color="#f00">**只有1個**</font>
+ 無限/完全背包問題:
  每<font color="#f00">**種**</font>物品個數有<font color="#f00">**無限多個**</font>
+ 有限/多重背包問題:
  每<font color="#f00">**種**</font>物品個數有<font color="#f00">**有限定數量**</font>
 
  
當然有非這三種的噁心題
先會這三種基本上無敵了

## 01背包問題

### 講解
先把接著要用到的變數規定好
     
. | .
--- | ---
weight|重量 
value|價值
 
只考慮第1到i項物品，背包體積為n時的最大價值，紀錄為:
>$$dp[i][n]$$



假設固定體積n的背包，且有k種物品考慮
可寫成(偽程式碼):

```cpp=
for(int i=0;i<k;i++){
    for(int j=0;j<n;j++){
        if(n>=weight[i]){
            dp[i][n]=max(dp[i-1][n],dp[i-1][n-weight[i]]+value[i]);
        }
        else{
            dp[i][n]=dp[i-1][n];
        }
    }    
}
```


不過有這樣空間複雜度很大
要減少空間複雜度可以用滾動dp
我們可以把轉移式寫成: 
>$$dp[j]=max(dp[j],dp[j-weight[i]+value[i])$$

這樣不只空間複雜度變小很多
轉移式看起來也更乾淨易懂了
但我認為沒人看得懂為何是長這樣
以下模板為偽程式碼

```cpp=
for(int i=0;i<物品數量;i++){
    for(j=背包最大承重;j>0;j--){
        if(j-weight[i]>=0){                            //講白話一點:背包還能裝東西就更新
            dp[j]=max(dp[j],dp[j-weight[i]]+value[i]); //dp[j]表示在背包最大承重為j時所能有的最大價值
        }
    }
}
```
### 範例練習

[zerojudge:b184: 5. 裝貨櫃問題](https://zerojudge.tw/ShowProblem?problemid=b184) AC(2ms, 336KB)
```cpp=
#include<bits/stdc++.h>
using namespace std;
#define int long long
#define endl "\n"
#define inf 1e9
#define maxn 10000005


signed main(){
    
    ios::sync_with_stdio(0);
    cin.tie(0);

    int n;
    int w=100;
    while(cin>>n){
        int weight[105];
        int value[105];
        int dp[105]={0};
        for(int i=1;i<=n;i++){
            cin>>weight[i]>>value[i];
        }
        for(int i=1;i<=n;i++){
            for(int j=100;j>0;j--){
                if(j-weight[i]>=0){
                    dp[j]=max(dp[j],dp[j-weight[i]]+value[i]);
                }
            }
        }
        cout<<dp[100]<<endl;
    }
}
//b184
```


[UVa:10130 - SuperSale](https://onlinejudge.org/index.php?option=com_onlinejudge&Itemid=8&page=show_problem&problem=1071)
[zerojudge:f440: 10130 - SuperSale](https://zerojudge.tw/ShowProblem?problemid=f440)(700ms)
```cpp=
#include<bits/stdc++.h>
using namespace std;
#define int long long
#define endl "\n"
#define inf 1e12

int value[1005];
int weight[1005];
int dp[1005];

signed main(){

    ios::sync_with_stdio(0);
    cin.tie(0);

    int k;
    cin>>k;
    for(int i=1;i<=k;i++){
        int n;
        cin>>n;
        for(int i=1;i<=n;i++){
            cin>>value[i]>>weight[i]; 
        }
        int m;
        cin>>m;
        int cnt=0;
        while(m--){
            int v;
            cin>>v;
            memset(dp,0,sizeof(dp));
            for(int i=1;i<=n;i++){
                for(int j=v;j>0;j--){
                    if(j-weight[i]>=0){
                        dp[j]=max(dp[j],dp[j-weight[i]]+value[i]);
                    }
                }
            }
            cnt+=dp[v];
        }
        cout<<cnt<<endl;
    }
}
```


### 其他類題
[zerojudge:a587: 祖靈好孝順 ˋˇˊ](https://zerojudge.tw/ShowProblem?problemid=a587)

## 無限/完全背包問題

### 講解
. | .
--- | ---
weight|重量 
value|價值

無限背包其實就只是可以挑同物很多次的01背包問題
用滾動dp寫出來的轉移式都是:
>$$dp[j]=max(dp[j],dp[j-weight[i]+value[i])$$
>
但在程式碼上有一個地方不同
應該看的出來有不一樣的地方
```cpp=
//01背包
for(int i=0;i<物品數量;i++){
    for(int j=背包最大承重;j>0;j--){
        if(j-weight[i]>=0){      //背包還有空間時
            dp[j]=max(dp[j],dp[j-weight[i]]+value[i]);
        }
    }
}
```

```cpp=
//無限背包
for(int i=0;i<物品數量;i++){
    for(int j=1;j<=背包最大承重;j++){
        if(j-weight[i]>=0){      //背包還有空間時
            dp[j]=max(dp[j],dp[j-weight[i]]+value[i]);
        }
    }
}
```

你會看到轉移式都一樣
不過無限背包要從1開始
無限背包其實就是找"性價比高的"感覺
最小的重量但有最大的價值
### 範例練習
[洛谷:P1616 疯狂的采药](https://www.luogu.com.cn/problem/P1616)(AC 83ms)
```cpp=
#include<bits/stdc++.h>
using namespace std;
#define int long long
#define endl "\n"
#define inf 1e9
#define maxn 10000005

int weight[10005];     //time limit，時間限制，把這當背包容量
int value[10005];
int dp[10000005]; 

signed main(){

    ios::sync_with_stdio(0);
    cin.tie(0);

    int t,m;
    cin>>t>>m; 
    for(int i=0;i<m;i++){
        cin>>weight[i]>>value[i];
    }
    for(int i=0;i<m;i++){
        for(int j=1;j<=t;j++){
            if(j-weight[i]>=0){
                dp[j]=max(dp[j],dp[j-weight[i]]+value[i]);
            }
        }
    }
    cout<<dp[t]<<endl;
}
```
### 其他類題


## 有限/多重背包問題

### 講解
. | .
--- | ---
weight|重量 
value|價值
num|數量


有限背包就是每個物品都限量時
背包最大能裝多少東西
以下是轉移式
k表示該物選用的數量

>$$dp[j]=max(dp[j-weight[i]*k]+value[i]*k)$$

模板偽程式碼:
```cpp=
for(int i=0;i<物品數量;i++){
    for(int j=背包最大承重;j>0;j--){
        for(int k=1;k<該物品有的數量;k++){
            if(j-weight[i]*k>=0){      //背包還有空間時
                dp[j]=max(dp[j],dp[j-weight[i]*k]+value[i]*k);
            }
        }
    }
}
```
### 範例練習
[tioj:1387. Striker的秘密](https://tioj.ck.tp.edu.tw/submissions/274841)(Results of submission #274841 AC 732ms)

```cpp=
#include<bits/stdc++.h>
using namespace std;
#define int long long
#define endl "\n"
#define inf 1e9
#define maxn 10000005

int dp[10005];

signed main(){

    ios::sync_with_stdio(0);
    cin.tie(0);

    int n;
    cin>>n;
    int weight[105];
    int value[105];
    int num[105];
    for(int i=0;i<n;i++){
        cin>>weight[i]>>value[i]>>num[i];
    }
    int t;
    cin>>t;
    for(int i=0;i<n;i++){
        for(int j=t;j>0;j--){
            for(int k=1;k<=num[i];k++){
                if(j-weight[i]*k>=0){
                    dp[j]=max(dp[j],dp[j-k*weight[i]]+k*value[i]);
                }
            }
        }
    }
    cout<<dp[t];
}
```
 ### 其他類題