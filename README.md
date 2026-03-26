1.	Implement Binary Search Tree (BST) in Python to perform the following operations using recursion: 
a.	Create a Binary Search Tree 
b.	Inorder Traversal 
c.	Preorder Traversal 
d.	Postorder Traversal 

class Node:
    def __init__(self,value):
        self.data=value
        self.left=None
        self.right=None
       
def insert(root, value):
    if root is None:
        return Node(value)
    if value == root.data:
        print("value alredy exists")
        return
    elif value < root.data:
        root.left = insert(root.left, value)
    else:
        if value > root.data:
            root.right = insert(root.right, value)
    return root

def inorder(root):
    if root!=None:
        inorder(root.left)
        print(root.data, end=" " )
        inorder(root.right)
       
def preorder(root):
    if root!=None:
        print(root.data, end=" " )
        preorder(root.left)
        preorder(root.right)

def postorder(root):
    if root!=None:
        postorder(root.left)
        postorder(root.right)
        print(root.data, end=" " )

root = Node(10)
insert(root, 5)
insert(root, 12)
insert(root, 1)
insert(root, 15)
print("\nInorder traversal:")
inorder(root)
print("\n\nPreorder traversal:")
preorder(root)
print("\n\nPostorder traversal:")
postorder(root)

2.	Implement a Binary Search Tree (BST) in Python with the following operations: 
a.	Insert a node 
b.	Search a node 
c.	Display the BST nodes using inorder traversal 

class Node:
    def __init__(self,value):
        self.data=value
        self.left=None
        self.right=None
       
def insert(root, value):
    if root is None:
        return Node(value)
    if value == root.data:
        print("value alredy exists")
        return
    elif value < root.data:
        root.left = insert(root.left, value)
    else:
        if value > root.data:
            root.right = insert(root.right, value)
    return root

def inorder(root):
    if root!=None:
        inorder(root.left)
        print(root.data, end=" " )
        inorder(root.right)
                     
def search(root, key):
    if root is None or root.data == key:
        return root
    if root.data < key:
        return search(root.right, key)
    # Key is smaller than root's key, search in the left subtree
    return search(root.left, key)

root = Node(10)
insert(root, 5)
insert(root, 12)
insert(root, 1)
insert(root, 15)
print("\n Inorder traversal:")
inorder(root)

key=int(input("\n enter the value to search from BST:"))
result = search(root, key)
if result:
    print(key, "Found in BST: ")
else:
    print(key, "Not Found in BST")

3.	Write a Python program to implement a Binary Search Tree (BST) and perform the following operations: 
a.	Insert nodes into the BST. 
b.	Count the following: 
-	Total number of nodes 
-	Number of leaf nodes (nodes with no children) 
-	Number of non-leaf (internal) nodes 

class Node:
    def __init__(self,value):
        self.data=value
        self.left=None
        self.right=None
       
def insert(root, value):
    if root is None:
        return Node(value)
    if value == root.data:
        print("value alredy exists")
        return
    elif value < root.data:
        root.left = insert(root.left, value)
    else:
        if value > root.data:
            root.right = insert(root.right, value)
    return root

def inorder(root):
    if root!=None:
        inorder(root.left)
        print(root.data, end=" " )
        inorder(root.right)
             
def count_leaf_nodes(root):
    if root is None:
        return 0
    if root.left is None and root.right is None:
        return 1
    return count_leaf_nodes(root.left) + count_leaf_nodes(root.right)

def count_non_leaf_nodes(root):
    if root is None or (root.left is None and root.right is None):
        return 0  		
    return 1 + count_non_leaf_nodes(root.left) + count_non_leaf_nodes(root.right)
            
def count_total_nodes(root):
    if root is None:
        return 0
    return 1 + count_total_nodes(root.left) + count_total_nodes(root.right)

root = Node(10)
insert(root, 5)
insert(root, 12)
insert(root, 1)
insert(root, 15)
print("\nInorder traversal:")
inorder(root)
print()
print("\nLeaf nodes: ", count_leaf_nodes(root))
print("\nNon-leaf nodes: ", count_non_leaf_nodes(root))
print("\nTotal nodes:",count_total_nodes(root))


