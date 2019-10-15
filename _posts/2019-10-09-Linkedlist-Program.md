---
title: Linked List- Program
tags: [Program, Implementation, Java, C  ]
style: fill
color: primary
description: A linked list is a linear data structure where each element is a separate object.
---

### For Detailed Concept [click here](https://ds.nisarahmed.me/concept/Linkedlist)
### [c](#c) , [Java](#java)
### <a name= "c"></a>C program to implement linked list
```


#include <stdio.h>
#include <stdlib.h>
 
struct node {
   int data;
   struct node *next;
};
 
struct node *start = NULL;
void insert_at_begin(int);
void insert_at_end(int);
void traverse();
void delete_from_begin();
void delete_from_end();
int count = 0;
 
int main () {
   int input, data;
   
   for (;;) {
      printf("1. Insert an element at beginning of linked list.\n");
      printf("2. Insert an element at end of linked list.\n");
      printf("3. Traverse linked list.\n");
      printf("4. Delete element from beginning.\n");
      printf("5. Delete element from end.\n");
      printf("6. Exit\n");
     
      scanf("%d", &input);
     
      if (input == 1) {
         printf("Enter value of element\n");
         scanf("%d", &data);
         insert_at_begin(data);
      }
      else if (input == 2) {
         printf("Enter value of element\n");
         scanf("%d", &data);
         insert_at_end(data);
      }
      else if (input == 3)
         traverse();
      else if (input == 4)
         delete_from_begin();  
      else if (input == 5)
         delete_from_end();
      else if (input == 6)
         break;
      else
         printf("Please enter valid input.\n");      
   }
   
   return 0;
}
 
void insert_at_begin(int x) {
   struct node *t;
   
   t = (struct node*)malloc(sizeof(struct node));
   count++;
     
   if (start == NULL) {
      start = t;
      start->data = x;
      start->next = NULL;
      return;
   }
   
   t->data = x;
   t->next = start;
   start = t;
}
 
void insert_at_end(int x) {
   struct node *t, *temp;
   
   t = (struct node*)malloc(sizeof(struct node));
   count++;
   
   if (start == NULL) {
      start = t;
      start->data = x;
      start->next = NULL;
      return;
   }
   
   temp = start;
   
   while (temp->next != NULL)
      temp = temp->next;  
   
   temp->next = t;
   t->data    = x;
   t->next    = NULL;
}
 
void traverse() {
   struct node *t;
   
   t = start;
   
   if (t == NULL) {
      printf("Linked list is empty.\n");
      return;
   }
   
   printf("There are %d elements in linked list.\n", count);
   
   while (t->next != NULL) {
      printf("%d\n", t->data);
      t = t->next;
   }
   printf("%d\n", t->data);
}
 
void delete_from_begin() {
   struct node *t;
   int n;
   
   if (start == NULL) {
      printf("Linked list is already empty.\n");
      return;
   }
   
   n = start->data;
   t = start->next;
   free(start);
   start = t;
   count--;
   
   printf("%d deleted from beginning successfully.\n", n);
}
 
void delete_from_end() {
   struct node *t, *u;
   int n;
     
   if (start == NULL) {
      printf("Linked list is already empty.\n");
      return;
   }
   
   count--;
   
   if (start->next == NULL) {
      n = start->data;
      free(start);
      start = NULL;
      printf("%d deleted from end successfully.\n", n);
      return;
   }
   
   t = start;
   
   while (t->next != NULL) {
      u = t;
      t = t->next;
   }
   
   n = t->data;
   u->next = NULL;
   free(t);
   
   printf("%d deleted from end successfully.\n", n);
}


```
### <a name="java"></a>Java program to implement linked list






