Q1stack push and pop operation.
#include <iostream>
using namespace std;

#define MAX 100

class Stack{
    private:
         int top;
         int arr[MAX];
    
    public:
         Stack(){
            top=-1;
         }    

         //Push Operation
         
         void push(int value){
            if(top>=MAX-1){
                cout<<"Stack Over flow,cannot push"<<value<<endl;
            }
            else{
                arr[++top]=value;
                cout<<value<<" pushed to stack"<<endl;
             }
         }
         //Pop Operation
         void pop(){
               if(top<0){
                cout<<"Stack Underflow:Cannot Pop"<<endl;
                 }
                 else{
                    cout<<arr[top--]<<" popped from stack"<<endl;
                 }
         }

         //Display the stack
         void display(){
            if(top<0){
                cout<<"Stack is empty"<<endl;
            }
            else{
                cout<<"Stack content:";
                for(int i=0;i<=top;i++){
                    cout<<arr[i]<<" ";
                }
                cout<<endl;
            }
         }

};
int main(){
    Stack s;
    s.push(10);
    s.push(20);
    s.push(30);
    s.display();

    s.pop();
    s.display();

    s.pop();
    s.pop();
    s.pop();

    return 0;
}
Q2 Write a c++ code for balanced parentheses.
#include <iostream>
#include <stack>
#include <string>

using namespace std;

bool isBalanced(string expr){
    stack<char> s;
     
    for(char ch:expr){
        if(ch=='('){
            s.push(ch);
        }
        else if(ch==')'){
            if(s.empty()) return false;
            s.pop();
        }
    }
    return s.empty();
}
int main(){
    string input;
    cout<<"Enter Expression:";
    cin>>input;

    if(isBalanced(input)){
        cout<<"Balanced"<<endl;
    }
    else{
        cout<<"Not Balanced"<<endl;
    }
}
3) Write a c++ code for implementing queue using two stacks.
#include <iostream>
#include <stack>

using namespace std;

class Queue{
    private:
       stack<int> s1,s2;

    public:
      //enqueue operations
      void enqueue(int x){
        s1.push(x);
      }

      //dequeue operations
      int dequeue(){
        if(s2.empty()){
            if(s1.empty()){
                cout<<"Queue is empty"<<endl;
                return -1;
            }
            //Transfer s1 to s2
            while(!s1.empty()){
                s2.push(s1.top());
                s1.pop();
            }
        }
        int front = s2.top();
        s2.pop();
        return front;
      }

      //peek operations 
      int peek(){
        if(s2.empty()){
            if(s1.empty()){
                cout<<"Queue is empty"<<endl;
                return -1;
            }
            //Transfer s1 to s2 
            while(!s1.empty()){
                s2.push(s1.top());
                s1.pop();
            }
        }
        return s2.top();
      }

      //check for empty value 
      bool isEmpty(){
        return s1.empty() && s2.empty();
      }
};
int main(){
    Queue q;

    q.enqueue(10);
    q.enqueue(20);
    q.enqueue(30);

    cout<<"Front Element:"<<q.peek()<<endl;
    cout<<"Dequeued:"<<q.dequeue()<<endl;
    cout<<"Dequeued:"<<q.dequeue()<<endl;
    cout<<"Is Queue Empty ? "<<(q.isEmpty() ? "Yes" : "No")<<endl;
    cout<<"Dequeue:"<<q.dequeue()<<endl;
    cout<<"Is Queue is Empty ? "<<(q.isEmpty() ? "Yes":"No")<<endl;
}
4) Write a c++ code for implementing queue front and rear operation.
#include <iostream>
using namespace std;

#define SIZE 5

int queue[SIZE];
int front=-1,rear=-1;

void enqueue(int value){
    if(rear==SIZE-1){
        cout<<"Queue is full\n";
    }else{
        if(front==-1)front=0;
        rear++;
        queue[rear]=value;
     cout<<value<<"enqueued\n";
    }
}
void dequeue(){
    if(front==-1||front>rear){
        cout<<"Queue is full\n";
    }else{
        cout<<queue[front]<<"dequeued\n";
    }
}

