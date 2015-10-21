# Coding-Interview-
Removing duplicates from the Linked List
package Test;
import java.util.Hashtable;

public class LinkedList1{
    public LinkedList1 next;
    public int data;
    
    
    public LinkedList1(int data){
        this.data = data;
    }
public void display(){
    System.out.println("Node" + ":" + data);
}     
    
 public static void main (String[] args){
    Linked runobj = new Linked();
    runobj.insertFirstLink(700);
    runobj.insertFirstLink(500);
    runobj.insertFirstLink(300);
    runobj.insertFirstLink(100);
    runobj.insertFirstLink(500);
    runobj.insertFirstLink(700);
    runobj.insertFirstLink(500);
    runobj.insertFirstLink(700);
    runobj.insertFirstLink(100);
    runobj.display();
    System.out.println("");
    System.out.println("");
    System.out.println("");
    LinkedList1 x = runobj.deletedups();
    runobj.display();
}   
}   

class Linked{
    public LinkedList1 firstLink;
    
    Linked(){
        
        firstLink = null;
    }
public boolean isEmpty(){
    return firstLink == null;
    }
public void insertFirstLink(int data){
    LinkedList1 newLink = new LinkedList1(data);
    newLink.next = firstLink;
    firstLink = newLink;
}

public void display(){
    LinkedList1 linkref = firstLink;
    while (linkref != null){
        linkref.display();
        System.out.println("Next Line" + linkref.next);
        linkref = linkref.next;
        //System.out.println();
    }
}    
    
public LinkedList1 deletedups(){
    
    Hashtable ht = new Hashtable();
    if (firstLink == null){
       System.out.println("Empty List");
    }  
    LinkedList1 currNode = firstLink.next;
    LinkedList1 prevNode = firstLink;
    int count =0;
    while(currNode!=null){
			int data = currNode.data;
			if(ht.contains(data)){
				prevNode.next = currNode.next;
				currNode = currNode.next;
			}else{
				ht.put(count, data);
				count++;
				prevNode = currNode;
				currNode = currNode.next;
			}
		
	}return firstLink;
}
}  
