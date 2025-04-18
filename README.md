
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

    return 0;
}
Q2 Write a c++ code for balanced parentheses.
#include <iostream>
#include <stack>
#include <string>

using namespace std;

bool isBalanced(string expr) {
    stack<char> s;

    for (char ch : expr) {
        if (ch == '(') {
            s.push(ch);
        } else if (ch == ')') {
            if (s.empty()) return false;
            s.pop();
        }
    }

    return s.empty();
}

int main() {
    string input;
    cout << "Enter expression: ";
    cin >> input;

    if (isBalanced(input)){
        cout << "Balanced" << endl;
    }else{
        cout << "Not Balanced" << endl;
    }

    return 0;
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

    return 0;
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

    return 0;

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
    return 0;
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

    return 0;
}
8) Write a c++ code for implementing bubble sort.
#include <iostream>
using namespace std;

int main(){
    int arr[]={56,34,64,20,15};
    int n=sizeof(arr)/sizeof(arr[0]);

cout<<"Original array: ";
for(int i=0;i<n;i++){
    cout<<arr[i]<<" ";
}
cout<<endl;



//bubble sort 
for(int i=0;i<n-1;i++){
    for(int j=0;j<n-i-1;j++){

        if(arr[j]>arr[j+1]){

           int temp=arr[j];
            arr[j]=arr[j+1];
            arr[j+1]=temp;
        }
    }
}
cout<<"Sorted array: ";
for(int i=0;i<n;i++){
    cout<<arr[i]<<" ";
}
return 0;
}
9) Write a c++ code for implementing selection sort.
#include <iostream>
using namespace std;

int main(){
    int arr[]={45,34,65,12,67,36,15};
    int n = sizeof(arr)/sizeof(arr[0]);

    cout<<"Original array: ";
    for(int i=0;i<n;i++){
        cout<<arr[i]<<" ";
    }
    cout<<endl;
  
    for(int i=0;i<n-1;i++){
        int min=i;
        for(int j=i+1;j<n;j++){
            if(arr[j]<arr[min])
            min=j;
        }
        int temp=arr[i];
        arr[i]=arr[min];
        arr[min]=temp;
    }
    cout<<"Sorted array: ";
    for(int i=0;i<n;i++){
        cout<<arr[i]<<" ";
    }
    return 0;
}
10)Write a c++ code for implementing insertion sort.
#include <iostream>
using namespace std;

int main(){
    int arr[]={34,23,54,12,75,45};
    int n = sizeof(arr)/sizeof(arr[0]);

    cout<<"Original array: ";
    for(int i=0;i<n;i++){
        cout<<arr[i]<<" ";
    }
    cout<<endl;

    for(int i=1;i<n;i++){
        int key=arr[i];
        int j=i-1;

        while(j>=0 && arr[j]>key){
            arr[j+1]=arr[j];
            j--;
        }
        arr[j+1]=key;
    }
    cout<<"Sorted array: ";
    for(int i=0;i<n;i++){
        cout<<arr[i]<<" ";
 }
}
11) Write a c++ code for implementing quick sort.
#include <iostream>
using namespace std;

int main() {
    int arr[] = {29, 10, 14, 37, 13};
    int n = sizeof(arr) / sizeof(arr[0]);


    cout << "Original array: ";
    for (int i = 0; i < n; i++)
        cout << arr[i] << " ";
    cout << endl;

    int stack[100]; 
    int top = -1;

    stack[++top] = 0;
    stack[++top] = n - 1;

    while (top >= 0) {
        int high = stack[top--];
        int low = stack[top--];

        int pivot = arr[high];
        int i = low - 1;

        for (int j = low; j < high; j++) {
            if (arr[j] < pivot) {
                i++;
                int temp = arr[i];
                arr[i] = arr[j];
                arr[j] = temp;
            }
        }

        int temp = arr[i + 1];
        arr[i + 1] = arr[high];
        arr[high] = temp;

        int p = i + 1; 

        if (p - 1 > low) {
            stack[++top] = low;
            stack[++top] = p - 1;
        }

        if (p + 1 < high) {
            stack[++top] = p + 1;
            stack[++top] = high;
        }
    }

    cout << "Sorted array:   ";
    for (int i = 0; i < n; i++)
        cout << arr[i] << " ";

    return 0;
}
12) Write a c++ code for implementing merge sort
#include <iostream>
using namespace std;

