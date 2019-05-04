# dp

## longest common subsequence(https://www.geeksforgeeks.org/longest-common-subsequence-dp-4/)
1. wiki(https://en.wikipedia.org/wiki/Longest_common_subsequence_problem)

```c++
int lcs(string A, string B){
   int m=A.size();
   int n=B.size();
   int dp[m+1][n+1];
   for(int i=0;i<=m;i++){
     for(int j=0;j<=m;j++){
        if(i==0 || j==0) dp[i][j]=0;
        else if(A[i]==B[j]) dp[i][j]=dp[i-1][j-1]+1;
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
