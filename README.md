class node{
public:
    int val;
    node* next;
    node(int val=0, node* next=nullptr) : val(val), next(next) {}

};



class MyLinkedList {
public:
    node* headnode;
    node* tailnode;
    int size;
    MyLinkedList() : size(0){
        headnode = new node();
        tailnode = headnode;
    }
    
    int get(int index) {
        if(index>=size)return -1;
        node* temp = headnode;
        for(int i=0;i<index;i++)temp = temp->next;
        return temp->next->val;
    }
    
    void addAtHead(int val) {
        if (size==0) {
            headnode->next = new node(val);
            tailnode = headnode->next;
            size++;
            return;
        }
        node* temp = new node(val,headnode->next);
        headnode->next = temp;
        size++;
    }
    
    void addAtTail(int val) {
        if(size==0) {addAtHead(val);return;}
        node* temp = new node(val);
        tailnode->next = temp;
        tailnode = temp;

    }
    
    void addAtIndex(int index, int val) {
        if(index<0||index>size)return;
        if(index==0&&size==0){addAtHead(val);return;}
        if(index==size){addAtTail(val);}
        node* front = headnode;
        for(int i=0;i<index;i++)front = front->next;
        node* temp = new node(val,front->next->next);
        front->next = temp;
        size++;
    }
    
    void deleteAtIndex(int index) {
        if(index<0||index>=size)return;
        if (size==1&&index==0) {
           node* temp = headnode->next;
           headnode->next = nullptr;
           tailnode = nullptr;
           size--;
           delete temp; 
           return;
        }
        node* temp = headnode;
        for(int i=0;i<index;i++)temp = temp->next;
         node* tem = temp->next ;
        temp->next = temp->next->next;
        delete tem;
        if (index==size-1) tailnode = temp->next;
        size--;
    }
};
