# Collection

## 1. Two ways to customize a comparer for a collection such as priority_queue, map
[link1](http://fusharblog.com/3-ways-to-define-comparison-functions-in-cpp/)
[link2](https://stackoverflow.com/questions/16111337/declaring-a-priority-queue-in-c-with-a-custom-comparator)
[function class](https://www.zhihu.com/question/38955439)

### a. Defining a compare function

```c++
bool compare (int a, int b){
     return a>b;
}

priority_queue<int,vector<int>,function<bool(int,int)>> pq;
map<int,function<bool(int,int)>> mp;
```

### b. Defining a compare functor

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

### c. These two methods can also be applied to sort function:

```c++
vector<int> v;
sort(begin(v),end(v),compare);
```