4.	Write a Python program to implement a Binary Search Tree (BST) and perform the following operations: 
a.	Insert nodes into the BST. 
b.	Create a copy of the BST. 
c.	Generate the mirror image of the BST. 

class Node:
    def __init__(self,value):
        self.data=value
        self.left=None
        self.right=None
       
def insert(root, value):
    if root is None:
        return Node(value)
    if value == root.data:
        print("value alredy exists")
        return
    elif value < root.data:
        root.left = insert(root.left, value)
    else:
        if value > root.data:
            root.right = insert(root.right, value)
    return root


def inorder(root):
    if root!=None:
        inorder(root.left)
        print(root.data, end=" " )
        inorder(root.right)
             
def copy_bst(root):
    if root is None:
        return None
    newroot = Node(root.data)
    newroot.left = copy_bst(root.left)
    newroot.right = copy_bst(root.right)
    return newroot

def mirror_bst(root):
    if root is None:
        return None
    left_mirror = mirror_bst(root.right)  
    right_mirror = mirror_bst(root.left)
    root.left = left_mirror
    root.right = right_mirror
    return root

root = Node(10)
insert(root, 5)
insert(root, 12)
insert(root, 1)
insert(root, 15)
print("\nInorder traversal:")
inorder(root)
print()

print("\nCopy of BST:")
copied_root = copy_bst(root)
inorder(copied_root)

print("\nMirror of BST:")
mirrored_root = mirror_bst(root)
inorder(mirrored_root)

5.	Write a Python program to implement a Binary Search Tree (BST) and perform Level-Order Traversal (also Known as Breadth-First Traversal) using a queue.

from collections import deque

class Node:
    def __init__(self, key):
        self.left = None
        self.right = None
        self.data = key

def level_order_traversal(root):
    if root is None:
        return

    queue = deque([root])

    while queue:
        node = queue.popleft()
        print(node.data, end=' ')

        if node.left:
            queue.append(node.left)
        if node.right:
            queue.append(node.right)

root = Node(1)
root.left = Node(2)
root.right = Node(3)
root.left.left = Node(4)
root.left.right = Node(5)

print("Level order traversal of the binary tree is:")
level_order_traversal(root)


6.	Implement a Binary Search Tree (BST) in Python with the following operations: 
a.	Insert a node 
b.	Delete a node (handle leaf node, node with one child, and node with two children) 
c.	Display the BST nodes using inorder traversal 

class Node:
    def __init__(self,value):
        self.data=value
        self.left=None
        self.right=None



def insert(root, value):
    if root is None:
        return Node(value)
    if value == root.data:
        print("value alredy exists")
        return
    elif value < root.data:
        root.left = insert(root.left, value)
    else:
        if value > root.data:
            root.right = insert(root.right, value)
    return root

def inorder(root):
    if root!=None:
        inorder(root.left)
        print(root.data, end=" " )
        inorder(root.right)
        
def preorder(root):
    if root!=None:
        print(root.data, end=" " )
        preorder(root.left)
        preorder(root.right)

def postorder(root):
    if root!=None:
        postorder(root.left)
        postorder(root.right)
        print(root.data, end=" " )

def delete(root, value):
    if root is None:
        return root
    if (value < root.data):
        root.left= delete(root.left, value)
    elif (value > root.data):
        root.right= delete(root.right, value)
    else:
        if root.left is None:
            temp = root.right
            del root
            return temp
        elif root.right is None:
            temp = root.left
            del root
            return temp
        temp = minValueNode(root.right)
        root.data= temp.data
        root.right=delete(root.right, temp.data)
    return root
        
def minValueNode(root):
    q = root
    while(q.left is not None):
        q = q.left
    return q     
               
root = None
ch=0
while ch != 8:
    print("BST Menu")
    print("1. Create")
    print("2. Insert")
    print("3. Delete")
    print("4. InOrder Traversal")
    print("5. PreOrder Traversal")
    print("6. PostOrder Traversal")
    print("7. Exit")
    ch=int(input("Enter Your Choice :"))
    if ch==1:
        n= int (input("How many nodes u want to create ?"))
        for i in range(0,n):
            key=int(input("Enter element which u want to enter :"))
            root=insert(root,key)
    if ch==2:
        key=int(input("Enter element which u want to enter :"))
        root=insert(root,key)
    if ch==3:
        key=int(input("Enter element which u want to delete :"))
        root=delete(root,key)
    if ch==4:
        inorder(root)
        print()
    if ch==5:
        preorder(root)
        print()
    if ch==6:
        postorder(root)
        print()
    if ch==7:
        break

