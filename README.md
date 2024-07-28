import java.util.Scanner;
import java.util.Stack;

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        // Read the size of the queue
        int n = scanner.nextInt();

        Queue queue = new Queue();

        // Enqueue 0 to N-1 numbers
        for (int i = 0; i < n; i++) {
            queue.enqueue(i);
        }

        // Dequeue all elements and print them
        while (!queue.isEmpty()) {
            System.out.print(queue.dequeue() + " ");
        }
    }
}

class Queue {
    private Stack<Integer> stack1;
    private Stack<Integer> stack2;

    public Queue() {
        stack1 = new Stack<>();
        stack2 = new Stack<>();
    }

    // Enqueue operation
    public void enqueue(int value) {
        stack1.push(value);
    }

    // Dequeue operation
    public int dequeue() {
        if (stack2.isEmpty()) {
            while (!stack1.isEmpty()) {
                stack2.push(stack1.pop());
            }
        }
        return stack2.pop();
    }

    // Check if the queue is empty
    public boolean isEmpty() {
        return stack1.isEmpty() && stack2.isEmpty();
    }
}