int main() {
    int arr[] = {29, 10, 14, 37, 13};
    int n = sizeof(arr) / sizeof(arr[0]);

    cout << "Unsorted array: ";
    for (int i = 0; i < n; i++)
        cout << arr[i] << " ";
    cout << endl;

    int temp[100];

    for (int size = 1; size < n; size *= 2) {
        for (int left = 0; left < n; left += 2 * size) {
            int mid = min(left + size - 1, n - 1);
            int right = min(left + 2 * size - 1, n - 1);

            int i = left;
            int j = mid + 1;
            int k = left;

            while (i <= mid && j <= right) {
                if (arr[i] < arr[j])
                    temp[k++] = arr[i++];
                else
                    temp[k++] = arr[j++];
            }

            while (i <= mid)
                temp[k++] = arr[i++];
            while (j <= right)
                temp[k++] = arr[j++];

            for (int x = left; x <= right; x++)
                arr[x] = temp[x];
        }
    }

    cout << "Sorted array:   ";
    for (int i = 0; i < n; i++)
        cout << arr[i] << " ";
    cout << endl;

    return 0;
}
13) Write a c++ code for implementing linear search.
#include <iostream>
using namespace std;

int main() {
    int arr[] = {10, 20, 30, 40, 50};
    int n = sizeof(arr) / sizeof(arr[0]);
    int key = 30;
    bool found = false;

    cout << "Array elements: ";
    for (int i = 0; i < n; i++)
        cout << arr[i] << " ";
    cout << endl;

    for (int i = 0; i < n; i++) {
        if (arr[i] == key) {
            cout << "Element " << key << " found at index " << i << endl;
            found = true;
            break;
        }
    }

    if (!found) {
        cout << "Element " << key << " not found in the array." << endl;
    }

    return 0;
}
14) Write a c++ code for implementing binary search.
#include <iostream>
using namespace std;

int main() {
    int arr[] = {10, 20, 30, 40, 50};
    int n = sizeof(arr) / sizeof(arr[0]);
    int key = 30;
    int low = 0, high = n - 1;
    bool found = false;

    cout << "Array elements: ";
    for (int i = 0; i < n; i++)
        cout << arr[i] << " ";
    cout << endl;

    while (low <= high) {
        int mid = (low + high) / 2;

        if (arr[mid] == key) {
            cout << "Element " << key << " found at index " << mid << endl;
            found = true;
            break;
        } else if (arr[mid] < key) {
            low = mid + 1;
        } else {
            high = mid - 1;
        }
    }

    if (!found) {
        cout << "Element " << key << " not found in the array." << endl;
    }

    return 0;
}
15) Write a c++ code for finding height of the BST.
#include <iostream>
using namespace std;

struct Node {
    int data;
    Node* left;
    Node* right;
};

Node* createNode(int value) {
    Node* newNode = new Node();
    newNode->data = value;
    newNode->left = newNode->right = nullptr;
    return newNode;
}


Node* insert(Node* root, int value) {
    if (root == nullptr)
        return createNode(value);

    if (value < root->data)
        root->left = insert(root->left, value);
    else if (value > root->data)
        root->right = insert(root->right, value);

    return root;
}


int findHeight(Node* root) {
    if (root == nullptr)
        return -1;  
    int leftHeight = findHeight(root->left);
    int rightHeight = findHeight(root->right);

    return 1 + max(leftHeight, rightHeight);
}