void showFront(){
    if(front==-1||front>rear){
        cout<<"Queue is full\n";
    }else{
        cout<<"Front:"<<queue[front]<<endl;
    }
}
void showRear(){
    if(rear==-1|| front>rear){
        cout<<"Queue is full\n";
    }else{
        cout<<"Rear:"<<queue[rear]<<endl;
    }
}
int main(){
    enqueue(10);
    enqueue(20);
    enqueue(30);

    showFront();
    showRear();

    dequeue();
    showFront();
    showRear();

    return 0;
}

5) Write a c++ code for counting total number of nodes in linked list.
   #include <iostream>
using namespace std;

struct Node{
    int data;
    Node*next;
};
int main(){
    Node*head=new Node();
    Node*second=new Node();
    Node*third=new Node();

    head->data=1;
    head->next=second;

    second->data=2;
    second->next=third;

    third->data=3;
    third->next=nullptr;

    int count=0;
    Node*temp=head;
    while(temp!=nullptr){
        count++;
        temp=temp->next;
    }
    cout<<"The number of nodes are "<<count<<endl;

    return 0;

}
6) Write a c++ code for finding cycle in the linked list.
#include <iostream>
using namespace std;

struct Node{
    int data;
    Node*next;
};

bool hasCycle(Node*head){
    Node*slow=head;
    Node*fast=head;

    while(fast && fast->next){
        slow=slow->next;
        fast=fast->next->next;

        if(slow==fast)
        return true;
    }
    return false;
}
int main(){
    Node*a=new Node{1,nullptr};
    Node*b=new Node{2,nullptr};
    Node*c=new Node{3,nullptr};

    a->next=b;
    b->next=c;
    c->next=b;
   
    if(hasCycle(a)){
        cout<<"Cycle is detected in the linked list\n";
    }
    else{
        cout<<"No cycle is detected in the linked list\n";
    }
    return 0;
}

7) Write a c++ code for reversing linked list.
#include <iostream>
using namespace std;

struct Node{
    int data;
    Node*next;
};
void printList(Node*head){
    while(head){
        cout<<head->data<<"->";
        head=head->next;
    }
    cout<<"Null"<<endl;
}
Node*reverseList(Node*head){
    Node*prev=nullptr;
    Node*current=head;

    while(current){
        Node*next=current->next;
        current->next=prev;
        prev=current;
        current=next;
    }
    return prev;
}
int main(){
    Node*head=new Node{1,nullptr};
    head->next=new Node{2,nullptr};
    head->next->next=new Node{3,nullptr};

    cout<<"Original List: ";
    printList(head);

    head=reverseList(head);
    cout<<"Reverse List: ";
    printList(head);

    return 0;
}
8) Write a c++ code for implementing bubble sort.
#include <iostream>
using namespace std;

int main() {
    int arr[] = {5, 3, 8, 4, 2};
    int n = sizeof(arr) / sizeof(arr[0]);

    
    cout << "Original array: ";
    for (int i = 0; i < n; i++)
        cout << arr[i] << " ";
    cout << endl;

    
    for (int i = 0; i < n - 1; i++) {
        for (int j = 0; j < n - i - 1; j++) {
            if (arr[j] > arr[j + 1]) {
                // Swap
                int temp = arr[j];
                arr[j] = arr[j + 1];
                arr[j + 1] = temp;
            }
        }
    }

    cout << "Sorted array:   ";
    for (int i = 0; i < n; i++)
        cout << arr[i] << " ";

    return 0;
}
9) Write a c++ code for implementing selection sort.
#include <iostream>
using namespace std;

int main() {
    int arr[] = {29, 10, 14, 37, 13};
    int n = sizeof(arr) / sizeof(arr[0]);

    // Print unsorted array
    cout << "Unsorted array: ";
    for (int i = 0; i < n; i++)
        cout << arr[i] << " ";
    cout << endl;

    // Selection Sort
    for (int i = 0; i < n - 1; i++) {
        int min = i;
        for (int j = i + 1; j < n; j++) {
            if (arr[j] < arr[min])
                min = j;
        }
        // Swap
        int temp = arr[i];
        arr[i] = arr[min];
        arr[min] = temp;
    }

    // Print sorted array
    cout << "Sorted array:   ";
    for (int i = 0; i < n; i++)
        cout << arr[i] << " ";

    return 0;
}
Write a c++ code for implementing insertion sort.
#include <iostream>
using namespace std;

