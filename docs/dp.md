# dp

## [longest common subsequence](https://www.geeksforgeeks.org/longest-common-subsequence-dp-4/)
1. [wiki](https://en.wikipedia.org/wiki/Longest_common_subsequence_problem)

```c++
int lcs(string A, string B){
   int m=A.size();
   int n=B.size();
   int dp[m+1][n+1];
   for(int i=0;i<=m;i++){
     for(int j=0;j<=m;j++){
        if(i==0 || j==0) dp[i][j]=0;
        else if(A[i-1]==B[j-1]) dp[i][j]=dp[i-1][j-1]+1;
        else dp[i][j]=max(dp[i-1][j],dp[i][j-1]);  
     }
   }
   return dp[m][n];
}


int main(){
  string A="AGGTAB";
  string B="GXTXAYB";
  cout << lcs(A,B);
  return 0;  
}
```


## [edit distance](https://www.geeksforgeeks.org/edit-distance-dp-5/)
1. similar to lcs, but allow replace this time.
2. get the minimal number of edits.

```c++
int editDist(string A, string B){
    int m=A.size();
    int n=B.size();
    int dp[m+1][n+1];
    for(int i=0;i<=m;i++){
      for(int j=0; j<=n;j++){
           if(i==0) dp[i][j]=j;
           else if(j==0) dp[i][j]=i;
           else if(A[i-1]==B[j-1]) dp[i][j]=dp[i-1][j-1];
           else dp[i][j]=min(min(dp[i-1][j],dp[i][j-1]),dp[i-1][j-1])+1;
       }
    }
   return dp[m][n];

}



int main(){
   string A="sunday";
   string B="saturday";
   cout<< editDist(A,B);
   return 0;

}
```

