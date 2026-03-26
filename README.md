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

    Got it 👍 — here is your **FINAL EXAM FORMAT ANSWER**
👉 **WITH QUESTIONS + FULL SQL CODE (Tables + INSERT + Queries together)**

---

# 🔷 **Q1. Property–Owner Database**

**Question:** Create a view to display the owner details having more than 2 properties.

```sql id="q1full1"
CREATE TABLE Owner (
    owner_name VARCHAR(50) PRIMARY KEY,
    addr VARCHAR(100),
    phno VARCHAR(15)
);

CREATE TABLE Property (
    pno INT PRIMARY KEY,
    p_desc VARCHAR(100),
    area VARCHAR(50),
    rate INT CHECK (rate > 0),
    owner_name VARCHAR(50),
    FOREIGN KEY (owner_name) REFERENCES Owner(owner_name)
);

INSERT INTO Owner VALUES
('Amit','Pune','1111'),
('Rahul','Mumbai','2222'),
('Sneha','Pune','3333');

INSERT INTO Property VALUES
(1,'Flat','pune',50000,'Amit'),
(2,'Villa','pune',80000,'Amit'),
(3,'Shop','pune',90000,'Amit'),
(4,'Flat','mumbai',60000,'Rahul'),
(5,'Plot','pune',95000,'Sneha');

CREATE VIEW owner_more_than_2_props AS
SELECT o.owner_name, o.addr, o.phno
FROM Owner o
JOIN Property p ON o.owner_name = p.owner_name
GROUP BY o.owner_name, o.addr, o.phno
HAVING COUNT(p.pno) > 2;
```

---

# 🔷 **Q2. Property–Owner Database**

**Question:** Create a view to find property details with maximum rate in Pune.

```sql id="q2full2"
CREATE VIEW max_rate_pune AS
SELECT *
FROM Property
WHERE area='pune'
AND rate=(SELECT MAX(rate) FROM Property WHERE area='pune');
```

---

# 🔷 **Q3. Student-Marks Database**

**Question:** Display student name, class and total marks scored.

```sql id="q3full3"
CREATE TABLE Student (
    rollno INT PRIMARY KEY,
    s_name VARCHAR(20) NOT NULL,
    address VARCHAR(25),
    class VARCHAR(10)
);

CREATE TABLE Subject (
    scode VARCHAR(10) PRIMARY KEY,
    subject_name VARCHAR(20)
);

CREATE TABLE Marks (
    rollno INT,
    scode VARCHAR(10),
    marks_scored INT,
    PRIMARY KEY (rollno, scode),
    FOREIGN KEY (rollno) REFERENCES Student(rollno),
    FOREIGN KEY (scode) REFERENCES Subject(scode)
);

INSERT INTO Student VALUES
(1,'Raj','Pune','FY'),
(2,'Simran','Mumbai','SY'),
(3,'Aman','Pune','TY');

INSERT INTO Subject VALUES
('S1','DBMS'),
('S2','OS'),
('S3','CN');

INSERT INTO Marks VALUES
(1,'S1',85),
(1,'S2',75),
(2,'S1',90),
(2,'S2',82),
(3,'S3',60);

CREATE VIEW student_total_marks AS
SELECT s.s_name, s.class, SUM(m.marks_scored) AS total_marks
FROM Student s
JOIN Marks m ON s.rollno=m.rollno
GROUP BY s.s_name,s.class
ORDER BY s.s_name;
```

---

# 🔷 **Q4. Student-Marks Database**

**Question:** Display students scoring more than 80.

```sql id="q4full4"
CREATE VIEW students_above_80 AS
SELECT s.s_name, sub.subject_name, m.marks_scored
FROM Student s
JOIN Marks m ON s.rollno=m.rollno
JOIN Subject sub ON m.scode=sub.scode
WHERE m.marks_scored > 80;
```

---

# 🔷 **Q5. Function using Cursor**

**Question:** Display student details based on address.

