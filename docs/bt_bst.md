# BT_BST

## 1. binary search

```c++
//return the index of the element = v; if not found, return -1
int binary_search(vector<int>& A, int v){
	int l=0;
	int r=A.size();//not A.size()-1, otherwise would be run for a single element
	while(l<r){
		int mid=(l+r)/2;
		if(A[mid]==v) return mid;
		else if(A[mid]>v) r=mid;
		else l=mid+1; 
	}
       //if not found, return upperbound of v 
       return l;
}
```

## 2. binary search lowerbound 
```c++
int binary_search_leftmost(vector<int>& A, int v){
	int l=0;
	int r=A.size();
	while(l<r){
		int mid=(l+r)/2;
		if(A[mid]>=v) r=mid;
		else l=mid+1;
	}
	return l;//if not found, return upperbound of v; if found, return the index of leftmost searched value
}
```

## 3. binary search upperbound
```c++
int binary_search_rightmost(vector<int>& A, int v){
	int l=0;
	int r=A.size();
	while(l<r){
		int mid=(l+r)/2;
		if(A[mid]>v) r=mid;
		else l=mid+1;
	}
	//not matter found or not found, return the upperbound of the searched element
        return l;
}
```

## 4. binary tree inorder iterative traversal
```c++
//A variation of iterative dfs. 
//For each node, push all the left children of its right child.
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
```
