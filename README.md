public class QueueDemo {
    
    // Queue interface
    public interface Queue { 
        void insert(Object ob); 
        Object remove(); 
        Object peek(); 
        boolean isEmpty(); 
        int size(); 
    }
    
    // ArrayQueue class implementing the Queue interface
    public static class ArrayQueue implements Queue { 
        private int maxSize; // maximum queue size 
        private Object[] que; // queue is an array 
        private int front; 
        private int rear; 
        private int count; // count of items in queue (queue size) 
        
        public ArrayQueue(int s) { // constructor 
            maxSize = s; 
            que = new Object[maxSize]; 
            front = 0; 
            rear = -1; 
            count = 0; 
        } 
        
        public void insert(Object item) { // add item at rear of queue 
            if (count == maxSize) { 
                System.out.println("Queue is Full"); 
                return; 
            } 
            rear = (rear + 1) % maxSize; 
            que[rear] = item; 
            count++; 
        } 
        
        public Object remove() { // delete item from front of queue 
            if (isEmpty()) { 
                System.out.println("Queue is Empty"); 
                return null; 
            } 
            Object tmp = que[front]; // save item to be deleted 
            que[front] = null; // make deleted item’s cell empty 
            front = (front + 1) % maxSize; 
            count--; 
            return tmp; 
        }
        
        public Object peek() { // peek at front of the queue 
            if (isEmpty()) { 
                System.out.println("Queue is Empty"); 
                return null; 
            } 
            return que[front]; 
        } 
        
        public boolean isEmpty() { // true if the queue is empty 
            return (count == 0); 
        } 
        
        public int size() { // current number of items in the queue 
            return count; 
        } 
        
        public void displayAll() { 
            System.out.print("Queue: "); 
            for (int i = 0; i < count; i++) {
                System.out.print(que[(front + i) % maxSize] + " ");
            }
            System.out.println(); 
        } 
    }

    // Main class to demonstrate the queue
    public static void main(String[] args) { 
        // queue holds a max of 5 items 
        ArrayQueue q = new ArrayQueue(5); 
        Object item; 
        q.insert('A'); 
        q.insert('B'); 
        q.insert('C'); 
        q.displayAll(); 
        item = q.remove(); // delete item 
        System.out.println(item + " is deleted"); 
        item = q.remove(); 
        System.out.println(item + " is deleted"); 
        q.displayAll(); 
        q.insert('D'); // insert 3 more items 
        q.insert('E'); 
        q.insert('F'); 
        q.displayAll(); 
        item = q.remove(); 
        System.out.println(item + " is deleted"); 
        q.displayAll(); 
        System.out.println("peek(): " + q.peek()); 
        q.insert('G'); 
        q.displayAll(); 
        System.out.println("Queue size: " + q.size()); 
    } 
}