void insertionSort(int arr[], int n) {
    for (int i = 1; i < n; i++) {
        int key = arr[i];
        int j = i - 1;

        while (j >= 0 && arr[j] > key) {
            arr[j + 1] = arr[j];
            j--;
        }
        arr[j + 1] = key;
    }
}

int main() {
    int arr[] = {12, 11, 13, 5, 6};
    int n = sizeof(arr) / sizeof(arr[0]);
    insertionSort(arr, n);
    for (int i = 0; i < n; i++) cout << arr[i] << " ";
    return 0;
}
11) Write a c++ code for implementing quick sort.
#include <iostream>
using namespace std;

int partition(int arr[], int low, int high) {
    int pivot = arr[high];
    int i = (low - 1);

    for (int j = low; j <= high - 1; j++) {
        if (arr[j] < pivot) {
            i++;
            swap(arr[i], arr[j]);
        }
    }
    swap(arr[i + 1], arr[high]);
    return (i + 1);
}

void quickSort(int arr[], int low, int high) {
    if (low < high) {
        int pi = partition(arr, low, high);
        quickSort(arr, low, pi - 1);
        quickSort(arr, pi + 1, high);
    }
}

int main() {
    int arr[] = {10, 7, 8, 9, 1, 5};
    int n = sizeof(arr) / sizeof(arr[0]);
    quickSort(arr, 0, n - 1);
    for (int i = 0; i < n; i++) cout << arr[i] << " ";
    return 0;
}
12) Write a c++ code for implementing merge sort.
#include <iostream>
using namespace std;

void merge(int arr[], int left, int mid, int right) {
    int n1 = mid - left + 1;
    int n2 = right - mid;

    int L[n1], R[n2];

    for (int i = 0; i < n1; i++) L[i] = arr[left + i];
    for (int i = 0; i < n2; i++) R[i] = arr[mid + 1 + i];

    int i = 0, j = 0, k = left;
    while (i < n1 && j < n2) {
        if (L[i] <= R[j]) {
            arr[k++] = L[i++];
        } else {
            arr[k++] = R[j++];
        }
    }

    while (i < n1) arr[k++] = L[i++];
    while (j < n2) arr[k++] = R[j++];
}

void mergeSort(int arr[], int left, int right) {
    if (left < right) {
        int mid = left + (right - left) / 2;

        mergeSort(arr, left, mid);
        mergeSort(arr, mid + 1, right);
        merge(arr, left, mid, right);
    }
}

int main() {
    int arr[] = {12, 11, 13, 5, 6, 7};
    int n = sizeof(arr) / sizeof(arr[0]);

    mergeSort(arr, 0, n - 1);

    cout << "Sorted array: ";
    for (int i = 0; i < n; i++) cout << arr[i] << " ";
    return 0;
}

13) Write a c++ code for implementing linear search.
#include <iostream>
using namespace std;

int linearSearch(int arr[], int n, int key) {
    for (int i = 0; i < n; i++) {
        if (arr[i] == key) return i;
    }
    return -1;
}

int main() {
    int arr[] = {2, 3, 4, 10, 40};
    int n = sizeof(arr) / sizeof(arr[0]);
    int key = 10;
    int result = linearSearch(arr, n, key);
    if (result != -1)
        cout << "Element found at index " << result;
    else
        cout << "Element not found.";
    return 0;
}
14) Write a c++ code for implementing binary search.
#include <iostream>
using namespace std;

int binarySearch(int arr[], int left, int right, int key) {
    while (left <= right) {
        int mid = left + (right - left) / 2;
        if (arr[mid] == key) return mid;
        if (arr[mid] < key)
            left = mid + 1;
        else
            right = mid - 1;
    }
    return -1;
}

int main() {
    int arr[] = {2, 3, 4, 10, 40};
    int n = sizeof(arr) / sizeof(arr[0]);
    int key = 10;
    int result = binarySearch(arr, 0, n - 1, key);
    if (result != -1)
        cout << "Element found at index " << result;
    else
        cout << "Element not found.";
    return 0;
}
15) Write a c++ code for finding height of the BST.
#include <iostream>
using namespace std;

struct Node {
    int data;
    Node* left;
    Node* right;
    Node(int val) : data(val), left(NULL), right(NULL) {}
};

