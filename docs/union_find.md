# disjoint set

## [disjoint_set]

```c++
class disjoint_set{
public:
    vector<int> pars;
    vector<int> ranks;
    disjoint_set(int n){
      pars=vector<int>(n);
      ranks=vector<int>(n,1);
      for(int i=0;i<n;i++) pars[i]=i;
   }

   int find_root(int node){
       while(pars[node]!=node) 
           node=pars[node];
       return node;
   }
   
  bool merge(int n1, int n2){
      int root_n1=find_root(n1);
      int root_n2=find_root(n2);
      if(root_n1==root_n2) return false;
      if(ranks[root_n2]>ranks[root_n1]) 
          swap(root_n1,root_n2);
      pars[root_n2]=root_n1;
      ranks[root_n1]=max(root_n1,ranks[root_n2]+1);
      return true;
  }

  int set_count(){
     int ans=0;
     for(int i=0;i<n;i++){
        ans+=(i==pars[i]);
     }
     return ans;
  }
};

```