int main() {
    Node* root = nullptr;

  
    root = insert(root, 50);
    insert(root, 30);
    insert(root, 70);
    insert(root, 20);
    insert(root, 40);
    insert(root, 60);
    insert(root, 80);

    int height = findHeight(root);
    cout << "Height of the BST: " << height << endl;

    return 0;
}
16) Write a c++ code for counting total number of nodes in BST.
#include <iostream>
using namespace std;

struct Node {
    int data;
    Node* left;
    Node* right;
};

Node* createNode(int value) {
    Node* newNode = new Node();
    newNode->data = value;
    newNode->left = newNode->right = nullptr;
    return newNode;
}

Node* insert(Node* root, int value) {
    if (root == nullptr)
        return createNode(value);
    
    if (value < root->data)
        root->left = insert(root->left, value);
    else
        root->right = insert(root->right, value);
    
    return root;
}

int countNodes(Node* root) {
    if (root == nullptr)
        return 0;
    return 1 + countNodes(root->left) + countNodes(root->right);
}

int main() {
    Node* root = nullptr;

    // Creating the BST
    root = insert(root, 10);
    insert(root, 5);
    insert(root, 15);
    insert(root, 3);
    insert(root, 7);

    cout << "Total number of nodes in the BST: " << countNodes(root) << endl;

    return 0;
}
17) Write a c++ code for implementing BFS.
#include <iostream>
#include <queue>
#include <vector>

using namespace std;

void BFS(int start, vector<vector<int>>& adj, int V) {
    vector<bool> visited(V, false); 
    queue<int> q;

    visited[start] = true; 
    q.push(start);

    while (!q.empty()) {
        int node = q.front();
        q.pop();
        cout << node << " "; 

        for (int neighbor : adj[node]) {
            if (!visited[neighbor]) {
                visited[neighbor] = true;
                q.push(neighbor);
            }
        }
    }
}

int main() {
    int V = 6;
    vector<vector<int>> adj(V);

    adj[0].push_back(1);
    adj[0].push_back(2);
    adj[1].push_back(3);
    adj[1].push_back(4);
    adj[2].push_back(5);

    cout << "BFS Traversal starting from node 0: ";
    BFS(0, adj, V); 

    return 0;
}
18) Write a c++ code for implementing DFS.
#include <iostream>
#include <vector>

using namespace std;

void DFS(int node, vector<vector<int>>& adj, vector<bool>& visited) {
    visited[node] = true;
    cout << node << " "; 

    for (int neighbor : adj[node]) {
        if (!visited[neighbor]) {
            DFS(neighbor, adj, visited);
        }
    }
}

int main() {
    int V = 6; 
    vector<vector<int>> adj(V);

    adj[0].push_back(1);
    adj[0].push_back(2);
    adj[1].push_back(3);
    adj[1].push_back(4);
    adj[2].push_back(5);

    vector<bool> visited(V, false);  
    cout << "DFS Traversal starting from node 0: ";
    DFS(0, adj, visited);  

    return 0;
}
19) Write a c++ code for implementing graph adjacency list and adjacency matrix.
#include <iostream>
#include <vector>
using namespace std;
void adjacencyList(vector<vector<int>>& graph) {
    for (int i = 0; i < graph.size(); i++) {
        cout << "Node " << i << ": ";
        for (int j : graph[i]) {
            cout << j << " ";
        }
        cout << endl;
    }
}

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
    const int SIZE = 10; 
    int hashTable[SIZE] = {0};  
    int values[] = {15, 25, 35}; 
    for (int i = 0; i < 3; i++) {
        int key = values[i] % SIZE;
        while (hashTable[key] != 0) {
            key = (key + 1) % SIZE;  
        }
        hashTable[key] = values[i];
    }
    for (int i = 0; i < SIZE; i++) {
        cout << i << ": " << hashTable[i] << endl;
    }
    return 0;
}
