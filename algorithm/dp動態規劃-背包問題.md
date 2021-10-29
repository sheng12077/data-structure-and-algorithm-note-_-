背包問題
====

經典的背包問題有3種:

+ 01背包問題:

  每**種**物品個數**只有1個**

+ 無限背包問題:

  每**種**物品個數**有無限多個**

+ 有限背包問題:

  每**種**物品個數**有限定數量**


01背包問題
===
 
  
*dp[i][n]* 表示只考慮第1到i項物品，背包體積為n時的最大價值。

假設固定體積n的背包，且有k種物品考慮

可寫成(偽程式碼):

```cpp
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

## 範例練習

[zerojudge:b184: 5. 裝貨櫃問題](https://zerojudge.tw/ShowProblem?problemid=b184) AC(2ms, 336KB)
```cpp
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
```cpp
#include<bits/stdc++.h>
using namespace std;
#define int long long
#define endl "\n"
#define inf 1e12

int cost[1005];
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
            cin>>cost[i]>>weight[i]; 
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
                        dp[j]=max(dp[j],dp[j-weight[i]]+cost[i]);
                    }
                }
            }
            cnt+=dp[v];
        }
        cout<<cnt<<endl;
    }
}
```


## 其他類題
[zerojudge:a587: 祖靈好孝順 ˋˇˊ](https://zerojudge.tw/ShowProblem?problemid=a587)



有限背包問題
===

[tioj:1387. Striker的秘密](https://tioj.ck.tp.edu.tw/submissions/274841)(Results of submission #274841 AC 732ms)

```cpp
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
