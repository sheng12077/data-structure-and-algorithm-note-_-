dp動態規劃-有限背包問題
====


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
