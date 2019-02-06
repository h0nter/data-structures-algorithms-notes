# Lecture 1
### Assesment
**Coursework:** Week 8, 12%; Week 12, 28%; = 40%
**Exam:** 60%

### Contents
**Data Structure:**
- A systematic way of organising and accessing data
- **No single, correct way** of doing this
- Depends on the problem

**Algorithm:**
- A finite sequence of basic operations, which for every valid input produce some output

**Algorithms + Data Structures = Programs**

---
### Data Structures
**Linear Data Structures**
- Arrays
- Linked Lists
- Queues
- Stacks

**Non-linear Data Structures**
- Trees
- Graphs

**Arrays**
- List of values referenced by array index
- Fixed size structure
- Objects (in Java)

**Linked Lists**
- Has a **head**
- Each **node** contains:
  - Data
  - **Next** pointer
  - Last item links to 'null'
- Ends with a **tail**

**Code requirements:**
- ListNode class
```java
public class ListNode{
  //instance variables
  pribate Object data;
  private ListNode next;
  
  //Constructor
  public ListNode(Object data, ListNode next){
    this.data = data;
    this.next = next;
  }
  
  //Get data from this node
  public Object getData(){
    return data;
  }
  
  //Set data for this node
  public void setData(Object data){
    this.data = data;
  }
  
  //Get the next list node
  public ListNode getNext(){
    return next;
  }
  
  public void setNext(ListNode next){
    this.next = next;
  }

}
```
- LinkedList class
```java
public class LinkedList{
  //instance variables
  private ListNode head;
  private int size;
  
  //Constructor
  public ListNode(){
    head = null;
    size = 0;
  }
  
  //Add another node to the list
  public void addFirst(ListNode n){
    n.setNext(head);
    head = n;
    size++;
  }
  
  public void addLast(ListNode n){
    if (!isEmpty()){
      ListNode cNode = head;
      ListNode next = head.getNext();
      while(next != null){
        cNode = next;
        next = cNode.getNext();
      }
      cNode.setNext(n);
      n.setNext(null);
      size++;
    }
  }
  
  public void addAt(ListNode n, int i){
    if (!isEmpty() && i <= size){
      ListNode cNode = head;
      ListNode next = head.getNext();
      for(int j = 1; j < i - 1; j++){
        cNode = next;
        next = cNode.getNext();
      }
      n.setNext(next);
      cNode.setNext(n);
      size++;
    }
  }
  
  //Remove node from the list
  public void removeFirst(){
    if (size > 1){
      head = head.getNext();
    }else{
      head = null;
    }
    size--;
  }
  
  public void removeLast(){
    if (!isEmpty()){
      ListNode cNode = head;
      ListNode next = head.getNext();
      for(int i = 1; i < size - 1; i++){
        cNode = next;
        next = cNode.getNext();
      }
      cNode.setNext(null);
      size--;
    }
  }
  
  public void removeAt(int index){
    if (!isEmpty() && index <= size && index >= 1){
      ListNode cNode = head;
      ListNode next = head.getNext();
      for(int i = 1; i < index - 1; i++){
        cNode = next;
        next = cNode.getNext();
      }
      if (size > 1){
        cNode.setNext(next.getNext());
      }else{
        head = null;
      }
      size--;
    }
  }
  
  //Test if the list is empty
  public boolean isEmpty(){
    return size < 1;
  }
  
  //Get the number of items in the list
  public int size(){
    return size;
  }
}
```
