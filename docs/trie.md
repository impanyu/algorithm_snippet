#Trie(Prefix Tree)

## implementing Trie

```c++
class trie_node{
private:
    trie_node** links;
    bool end;
public:
    trie_node(){
       links= new trie_node*[26];
       end=false;
       for(int i=0;i<26;i++) 
         links[i]=0; 
   }
   ~ trie_node(){
       for(int i=0; i<26; i++)
         if(links[i]) delete links[i];   
   }
   bool contains_key(char ch){
      return links[ch-'a']!=nullptr; 
  }
  trie_node* get(char ch){
    return links[ch-'a'];
  }
  void put(char ch, trie_node* node){
      links[ch-'a']=node;
  }
  void set_end(){
      end=true;
  }
  bool is_end(){
      return end;
  }
};

class trie{
private:
  trie_node* root;
  trie_node* search_prefix(string word){
     trie_node* node=root;
     for(int i=0; i<word.length();i++){
         char cur_letter= word[i];
         if(node->contains_key(cur_letter))
              node=node->get(cur_letter);
         else
              return nullptr;
     }
     return node;
  }
   
public:
  trie(){
       root= new trie_node();
  }
  ~trie(){
       delete root;
  }

  void insert(string word){
   trie_node* node= root;
   for(int i=0; i< word.length();i++){
     char cur_letter=word[i];
     if(!node->contains_key(cur_letter))
           node->put(current_char,new trie_node());
     node = node->get(current_letter);
  }
   node->set_end();
 }

 bool search(string key){
    trie_node* node= search_prefix(key);
    return node !=nullptr && node->is_end();
 }
 bool start_with(string prefix){
    trie_node* node=search_prefix(prefix);
    return node!=nullptr;
 }
};
 
 

 
 
  





}


```