int findHeight(Node* root) {
    if (root == NULL) return -1;
    int leftHeight = findHeight(root->left);
    int rightHeight = findHeight(root->right);
    return max(leftHeight, rightHeight) + 1;
}

int main() {
    Node* root = new Node(10);
    root->left = new Node(5);
    root->right = new Node(20);
    cout << "Height of the BST: " << findHeight(root);
    return 0;
}
16) Write a c++ code for counting total number of nodes in BST.
#include <iostream>
using namespace std;

struct Node {
    int data;
    Node* left;
    Node* right;
    Node(int val) : data(val), left(NULL), right(NULL) {}
};

int countNodes(Node* root) {
    if (root == NULL) return 0;
    return countNodes(root->left) + countNodes(root->right) + 1;
}

int main() {
    Node* root = new Node(10);
    root->left = new Node(5);
    root->right = new Node(20);
    cout << "Total number of nodes in BST: " << countNodes(root);
    return 0;
}
17) Write a c++ code for implementing BFS.
#include <iostream>
#include <queue>
#include <vector>
using namespace std;

void bfs(int start, vector<vector<int>>& graph, int vertices) {
    vector<bool> visited(vertices, false);
    queue<int> q;

    q.push(start);
    visited[start] = true;

    while (!q.empty()) {
        int node = q.front();
        q.pop();
        cout << node << " ";

        for (int neighbor : graph[node]) {
            if (!visited[neighbor]) {
                visited[neighbor] = true;
                q.push(neighbor);
            }
        }
    }
}

int main() {
    vector<vector<int>> graph = {{1, 2}, {0, 3}, {0, 3}, {1, 2}};
    bfs(0, graph, 4);  // Starting BFS from node 0
    return 0;
}
18) Write a c++ code for implementing DFS.
#include <iostream>
#include <vector>
using namespace std;

void dfs(int node, vector<vector<int>>& graph, vector<bool>& visited) {
    visited[node] = true;
    cout << node << " ";

    for (int neighbor : graph[node]) {
        if (!visited[neighbor]) {
            dfs(neighbor, graph, visited);
        }
    }
}

int main() {
    vector<vector<int>> graph = {{1, 2}, {0, 3}, {0, 3}, {1, 2}};
    vector<bool> visited(4, false);  // 4 vertices
    dfs(0, graph, visited);  // Starting DFS from node 0
    return 0;
}
19) Write a c++ code for implementing graph adjacency list and adjacency matrix.
#include <iostream>
#include <vector>
using namespace std;

// Adjacency List Representation
void adjacencyList(vector<vector<int>>& graph) {
    for (int i = 0; i < graph.size(); i++) {
        cout << "Node " << i << ": ";
        for (int j : graph[i]) {
            cout << j << " ";
        }
        cout << endl;
    }
}

// Adjacency Matrix Representation
void adjacencyMatrix(vector<vector<int>>& graph) {
    int n = graph.size();
    vector<vector<int>> matrix(n, vector<int>(n, 0));
    for (int i = 0; i < n; i++) {
        for (int j : graph[i]) {
            matrix[i][j] = 1;
        }
    }

    for (int i = 0; i < n; i++) {
        for (int j = 0; j < n; j++) {
            cout << matrix[i][j] << " ";
        }
        cout << endl;
    }
}

int main() {
    vector<vector<int>> graph = {{1, 2}, {0, 3}, {0, 3}, {1, 2}};
    cout << "Adjacency List:" << endl;
    adjacencyList(graph);
    cout << "Adjacency Matrix:" << endl;
    adjacencyMatrix(graph);
    return 0;
}
20) Write a c++ code to implement hash table.
#include <iostream>
using namespace std;

int main() {
    const int SIZE = 10;  // Fixed size hash table
    int hashTable[SIZE] = {0};  // Initialize all elements to 0

    // Inserting values into hash table
    int values[] = {15, 25, 35};  // Example values
    for (int i = 0; i < 3; i++) {
        int key = values[i] % SIZE;
        while (hashTable[key] != 0) {
            key = (key + 1) % SIZE;  // Linear probing
        }
        hashTable[key] = values[i];
    }

    // Displaying hash table
    for (int i = 0; i < SIZE; i++) {
        cout << i << ": " << hashTable[i] << endl;
    }
    return 0;
}
