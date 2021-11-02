模板
```cpp
int arr[maxn];
int tree[maxn];
void build(int node,int start,int end){
    if(start==end){
        tree[node]=arr[start];
    }
    else{
        int mid=(start+end)/2;
        int left_node=2*node+1;
        int right_node=2*node+2;
        build(left_node,start,mid);
        build(right_node,mid+1,end);
        tree[node]=tree[left_node]+tree[right_node];
    }
}

int query(int node,int start,int end,int left,int right){
    if(right<start or left>end){
        return 0;
    }
    else if(left<=start and end<=right){
        return tree[node];
    }
    else if(start==end){
        return tree[node];
    }
    else{
        int mid=(start+end)/2;
        int left_node=2*node+1;
        int right_node=2*node+2;
        int sum_left=query(left_node,start,mid,left,right);
        int sum_right=query(right_node,mid+1,end,left,right);
        return sum_left+sum_right;
    }
}

void update(int node,int start,int end,int index,int value){
    if(start==end){
        arr[index]=value;
        tree[node]=value;
    }
    else{
        int mid=(start+end)/2;
        int left_node=2*node+1;
        int right_node=2*node+2;
        if(index>=start and index<=mid){
            update(left_node,start,mid,index,value);
        }
        else{
            update(right_node,mid+1,end,index,value);
        }
        tree[node]=tree[left_node]+tree[right_node];
    }
}
```