1.	Implement Binary Search Tree (BST) in Python to perform the following operations using recursion: 
a.	Create a Binary Search Tree 
b.	Inorder Traversal 
c.	Preorder Traversal 
d.	Postorder Traversal 

class Node:
    def __init__(self,value):
        self.data=value
        self.left=None
        self.right=None
       
def insert(root, value):
    if root is None:
        return Node(value)
    if value == root.data:
        print("value alredy exists")
        return
    elif value < root.data:
        root.left = insert(root.left, value)
    else:
        if value > root.data:
            root.right = insert(root.right, value)
    return root

def inorder(root):
    if root!=None:
        inorder(root.left)
        print(root.data, end=" " )
        inorder(root.right)
       
def preorder(root):
    if root!=None:
        print(root.data, end=" " )
        preorder(root.left)
        preorder(root.right)

def postorder(root):
    if root!=None:
        postorder(root.left)
        postorder(root.right)
        print(root.data, end=" " )

root = Node(10)
insert(root, 5)
insert(root, 12)
insert(root, 1)
insert(root, 15)
print("\nInorder traversal:")
inorder(root)
print("\n\nPreorder traversal:")
preorder(root)
print("\n\nPostorder traversal:")
postorder(root)

2.	Implement a Binary Search Tree (BST) in Python with the following operations: 
a.	Insert a node 
b.	Search a node 
c.	Display the BST nodes using inorder traversal 

class Node:
    def __init__(self,value):
        self.data=value
        self.left=None
        self.right=None
       
def insert(root, value):
    if root is None:
        return Node(value)
    if value == root.data:
        print("value alredy exists")
        return
    elif value < root.data:
        root.left = insert(root.left, value)
    else:
        if value > root.data:
            root.right = insert(root.right, value)
    return root

def inorder(root):
    if root!=None:
        inorder(root.left)
        print(root.data, end=" " )
        inorder(root.right)
                     
def search(root, key):
    if root is None or root.data == key:
        return root
    if root.data < key:
        return search(root.right, key)
    # Key is smaller than root's key, search in the left subtree
    return search(root.left, key)

root = Node(10)
insert(root, 5)
insert(root, 12)
insert(root, 1)
insert(root, 15)
print("\n Inorder traversal:")
inorder(root)

key=int(input("\n enter the value to search from BST:"))
result = search(root, key)
if result:
    print(key, "Found in BST: ")
else:
    print(key, "Not Found in BST")

3.	Write a Python program to implement a Binary Search Tree (BST) and perform the following operations: 
a.	Insert nodes into the BST. 
b.	Count the following: 
-	Total number of nodes 
-	Number of leaf nodes (nodes with no children) 
-	Number of non-leaf (internal) nodes 

class Node:
    def __init__(self,value):
        self.data=value
        self.left=None
        self.right=None
       
def insert(root, value):
    if root is None:
        return Node(value)
    if value == root.data:
        print("value alredy exists")
        return
    elif value < root.data:
        root.left = insert(root.left, value)
    else:
        if value > root.data:
            root.right = insert(root.right, value)
    return root

def inorder(root):
    if root!=None:
        inorder(root.left)
        print(root.data, end=" " )
        inorder(root.right)
             
def count_leaf_nodes(root):
    if root is None:
        return 0
    if root.left is None and root.right is None:
        return 1
    return count_leaf_nodes(root.left) + count_leaf_nodes(root.right)

def count_non_leaf_nodes(root):
    if root is None or (root.left is None and root.right is None):
        return 0  		
    return 1 + count_non_leaf_nodes(root.left) + count_non_leaf_nodes(root.right)
            
def count_total_nodes(root):
    if root is None:
        return 0
    return 1 + count_total_nodes(root.left) + count_total_nodes(root.right)