#### Java LinkedList Example
```
import java.util.*;  
public class LinkedList1{  
 public static void main(String args[]){  
  
  LinkedList<String> al=new LinkedList<String>();  
  al.add("Ravi");  
  al.add("Vijay");  
  al.add("Ravi");  
  al.add("Ajay");  
  
  Iterator<String> itr=al.iterator();  
  while(itr.hasNext()){  
   System.out.println(itr.next());  
  }  
 }  
}  
```
```
Output: Ravi
       Vijay
       Ravi
       Ajay
```
#### Java LinkedList example to add elements
Here, we see different ways to add elements.
```
import java.util.*;  
public class LinkedList2{  
 public static void main(String args[]){  
 LinkedList<String> ll=new LinkedList<String>();  
           System.out.println("Initial list of elements: "+ll);  
           ll.add("Ravi");  
           ll.add("Vijay");  
           ll.add("Ajay");  
           System.out.println("After invoking add(E e) method: "+ll);  
           //Adding an element at the specific position  
           ll.add(1, "Gaurav");  
           System.out.println("After invoking add(int index, E element) method: "+ll);  
           LinkedList<String> ll2=new LinkedList<String>();  
           ll2.add("Sonoo");  
           ll2.add("Hanumat");  
           //Adding second list elements to the first list  
           ll.addAll(ll2);  
           System.out.println("After invoking addAll(Collection<? extends E> c) method: "+ll);  
           LinkedList<String> ll3=new LinkedList<String>();  
           ll3.add("John");  
           ll3.add("Rahul");  
           //Adding second list elements to the first list at specific position  
           ll.addAll(1, ll3);  
           System.out.println("After invoking addAll(int index, Collection<? extends E> c) method: "+ll);  
           //Adding an element at the first position  
           ll.addFirst("Lokesh");  
           System.out.println("After invoking addFirst(E e) method: "+ll);  
           //Adding an element at the last position  
           ll.addLast("Harsh");  
           System.out.println("After invoking addLast(E e) method: "+ll);  
             
 }  
}  
```
```
Initial list of elements: []
After invoking add(E e) method: [Ravi, Vijay, Ajay]
After invoking add(int index, E element) method: [Ravi, Gaurav, Vijay, Ajay]
After invoking addAll(Collection<? extends E> c) method: 
[Ravi, Gaurav, Vijay, Ajay, Sonoo, Hanumat]
After invoking addAll(int index, Collection<? extends E> c) method: 
[Ravi, John, Rahul, Gaurav, Vijay, Ajay, Sonoo, Hanumat]
After invoking addFirst(E e) method: 
[Lokesh, Ravi, John, Rahul, Gaurav, Vijay, Ajay, Sonoo, Hanumat]
After invoking addLast(E e) method: 
[Lokesh, Ravi, John, Rahul, Gaurav, Vijay, Ajay, Sonoo, Hanumat, Harsh]
```
#### Java LinkedList example to remove elements
 Here, we see different ways to remove an element.

```
import java.util.*;  
public class LinkedList3 {  
  
        public static void main(String [] args)  
        {  
           LinkedList<String> ll=new LinkedList<String>();  
           ll.add("Ravi");  
           ll.add("Vijay");  
           ll.add("Ajay");  
           ll.add("Anuj");  
           ll.add("Gaurav");  
           ll.add("Harsh");  
           ll.add("Virat");  
           ll.add("Gaurav");  
           ll.add("Harsh");  
           ll.add("Amit");  
           System.out.println("Initial list of elements: "+ll);  
         //Removing specific element from arraylist  
              ll.remove("Vijay");  
              System.out.println("After invoking remove(object) method: "+ll);   
         //Removing element on the basis of specific position  
              ll.remove(0);  
              System.out.println("After invoking remove(index) method: "+ll);   
              LinkedList<String> ll2=new LinkedList<String>();  
              ll2.add("Ravi");  
              ll2.add("Hanumat");  
         // Adding new elements to arraylist  
              ll.addAll(ll2);  
              System.out.println("Updated list : "+ll);   
         //Removing all the new elements from arraylist  
              ll.removeAll(ll2);  
              System.out.println("After invoking removeAll() method: "+ll);   
         //Removing first element from the list  
              ll.removeFirst();  
              System.out.println("After invoking removeFirst() method: "+ll);  
          //Removing first element from the list  
              ll.removeLast();  
              System.out.println("After invoking removeLast() method: "+ll);  
          //Removing first occurrence of element from the list  
              ll.removeFirstOccurrence("Gaurav");  
              System.out.println("After invoking removeFirstOccurrence() method: "+ll);  
          //Removing last occurrence of element from the list  
              ll.removeLastOccurrence("Harsh");  
              System.out.println("After invoking removeLastOccurrence() method: "+ll);  
  
              //Removing all the elements available in the list       
              ll.clear();  
              System.out.println("After invoking clear() method: "+ll);   
       }  
    }     
    ```
    ```              
Initial list of elements: [Ravi, Vijay, Ajay, Anuj, Gaurav, Harsh, Virat, Gaurav, Harsh, Amit]
After invoking remove(object) method: [Ravi, Ajay, Anuj, Gaurav, Harsh, Virat, Gaurav, Harsh, Amit]
After invoking remove(index) method: [Ajay, Anuj, Gaurav, Harsh, Virat, Gaurav, Harsh, Amit]
Updated list : [Ajay, Anuj, Gaurav, Harsh, Virat, Gaurav, Harsh, Amit, Ravi, Hanumat]
After invoking removeAll() method: [Ajay, Anuj, Gaurav, Harsh, Virat, Gaurav, Harsh, Amit]
After invoking removeFirst() method: [Gaurav, Harsh, Virat, Gaurav, Harsh, Amit]
After invoking removeLast() method: [Gaurav, Harsh, Virat, Gaurav, Harsh]
After invoking removeFirstOccurrence() method: [Harsh, Virat, Gaurav, Harsh]
After invoking removeLastOccurrence() method: [Harsh, Virat, Gaurav]
After invoking clear() method: []
```
#### Java LinkedList Example to reverse a list of elements

