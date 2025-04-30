# Queues
actions in a queue
#include <iostream>
using namespace std;
#define MAX 5 // Maximum size of the queue
class Queue {
int front, rear;
int queue[MAX]; // Array to store elements
public:
Queue() {

        front = -1;
        rear = -1;
    }
    // Enqueue operation to add an element to the queue
    void Enqueue(int value) {
        if (rear == MAX - 1) {
            cout << "Queue is full! Overflow condition.\n";
        } else {
            if (front == -1) front = 0; // Initialize front to 0 on first enqueue
            rear++;
            queue[rear] = value;
            cout << "Enqueued: " << value << endl;
        }
    }
    // Dequeue operation to remove an element from the queue
    void Dequeue() {
        if (front == -1 || front > rear) {
            cout << "Queue is empty! Underflow condition.\n";
        } else {
            cout << "Dequeued: " << queue[front] << endl;
            front++;
            if (front > rear) { // Reset the queue when all elements are dequeued
                front = rear = -1;
            }
        }
    }
    // Display operation to show the queue elements

    void Display() {
        if (front == -1) {
            cout << "Queue is empty!\n";
        } else {
            cout << "Queue elements: ";
            for (int i = front; i <= rear; i++) {
                cout << queue[i] << " ";
            }
            cout << endl;
        }
    }
};
int main() {
    Queue q;
    int choice, value;
    do {
        cout << "\nQueue Operations:\n";
        cout << "1. Enqueue\n";
        cout << "2. Dequeue\n";
        cout << "3. Display\n";
        cout << "4. Exit\n";
        cout << "Enter your choice: ";
        cin >> choice;
        switch (choice) {
        case 1:
            cout << "Enter value to enqueue: ";
            cin >> value;
            q.Enqueue(value);
            break;
        case 2:
            q.Dequeue();
            break;
        case 3:
            q.Display();
            break;
        case 4:
            cout << "Exiting...\n";
            break;
        default:
            cout << "Invalid choice! Please try again.\n";
        }
    } while (choice != 4);
    return 0;
}