root = Node(10)
insert(root, 5)
insert(root, 12)
insert(root, 1)
insert(root, 15)
print("\nInorder traversal:")
inorder(root)
print()
print("\nLeaf nodes: ", count_leaf_nodes(root))
print("\nNon-leaf nodes: ", count_non_leaf_nodes(root))
print("\nTotal nodes:",count_total_nodes(root))


4.	Write a Python program to implement a Binary Search Tree (BST) and perform the following operations: 
a.	Insert nodes into the BST. 
b.	Create a copy of the BST. 
c.	Generate the mirror image of the BST. 

class Node:
    def __init__(self,value):
        self.data=value
        self.left=None
        self.right=None
       
def insert(root, value):
    if root is None:
        return Node(value)
    if value == root.data:
        print("value alredy exists")
        return
    elif value < root.data:
        root.left = insert(root.left, value)
    else:
        if value > root.data:
            root.right = insert(root.right, value)
    return root


def inorder(root):
    if root!=None:
        inorder(root.left)
        print(root.data, end=" " )
        inorder(root.right)
             
def copy_bst(root):
    if root is None:
        return None
    newroot = Node(root.data)
    newroot.left = copy_bst(root.left)
    newroot.right = copy_bst(root.right)
    return newroot

def mirror_bst(root):
    if root is None:
        return None
    left_mirror = mirror_bst(root.right)  
    right_mirror = mirror_bst(root.left)
    root.left = left_mirror
    root.right = right_mirror
    return root

root = Node(10)
insert(root, 5)
insert(root, 12)
insert(root, 1)
insert(root, 15)
print("\nInorder traversal:")
inorder(root)
print()

print("\nCopy of BST:")
copied_root = copy_bst(root)
inorder(copied_root)

print("\nMirror of BST:")
mirrored_root = mirror_bst(root)
inorder(mirrored_root)

5.	Write a Python program to implement a Binary Search Tree (BST) and perform Level-Order Traversal (also Known as Breadth-First Traversal) using a queue.

from collections import deque

class Node:
    def __init__(self, key):
        self.left = None
        self.right = None
        self.data = key

def level_order_traversal(root):
    if root is None:
        return

    queue = deque([root])

    while queue:
        node = queue.popleft()
        print(node.data, end=' ')

        if node.left:
            queue.append(node.left)
        if node.right:
            queue.append(node.right)

root = Node(1)
root.left = Node(2)
root.right = Node(3)
root.left.left = Node(4)
root.left.right = Node(5)

print("Level order traversal of the binary tree is:")
level_order_traversal(root)


6.	Implement a Binary Search Tree (BST) in Python with the following operations: 
a.	Insert a node 
b.	Delete a node (handle leaf node, node with one child, and node with two children) 
c.	Display the BST nodes using inorder traversal 

class Node:
    def __init__(self,value):
        self.data=value
        self.left=None
        self.right=None



def insert(root, value):
    if root is None:
        return Node(value)
    if value == root.data:
        print("value alredy exists")
        return
    elif value < root.data:
        root.left = insert(root.left, value)
    else:
        if value > root.data:
            root.right = insert(root.right, value)
    return root

def inorder(root):
    if root!=None:
        inorder(root.left)
        print(root.data, end=" " )
        inorder(root.right)
        
def preorder(root):
    if root!=None:
        print(root.data, end=" " )
        preorder(root.left)
        preorder(root.right)

def postorder(root):
    if root!=None:
        postorder(root.left)
        postorder(root.right)
        print(root.data, end=" " )

def delete(root, value):
    if root is None:
        return root
    if (value < root.data):
        root.left= delete(root.left, value)
    elif (value > root.data):
        root.right= delete(root.right, value)
    else:
        if root.left is None:
            temp = root.right
            del root
            return temp
        elif root.right is None:
            temp = root.left
            del root
            return temp
        temp = minValueNode(root.right)
        root.data= temp.data
        root.right=delete(root.right, temp.data)
    return root
        
def minValueNode(root):
    q = root
    while(q.left is not None):
        q = q.left
    return q     
               