```sql id="q5full5"
CREATE OR REPLACE FUNCTION get_student_details(p_addr VARCHAR)
RETURNS VOID AS $$
DECLARE rec RECORD;
BEGIN
FOR rec IN
    SELECT s.s_name, sub.subject_name, m.marks_scored
    FROM Student s
    JOIN Marks m ON s.rollno=m.rollno
    JOIN Subject sub ON m.scode=sub.scode
    WHERE s.address=p_addr
LOOP
    RAISE NOTICE 'Name: %, Subject: %, Marks: %',
    rec.s_name, rec.subject_name, rec.marks_scored;
END LOOP;
END;
$$ LANGUAGE plpgsql;
```

---

# 🔷 **Q6. Function using Cursor**

**Question:** Calculate total marks of each student.

```sql id="q6full6"
CREATE OR REPLACE FUNCTION total_marks_all()
RETURNS VOID AS $$
DECLARE rec RECORD;
total INT;
BEGIN
FOR rec IN SELECT rollno,s_name FROM Student LOOP
    SELECT SUM(marks_scored) INTO total FROM Marks WHERE rollno=rec.rollno;
    RAISE NOTICE 'Name: %, Total: %',rec.s_name,total;
END LOOP;
END;
$$ LANGUAGE plpgsql;
```

---

# 🔷 **Q7. Trigger**

**Question:** Before deleting student record display message.

```sql id="q7full7"
CREATE OR REPLACE FUNCTION before_delete_student()
RETURNS TRIGGER AS $$
BEGIN
RAISE NOTICE 'Student record is being deleted';
RETURN OLD;
END;
$$ LANGUAGE plpgsql;

CREATE TRIGGER trg_before_delete_student
BEFORE DELETE ON Student
FOR EACH ROW
EXECUTE FUNCTION before_delete_student();
```

---

# 🔷 **Q8. Trigger**

**Question:** Ensure marks are between 10 and 100.

```sql id="q8full8"
CREATE OR REPLACE FUNCTION check_marks()
RETURNS TRIGGER AS $$
BEGIN
IF NEW.marks_scored < 10 OR NEW.marks_scored > 100 THEN
RAISE EXCEPTION 'Invalid Marks';
END IF;
RETURN NEW;
END;
$$ LANGUAGE plpgsql;

CREATE TRIGGER trg_check_marks
BEFORE INSERT OR UPDATE ON Marks
FOR EACH ROW
EXECUTE FUNCTION check_marks();
```

---

# 🔷 **Q9. Bank Database**

**Question:** Customers with loan less than required.

```sql id="q9full9"
CREATE TABLE Branch (
    br_id INT PRIMARY KEY,
    br_name VARCHAR(30),
    br_city VARCHAR(20)
);

CREATE TABLE Customer (
    cno INT PRIMARY KEY,
    c_name VARCHAR(20),
    caddr VARCHAR(35),
    city VARCHAR(20),
    dob DATE
);

CREATE TABLE Loan_application (
    lno INT PRIMARY KEY,
    l_amt_required INT CHECK (l_amt_required>0),
    l_amt_approved INT,
    l_date DATE
);

CREATE TABLE Ternary (
    br_id INT,
    cno INT,
    lno INT,
    PRIMARY KEY(br_id,cno,lno),
    FOREIGN KEY (br_id) REFERENCES Branch(br_id),
    FOREIGN KEY (cno) REFERENCES Customer(cno),
    FOREIGN KEY (lno) REFERENCES Loan_application(lno)
);

INSERT INTO Branch VALUES (1,'SBI','Pune'),(2,'HDFC','Mumbai');
INSERT INTO Customer VALUES (1,'Ravi','Pune','Pune','2000-06-10'),
(2,'Neha','Mumbai','Mumbai','1999-05-05');

INSERT INTO Loan_application VALUES
(1,50000,40000,'2023-01-01'),
(2,60000,60000,'2023-02-01');

INSERT INTO Ternary VALUES (1,1,1),(2,2,2);

CREATE VIEW loan_less_than_required AS
SELECT c.*
FROM Customer c
JOIN Ternary t ON c.cno=t.cno
JOIN Loan_application l ON t.lno=l.lno
WHERE l.l_amt_approved < l.l_amt_required;
```

