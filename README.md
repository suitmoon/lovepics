class Node{
public:
    int val;
    Node* nextnode;
    Node() = default;
    Node(int val):val(val),nextnode(nullptr){};
    Node(int val,node* nextnode):val(val),nextnode(nextnode){};
}



class MyLinkedList {
public:
    int size;
    Node* headnode,tailnode;
    MyLinkedList():size(0),headnode(nullptr),tailnode(nullptr){}
    
    
    int get(int index) {
      if(index>=size)return -1;
      Node* targetnode = headnode;
      for(int i =0;i<index;i++)
        targetnode = targetnode->next;
      return targetnode;      
    }
    
    void addAtHead(int val) {
	size++;
        if(headnode){Node* temp = new Node(val,headnode);headnode = temp;}
        else{headnode = new Node(val);tailnode=headnode;}
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
	for(i=0;i<index-1;i++)rear = rear->next;
	Node* tempnext = rear->next;
	Node* temp = new Node(val,tempnext);
	rear->next = temp;	  	
	size++;
    }
    
    void deleteAtIndex(int index) {
        if(index>=size)return;
	if(index==0){headnode=headnode->next;size--;}
	Node* rear = head;
	for(int i = 0;i<index-1;i++)rear = rear->next;
	rear->next = rear->next->next;	
    }
};

/**
 * Your MyLinkedList object will be instantiated and called as such:
 * MyLinkedList* obj = new MyLinkedList();
 * int param_1 = obj->get(index);
 * obj->addAtHead(val);
 * obj->addAtTail(val);
 * obj->addAtIndex(index,val);
 * obj->deleteAtIndex(index);
 */
