// 1. Stack Push and Pop
#include<iostream>
using namespace std;

int main() {
    int stack[100], top = -1;

    // Push
    stack[++top] = 10;
    stack[++top] = 20;

    // Pop
    top--;

    // Display
    for(int i = 0; i <= top; i++)
        cout << stack[i] << " ";
    return 0;
}
//  2. Balanced Parentheses
#include<iostream>
using namespace std;

int main() {
    string s = "(()())";
    int bal = 0;

    for(char c : s) {
        if(c == '(') bal++;
        else bal--;
        if(bal < 0) break;
    }

    if(bal == 0) cout << "Balanced";
    else cout << "Not Balanced";
    return 0;
}

//  3. Queue using 2 Stacks (Simplest Conceptual)

#include<iostream>
using namespace std;

int main() {
    int stack1[100], stack2[100], top1 = -1, top2 = -1;

    // Enqueue
    stack1[++top1] = 10;
    stack1[++top1] = 20;

    // Dequeue
    while(top1 != -1)
        stack2[++top2] = stack1[top1--];

    cout << stack2[top2--];
    return 0;
}

// 4. Queue Front & Rear

#include<iostream>
using namespace std;

int main() {
    int q[100], front = 0, rear = -1;

    q[++rear] = 5;
    q[++rear] = 10;

    cout << "Front: " << q[front] << "\n";
    cout << "Rear: " << q[rear];

    return 0;
}

//  5. Count Nodes in Linked List
#include<iostream>
using namespace std;

struct Node {
    int data;
    Node* next;
};

int main() {
    Node a = {1, nullptr};
    Node b = {2, nullptr};
    a.next = &b;  

    int count = 0;
    Node* temp = &a;
    while (temp) {
        count++;
        temp = temp->next;
    }

    cout << "Nodes: " << count;
    return 0;
}

// 6. Detect Cycle in Linked List (Floyd’s)

#include<iostream>
using namespace std;

struct Node {
    int data;
    Node* next;
};

bool hasCycle(Node* head) {
    Node *slow = head, *fast = head;
    while(fast && fast->next) {
        slow = slow->next;
        fast = fast->next->next;
        if(slow == fast) return true;
    }
    return false;
}

int main() {
    Node* a = new Node{1, nullptr};
    Node* b = new Node{2, nullptr};
    Node* c = new Node{3, nullptr};
    a->next = b; b->next = c; c->next = a; // Cycle

    cout << (hasCycle(a) ? "Cycle" : "No Cycle");
    return 0;
}

// 7. Reverse Linked List
#include<iostream>
using namespace std;

struct Node {
    int data;
    Node* next;
};

int main() {
    Node *a = new Node{1, new Node{2, new Node{3, nullptr}}};
    Node *prev = nullptr, *curr = a, *next;

    while(curr) {
        next = curr->next;
        curr->next = prev;
        prev = curr;
        curr = next;
    }

    while(prev) {
        cout << prev->data << " ";
        prev = prev->next;
    }

    return 0;
}

// 8. Bubble Sort
#include<iostream>
using namespace std;

int main() {
    int a[] = {4, 2, 1, 5}, n = 4;

    for(int i=0;i<n-1;i++)
        for(int j=0;j<n-i-1;j++)
            if(a[j]>a[j+1])
                swap(a[j], a[j+1]);

    for(int i=0;i<n;i++) cout << a[i] << " ";
    return 0;
}

// 9. Selection Sort
#include<iostream>
using namespace std;

int main() {
    int a[] = {4, 1, 3, 2}, n = 4;

    for(int i=0;i<n-1;i++) {
        int min = i;
        for(int j=i+1;j<n;j++)
            if(a[j] < a[min]) min = j;
        swap(a[i], a[min]);
    }

    for(int i=0;i<n;i++) cout << a[i] << " ";
    return 0;
}
//  10. Insertion Sort
#include<iostream>
using namespace std;

int main() {
    int a[] = {5, 3, 1, 4}, n = 4;

    for(int i=1;i<n;i++) {
        int key = a[i], j = i-1;
        while(j >= 0 && a[j] > key)
            a[j+1] = a[j--];
        a[j+1] = key;
    }

    for(int i=0;i<n;i++) cout << a[i] << " ";
    return 0;
}

// 11. Binary Search
#include<iostream>
using namespace std;

