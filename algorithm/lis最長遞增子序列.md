lis最長遞增子序列
===
[zerojudge:d242: 00481 - What Goes Up](https://zerojudge.tw/ShowProblem?problemid=d242)
```cpp
#include <bits/stdc++.h>
using namespace std;
#define int long long

signed main(){

	ios_base::sync_with_stdio(0);
	cin.tie(0);

    int num;
    vector<int>a;                    //a[ ]:讀入測資
    while(cin>>num){  
        a.push_back(num);
    }
    int n=a.size();
    int dp[n+1];                     //dp[idx]：掃描測資至 index-i 時的最長遞增子序列的長度
    vector<int>vec;                  //vec[i]：紀錄可位居第 i 順位的最小值 (讓後續數字有機會發展出更長的遞增子序列)。

    dp[0]=1;
    vec.push_back(a[0]);
    int len=1;
    for(int i=0;i<n;i++){
        if(a[i]>vec.back()){            //比vec.back()大，直接加進vec的尾部
            vec.push_back(a[i]);
            len++;
            dp[i]=len;
        }
        else{
            auto k=lower_bound(vec.begin(),vec.end(),a[i]);    //把第一個比a[i]小的替換(取代)掉
            *k=a[i];
            dp[i]=(k-vec.begin()+1);
        }
    }
    cout<<len<<"\n"<<"-"<<"\n";
    vector<int>ans;

    //由 dp，從後往前找出最長遞增子序列的值
    for(int i=n-1;i>=0;i--){
        if(len==dp[i]){
            len--;
            ans.push_back(a[i]);
        }
    }
    reverse(ans.begin(),ans.end());                    
    for(int i=0;i<ans.size();i++){
        cout<<ans[i]<<"\n";
    }
}
//d242
```