---

# 🔷 **Q10. Bank Database**

**Question:** Customers with June birthdays.

```sql id="q10full10"
CREATE VIEW june_birthdays AS
SELECT * FROM Customer
WHERE EXTRACT(MONTH FROM dob)=6;
```

---

# 🔷 **Q11. Function**

**Question:** Count customers of branch.

```sql id="q11full11"
CREATE OR REPLACE FUNCTION total_customers(p_branch_name VARCHAR)
RETURNS INT AS $$
DECLARE total INT;
BEGIN
SELECT COUNT(DISTINCT t.cno) INTO total
FROM Branch b
JOIN Ternary t ON b.br_id=t.br_id
WHERE b.br_name=p_branch_name;
RETURN total;
END;
$$ LANGUAGE plpgsql;
```

---

# 🔷 **Q12. Function**

**Question:** Maximum loan approved.

```sql id="q12full12"
CREATE OR REPLACE FUNCTION max_loan()
RETURNS INT AS $$
DECLARE m INT;
BEGIN
SELECT MAX(l_amt_approved) INTO m FROM Loan_application;
RETURN m;
END;
$$ LANGUAGE plpgsql;
```

---

# 🔷 **Q13–Q17 Project–Employee**

**Question:** Functions on project & employee.

```sql id="q13full13"
CREATE TABLE Project (
    pno INT PRIMARY KEY,
    p_name VARCHAR(30),
    ptype VARCHAR(20),
    duration INT
);

CREATE TABLE Employee (
    eno INT PRIMARY KEY,
    e_name VARCHAR(20),
    qualification VARCHAR(15),
    joindate DATE
);

CREATE TABLE Proj_Emp (
    pno INT,
    eno INT,
    start_date DATE,
    no_of_hours_worked INT,
    PRIMARY KEY(pno,eno),
    FOREIGN KEY (pno) REFERENCES Project(pno),
    FOREIGN KEY (eno) REFERENCES Employee(eno)
);

INSERT INTO Project VALUES (1,'BankSys','IT',12),(2,'WebApp','IT',6);
INSERT INTO Employee VALUES (1,'Anil','BE','2009-05-01'),
(2,'Sunil','BE','2012-06-01');

INSERT INTO Proj_Emp VALUES
(1,1,'2023-01-01',100),
(1,2,'2023-02-01',120);

CREATE OR REPLACE FUNCTION emp_count_project(pname VARCHAR)
RETURNS INT AS $$
DECLARE total INT;
BEGIN
SELECT COUNT(pe.eno) INTO total
FROM Project p JOIN Proj_Emp pe ON p.pno=pe.pno
WHERE p.p_name=pname;
RETURN total;
END;
$$ LANGUAGE plpgsql;

CREATE OR REPLACE FUNCTION emp_before_date()
RETURNS INT AS $$
DECLARE total INT;
BEGIN
SELECT COUNT(*) INTO total
FROM Employee
WHERE joindate < '2010-10-03';
RETURN total;
END;
$$ LANGUAGE plpgsql;
```

---

# 🔷 **Q15. Procedure**

**Question:** Transfer ₹1000 from account 10 to 20.

```sql id="q15full15"
CREATE TABLE Account (
    acc_no INT PRIMARY KEY,
    balance INT
);

INSERT INTO Account VALUES (10,5000),(20,3000);

CREATE OR REPLACE PROCEDURE transfer_amount()
LANGUAGE plpgsql
AS $$
BEGIN
UPDATE Account SET balance=balance-1000 WHERE acc_no=10;
UPDATE Account SET balance=balance+1000 WHERE acc_no=20;
END;
$$;
```

---






