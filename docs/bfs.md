# bfs

## [BFS](https://www.geeksforgeeks.org/breadth-first-search-or-bfs-for-a-graph/) 


```c++
class Graph{
private:
    int V;
    list<int> *adj;
    bool * visited;
    list<int> queue;
public:
    Graph(int V);
    void add_edge(int v, int w);
    void bfs(int s);
}  

Graph::Graph(int V){
    this->V=V;
    adj=new list<int>[V];
    visited=new bool[V];
    queue=list<int>(V); 
    for(int i=0;i<V;i++)
       visited[i]=false;
};

void Graph::add_edge(int v,int w){
   adj[v].push_back(w);
}

void Graph::bfs(int s){
    visited[s]=true;
    queue.push_back(s);
    while(!queue.empty()){
      int node=queue.front();
      queue.pop_front();
      cout<<node<<" ";
      for(list<int>::iterator i=adj[node].begin();i!=adj[node].end();i++){
         if(!visited[*i]){
              visited[*i]=true;
              queue.push_back(*i);
          }
     }  
   }
}

int main(){
 Graph g(4);
 g.add_edge(0,1);
 g.add_edge(0,2);
 g.add_edge(1,2);
 g.add_edge(2,0);
 g.add_edge(2,3);
 g.add_edge(3,3);

 cout<< "Following is Breath First Traversal "
     <<"(starting from vertex 2)\n";
 g.bfs(2);
 return 0;
}
```





## [Kahn's algorithm for Topological Sorting](https://www.geeksforgeeks.org/topological-sorting-indegree-based-solution/)
1. bfs based construct, use a queue to keep all the nodes with in_degree==0
2. for each node, substract the in_degree of all its neigbours by one, and add them to queue when in_degree reaches 0
3. another method is prim's, which is a dfs based method 


```c++
class Graph{
private:
   int V;
   list<int>* adj;
   int* in_degree;
   queue<int> q;
   vector<int> top_order;
public:
   Graph(int V);
   void add_edge(int u, int v);
   void topological_sort();
};

Graph::Graph(int V){
   this->V=V;
   in_degree=new int[V];
   adj=new list<int>(V);
}

void Graph::add_edge(int u,int v){
   adj[u].push_back(v);
}

void Graph::topological_sort(){
  int count=0; 
  for(int u=0;u<V;u++){
      for(list<int>::iterator i=adj[u].begin();i!=adj[u].end();i++)
          in_degree[*i]++;
   }
   for(int i=0;i<V;i++)
     if(in_degree[i]==0)
           q.push(i);
 
   while(!q.empty()){
      int u=q.front();
      q.pop();
      top_order.push_back(q);
      for(list<int>::iterator i=adj[u].begin();i!=adj[u].end();i++)
         if(--in_degree[*i]==0)
           q.push(*i);
      count++;
   }
   
  if(count!=V){
     cout<< "There exists a cycle in the graph\n";
     return;
  }
}

void Graph::print_topological_order(){
  for(int i=0;i<V;i++)
    cout<<top_order[i]<<" ";
  cout<<endl;
}



int main()
{
  Graph g(6);
  g.add_edge(5,2);
  g.add_edge(5,0);
  g.add_edge(4,0);
  g.add_edge(4,1);
  g.add_edge(2,3);
  g.add_edge(3,1);
  
  cout << "Following is a Topological Sort of graph\n";
  g.topological_sort();
  g.print_topological_order();
  return 0;  
}

```



