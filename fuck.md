```cpp
#include<bits/stdc++.h>
using namespace std; 
int N,a,b,ans=0;
vector<int> vec [200005];


int F(int now,int father,int deg){
	int fir=deg,sec=deg,tt;     //tt占存資料
    for (auto i:vec[now]){  
        if (i!=father){
            tt=F(i,now,deg+1);
			if(tt>fir){
				sec=fir;
				fir=tt;
			}
			else if(tt>sec){
                sec=tt;
            }
        }
    }
	ans=max(ans,(fir-deg)+(sec-deg));
	return fir;
}



signed main(){
    while (cin>>N){
        for (int i=0;i<N;i++){
            vec[i].clear();
        }
		ans=0;
        for (int i=0;i<N-1;i++){
        cin>>a>>b;
        vec[a].push_back(b);
        vec[b].push_back(a);
        }
		F(1,-1,0);
		cout<<ans<<"\n";
        ans=0;
        vec[200005];
    }
}
```
