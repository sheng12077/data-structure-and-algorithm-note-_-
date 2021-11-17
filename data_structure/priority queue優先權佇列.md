priority queue優先權佇列
====

[洛谷:P3378 【模板】堆](https://www.luogu.com.cn/problem/P3378)
```cpp
#include<bits/stdc++.h>
using namespace std;
#define int long long
#define endl "\n"
#define inf 2e18
#define maxn 10005
#define mod 100003


priority_queue<int,vector<int>,greater<int>>pq;

void op1(int k){
    pq.push(k);
}

void op2(){
    cout<<pq.top()<<endl;
}

void op3(){
    pq.pop();
}


signed main(){

    ios::sync_with_stdio(0);
    cin.tie(0);

    int n;
    cin>>n;
    for(int i=0;i<n;i++){
        int o;
        cin>>o;
        if(o==1){
            int x;
            cin>>x;
            op1(x);
        }
        else if(o==2){
            op2();
        }
        else{
            op3();
        }
    }
}
```
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
[tioj:1424. 手續費 (Fee)](https://tioj.ck.tp.edu.tw/submissions/269562)(Results of submission #269562 AC 96ms)
```cpp
#include <bits/stdc++.h>
using namespace std;
#define int long long  

signed main(){

	ios_base::sync_with_stdio(0);
	cin.tie(0);

	int n;
	cin>>n;
	priority_queue<int,vector<int>,greater<int>>pq;
	int ans=0;
	for(int i=0;i<n;i++){
		int k;
		cin>>k;
		pq.push(k);
	}
	for(int i=0;i<n-1;i++){
		int a=pq.top();
		pq.pop();
		int b=pq.top();
		pq.pop();
		pq.push(a+b);
		ans+=(a+b);
	}
	cout<<ans<<"\n";
}
```