root = None
ch=0
while ch != 8:
    print("BST Menu")
    print("1. Create")
    print("2. Insert")
    print("3. Delete")
    print("4. InOrder Traversal")
    print("5. PreOrder Traversal")
    print("6. PostOrder Traversal")
    print("7. Exit")
    ch=int(input("Enter Your Choice :"))
    if ch==1:
        n= int (input("How many nodes u want to create ?"))
        for i in range(0,n):
            key=int(input("Enter element which u want to enter :"))
            root=insert(root,key)
    if ch==2:
        key=int(input("Enter element which u want to enter :"))
        root=insert(root,key)
    if ch==3:
        key=int(input("Enter element which u want to delete :"))
        root=delete(root,key)
    if ch==4:
        inorder(root)
        print()
    if ch==5:
        preorder(root)
        print()
    if ch==6:
        postorder(root)
        print()
    if ch==7:
        break

1.	Write a Python program to sort n randomly generated elements using Heap sort method.

def heapify(a, n, i):
    largest = i    
    left = 2 * i + 1    
    right = 2 * i + 2  

    if left < n and a[left] > a[largest]:
        largest = left

    if right < n and a[right] > a[largest]:
        largest = right

    if largest != i:
        a[i], a[largest] = a[largest], a[i]
        heapify(a, n, largest)

