Stack: 
/*
 * Click nbfs://nbhost/SystemFileSystem/Templates/Licenses/license-default.txt to change this license
 * Click nbfs://nbhost/SystemFileSystem/Templates/Classes/Main.java to edit this template
 */
package stack;
import java.util.EmptyStackException;

/**
 *
 * @author ACER
 */
public class Stack {
    private Node top;
    private int length;

    private class Node {
        private int value;
        private Node next;
        
        public Node(int value){
            this.value = value;
            this.next = null;
        }
    }
    
    public Stack(){
        this.top = null;
        this.length = 0;
    }
    
    public int length(){
        return length;
    }
    
    public boolean isEmpty(){
        return length == 0;
    }
    
    public void printStack(){
        Node current = this.top;
        while (current != null){
            System.out.print(current.value + " -> ");
            current = current.next;
        }
        System.out.println("null");
    }
    
    public void push(int value){
        Node newNode = new Node(value);
        if(this.isEmpty()){
            this.top = newNode;
            this.length += 1;
            return;
        }
        newNode.next = this.top;
        this.top = newNode;
        this.length += 1;
    }
    
    public Node pop(){
        if (this.isEmpty()){
            throw new EmptyStackException();
        }
        Node temp = this.top;
        this.top = this.top.next;
        temp.next = null; // optional
        this.length -= 1;
        return temp;
    }
    
    public Node peek(){
        return this.top;
    }
    /**
     * @param args the command line arguments
     */
   public static void main(String[] args) {
         Stack myStack = new Stack();
        
        myStack.push(10);
        myStack.push(20);
        myStack.push(15);
        myStack.push(8);
        myStack.push(6);
        myStack.printStack();
        
        Node poppedNode = myStack.pop();
        System.out.println("Just popped: " + poppedNode.value);
        myStack.printStack();
        System.out.println("Top of stack: " + myStack.peek().value);
    }
}
