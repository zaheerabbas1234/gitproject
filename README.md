public class ArrayStackDemo {

    // Stack interface
    public interface Stack {
        void push(Object ob);
        Object pop();
        Object peek();
        boolean isEmpty();
        int size();
    }

    // ArrayStack class implementing the Stack interface
    public static class ArrayStack implements Stack {
        private Object[] a; // stack array
        private int top; // stack top
        
        public ArrayStack(int n) { // constructor
            a = new Object[n]; // create stack array
            top = -1; // no items in the stack
        }
        
        public void push(Object item) { // add an item on top of stack
            if (top == a.length - 1) {
                System.out.println("Stack is full");
                return;
            }
            top++; // increment top
            a[top] = item; // insert an item
        }
        
        public Object pop() { // remove an item from top of stack
            if (isEmpty()) {
                System.out.println("Stack is empty");
                return null;
            }
            Object item = a[top]; // access top item
            top--; // decrement top
            return item;
        }
        
        public Object peek() { // get top item of stack
            if (isEmpty()) return null;
            return a[top];
        }
        
        public boolean isEmpty() { // true if stack is empty
            return (top == -1);
        }
        
        public int size() { // returns number of items in the stack
            return top + 1;
        }
    }

    // Main class to demonstrate the stack
    public static void main(String[] args) {
        ArrayStack stk = new ArrayStack(4); // create stack of size 4
        Object item;
        
        stk.push('A'); // push 3 items onto stack
        stk.push('B');
        stk.push('C');
        System.out.println("size(): " + stk.size());
        
        item = stk.pop(); // delete item
        System.out.println(item + " is deleted");
        
        stk.push('D'); // add three more items to the stack
        stk.push('E');
        stk.push('F');
        System.out.println(stk.pop() + " is deleted");
        
        stk.push('G'); // push one item
        item = stk.peek(); // get top item from the stack
        System.out.println(item + " is on top of stack");
    }
}
