#code snippets
1. ### binary search
```c++
//return the index of the element = v; if not found, return -1
int binary_search(vector<int>& A, int v){
	int l=0;
	int r=A.size()-1;
	while(l<=r){
		int mid=(l+r)/2;
		if(A[mid]==v) return mid;
		else if(A[mid]<v) l=mid+1;
		else r=mid-1; 
	}
	return -1;// this line could be changed to "return l;" to return the number of values less than v if not found the exact v 
}
```



2. ### binary search leftmost 
```c++
int binary_search_leftmost(vector<int>& A, int v){
	int l=0;
	int r=A.size();
	while(l<r){
		int mid=(l+r)/2;
		if(A[mid]<v) l=mid+1;
		else r=mid;
	}
	return l;//if not found, return the number of values less than v
}
```

3. ### binary search rightmost
```c++
int binary_search_rightmost(vector<int>& A, int v){
	int l=0;
	int r=A.size();
	while(l<r){
		int mid=(l+r)/2;
		if(A[mid]<=v) l=mid+1;
		else r=mid;
	}
	return l-1;// if not found, still return the number of values less than v
}
```

