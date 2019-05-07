# graph

## [prim's MST without priority queue](https://www.geeksforgeeks.org/prims-minimum-spanning-tree-mst-greedy-algo-5/)
1. use an array visited to store the visiting status
2. for each iteration, find the node with minimal key and for each of its neighbours, update the key.
3. similar to a bfs construct
4. [wiki page](https://en.wikipedia.org/wiki/Minimum_spanning_tree)
5. another algorithm is kruscal's which manipulate edges instead of nodes.
6. time complexity O(V^2)

```c++
class Graph{
private:   
    int V;
    bool* visited;
    int min_key();
    int** graph;
    int* key;
    int* parent;
public:
    Graph(int V);
    void prim_MST();
};

Graph::Graph(int v){
   this->V=V;
   graph=new int* [V];
   key=new int[V];
   visited=new bool[V];
   parent=new int[V];
   for(int i=0;i<V;i++){
      key[i]=INT_MAX;
      visited[i]=false;
      graph[i]=new int[V];
      for(int j=0;j<V;j++)
         graph[i][j]=0;
   }
}

int Graph::min_key(){
  int min=INT_MAX, min_index;
  for(int v=0; v<V;v++)
     if(visited[v] == false && key[v]< min){
        min=key[v];
        min_index =v;
     }
  return min_index;
}

void Graph::prim_MST(){
  key[0]=0;
  parent[0]=-1;
  for(int i=0;i<V-1;i++){
    int u=min_key();
    visited[i]=true;
    for(int v=0;v<V;v++){
      if(graph[u][v] && !visited[v] && graph[u][v]<key[v])
           parent[v]=u, key[v]=graph[u][v]; 
    }
  }
}

void Graph::print_MST(){
   for(int i=1;i<V;i++)
       cout<<parent[i]<<"-"<<i<<" "<<graph[i][parent[i]];
}

void Graph::add_edge(int u, int v,int weight){
  graph[u][v]=weight;
  graph[v][u]=weight;

}

int main()
{
 int V=5;
 Graph g(5);
 g.add_edge(0,1,2);
 g.add_edge(0,3,6);
 g.add_edge(1,0,2);
 g.add_edge(1,1,3);
 g.add_edge(1,2,3);
 g.prim_MST();
 g.print_MST();
 return 0;
}

```
