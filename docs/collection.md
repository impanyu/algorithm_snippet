# Collection

## 1. Three ways to customize a comparator for a collection such as priority_queue, map
[link1](http://fusharblog.com/3-ways-to-define-comparison-functions-in-cpp/)
[link2](https://stackoverflow.com/questions/16111337/declaring-a-priority-queue-in-c-with-a-custom-comparator)
[function class](https://www.zhihu.com/question/38955439)

### a. Defining a compare function

```c++
bool compare (int a, int b){
     return a>b;
}

priority_queue<int,vector<int>,function<bool(int,int)>> pq(compare);
map<int,int,function<bool(int,int)>> mp(compare);
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
map<int,int,compare> mp;
``` 

### c.overload a compare method

```c++
class A{
private:
  int x=0;
public:
  bool operator< (const A other ){
      return self.x<other.x; 
   }
}
```


### d. First two methods can also be applied to sort function:

```c++
vector<int> v;
sort(begin(v),end(v),compare());
```

##  [Add hash method to a pair<> class](https://www.techiedelight.com/use-pair-key-std-unordered_set-cpp/)

```c++
class pair_hash
{
   template<class T1, class T2>
   std::size_t operator()(pair<T1,T2> const& pair) const{
       std::size_t h1=std::hash<T1>()(pair.first);
       std::size_t h2=std::hash<T2>()(pair.second);
       return h1^h2;  
   }
}

int main(){
   unordered_set<pair<string,int>,pair_hash> set ={{"two",2},{"one",1},{"four",4},{"three",3}};
   for (auto &p : set){
    cout<< p.first<<": "<<p.second<<"\n";
   }
   return 0;

}


```