int main() {
    int a[] = {1, 3, 5, 7, 9}, n = 5, key = 5;
    int l = 0, r = n-1, mid;

    while(l <= r) {
        mid = (l + r)/2;
        if(a[mid] == key) {
            cout << "Found at " << mid;
            return 0;
        } else if(a[mid] < key)
            l = mid + 1;
        else
            r = mid - 1;
    }

    cout << "Not Found";
    return 0;
}

// 12. Linear Search
#include<iostream>
using namespace std;

int main() {
    int a[] = {2, 4, 6, 8}, n = 4, key = 6;

    for(int i = 0; i < n; i++) {
        if(a[i] == key) {
            cout << "Found at " << i;
            return 0;
        }
    }

    cout << "Not Found";
    return 0;
}


// 13. Binary Tree Inorder Traversal

#include<iostream>
using namespace std;

struct Node {
    int data;
    Node* left;
    Node* right;
};

void inorder(Node* root) {
    if(root == nullptr) return;
    inorder(root->left);
    cout << root->data << " ";
    inorder(root->right);
}

int main() {
    Node* root = new Node{1, nullptr, nullptr};
    root->left = new Node{2, nullptr, nullptr};
    root->right = new Node{3, nullptr, nullptr};

    inorder(root);
    return 0;
}

// 14. Binary Tree Preorder Traversal

#include<iostream>
using namespace std;

struct Node {
    int data;
    Node* left;
    Node* right;
};

void preorder(Node* root) {
    if(root == nullptr) return;
    cout << root->data << " ";
    preorder(root->left);
    preorder(root->right);
}

int main() {
    Node* root = new Node{1, new Node{2, nullptr, nullptr}, new Node{3, nullptr, nullptr}};
    preorder(root);
    return 0;
}

//  15. Binary Tree Postorder Traversal
#include<iostream>
using namespace std;

struct Node {
    int data;
    Node* left;
    Node* right;
};

void postorder(Node* root) {
    if(root == nullptr) return;
    postorder(root->left);
    postorder(root->right);
    cout << root->data << " ";
}

int main() {
    Node* root = new Node{1, new Node{2, nullptr, nullptr}, new Node{3, nullptr, nullptr}};
    postorder(root);
    return 0;
}

//  16. BST Insert and Inorder Display
 #include<iostream>
using namespace std;

struct Node {
    int data;
    Node* left;
    Node* right;
};

Node* insert(Node* root, int key) {
    if(!root) return new Node{key, nullptr, nullptr};
    if(key < root->data) root->left = insert(root->left, key);
    else root->right = insert(root->right, key);
    return root;
}

void inorder(Node* root) {
    if(root) {
        inorder(root->left);
        cout << root->data << " ";
        inorder(root->right);
    }
}

//  17. Graph Using Adjacency Matrix

int main() {
    Node* root = nullptr;
    root = insert(root, 10);
    insert(root, 5);
    insert(root, 15);
    inorder(root);
    return 0;
}



#include<iostream>
using namespace std;

int main() {
    int g[3][3] = { {0,1,0}, {1,0,1}, {0,1,0} };

    for(int i=0;i<3;i++) {
        for(int j=0;j<3;j++)
            cout << g[i][j] << " ";
        cout << endl;
    }
    return 0;
}

//18. DFS (Recursive)

#include<iostream>
using namespace std;

int g[4][4] = {
    {0,1,0,1},
    {1,0,1,0},
    {0,1,0,1},
    {1,0,1,0}
};
int vis[4] = {0};

void dfs(int v) {
    vis[v] = 1;
    cout << v << " ";
    for(int i=0;i<4;i++)
        if(g[v][i] && !vis[i])
            dfs(i);
}

int main() {
    dfs(0);
    return 0;
}

//  19. BFS
#include<iostream>
using namespace std;

int g[4][4] = {
    {0,1,1,0},
    {1,0,0,1},
    {1,0,0,1},
    {0,1,1,0}
};
int vis[4] = {0};

int main() {
    int q[10], front = 0, rear = 0;
    q[rear++] = 0;
    vis[0] = 1;

    while(front < rear) {
        int node = q[front++];
        cout << node << " ";
        for(int i = 0; i < 4; i++) {
            if(g[node][i] && !vis[i]) {
                q[rear++] = i;
                vis[i] = 1;
            }
        }
    }

    return 0;
}

// 20. Hash Table (Basic Array)

#include<iostream>
using namespace std;

int main() {
    int hash[10] = {0};
    int arr[] = {3, 5, 7};

    for(int i = 0; i < 3; i++)
        hash[arr[i]] = 1;

    cout << "Is 5 present? " << (hash[5] ? "Yes" : "No");
    return 0;
}
