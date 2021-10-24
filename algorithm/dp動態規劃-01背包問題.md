dp動態規劃-背包問題
=====

[zerojudge:b184: 5. 裝貨櫃問題](https://zerojudge.tw/ShowProblem?problemid=b184) AC(2ms, 336KB)
```cpp
#include<bits/stdc++.h>
using namespace std;
#define int long long
#define endl "\n"

signed main(){
    
    ios::sync_with_stdio(0);
    cin.tie(0);

    int n;
    int w=100;
    while(cin>>n){
        int weight[105];
        int cost[105];
        int dp[105]={0};
        for(int i=1;i<=n;i++){
            cin>>weight[i]>>cost[i];
        }
        for(int i=1;i<=n;i++){
            for(int j=100;j>0;j--){
                if(j-weight[i]>=0){
                    dp[j]=max(dp[j],dp[j-weight[i]]+cost[i]);
                }
            }
        }
        cout<<dp[100]<<endl;
    }
}
//b184
```
