class node {
    public:
      node* next;
      int val;
      node()=default;
      node(node* node=nullptr,int val=0):next(node),val(val){}
};



class MyLinkedList {
public:
    node* linkhead;
    int size;
    MyLinkedList():size(0){
        linkhead = new node();
    }
    
    int get(int index) {
      if(index>=size)return -1;
      node* temp = linkhead;
      for (int i = 0; i < index; i++) temp = temp->next;
      return temp->next->val;  
    }
    
    void addAtHead(int val) {
        node* newhead = new node(linkhead->next,val);
        linkhead->next = newhead;
        size++;
    }
    
    void addAtTail(int val) {
        addAtIndex(size, val)
    }
    
    void addAtIndex(int index, int val) {
        if (index==-1||index>size) return;
        if (index==0) {addAtHead(val);return;}
        node* front = linkhead;
        for (int i = 0; i < index; i++) front = front->next;
        node* newnode = new node(front->next,val);  
        front->next = newnode;
        size++;          
    }
    
    void deleteAtIndex(int index) {
        if(index==-1||index>size-1) return;
        if(index==0) {
            node* temp = linkhead->next;
            linkhead->next = linkhead->next->next;
            delete temp;
            size--;
            return;
        }
        node* front = linkhead;
        for (int i = 0; i < index; i++) front = front->next;
        node* temp = front->next;
        front->next = front->next->next;
        delete temp;
        size--;
    }
};
