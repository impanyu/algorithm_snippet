# Collection

### Two ways to customize a comparer for a collection such as priority_queue, map
// 1. defining a compare function

```c++
bool compare (int a, int b){
     return a>b;
}

priority_queue<int,vector<int>,function<bool(int,int)>> pq;
map<int,function<bool(int,int)>> mp;
```

//2. defining a compare functor

```c++
class compare
{
public:
    bool operator()(int a, int b)
    {
        return a>b;
    }
};

priority_queue<int,vector<int>,compare>> pq; 
map<int,compare> mp;
``` 

### These two methods can also be applied to sort function:

```c++
vector<int> v;
sort(begin(v),end(v),compare);
```

