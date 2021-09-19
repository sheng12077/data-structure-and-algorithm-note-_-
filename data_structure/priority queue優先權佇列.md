priority queue優先權佇列
====
[zerojudge:d221: 10954 - Add All](https://zerojudge.tw/ShowProblem?problemid=d221)AC (23ms, 444KB)
```cpp
#include <bits/stdc++.h>
using namespace std;
#define int long long  

signed main(){

	ios_base::sync_with_stdio(0);
	cin.tie(0);

	int n;
	while(cin>>n and n!=0){
		priority_queue <int, vector<int>, greater<int>> pq;
		int ans=0;
		for(int i=0;i<n;i++){
			int num;
			cin>>num;
			pq.push(num);
		}
		for(int i=0;i<n-1;i++){
			int a=pq.top();
			pq.pop();
			int b=pq.top();
			pq.pop();
			ans+=a+b;
			pq.push(a+b);
		}
		cout<<ans<<"\n";
	}
}
```
