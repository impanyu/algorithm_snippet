# BT_BST

### 1. binary search
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
       //this line could be changed to "return l;" to return the number of values less than v if not found the exact v 
       return -1;
}
```



### 2. binary search leftmost 
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

### 3. binary search rightmost
```c++
int binary_search_rightmost(vector<int>& A, int v){
	int l=0;
	int r=A.size();
	while(l<r){
		int mid=(l+r)/2;
		if(A[mid]<=v) l=mid+1;
		else r=mid;
	}
        // if not found, still return the number of values less than v
	return l-1;
}
```

### 4. binary tree inorder iterative traversal
A variation of iterative dfs. For each node, push all the left children of its right child.
void isValidBST(TreeNode* root) {  
      stack<TreeNode*> s;
      while(root!=nullptr){
          s.push(root);
          root=root->left;
      }
      while(!s.empty()){
          TreeNode* current=s.top();
          s.pop();
          cout<<current->val;
          TreeNode* right=current->right;
          while(right!=nullptr){
              s.push(right);
              right=right->left;
          }
      }
}
