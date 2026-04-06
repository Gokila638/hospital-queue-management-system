# Hospital Queue Management System

This project simulates a hospital queue using a **circular queue** in C++. It handles **Emergency** and **Normal** patients separately and serves Emergency patients first.

## Features
- Add patient (Emergency or Normal)
- Serve patient (Emergency priority)
- Display all patients in queues
- Count patients in each queue
- Peek next patient to be served
- Exit program

## Data Structure
- **Circular Queue (FIFO)** with fixed size (`MAX = 5`)  
- Emergency patients are always served first; Normal patients are served only if there are no emergency patients.

## Sample Console Output (One Example per Option)

### 1. Add Patient
## Sample Console Output (One Example per Menu Option)

### 1. Add Patient
Enter choice: 1  
Enter ID: 101  
Enter Name: Alice  
Type (1-Emergency, 2-Normal): 1  

---

### 2. Serve Patient
Enter choice: 2  
Serving: ID=101 Name=Arun

---

### 3. Display Queues
Enter choice: 3  
Emergency Queue: [ID:101 Arun]  
Normal Queue: No patients  

---

### 4. Count Patients
Enter choice: 4  
Emergency Count: 1  
Normal Count: 0  

---

### 5. Peek Next Patient
Enter choice: 5  
Next Patient: ID=101 Name=Arun

---

### 6. Exit Program
Enter choice: 6  
Program exited
