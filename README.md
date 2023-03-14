# Queue_data_structure



import java.util.*;
public class Al_queue {
    //1.queue using stack
   /*
    static class Queue

    {
        static int arr[];
        static int size;
        static int rear;
        Queue(int n)
        {
            arr = new int[n];
            size = n;
            rear = -1;
        }
        public static boolean isEmpty()
        {
            return rear == -1;
        }
        //add opn
        public static void add(int data)
        {
            if(rear == size-1)
            {
                System.out.println("Queue is full");
                return;
            }
            rear = rear+1;
            arr[rear] = data;
        }

        //remove opn
        public static int remove()
        {
            if(isEmpty())
            {
                System.out.println("Empty queue");
                return -1;
            }
            int front = arr[0];
            for(int i=0;i<rear;i++)
            {
                arr[i] = arr[i+1];
            }
            rear = rear-1;
            return front;
        }

        //peek opn
        public static int peek() {
            if (isEmpty())
            {
                System.out.println("Empty queue");
                return -1;
            }
            return arr[0];
        }

    }
    public static void main(String args[])
    {
        Queue q = new Queue(5);
        q.add(1);
        q.add(2);
        q.add(3);
        while(!q.isEmpty())
        {
            System.out.println(q.peek());
            q.remove();
        }
    }

    */


    //2 Circular queue using array
    /*
    static class Queue

    {
        static int arr[];
        static int size;
        static int rear;
        static int front;
        Queue(int n)
        {
            arr = new int[n];
            size = n;
            rear = -1;
            front = -1;
        }
        public static boolean isEmpty()
        {
            return rear == -1 && front == -1;
        }
        public static boolean isFull()
        {
            return (rear+1)%size == front;
        }
        //add opn
        public static void add(int data)
        {
            if(isFull())
            {
                System.out.println("Queue is full");
                return;
            }
            //add 1st element
            if(front == -1)
            {
                front =0;
            }
            rear = (rear+1)%size;
            arr[rear] = data;
        }

        //remove opn
        public static int remove()
        {
            if(isEmpty())
            {
                System.out.println("Empty queue");
                return -1;
            }
            int result = arr[front];
            //last elem delete
            if(rear == front)
            {
                rear = front = -1;
            }
            else
            {
                front = (front+1)%size;
            }
            return result;
        }

        //peek opn
        public static int peek() {
            if (isEmpty())
            {
                System.out.println("Empty queue");
                return -1;
            }
            return arr[front];
        }

    }
    public static void main(String args[])
    {
        Queue q = new Queue(5);
        q.add(1);
        q.add(2);
        q.add(3);
        System.out.println(q.remove());
        q.add(4);
        System.out.println(q.remove());
        q.add(5);
        while(!q.isEmpty())
        {
            System.out.println(q.peek());
            q.remove();
        }
    }

     */




    //3 implement queue using linked list
    /*static class Node
    {
        int data;
        Node next;

        Node(int data)
        {
            this.data = data;
            this.next = null;
        }
    }
    static class Queue
    {
        static Node head = null;
        static Node tail = null;
        public static boolean isEmpty()
        {
            return head==null && tail==null;
        }
        //add opn
        public static void add(int data)
        {
            Node newNode = new Node(data);
            if(head == null)
            {
               head = tail = newNode;
               return;
            }
            tail.next = newNode;
            tail = newNode;
        }

        //remove opn
        public static int remove()
        {
            if(isEmpty())
            {
                System.out.println("Empty queue");
                return -1;
            }
            int front = head.data;
            //single elem
            if(tail == head)
            {
                tail = head = null;
            }
            else
            {
                head = head.next;
            }
            return front;
        }

        //peek opn
        public static int peek() {
            if (isEmpty())
            {
                System.out.println("Empty queue");
                return -1;
            }
            return head.data;
        }

    }
    public static void main(String args[])
    {
        Queue q = new Queue();
        q.add(1);
        q.add(2);
        q.add(3);
        while(!q.isEmpty())
        {
            System.out.println(q.peek());
            q.remove();
        }
    }

     */



    //4 implement queue using collection framework
   /* public static void main(String args[])
    {
       Queue<Integer> q=new LinkedList<>();
        q.add(1);
        q.add(2);
        q.add(6);
        while(!q.isEmpty())
        {
            System.out.println(q.peek());
            q.remove();
        }
    }

    */




    //5 Queue using two stack
    static class Queue
    {
        static Stack<Integer> s1 = new Stack<>();
        static Stack<Integer> s2 = new Stack<>();
        public static boolean isEmpty()
        {
            return s1.isEmpty();
        }
        //Add
        public static void add(int data)
        {
            while(!s1.isEmpty())
            {
                s2.push(s1.pop());
            }
            s1.push(data);
            while(!s2.isEmpty())
            {
                s1.push(s2.pop());
            }
        }
        //remove
        public static int remove()
        {
            if(isEmpty())
            {
                System.out.println("Queue empty");
                return -1;
            }
            return s1.pop();
        }
        //peek
        public static int peek()
        {
            if(isEmpty())
            {
                System.out.println("Queue empty");
                return -1;
            }
            return s1.peek();
        }
    }
    public static void main(String args[])
    {
        Queue q = new Queue();
        q.add(1);
        q.add(2);
        q.add(3);
        while(!q.isEmpty())
        {
            System.out.println(q.peek());
            q.remove();
        }
    }

}