```
import java.util.*;  
public class LinkedList4{  
 public static void main(String args[]){  
  
  LinkedList<String> ll=new LinkedList<String>();  
           ll.add("Ravi");  
           ll.add("Vijay");  
           ll.add("Ajay");  
           //Traversing the list of elements in reverse order  
           Iterator i=ll.descendingIterator();  
           while(i.hasNext())  
           {  
               System.out.println(i.next());  
           }  
             
 }  
}  
```
```
Output: Ajay
Vijay
Ravi
```
#### Java LinkedList Example: Book
```
import java.util.*;  
class Book {  
int id;  
String name,author,publisher;  
int quantity;  
public Book(int id, String name, String author, String publisher, int quantity) {  
    this.id = id;  
    this.name = name;  
    this.author = author;  
    this.publisher = publisher;  
    this.quantity = quantity;  
}  
}  
public class LinkedListExample {  
public static void main(String[] args) {  
    //Creating list of Books  
    List<Book> list=new LinkedList<Book>();  
    //Creating Books  
    Book b1=new Book(101,"Let us C","Yashwant Kanetkar","BPB",8);  
    Book b2=new Book(102,"Data Communications & Networking","Forouzan","Mc Graw Hill",4);  
    Book b3=new Book(103,"Operating System","Galvin","Wiley",6);  
    //Adding Books to list  
    list.add(b1);  
    list.add(b2);  
    list.add(b3);  
    //Traversing list  
    for(Book b:list){  
    System.out.println(b.id+" "+b.name+" "+b.author+" "+b.publisher+" "+b.quantity);  
    }  
}  
} 

```
```
Output:

101 Let us C Yashwant Kanetkar BPB 8
102 Data Communications & Networking Forouzan Mc Graw Hill 4
103 Operating System Galvin Wiley 6
```



 ```
  /***************************************************************************
 * A Linked List class with a private static inner Node class.
 *
 *****************************************************************************/

import java.util.*;

public class LinkedList<AnyType> implements Iterable<AnyType>
{
   private Node<AnyType> head;

 /**
   *  Constructs an empty list
   */
   public LinkedList()
   {
      head = null;
   }
 /**
   *  Returns true if the list is empty
   *
   */
   public boolean isEmpty()
   {
      return head == null;
   }
 /**
   *  Inserts a new node at the beginning of this list.
   *
   */
   public void addFirst(AnyType item)
   {
      head = new Node<AnyType>(item, head);
   }
 /**
   *  Returns the first element in the list.
   *
   */
   public AnyType getFirst()
   {
      if(head == null) throw new NoSuchElementException();

      return head.data;
   }
 /**
   *  Removes the first element in the list.
   *
   */
   public AnyType removeFirst()
   {
      AnyType tmp = getFirst();
      head = head.next;
      return tmp;
   }
 /**
   *  Inserts a new node to the end of this list.
   *
   */
   public void addLast(AnyType item)
   {
      if( head == null)
         addFirst(item);
      else
      {
         Node<AnyType> tmp = head;
         while(tmp.next != null) tmp = tmp.next;

         tmp.next = new Node<AnyType>(item, null);
      }
   }
 /**
   *  Returns the last element in the list.
   *
   */
   public AnyType getLast()
   {
      if(head == null) throw new NoSuchElementException();

      Node<AnyType> tmp = head;
      while(tmp.next != null) tmp = tmp.next;

      return tmp.data;
   }
 /**
   *  Removes all nodes from the list.
   *
   */
   public void clear()
   {
      head = null;
   }
 /**
   *  Returns true if this list contains the specified element.
   *
   */
   public boolean contains(AnyType x)
   {
      for(AnyType tmp : this)
         if(tmp.equals(x)) return true;

      return false;
   }
 /**
   *  Returns the data at the specified position in the list.
   *
   */
   public AnyType get(int pos)
   {
      if (head == null) throw new IndexOutOfBoundsException();

      Node<AnyType> tmp = head;
      for (int k = 0; k < pos; k++) tmp = tmp.next;

      if( tmp == null) throw new IndexOutOfBoundsException();

      return tmp.data;
   }
 /**
   *  Returns a string representation
   *
   */
   public String toString()
   {
      StringBuffer result = new StringBuffer();
      for(Object x : this)
      	result.append(x + " ");

      return result.toString();
   }
 /**
   *  Inserts a new node after a node containing the key.
   *
   */
   public void insertAfter(AnyType key, AnyType toInsert)
   {
      Node<AnyType> tmp = head;

      while(tmp != null && !tmp.data.equals(key)) tmp = tmp.next;

      if(tmp != null)
         tmp.next = new Node<AnyType>(toInsert, tmp.next);
   }
 /**
   *  Inserts a new node before a node containing the key.
   *
   */
   public void insertBefore(AnyType key, AnyType toInsert)
   {
      if(head == null) return;

      if(head.data.equals(key))
      {
         addFirst(toInsert);
         return;
      }

      Node<AnyType> prev = null;
      Node<AnyType> cur = head;

      while(cur != null && !cur.data.equals(key))
      {
         prev = cur;
         cur = cur.next;
      }
      //insert between cur and prev
      if(cur != null)
         prev.next = new Node<AnyType>(toInsert, cur);
   }
 /**
   *  Removes the first occurrence of the specified element in this list.
   *
   */
   public void remove(AnyType key)
   {
      if(head == null)
         throw new RuntimeException("cannot delete");

      if( head.data.equals(key) )
      {
         head = head.next;
         return;
      }

      Node<AnyType> cur  = head;
      Node<AnyType> prev = null;

      while(cur != null && !cur.data.equals(key) )
      {
         prev = cur;
         cur = cur.next;
      }

      if(cur == null)
         throw new RuntimeException("cannot delete");

      //delete cur node
      prev.next = cur.next;
   }
 /**
   *  Returns a deep copy of the list
   *  Complexity: O(n^2)
   */
   public  LinkedList<AnyType> copy1()
   {
      LinkedList<AnyType> twin = new LinkedList<AnyType>();
      Node<AnyType> tmp = head;
      while(tmp != null)
      {
         twin.addLast( tmp.data );
         tmp = tmp.next;
      }

      return twin;
   }
 /**
   *  Returns a deep copy of the list
   *  Complexity: O(n)
   */
   public LinkedList<AnyType> copy2()
   {
      LinkedList<AnyType> twin = new LinkedList<AnyType>();
      Node<AnyType> tmp = head;
      while(tmp != null)
      {
         twin.addFirst( tmp.data );
         tmp = tmp.next;
      }

      return twin.reverse();
   }
 /**
   *  Reverses the list
   *  Complewxity: O(n)
   */
   public LinkedList<AnyType> reverse()
   {
      LinkedList<AnyType> list = new LinkedList<AnyType>();
      Node<AnyType> tmp = head;
      while(tmp != null)
      {
         list.addFirst( tmp.data );
         tmp = tmp.next;
      }
      return list;
   }
 /**
   *  Returns a deep copy of the immutable list
   *  It uses a tail reference.
   *  Complexity: O(n)
   */
   public LinkedList<AnyType> copy3()
   {
      LinkedList<AnyType> twin = new LinkedList<AnyType>();
      Node<AnyType> tmp = head;
      if(head==null) return null;
      twin.head = new Node<AnyType>(head.data, null);
      Node<AnyType> tmpTwin = twin.head;
      while(tmp.next != null)
      {
         tmp = tmp.next;
         tmpTwin.next = new Node<AnyType>(tmp.data, null);
         tmpTwin = tmpTwin.next;
      }

      return twin;
   }

 /*******************************************************
 *
 *  The Node class
 *
 ********************************************************/
   private static class Node<AnyType>
   {
      private AnyType data;
      private Node<AnyType> next;

      public Node(AnyType data, Node<AnyType> next)
      {
         this.data = data;
         this.next = next;
      }
   }

 /*******************************************************
 *
 *  The Iterator class
 *
 ********************************************************/

   public Iterator<AnyType> iterator()
   {
      return new LinkedListIterator();
   }

   private class LinkedListIterator  implements Iterator<AnyType>
   {
      private Node<AnyType> nextNode;

      public LinkedListIterator()
      {
         nextNode = head;
      }

      public boolean hasNext()
      {
         return nextNode != null;
      }

      public AnyType next()
      {
         if (!hasNext()) throw new NoSuchElementException();
         AnyType res = nextNode.data;
         nextNode = nextNode.next;
         return res;
      }

      public void remove() { throw new UnsupportedOperationException(); }
   }



/*****   Include the main() for testing and debugging  *****/


   public static void main(String[] args)
   {
      LinkedList<String> list = new LinkedList <String>();
      list.addFirst("p");
      list.addFirst("a");
      list.addFirst("e");
      list.addFirst("h");
      System.out.println(list);

		LinkedList<String> twin = list.copy3();
      System.out.println(twin);

      System.out.println(list.get(0));
//		System.out.println(list.get(4));   //exception

      list.addLast("s");
      Iterator itr = list.iterator();
      while(itr.hasNext())
         System.out.print(itr.next() + " ");
      System.out.println();

      for(Object x : list)
         System.out.print(x + " ");
      System.out.println();

      list.insertAfter("e", "ee");
      System.out.println(list);
      System.out.println(list.getLast());

      list.insertBefore("h", "yy");
      System.out.println(list);

      list.remove("p");
      System.out.println(list);
	}
}


````