def heapSort(a):
    n = len(a)

    for i in range(n // 2 - 1, -1, -1):
        heapify(a, n, i)

    for i in range(n - 1, 0, -1):
        a[i], a[0] = a[0], a[i]  	# Swap max to end
        heapify(a, i, 0)

a = [12, 11, 13, 5, 6, 7,10]
heapSort(a)
print("Sorted array is:", a)











2.	Write a Python program to implement Huffman Encoding for a given set of characters and their corresponding frequencies. The program should build a Huffman tree and assign binary codes to each character such that the total encoded message length is minimized.
# Huffman Coding in python

string = 'BCAADDDCCACACAC'

# Creating tree nodes
class NodeTree(object):

    def __init__(self, left=None, right=None):
        self.left = left
        self.right = right

    def children(self):
        return (self.left, self.right)

    def nodes(self):
        return (self.left, self.right)

    def __str__(self):
        return '%s_%s' % (self.left, self.right)


# Main function implementing huffman coding
def huffman_code_tree(node, left=True, binString=''):
    if type(node) is str:
        return {node: binString}
    (l, r) = node.children()
    d = dict()
    d.update(huffman_code_tree(l, True, binString + '0'))
    d.update(huffman_code_tree(r, False, binString + '1'))
    return d








# Calculating frequency
freq = {}
for c in string:
    if c in freq:
        freq[c] += 1
    else:
        freq[c] = 1

freq = sorted(freq.items(), key=lambda x: x[1], reverse=True)

nodes = freq

while len(nodes) > 1:
    (key1, c1) = nodes[-1]
    (key2, c2) = nodes[-2]
    nodes = nodes[:-2]
    node = NodeTree(key1, key2)
    nodes.append((node, c1 + c2))

    nodes = sorted(nodes, key=lambda x: x[1], reverse=True)

huffmanCode = huffman_code_tree(nodes[0][0])

print(' Char | Huffman code ')
print('----------------------')
for (char, frequency) in freq:
    print(' %-4r |%12s' % (char, huffmanCode[char]))

Output:
Char | Huffman code 
----------------------
 'C'  |           0
 'A'  |          11
 'D'  |         101
 'B'  |         100

Write a python program that accepts the vertices and edges of a undirected graph and store it as an adjacency matrix. Implement functions to print indegree, outdegree and total degree of all vertices of graph.

class Graph:
    n = 0
    g =[[0 for x in range( 10 )] for y in range(10)]
    
    def __init__(self,x):
        self.n= x
        for i in range(0, self.n):
            for j in range(0, self.n):
                self.g[i][j]= 0
                
    def displayAdjacencyMatrix(self):
        print("\n\n Adjacency Matrix:")
        for i in range(0, self.n):
            for j in range(0, self.n):
                print(self.g[i][j], end =" ")
            print()
            
    def addEdge(self, x, y):
        if(x>=self.n) or (y>= self.n):
            print("Vertex does not exists ..!")
        if(x==y):
            print("Same Vertex")
        else:
            self.g[y][x]= 1
            self.g[x][y]= 1
                 
    def displayDegree (self):
        print("Degree of all vertices of graph : ")
        for i in range(0, self.n):
            print(i ,",-->",end="")
            cnt=0
            for j in range(0,self.n):
                if(self.g[i][j]==1):
                    cnt=cnt+1
            print(cnt)
  
ch=0
while ch!=5:
    print("Menu")
    print("1.Initialize Graph")
    print("2 . Add Edge")
    print("3 . Display Adjacency Matrix")
    print("4 . Display Degree of Vertex")
    print("5 . Exit")
    ch = int (input("Enter Your Choice :"))
    if ch== 1:
        n=int (input("How many vertices ?"))
        obj=Graph(n)
    if ch== 2:
        s=int(input("Enter source vertex :"))
        d=int (input("Enter destination vertex :"))
        obj.addEdge(s,d)
    if ch == 3:
        obj.displayAdjacencyMatrix()
    if ch ==4:
        obj.displayDegree()
    if ch ==5:
        break




Write a python program that accepts the vertices and edges of a directed graph and store it as an adjacency matrix. Implement functions to print indegree, outdegree and total degree of all vertices of graph.

class Graph:
    n = 0
    g =[[0 for x in range( 10 )] for y in range(10)]
    
    def __init__(self,x):
        self.n= x
        for i in range(0, self.n):
            for j in range(0, self.n):
                self.g[i][j]= 0
                
    def displayAdjacencyMatrix(self):
        print("\n\n Adjacency Matrix:")
        for i in range(0, self.n):
            for j in range(0, self.n):
                print(self.g[i][j], end =" ")
            print()
            
    def addEdge(self, x, y):
        if(x>=self.n) or (y>= self.n):
            print("Vertex does not exists ..!")
        if(x==y):
            print("Same Vertex")
        else:
            self.g[x][y]= 1
                 
    def displayOutDegree (self):
        print("OutDegree of all vertices of graph : ")
        for i in range(0, self.n):
            print(i ,",-->",end="")
            cnt=0
            for j in range(0,self.n):
                if(self.g[i][j]==1):
                    cnt=cnt+1
            print(cnt)
    
    def displayInDegree (self):
        print("InDegree of all vertices of graph : ")
        for i in range(0, self.n):
            print(i ,",-->",end="")
            cnt=0
            for j in range(0,self.n):
                if(self.g[j][i]==1):
                    cnt=cnt+1
            print(cnt)
ch=0
while ch!=6:
    print("Menu")
    print("1.Initialize Graph")
    print("2 . Add Edge")
    print("3 . Display Adjacency Matrix")
    print("4 . Display OutDegree of Vertex")
    print("5 . Display InDegree of Vertex")
    print("6 . Exit")
    ch = int (input("Enter Your Choice :"))
    if ch== 1:
        n=int (input("How many vertices ?"))
        obj=Graph(n)
    if ch== 2:
        s=int(input("Enter source vertex :"))
        d=int (input("Enter destination vertex :"))
        obj.addEdge(s,d)
    if ch == 3:
        obj.displayAdjacencyMatrix()
    if ch ==4:
        obj.displayOutDegree()
    if ch ==5:
        obj.displayInDegree()
    if ch ==6:
        break



Write a python program that accepts the vertices and edges of a graph. Create adjacency list. Implement functions to print indegree, outdegree and total degree of all vertex of graph. 

class AdjNode:
    def __init__(self, value):
        self.vertex = value
        self.next = None

class Graph:
    def __init__(self, num):
        self.V = num
        self.graph = [None] * self.V

    # Add edges
    def add_edge(self, s, d):
        node = AdjNode(d)
        node.next = self.graph[s]
        self.graph[s] = node

        node = AdjNode(s)
        node.next = self.graph[d]
        self.graph[d] = node

    # Print the graph
    def print_agraph(self):
        for i in range(self.V):
            print("Vertex " + str(i) + ":", end="")
            temp = self.graph[i]
            while temp:
                print(" -> {}".format(temp.vertex), end="")
                temp = temp.next
            print(" \n")


if __name__ == "__main__":
    V = 5

    # Create graph and edges
    graph = Graph(V)
    graph.add_edge(0, 1)
    graph.add_edge(0, 2)
    graph.add_edge(0, 3)
    graph.add_edge(1, 2)

    graph.print_agraph()



