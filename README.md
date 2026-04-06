# hospital-queue-management-system
Hospital Queue using Circular Queue in C++
#include <iostream>
using namespace std;

#define MAX 5

// Patient structure
struct Patient {
    int id;
    string name;
};

// Circular Queue
class Queue {
    Patient data[MAX];
    int front, rear;

public:
    Queue() {
        front = -1;
        rear = -1;
    }

    bool isEmpty() {
        return front == -1;
    }

    bool isFull() {
        return front == (rear + 1) % MAX;
    }

    void enqueue(int id, string name) {
        if (isFull()) {
            cout << "Queue is full\n";
            return;
        }

        if (isEmpty()) {
            front = rear = 0;
        } else {
            rear = (rear + 1) % MAX;
        }

        data[rear].id = id;
        data[rear].name = name;
    }

    void dequeue() {
        if (isEmpty()) {
            cout << "Queue is empty\n";
            return;
        }

        cout << "Serving: ID=" << data[front].id
             << " Name=" << data[front].name << endl;

        if (front == rear) {
            front = rear = -1;
        } else {
            front = (front + 1) % MAX;
        }
    }

    void display() {
        if (isEmpty()) {
            cout << "No patients\n";
            return;
        }

        int i = front;
        while (true) {
            cout << "[ID:" << data[i].id << " " << data[i].name << "] ";
            if (i == rear) break;
            i = (i + 1) % MAX;
        }
        cout << endl;
    }

    int count() {
        if (isEmpty()) return 0;

        if (rear >= front)
            return rear - front + 1;
        else
            return MAX - front + rear + 1;
    }

    void peek() {
        if (!isEmpty()) {
            cout << "Next Patient: ID=" << data[front].id
                 << " Name=" << data[front].name << endl;
        } else {
            cout << "Queue is empty\n";
        }
    }
};

int main() {
    Queue normal, emergency;

    int choice, id, type;
    string name;

    while (true) {
        cout << "\n1.Add Patient\n2.Serve Patient\n3.Display\n4.Count\n5.Peek\n6.Exit\n";
        cout << "Enter choice: ";
        cin >> choice;

        switch (choice) {

        case 1:
            cout << "Enter ID: ";
            cin >> id;

            cout << "Enter Name: ";
            cin >> name;

            cout << "Type (1-Emergency, 2-Normal): ";
            cin >> type;

            if (type == 1)
                emergency.enqueue(id, name);
            else
                normal.enqueue(id, name);
            break;

        case 2:
            if (!emergency.isEmpty())
                emergency.dequeue();
            else
                normal.dequeue();
            break;

        case 3:
            cout << "Emergency Queue: ";
            emergency.display();
            cout << "Normal Queue: ";
            normal.display();
            break;

        case 4:
            cout << "Emergency Count: " << emergency.count() << endl;
            cout << "Normal Count: " << normal.count() << endl;
            break;

        case 5:
            if (!emergency.isEmpty())
                emergency.peek();
            else
                normal.peek();
            break;

        case 6:
            return 0;

        default:
            cout << "Invalid choice\n";
        }
    }
}
