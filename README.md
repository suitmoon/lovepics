class Node{
public:
    int val;
    Node* next;
    Node() = default;
    Node(int val):val(val),next(nullptr){};
    Node(int val,Node* nextnode):val(val),next(nextnode){};

};



class MyLinkedList {
public:
    int size;
    Node* headnode;
    Node* tailnode;
    MyLinkedList():size(0),headnode(nullptr),tailnode(nullptr){}
    
    
    int get(int index) {
      if(index>=size)return -1;
      Node* targetnode = headnode;
      for(int i =0;i<index;i++)
        targetnode = targetnode->next;
      return targetnode->val;      
    }
    
    void addAtHead(int val) {
	    size++;
        if(headnode){Node* temp = new Node(val,headnode);headnode = temp;}
        else{
            headnode = new Node(val);
            tailnode = headnode;
        }
    }
    
    void addAtTail(int val) {

      if(size==0){addAtHead(val);}
      else{
	Node* temp = new Node(val);
	tailnode->next = temp;
	tailnode = tailnode->next;
      }
      size++;         
    }
    
    void addAtIndex(int index, int val) {
        if(index>size) return;
        if(index==0){addAtHead(val); return;}
		if(index==size){addAtTail(val); return;}
        Node* rear = headnode;	
	    for(int i=0;i<index-1;i++)rear = rear->next;
	    Node* tempnext = rear->next;
	    Node* temp = new Node(val,tempnext);
	    rear->next = temp;	  	
	    size++;
    }
    
    void deleteAtIndex(int index) {
        if(index>=size)return;
	    if(index==0){
            headnode=headnode->next;
            size--;
            if(size==0)tailnode=nullptr;
            return;
        }
	    Node* rear = headnode;
	    for(int i = 0;i<index-1;i++)rear = rear->next;
	    rear->next = rear->next->next;	
    }
};
