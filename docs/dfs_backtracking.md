# dfs_backtracking

## [topological sorting using dfs](https://www.geeksforgeeks.org/topological-sorting/)
1. pretty much the same as dfs, except for each node, we add it to a stack after complete all its children.(add node from end to front)
2. [wiki page](https://en.wikipedia.org/wiki/Topological_sorting), another method is kahn, in which we add the node with no incoming edge and delete its outbound edges.(add node from front to end)

```c++
class Graph{
   int v;
   list<int> *adj;// adjacent list
   stack<int> st;
   bool* visited;
   void topological_sort_util(int v);
public:
   Graph(int v);
   void addEdge(int v, int w);
   void topological_sort();
};
Graph::Graph(int v){
  this->V=V;
  adj=new list<int>[V];
  visited=new bool[V];
}

void Graph::add_edge(int v, int w){
   adj[v].push_back(w);
}

void Graph::topological_sort_util(int v){
    visited[v]=true;
    for(list<int>::iterator i=adj[v].begin();i!=adj[v].end();i++){
       if(!visited[*i])
          topological_sort_util(*i);
    } 
    st.push(v);

}

void Graph::topological_sort(){
   for(int i=0;i<v;i++)  visited[i]=false;
   for(int i=0;i<v;i++){
     if(visited[i]==false)
        topological_sort_util(i);
   }
   while(!st.empty()){
      cout<<st.top()<<" ";
      st.pop();
   }

}

int main(){
   Graph g(6);
   g.add_edge(5,2);
   g.add_edge(5,0);
   g.add_edge(4,0);
   g.add_edge(4,1);
   g.add_edge(2,3);
   g.add_edge(3,1);

   cout<< "Following is a Topological Sorting of a given graph: \n"
   g.topolocal_sort();
   return 0;


}

```

