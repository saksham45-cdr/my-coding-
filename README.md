# my-coding-
# just personal use case and development 

// Linked list --> linear , non-contigous mmemory type data structure + dynamic [ resizeable at runtime ]
// unidirectional [ traversed in forward usinng head (first node )]
/// some functions of linked list :
// push front --> push element before head  --> counter function : pop front 
// push back --> push at last of linked list --> counter function :pop back 


#include <iostream>
using namespace std ;
struct node {
    int data ;
    node *next ;
};
 
node *head = NULL  ;


// push front function 
void pushfront (int x ){
    node *temp = new node ; // creates a new node 
    temp->data = x ;        // feeds data to new node 
    temp->next =  head ;    // joins the seperate node to the whole                                                        list 
    head = temp;  // updates the head pointer 
    
    
};

/// push back function 
void pushback (int x ){
    node *p = head ;
    while (p->next != NULL){
        p = p->next ;
    }
    
    p->next = new node ;
    p->next->data = x ;
    p->next->next = NULL;
    
};
// this code faults for head= null (empty list) because:“The code assumes a non-empty list; if head is NULL, dereferencing p->next results in a segmentation fault.” 

void display (){
    node *p = head ;
    while (p != NULL){
        cout << p->data << " " ;
        p=p->next ;
        
    }
};

//“Reversal is done by iteratively changing the next pointer of each node to point to its previous node.
void reverseLL (){
    node *curr = head ;
    node *prev = NULL;
    node* nextelement ;
    while (curr!= NULL){
        nextelement = curr->next ;
        curr -> next = prev ;
        prev = curr ;
        curr= nextelement;
        
    }
     head = prev ;
    
    
}



int main() {
    // pointer --> stores adress not value 
    int x = 10 ;
    int *ptr = &x ;
    head = NULL; // points to the first node 

    head = new node ;
    head -> data = 10 ;
    head->next = NULL;

    node *second ;
    second = new node ;
    second -> data = 20 ;
    head->next = second ;
    reverseLL();

    display();
    
    
    
    
    
    
    

    return 0;
}
