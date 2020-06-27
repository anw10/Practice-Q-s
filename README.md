# Answers to Firecode Questions

<!-- ## Table of Contents

- [Background](#background) -->

# Palindrome Tester

***
A palindrome is a string or sequence of characters that reads the same backward as forward. For example, "madam" is a palindrome. Write a method that takes in a String and returns a boolean -> true if the input String is a palindrome and false if it is not. An empty string and a null input are considered palindromes. You also need to account for the space character. For example, "race car" should return false as read backward it is "rac ecar".

Examples:

isStringPalindrome("madam") -> true
isStringPalindrome("aabb") -> false
isStringPalindrome("race car") -> false
isStringPalindrome("") -> true
isStringPalindrome(null) -> true
***

```
// java.util.* and java.util.streams.* have been imported for this problem.
// You don't need any other imports.

public static boolean isStringPalindrome(String str){
    
    if(str == null || str == ""){
        return true;
    }
    
    for(int i =0; i< str.length(); i++){
        if(str.charAt(i) != str.charAt(str.length() -1 -i)){
            return false;
        }
    }
    return true;

}
```

# Binary Search on Array of Integers

***
Write a method that searches an Array of integers for a given integer using the
Binary Search Algorithm. If the input integer is found in the array, return true. Otherwise, return false.
You can assume that the given array of integers is already sorted
in ascending order.
Examples:

binarySearch({2,5,7,8,9},9) -> true

binarySearch({2,8,9,12},6) -> false

binarySearch({2},4) -> false

binarySearch({},9) -> false

   {} -> [Empty] Array

***

// java.util.* and java.util.streams.* have been imported for this problem.
// You don't need any other imports.

public static Boolean binarySearch(int[] arr, int n){
  
int left = 0;
int right = (arr.length)-1;

while(left <= right){

int mid = (right + left)/2;
  
    if(arr[mid] == n){
        return true;
    }    
    if(arr[mid] < n){
        left = mid+1;
    }else{
        right = mid - 1;
    }
}

return false;
}

# Fibonacci Number 

***
The Fibonacci Sequence is the series of numbers: 0, 1, 1, 2, 3, 5, 8, 13, 21, 34, ... The next number is found by adding up the two numbers before it.

Write a recursive method fib(n) that returns the nth Fibonacci number. n is 0 indexed, which means that in the sequence 0, 1, 1, 2, 3, 5, 8, 13, 21, 34, ..., n == 0 should return 0 and n == 3 should return 2. Assume n is less than 15.

Even though this problem asks you to use recursion, more efficient ways to solve it include using an Array, or better still using 3 volatile variables to keep a track of all required values. Check out this blog post to examine better solutions for this problem.
***

```
// java.util.* and java.util.streams.* have been imported for this problem.
// You don't need any other imports.

public static int fib(int n) {

if(n == 0){
    return 0;
}

if(n <=2){
    return 1;
}

return fib(n-1) + fib(n-2);

}
```

# Repeated Elements in an Array 

***
Write a method duplicate to find the repeated or duplicate elements in an array.
This method should return a list of repeated integers in a string with the elements sorted in ascending order (as illustrated below).


duplicate({1,3,4,2,1}) --> "[1]"

duplicate({1,3,4,2,1,2,4}) --> "[1, 2, 4]"



Note: You may use toString() method to return the
standard string representation of most data structures, and
Arrays.sort() to sort your result.
***

```
// java.util.* and java.util.streams.* have been imported for this problem.
// You don't need any other imports.

public static String duplicate(int[] numbers){
    
Arrays.sort(numbers);
Set<Integer> set = new HashSet();
for(int i = 0; i< numbers.length-1; i++){
    if(numbers[i] == numbers[i+1]){
        set.add(numbers[i]);
    }
}

return set.toString(); 
}
```

# Merge Two Sorted Arrays


***
The idea behind the classic Mergesort algorithm is to divide an array in half, sort each half, and then use
a merge() method to merge the two halves into a single sorted array.


Implement the merge() method that takes in
two sorted arrays and returns a third sorted array that contains elements of both the input arrays.

You can assume
that the input arrays will always be sorted in ascending order and can have different sizes.


Examples:

merge({2,5,7,8,9},{9}) -> {2,5,7,8,9,9}
merge()({7,8},{1,2}) -> {1,2,7,8}
merge()({2},{}) -> {2}
   {} -> [Empty] Array

***

```
// java.util.* and java.util.streams.* have been imported for this problem.
// You don't need any other imports.

public static int[] merge(int[] arrLeft, int[] arrRight){
  
int[] temp = new int[arrLeft.length+arrRight.length];

int i =0;
int j = 0;
int k = 0;

int l = arrLeft.length;
int r = arrRight.length;

while( i <l && j < r ){
    
    if(arrLeft[i] < arrRight[j]){
        temp[k] = arrLeft[i];
        k++;
        i++;
    }else{
        temp[k] = arrRight[j];
        k++;
        j++;
    }
    
}

while(i < l){
    temp[k] = arrLeft[i];
    k++;
    i++;
}

while( j < r){
    temp[k] = arrRight[j];
        k++;
        j++;
}

return temp;

}
```

# Find the Middle of a List in a Single Pass 

***

***

```
// java.util.* and java.util.streams.* have been imported for this problem.
// You don't need any other imports.

public ListNode findMiddleNode(ListNode head) {

if(head == null){
    return null;
}

ListNode mid = head;
ListNode curr = head;

while(curr.next != null && curr.next.next != null){
    curr = curr.next.next;
    mid = mid.next;
}

return mid;

}
```

# Iterative Preorder Traversal 

***

***

```
// java.util.* and java.util.streams.* have been imported for this problem.
// You don't need any other imports.

public ArrayList<Integer> preorderItr(TreeNode root) {
    
ArrayList<Integer> temp = new ArrayList<>(1);
Stack<TreeNode> node = new Stack<>();

if(root == null){
    return temp;
}

node.push(root);

while(node.empty() == false){

    TreeNode tempNode = node.pop();
    temp.add(tempNode.data);

    if(tempNode.right != null){
        node.push(tempNode.right);
    }

    if(tempNode.left != null){
        node.push(tempNode.left);
    }

}
return temp;
}
```

# BST Validation

***

***

```
// java.util.* and java.util.streams.* have been imported for this problem.
// You don't need any other imports.


public static boolean checkBST(TreeNode root, int min, int max){
    if(root == null){
        return true;
    }
    
    if(root.data < min || root.data > max){
        return false;
    }
    
    return checkBST(root.left, min, root.data-1) && checkBST(root.right, root.data+1,max );
}

public static boolean validateBST(TreeNode root) {
 return checkBST( root,  Integer.MIN_VALUE,  Integer.MAX_VALUE);
}


```

# Question Name

***
Write a method to compute the binary representation of a positive integer. The method should return a string with 1s and 0s.

computeBinary(6) ==> "110"
computeBinary(5) ==> "101"

Note: Use the minimum number of binary digits needed for the representation (Truncate unnecessary trailing 0s).
computeBinary(5) ==> "0101" (incorrect)
computeBinary(5) ==> "101" (correct)

Note:
Can be done with packaged method as done below
***


```
// java.util.* and java.util.streams.* have been imported for this problem.
// You don't need any other imports.

public static String computeBinary(int val) {


return (Integer.toBinaryString(val));

}
```

# Permutations!

***

Implement a method that checks if two strings are permutations of each other.


permutation("CAT","ACT") --> true

permutation("hello","aloha") --> false
***

```
// java.util.* and java.util.streams.* have been imported for this problem.
// You don't need any other imports.

public static boolean permutation(String str1, String str2) {

if(str1.length() != str2.length()){
    return false;
}
    
HashMap<Integer,Character> map = new HashMap<Integer,Character>();


for(int i = 0; i<str1.length(); i++){
    if(!map.containsValue(str1.charAt(i))){
        map.put(i,str1.charAt(i));
    }
}

for(int j =0; j< str2.length(); j++){
    if(!map.containsValue(str2.charAt(j))){
        return false;
    }
}

return true;
    
}
```

# Delete the Head Node of a Circular Linked List

***
Given a circular linked list, implement a method to delete its head node. Return the list's new head node.

*x = indicates head node
1->2->3->4->*1 ==> 2->3->4->*2
***

```
// java.util.* and java.util.streams.* have been imported for this problem.
// You don't need any other imports.

public ListNode deleteAtHead(ListNode head) {
                
ListNode temp = head;

if(head == null || head.next == head){
    return null;
}

while(temp.next != head){
temp = temp.next;  
}

temp.next = head.next;
//head.next = null;
head = temp.next;

   return head;
}
```

# Flip it! 

***
You are given an m x n 2D image matrix where each integer represents a pixel. Flip it in-place along its vertical axis.

***

```
// java.util.* and java.util.streams.* have been imported for this problem.
// You don't need any other imports.

public static void flipItVerticalAxis(int[][] matrix) {
    for(int i =0; i< matrix.length; i++){
        for(int j =0; j< (matrix[0].length/2); j++){
            int temp = matrix[i][j];
            matrix[i][j] = matrix[i][matrix[0].length-1];
            matrix[i][matrix[0].length-1] = temp;        
        }
    }
}
```

# Height of a Binary Tree 

***

***

```
// java.util.* and java.util.streams.* have been imported for this problem.
// You don't need any other imports.

public int findHeight(TreeNode root) { 
    if(root == null){
        return 0;    
    }
 return 1+Math.max(findHeight(root.left),findHeight(root.right));
}
```

# Find a Node in a Binary Tree Without Using Recursion 

***

***

```
// java.util.* and java.util.streams.* have been imported for this problem.
// You don't need any other imports.

public TreeNode findNode(TreeNode root, int val) {
    

if(root == null){
    return null;
}

Stack<TreeNode> stack = new Stack<>();

stack.push(root);

while(!stack.empty()){
    TreeNode curr = stack.pop();
    
    if(curr.data == val){
        return curr;
    }
    
    if(curr.left != null){
        stack.push(curr.left);
    }
    
    if(curr.right != null){
        stack.push(curr.right);
    }
}

return null;

}
```


# Find the Transpose of a Square Matrix

***

***
```
// java.util.* and java.util.streams.* have been imported for this problem.
// You don't need any other imports.

public static void transposeMatrix(int[][] matrix) {
    
    int rows = matrix.length;
    int cols = matrix[0].length;
    
    // int[][] nmatrix = new int[cols][rows];
    
     for(int i = 0; i< rows; i++){
         for(int j = 0; j <= i-1 ; j++){
            int temp = matrix[i][j];
            matrix[i][j] = matrix[j][i];
            matrix[j][i] = temp;
         }
     }
    
}
```

# Find the Sum of all Elements in a Binary Tree

***
Given a binary tree, write a method to find and return the sum of all the elements using recursion. For an empty tree the sum is 0.

***

```
// java.util.* and java.util.streams.* have been imported for this problem.
// You don't need any other imports.

public int sum(TreeNode root) { 
    
if(root == null){
    return 0;
}

return root.data + sum(root.left) + sum(root.right);

}
```

# Count the Leaves! 

***
Write a function to find the total number of leaf nodes in a binary tree. A node is described as a leaf node if it doesn't have any children. If there are no leaf nodes, return 0.


***

```
public int numberOfLeaves(TreeNode root) { 
    
    if(root == null){
        return 0;
    }
    
    Stack<TreeNode> stack = new Stack<TreeNode>();
    
    int count = 0;
    stack.push(root);
    
    while(!stack.empty()){
        TreeNode curr = stack.pop();

        if(curr.left != null){
            stack.push(curr.left);
        }
        if(curr.right != null){
            stack.push(curr.right);
        }
        
        if( curr.left == null && curr.right == null ){
            count++;
        }
    
    }
    return count;

}

```

# Delete a List's Head Node

***
Given a singly-linked list, write a method to delete the first node of the list and return the new head.

***

```
// java.util.* and java.util.streams.* have been imported for this problem.
// You don't need any other imports.

public ListNode deleteAtHead(ListNode head) {
        
    if(head == null){
        return null;
    }
    
    return head=head.next ;
    
}
```

# String Compression

***
Compress a sorted String by replacing instances of repeated characters with the character followed by the count of the character.


compressString("aaabbbbbcccc") --> a3b5c4
compressString("aabbbbccc") --> a2b4c3
compressString("abc") --> abc


Note: This kind of compression will only be effective when the count of consecutive identical characters is greater than 1.

***

```
// java.util.* and java.util.streams.* have been imported for this problem.
// You don't need any other imports.

public static String compressString(String text) {

StringBuilder sb = new StringBuilder();
HashMap<Character,Integer> map = new HashMap<Character, Integer>();

for(int i = 0; i< text.length(); i++){
    
    if(!map.containsKey(text.charAt(i))){
        map.put(text.charAt(i), 1);
    }else{
        int temp =  map.get(text.charAt(i));
        temp++;
        map.put(text.charAt(i), temp);
    }
    
}

Set set = map.keySet();

for(Map.Entry<Character,Integer> entry: map.entrySet() ){
    sb.append(entry.getKey());
    if(entry.getValue() != 1){
    sb.append(entry.getValue());
    }
}

return sb.toString();
}
```

# POW!

***
Write a method - pow(x,n) that returns the value of x raised to the power of n (xn). n can be negative!

***

```
// java.util.* and java.util.streams.* have been imported for this problem.
// You don't need any other imports.

public static double pow(double x, int n) {
    
    if(n == 0){
        return 1;
    }     
    
    if(n == 1){
        return x;
    }
    
    if(x == 0){
        return x;
    }
    
    if(n < 0){
        return pow(1/x, -n);
    }
    
    if(n%2 > 0){
        return x*pow(x*x, n/2);
    }
    return pow(x*x, n/2);

}
```

# Max Gain

***
Given an array of integers, write a method - maxGain - that returns the maximum gain. Maximum Gain is defined as the maximum difference between 2 elements in a list such that the larger element appears after the smaller element. If no gain is possible, return 0.


***

```
// java.util.* and java.util.streams.* have been imported for this problem.
// You don't need any other imports.

public static int maxGain(int[] a) {
    
    int first = Integer.MAX_VALUE;
    int max = 0;
    int temp = 0;
    
    for(int i = 0; i< a.length; i++){
        if(a[i] < first){
        first = a[i];
        }
        
        temp = a[i] - first;
        if(temp > max){
            max = temp;
        }
    }

return max;

}
```


# Is this Integer a Palindrome? 

***
Write a method that checks if a given integer is a palindrome - without allocating additional heap space

***

```
// java.util.* and java.util.streams.* have been imported for this problem.
// You don't need any other imports.

public static Boolean isIntPalindrome(int x) {            

int rev = 0;
int temp = x;
while(x > 0){
    
    rev = rev*10 + x%10;
    x = x/10;
}

if(rev == temp){
    return true;
}
    return false;
}
```

# Find the First Non Duplicate Character in a String

***
Find the first non-duplicate character in a string. Return null if no unique character is found.

firstNonRepeatedCharacter( "abcdcd" ) --> 'a'
firstNonRepeatedCharacter( "cbcd" ) --> 'b'
firstNonRepeatedCharacter( "cdcd" ) --> null


***

```
// java.util.* and java.util.streams.* have been imported for this problem.
// You don't need any other imports.

public static Character firstNonRepeatedCharacter(String str) {

HashMap<Character, Integer> map = new HashMap<Character,Integer>();

for(int i =0 ; i< str.length(); i++){
    if(!map.containsKey(str.charAt(i))){
        map.put(str.charAt(i), 1);
    }else{
    map.put(str.charAt(i), (map.get(str.charAt(i)) + 1));
    }
}

for(Character ch : map.keySet()){
    if(map.get(ch) == 1){
        return ch;
    }
}

return null;
    
}
```

# Selection Sort

***
Selection sort offers improved performance over bubble sort, especially for arrays with a large number of elements. Where bubble sort accumulated the largest elements towards the end of the array, selection sort accumulates the smallest elements at the beginning of the array.

Write a method that uses the selection sort algorithm to sort an input array of integers. See the hints and click the red colored links for additonal details on the algorithm.

***

```
// java.util.* and java.util.streams.* have been imported for this problem.
// You don't need any other imports.

public static int[] selectionSortArray(int[] arr){
    
for(int i = 0; i< arr.length; i++){
    int temp = arr[i];
    int indx = i;
    for(int j = i+1; j<arr.length; j++){
        if(arr[j] < temp){
            temp = arr[j];
            indx = j;
        }
    }
    int temp2 = arr[i];
    arr[i] = temp;
    arr[indx] = temp2;
    
}
    return arr;
}
```

# Anagrams 

***
Write a method isAnagram that checks if two lowercase input Strings are anagrams of each other. An anagram of a String is a String that is formed by simply re-arranging its letters, using each letter exactly once. Your algorithm should run in linear O(n) time and use constant O(1) space.

***

```
// java.util.* and java.util.streams.* have been imported for this problem.
// You don't need any other imports.

public static boolean isAnagram(String input1, String input2) {
    
    if(input1 == null && input2 == null){
        return false;
    }
    
    if(input1.length() != input2.length()){
        return false;
    }
    
    char[] buffer = new char[256];
    
    for(int i = 0; i < input1.length(); i++){
        buffer[(int)input1.charAt(i)] += 1;
        buffer[(int)input2.charAt(i)] += 1;
    }
    
    for(int i = 0; i< buffer.length; i++){
        if(buffer[i] == 1){
            return false;
        }
    }
    
    return true;
    
}
```

# Delete the Node at a Particular Position in a Linked List 

***
Given a singly-linked list, implement a method to delete the node at a given position (starting from 1 as the head position) and return the head of the list. Do nothing if the input position is out of range.
***

```
// java.util.* and java.util.streams.* have been imported for this problem.
// You don't need any other imports.

public ListNode deleteAtMiddle(ListNode head, int position) {
        
ListNode curr = head;

if(head == null){
    return null;
}

if(position == 1){
    head = head.next;
    return head;
}

for(int i = 1; i < position-1; i++){
    if(curr.next != null){
        curr = curr.next;
    }else{
        return head;
    }
}

if(curr.next.next != null){
curr.next = curr.next.next;
}else{
    curr.next = null;
}
return head;
    
}
```
# Delete a Circular-Linked List's Tail Node 

***
Given a circular-linked list, write a function to delete its tail node and return the modified list's head. *x = indicates head node

1->2->3->4->*1 ==> 1->2->3->*1


***
```
// java.util.* and java.util.streams.* have been imported for this problem.
// You don't need any other imports.

public ListNode deleteAtTail(ListNode head) {
    
ListNode curr = head;

while(curr.next.next != head){
    curr = curr.next;
}

curr.next = head;

return head;

}
```
# Insert Stars 

***
Given a string, recursively compute a new string where the identical adjacent characters in the original string are separated by a "*".


***

```
// java.util.* and java.util.streams.* have been imported for this problem.
// You don't need any other imports.

public static String insertPairStar(String s) {
 
if(s == null || s == "" || s.length() == 1 ){
    return s;
}

if(s.charAt(0) == s.charAt(1)){
    return s.substring(0,1) + "*" + insertPairStar(s.substring(1,s.length())) ;
}else{
    return s.substring(0,1) + insertPairStar(s.substring(1,s.length())) ;
}

}
```

# Insert a Node at the End of a Linked List 

***
Write a method to insert a node at the end of a singly-linked list. Return the head of the modified list.

***

```
// java.util.* and java.util.streams.* have been imported for this problem.
// You don't need any other imports.

public ListNode insertAtTail(ListNode head, int data) {
    
    if(head == null){
        return head = new ListNode(data);
    }

    ListNode curr = head;
    
    while(curr.next != null){
        curr = curr.next;
    }
    
    curr.next = new ListNode(data);
    
    return head;

}
```

# Even or Odd?

***
Given a singly-linked list, check whether its length is even or odd in a single pass. An Empty list has 0 nodes which makes the number of nodes in it even.

***
```
// java.util.* and java.util.streams.* have been imported for this problem.
// You don't need any other imports.

public Boolean isListEven(ListNode head) {

int count = 1;

if(head == null){
    return true;
}

while(head.next != null){
    head = head.next;
    count++;
}
if(count%2 == 0){
    return true;
}

return false;

}
```


# Recursive Preorder Traversal 

***
Given a binary tree, write a method to recursively traverse the tree in the preorder manner. Mark a node as visited by adding its data to the list - Arraylist <Integer> preorderedList.

***

```
// java.util.* and java.util.streams.* have been imported for this problem.
// You don't need any other imports.

//Populated the elements of the tree  in the below list in preorder format
ArrayList<Integer> preorderedList = new ArrayList<Integer>();
public void preorder(TreeNode root) {
   
if(root != null){
    preorderedList.add(root.data);

if(root.left != null){
    preorder(root.left);
}

if(root.right != null){
    preorder(root.right);
}
}

}
```

# Find the Missing Number in a Set of Numbers from 1 to 10

***
Given an Array containing 9 numbers ranging from 1 to 10, write a method to find the missing number. Assume you have 9 numbers between 1 to 10 and only one number is missing.


findMissingNumber({1,2,4,5,6,7,8,9,10}) --> 3

***

```
// java.util.* and java.util.streams.* have been imported for this problem.
// You don't need any other imports.

public static int findMissingNumber(int[] arr) {
    

int sum = 0;

for(int i =0; i< arr.length; i++){
    sum += arr[i];
}

return 55-sum;
 
}
```
# Find the Max Element in a Binary Tree Recursively 

***
Given a binary tree, write a recursive method to return the maximum element.

***

```
// java.util.* and java.util.streams.* have been imported for this problem.
// You don't need any other imports.

public int findMax(TreeNode root) {
    
if(root != null){
    int temp = root.data;
    return Math.max(temp,(Math.max(findMax(root.left), findMax(root.right))));
}
return 0;
}
```

# Better Fibonacci

***
The Fibonacci Sequence is the series of numbers: 0, 1, 1, 2, 3, 5, 8, 13, 21, 34, ... The next number is found by adding up the two numbers before it.

Your goal is to write an optimal method - betterFibonacci that returns the nth Fibonacci number in the sequence. n is 0 indexed, which means that in the sequence 0, 1, 1, 2, 3, 5, 8, 13, 21, 34, ..., n == 0 should return 0 and n == 3 should return 2. Your method should exhibit a runtime complexity of O(n) and use constant O(1) space. With this implementation, your method should be able to compute larger sequences where n > 40.


Examples:

fib(0) ==> 0

fib(1) ==> 1

fib(3) ==> 2
***

```
// java.util.* and java.util.streams.* have been imported for this problem.
// You don't need any other imports.

public static int betterFibonacci(int n) {
    int n1 = 0;
    int n2 = 0;
    
    for(int i = 0; i < n+1; i++){
        if(i == 0){
        continue;
        }
    
        if(i == 1){
        n2 =1;
        continue;
        }
        
        int temp = n1 + n2;
        n1 = n2;
        n2 = temp;
        
    }
    
    return n2;
    
}
```

# Find the size of the Binary Tree

***
Given a binary tree, write a method to return its size. The size of a tree is the number of nodes it contains.

***

```
// java.util.* and java.util.streams.* have been imported for this problem.
// You don't need any other imports.

public int size(TreeNode root) {
                              

if(root != null){
    return 1+size(root.left)+size(root.right);
}

return 0;
    
}

```

# Insert a Node at the Front of a Linked List

***
Write a method to insert a node at the front of a singly-linked list and return the head of the modified list.

***

```
// java.util.* and java.util.streams.* have been imported for this problem.
// You don't need any other imports.

public ListNode insertAtHead(ListNode head, int data) {

    if(head == null){
        return new ListNode(data);
    }        
    
    ListNode curr = new ListNode(data);
    
    curr.next = head;
    
    return curr;
}

```

# Couple Sum

***

***

```
// java.util.* and java.util.streams.* have been imported for this problem.
// You don't need any other imports.

public static int[] coupleSum(int[] numbers, int target) {
    
    int[] ret = new int[2];
    HashMap<Integer, Integer> map = new HashMap<Integer,Integer>();
    
    for(int i =0; i<numbers.length; i++){
        if(map.containsKey(numbers[i])){
            ret[0] = i;
            ret[1] = i+1;
            return ret;
        }else{
            map.put(target-numbers[i], i);
        }
    }
    
    return ret;
}

```

# Isomorphic Strings 

***

***

```
// java.util.* and java.util.streams.* have been imported for this problem.
// You don't need any other imports.

public static boolean isIsomorphic(String input1, String input2) {
    
    if(input1 == "" && input2 == ""){
        return true;
    }
    
    HashMap<Character, Integer> strmap = new HashMap<Character,Integer>();
    HashMap<Character, Integer> strmap2 = new HashMap<Character,Integer>();

    for(int i = 0; i< input1.length(); i++){
        if(!strmap.containsKey(input1.charAt(i))){
            strmap.put(input1.charAt(i), 1);
        }else{
            strmap.put(input1.charAt(i), strmap.get(input1.charAt(i)) + 1);
        }
        
        
        if(!strmap2.containsKey(input2.charAt(i))){
            strmap2.put(input2.charAt(i), 1);
        }else{
            strmap2.put(input2.charAt(i), strmap2.get(input2.charAt(i)) + 1);
        }
        
        if(strmap.size() != strmap2.size()){
            return  false;
        }
    }
    
    return true;
    
}

```

# Remove Duplicates from a List of Words 

***
Given a List of Strings, write a method removeDuplicates that removes duplicate words from the List and returns an ArrayList of all the unique words. The returned ArrayList should be lexically alphabetically.

Input: [Hi, Hello, Hey, Hi, Hello, Hey]

Output: [Hello, Hey, Hi]


***

```
// java.util.* and java.util.streams.* have been imported for this problem.
// You don't need any other imports.

public static ArrayList<String> removeDuplicates(List<String> input) {
      
    TreeSet<String> retSet = new TreeSet<String>();

    for(int i =0; i<input.size(); i++){
        String temp = input.get(i);
        for(int j =i+1; j<input.size(); j++){
            if(temp.equals(input.get(j))){
                input.remove(j);
            }
            retSet.add(input.get(i));
        }
    }
    ArrayList<String> retList = new ArrayList<String>(retSet);
    
    
    // for(int i = 0; i<input.size(); i++){
    //     retSet.add(input.get(i));
    // }

return retList;
}
```

# Power of 2 

***

***

```
// java.util.* and java.util.streams.* have been imported for this problem.
// You don't need any other imports.

public static boolean isPowOfTwo(int num) {
    if(num == 0 || num == 1){
        return true;
    }
    return num%2 == 0;
}

```

# Find the Nth Node from the end without using extra memory - Linked List 

***
Given a singly-linked list, implement the method that returns Nth node from the end of the list without using extra memory (constant space complexity).

***

```
// java.util.* and java.util.streams.* have been imported for this problem.
// You don't need any other imports.

public ListNode findNthNodeFromEnd(ListNode head, int n) {
               
    if(head == null){
        return head;
    }
    
    ListNode temp = head;
    int count = 1;
    while(temp.next!= null){
        temp = temp.next;
        count++;
    }
    
    if(n>count || n<0){
        return null;
    }
    
    for(int i = 0; i<count-n; i++){
        head = head.next;
    }
    
    return head;
}
```

# Find the Maximum Number of Repetitions

***
Given an Array of integers, write a method that will return the integer with the maximum number of repetitions. Your code is expected to run with O(n) time complexity and O(1) space complexity. The elements in the array are between 0 to size(array) - 1 and the array will not be empty.

f({3,1,2,2,3,4,4,4}) --> 4


***

```
// java.util.* and java.util.streams.* have been imported for this problem.
// You don't need any other imports.

public static int getMaxRepetition(int[] a) {
    
int k = a.length;
for(int i = 0; i<a.length; i++){
    a[a[i]%k] += k ;
}

int max = 0;
int indx = 0;
for(int i =1; i<a.length; i++){
    if(a[i] > max){
        max = a[i];
        indx = i;
    }
}

    return indx;
}

```

# Number of Full Nodes in a Binary Tree 

***
Write a function to iteratively determine the total number of "full nodes" in a binary tree. A full node contains left and right child nodes. If there are no full nodes, return 0.


***

```
// java.util.* and java.util.streams.* have been imported for this problem.
// You don't need any other imports.

public int numberOfFullNodes(TreeNode root) { 
    
if(root == null){
    return 0;
}
    
Stack<TreeNode> stack = new Stack<TreeNode>();
stack.push(root);
int count = 0;
while(!stack.empty()){
    TreeNode temp = stack.pop();
    if(temp.left != null && temp.right != null){
        count++;
    }
    
    if(temp.left != null){
        stack.push(temp.left);
    }
    
    if(temp.right != null){
        stack.push(temp.right);
    }
}

return count;
    
}
```

# Find the Maximum BST Node 

***
Given a Binary Search Tree, return the node with the maximum data.

***

```
// java.util.* and java.util.streams.* have been imported for this problem.
// You don't need any other imports.

public TreeNode findMax(TreeNode root) {
     
   if(root == null){
       return null;
   }
    while(root.right!= null){
        root = root.right;
    }

return root;
    
}
```

# Insert a Node at the Tail of a Circular Linked List 

***
Given a circular linked list, write a method to insert a node at its tail. Return the list's head.


***

```
// java.util.* and java.util.streams.* have been imported for this problem.
// You don't need any other imports.

public ListNode insertAtTail(ListNode head, int data) {
    
if(head == null){
    head = new ListNode(data);
    head.next = head;
    return head;
}
ListNode curr = head;

while(curr.next != head){
    curr = curr.next;
}

curr.next = new ListNode(data);
curr.next.next = head;

return head;

}
```

# Number of Half Nodes in a Binary Tree
***
Write a function to find the total number of half nodes in a binary tree. A half node is a node which has exactly one child node. If there are no half nodes, return 0.

***

```
// java.util.* and java.util.streams.* have been imported for this problem.
// You don't need any other imports.

public int numberOfHalfNodes(TreeNode root) { 
   if(root == null){
       return 0;
   }                    

Stack<TreeNode> stack = new Stack<TreeNode>();

stack.push(root);
int hcount = 0;

while(!stack.empty()){
    TreeNode temp =  stack.pop();
    
    if(temp.left != null && temp.right == null){
        hcount++;
    }
    if(temp.right != null && temp.left == null){
        hcount++;
    }
    
    if(temp.left != null){
        stack.push(temp.left);
    }
    
    if(temp.right != null){
        stack.push(temp.right);
    }
}

return hcount;
 
}
```

# Remove Duplicate Nodes 

***
Given a singly-linked list, remove duplicates in the list and return head of the list. Target a worst case space complexity of O(n).

***

```
// java.util.* and java.util.streams.* have been imported for this problem.
// You don't need any other imports.

public ListNode removeDuplicates(ListNode head) {
        
if(head == null){
    return null;
}
ListNode curr = head;

while(curr.next != null){
    ListNode temp = curr;
    while(temp.next != null){
        if(temp.next.data == curr.data){
            temp.next = temp.next.next;
        }else{
            temp = temp.next;
        }
    }
    curr = curr.next;
}


 return head;   
}
```

# Find the Diameter of a BST

***

***

```
// java.util.* and java.util.streams.* have been imported for this problem.
// You don't need any other imports.

public int diameter(TreeNode root) {

if(root == null){
    return 0;
}

int left = 0;
if(root.left != null){    
left = findHeight(root.left);
}


int right = 0;
if(root.right != null){
right = findHeight(root.right);
}


return Math.max(1+left+right , Math.max(diameter(root.left) , diameter(root.right)));

}
```

# Find the kth Largest Node in a BST

***

***

```
// java.util.* and java.util.streams.* have been imported for this problem.
// You don't need any other imports.

public   LinkedList<TreeNode> recurr(TreeNode root, LinkedList<TreeNode> list){
    if(root.left != null){
    recurr(root.left, list);
    }
    list.add(root);
    if(root.right != null){
    recurr(root.right, list);
    }
    return list;
}

public TreeNode findKthLargest(TreeNode root, int k) {
    if(root == null){
        return null;
    }
    
    
    LinkedList<TreeNode> list = recurr(root,new LinkedList <TreeNode>());
    
    return list.get(list.size() - k);
    
    
}

```

# Find the Sum of all Elements in a Binary Tree Iteratively 

***
Given a binary tree, write a method to find and return the sum of all nodes of the tree iteratively.

***

```
// java.util.* and java.util.streams.* have been imported for this problem.
// You don't need any other imports.

public int sumItr(TreeNode root) { 
    if(root == null){
        return 0;
    }
    
int sum = 0;

Stack<TreeNode> stack = new Stack<TreeNode>();
stack.push(root);

while(!stack.empty()){
    TreeNode curr = stack.pop();
    
    sum += curr.data;
    if(curr.right != null){
        stack.push(curr.right);
    }
    
    if(curr.left != null){
        stack.push(curr.left);
    }
}
return sum;

}
```

# Horizontal Flip

***
You are given an m x n 2D image matrix where each integer represents a pixel. Flip it in-place along its horizontal axis.

***

```
// java.util.* and java.util.streams.* have been imported for this problem.
// You don't need any other imports.

public static void flipHorizontalAxis(int[][] matrix) {
    for(int i =0; i<matrix.length/2; i++){
        for(int j=0; j<matrix[0].length; j++){
            int temp = matrix[i][j];
            matrix[i][j] = matrix[matrix.length-1-i][j];
            matrix[matrix.length-1-i][j] = temp;
        }
    }
}

```

# Maximum Sum Path 

***

***

```
// java.util.* and java.util.streams.* have been imported for this problem.
// You don't need any other imports.

public static int maxSumPathMain(TreeNode root, int[] maxRecHolder){
    if(root == null){
        return 0;
    }
    
    int leftSum = maxSumPathMain(root.left, maxRecHolder);
    int  rightSum = maxSumPathMain(root.right, maxRecHolder);
   
    int nodeCumVal = Math.max(root.data + leftSum, root.data + rightSum);
     
    maxRecHolder[0] = Math.max(maxRecHolder[0], leftSum+root.data+rightSum);
    
    
    
    return nodeCumVal;
    
}

public static int maxSumPath(TreeNode root) {
    int[] maxRecHolder = new int[1];
    maxSumPathMain(root,maxRecHolder);
    return maxRecHolder[0];
        
}

```

# Looping Lists : Space complexity O(n)

***
Given a singly-linked list, implement a method to check if the list has cycles. The space complexity can be O(n). If there is a cycle, return true otherwise return false. Empty lists should be considered non-cyclic.

***

```
// java.util.* and java.util.streams.* have been imported for this problem.
// You don't need any other imports.

public Boolean isCyclic(ListNode head) {
    
HashSet<Integer> set = new HashSet<>();

if(head == null || head.next == null){
    return false;
}

ListNode curr = head;

while(curr.next != null){
    if(!set.contains(curr.data)){
        set.add(curr.data);
    }else{
        return true;
    }
    curr = curr.next;
}

return false;
}

```

# Bubble Sort
***
Write a method that takes in an array of ints and uses the Bubble Sort algorithm to sort the array 'in place' in ascending order. The method should return the same, in-place sorted array.

Note: Bubble sort is one of the most inefficient ways to sort a large array of integers. Nevertheless, it is an interview favorite. Bubble sort has a time complexity of O(n2). However, if the sample size is small, bubble sort provides a simple implementation of a classic sorting algorithm.

***

```
// java.util.* and java.util.streams.* have been imported for this problem.
// You don't need any other imports.

public static int[] bubbleSortArray(int[] arr){
    
for(int i = arr.length-1; i>0; i--){
    for(int j = 0; j < i; j++){
        if(arr[j] > arr[j+1]){
            int temp = arr[j];
            arr[j] = arr[j+1];
            arr[j+1] = temp;
        }
    }
}

    
    return arr;
}

```

# Print Paths

***
You're given a 2D board which contains an m x n matrix of chars - char[][] board. Write a method - printPaths that prints all possible paths from the top left cell to the bottom right cell. Your method should return an ArrayList of Strings, where each String represents a path with characters appended in the order of movement. You're only allowed to move down and right on the board. The order of String insertion in the ArrayList does not matter.

Example:

Input Board :      
{
    {A, X},
    {D, E}
}
Output: ["ADE", "AXE"]

***

```
// java.util.* and java.util.streams.* have been imported for this problem.
// You don't need any other imports.

public ArrayList<String> printPaths(char[][] board){
    
    ArrayList<String> ret = new ArrayList<>();
    StringBuilder sb = new StringBuilder();
    
    search(0 ,0, board, sb, ret);
    
    return ret;
    
}

public void search( int i, int j, char[][] board, StringBuilder sb, ArrayList ret){

if(i > board.length-1 || j>board[0].length-1) {
    return;
}  

sb.append(board[i][j]);

if(i == board.length-1 && j == board[0].length-1){
    ret.add(sb.toString());
    sb.deleteCharAt(sb.length()-1);
    return;
}

search(i, j+1, board, sb, ret);
search(i+1, j, board, sb, ret);

sb.deleteCharAt(sb.length()-1);
    
```

# Distance of a node from the root

***

***

```
// java.util.* and java.util.streams.* have been imported for this problem.
// You don't need any other imports.

public int pathLengthFromRoot(TreeNode root, int n1) {
    
    Queue<TreeNode> queue = new LinkedList<>();
    queue.add(root);
    queue.add(null);
    
    int size = 1;
    
    while(!queue.isEmpty()){
        TreeNode curr = queue.poll();
        
         if(curr != null &&  curr.data == n1){
            return size;
        }
        
       
        if(curr == null){
            size++;
            queue.add(null);
            continue;
            
        }
        
        if(curr.left != null){
            queue.add(curr.left);
        }
        
        if(curr.right != null){
            queue.add(curr.right);
        }
    }
    
    return size;
    
    
}
```

# Jam into a BST

***

***

```
// java.util.* and java.util.streams.* have been imported for this problem.
// You don't need any other imports.

public TreeNode insert(TreeNode root, int data) { 
    
    Queue<TreeNode> queue = new LinkedList<>();
    
    if(root == null){
        root = new TreeNode(data);
    }
    
    queue.add(root);
    
    while(!queue.isEmpty()){
        
        TreeNode curr = queue.remove();

        if(data > curr.data){
            if(curr.right != null){
                queue.add(curr.right);
            }else{
                curr.right = new TreeNode(data);
            }
        }
        
        if(data < curr.data){
            if(curr.left != null){
                queue.add(curr.left);
            }else{
                curr.left = new TreeNode(data);
            }
        }

    }
    
    return root;


}
```

# Rotate Linear Array

***

***

```
// java.util.* and java.util.streams.* have been imported for this problem.
// You don't need any other imports.

public static int[] rotateLeft(int[] arr, int k) {
    
    k = k%arr.length;
    
    for(int i =0 ; i< k; i++){
        
        int temp = arr[0];
        for(int j = 0; j< arr.length-1; j++){
            arr[j] = arr[j+1];    
        }
        arr[arr.length-1] = temp;
    }
    
    return arr;
    
}
```


# The Deepest Node 

***
Given a binary tree, write a method to find and return its deepest node. Return null for an empty tree.

***

```
// java.util.* and java.util.streams.* have been imported for this problem.
// You don't need any other imports.

public TreeNode findDeepest(TreeNode root) { 

if(root== null){
    return null;
}


Queue<TreeNode> queue = new LinkedList<>();

queue.add(root);

TreeNode curr = new TreeNode();

while(!queue.isEmpty()){
    curr = queue.remove();
    
    if(curr.left != null){
        queue.add(curr.left);
    }
    
    if(curr.right != null){
        queue.add(curr.right);
    }
    
}

return curr;
}
```

# Replace all Spaces

***
Write a method to replace all spaces in a string with a given replacement string.

replace("This is a test","/") --> "This/is/a/test"

Note: Avoid using the in-built String.replaceAll() method.

***

```
// java.util.* and java.util.streams.* have been imported for this problem.
// You don't need any other imports.

public static String replace(String a, String b) {

StringBuilder sb = new StringBuilder();

for(int i = 0; i< a.length();i++){
    if(a.charAt(i) == ' '){
      sb.append(b);  
    }else{
    sb.append(a.charAt(i));
}
}

return sb.toString();

}
```

# Are these Binary Trees Identical? 

***
Given two binary trees, determine if they are identical. If they are, return true otherwise return false.

***

```
// java.util.* and java.util.streams.* have been imported for this problem.
// You don't need any other imports.

public boolean isIdentical(TreeNode root1, TreeNode root2) {
    
if(root1==null && root2== null){
    return true;
}

if(root1 == null && root2 != null){
    return false;
}

if(root1!= null && root2 == null){
    return false;
}

return (root1.data == root2.data && isIdentical(root1.left, root2.left) && isIdentical(root1.right,root2.right));

}
```

# Fill in the Ancestors of the Node in a Binary Tree

***

***

```
// java.util.* and java.util.streams.* have been imported for this problem.
// You don't need any other imports.

//Populate the list of ancestors from bottom to top in the below list.
public ArrayList<Integer> ancestorsList = new ArrayList<Integer>();
public boolean printAncestors(TreeNode root, int nodeData) {
                       

if(root == null ){
    return false;
}

if(root.data == nodeData){
    return true;
}

if(printAncestors(root.left,nodeData) ==true  || printAncestors(root.right,nodeData) == true){
    ancestorsList.add(root.data);
    return true;
}

return false;
}
```

# Print all Nodes in the Range a .. b in a given BST 

***

***

```
// java.util.* and java.util.streams.* have been imported for this problem.
// You don't need any other imports.

public  ArrayList<Integer> rangeList = new ArrayList<Integer>();
public void printRange(TreeNode root, int a, int b) {

if(root != null){
                       
printRange(root.left, a, b);
if(root.data <= b && root.data >= a){
    rangeList.add(root.data);
}

printRange(root.right, a, b);
}

}
```

# Unique Chars in a String 

***

***

```
// java.util.* and java.util.streams.* have been imported for this problem.
// You don't need any other imports.

public static boolean areAllCharactersUnique(String str){
    
    if(str == null){
        return true;
    }
    
    HashSet<Character> set = new HashSet<Character>();
    
    for(int i = 0; i< str.length(); i++){
        if(!set.contains(str.charAt(i))){
            set.add(str.charAt(i));
        }else{
            return false;
        }
    }

return true;

}
```

# Mobile Game Range Module - Merging Ranges

***

***

```
// java.util.* and java.util.streams.* have been imported for this problem.
// You don't need any other imports.

public static ArrayList<Interval> mergeIntervals(ArrayList<Interval> intervalsList) {
    
    ArrayList<Interval> output = new ArrayList<Interval>();
    
    if(intervalsList.isEmpty()){
        return output;
    }
    
    if(intervalsList.size() == 1){
        return intervalsList;
    }
    
    Collections.sort(intervalsList, new Comparator<Interval>() {
        @Override
        public int compare (Interval o1, Interval o2){
            return Integer.compare(o1.start, o2.start);
        }
    });
    //System.out.println(intervalsList);
    
    Interval prev = intervalsList.get(0);
    
    for(int i = 1 ; i <= intervalsList.size() -1 ; i++ ){
     Interval curr = intervalsList.get(i);
        
        if(curr.start <= prev.end) {
            prev = new Interval(prev.start, Math.max(curr.end, prev.end));
            
        }else{
            output.add(prev);
            prev = curr;
        }
    }
    output.add(prev);

    
    return output;
}
```

# Insert a Node at a specified position in a Linked List 

***
Given a singly-linked list, implement a method to insert a node at a specific position and return the head of the list.

If the given position is greater than the list size, simply insert the node at the end.


***

```
// java.util.* and java.util.streams.* have been imported for this problem.
// You don't need any other imports.

public ListNode insertAtPosition(ListNode head, int data, int pos) {

    if(head == null){
        return (head = new ListNode(4));
    }
    
    if(pos == 1){
        ListNode nhead = new ListNode(data);
        nhead.next = head;
        return nhead;
    }
    
    ListNode curr = head;
    int counter = 1;
    
    while(curr.next != null){
        if(pos == (counter + 1)){
            ListNode temp = curr.next;
            curr.next = new ListNode(data);
            curr.next.next = temp;
        }
        curr = curr.next;
        counter++;
    }
    
    if(pos > counter){
        curr.next = new ListNode(data);
    }


    return head;

}
```

# Delete a List's Tail Node

***
Given a singly-linked list, write a method to delete its last node and return the head.

***

```
// java.util.* and java.util.streams.* have been imported for this problem.
// You don't need any other imports.

public ListNode deleteAtTail(ListNode head) {
    
    if(head == null || head.next == null){
        return null;
    }
    
    ListNode curr = head;
    while(curr.next.next != null){
        curr = curr.next;
    }    
    
    curr.next = null;
    return head;
    
}
```

# Reverse a string

***
Write a method that takes in a String and returns the reversed version of the String.

***

```
// java.util.* and java.util.streams.* have been imported for this problem.
// You don't need any other imports.

public static String reverseString(String str){
    if(str == null ){
        return null;
    }
    StringBuilder sb = new StringBuilder(str);
    
    sb.reverse();
    
    return sb.toString();
}

```

# Levelorder Traversal 

***
Given a binary tree, write a method to perform a levelorder traversal and return an ArrayList of integers containing the data of the visited nodes in the correct order.

***

```
// java.util.* and java.util.streams.* have been imported for this problem.
// You don't need any other imports.

public ArrayList<Integer> levelorder(TreeNode root) {
    
    Queue<TreeNode> queue = new LinkedList<TreeNode>();
    ArrayList<Integer> arr = new ArrayList<Integer>();
    
    if(root == null){
        return arr;
    }
    
    queue.add(root);
    
    while(queue.isEmpty() == false){
        TreeNode temp = queue.remove();
        
        arr.add(temp.data);
        
        if(temp.left != null){
        queue.add(temp.left);
        }
        
        if(temp.right != null){
        queue.add(temp.right);
        }
    }
    
    return arr;

}
```

# Generate Combinations of Parentheses 

***
Write a method to return all valid combinations of n-pairs of parentheses.

The method should return an ArrayList of strings, in which each string represents a valid combination of parentheses.

The order of the strings in the ArrayList does not matter.


***

```
// java.util.* and java.util.streams.* have been imported for this problem.
// You don't need any other imports.

public static ArrayList<String> combParenthesis(int pairs) {
    
    ArrayList<String> arr = new ArrayList<String>();
    StringBuilder sb = new StringBuilder();
    
    parenhelper(arr ,"", 0, 0, pairs*2);
    
    return arr;
}

public static void parenhelper(ArrayList<String> arr,String sb, int left, int right, int max){
    if(max == sb.length()){
        arr.add(sb);
        return;
    }
    
    if(left < max/2){
        parenhelper(arr, sb+"(", left+1, right, max);
    }
    
    if(right < left){
        parenhelper(arr, sb +")", left, right+1, max);
    }
}
```

# Insert a Node at the Specified Position in Doubly Linked List

***
In doubly linked list, implement a method to insert a node at specified position and return the list's head. Do nothing if insertion position is outside the bounds of the list.


***

```
// java.util.* and java.util.streams.* have been imported for this problem.
// You don't need any other imports.

public DoublyLinkedNode insertAtPos(DoublyLinkedNode head, int data, int pos) {
    
    int counter = 1;
    DoublyLinkedNode curr = head;
    
    if(head == null && pos == 1){
        return new DoublyLinkedNode(data);
    }
    
    if(head == null){
        return null;
    }
    
    if(pos == 1){
        DoublyLinkedNode temp2 = new DoublyLinkedNode(data);
        temp2.next = head;
        return temp2;
    }
    
    while(curr != null){
        if(counter == pos-1){
            DoublyLinkedNode temp = curr.next;
            curr.next = new DoublyLinkedNode(data);
            curr.next.next = temp;
            curr.next.prev = curr;
            curr = curr.next;
        }
        curr = curr.next;
        counter++;

    }

    return head;
}
```

# Iterative Inorder Traversal

***
Given a binary tree, write a method to perform the inorder traversal iteratively. Append the data of each node visited to an ArrayList. Return an empty Arraylist in the case of an empty tree.


***

```
// java.util.* and java.util.streams.* have been imported for this problem.
// You don't need any other imports.

public ArrayList<Integer> inorderItr(TreeNode root) {
    
    ArrayList<Integer> list = new ArrayList<Integer>();
    
    Stack<TreeNode> stack = new Stack<TreeNode>();
    
    if(root == null){
        return list;
    }
    
    TreeNode curr = root;
    
    while(curr != null || !stack.empty()){
        
        while(curr != null){
            stack.push(curr);
            curr = curr.left;
        }
        
        curr = stack.pop();
        
        list.add(curr.data);
        
        curr = curr.right;

    }
    
    return list;

}
```

# Delete the Node at the Specific Position in a Doubly Linked List

***
Given a doubly-linked list, write a method to delete the node at a given position (starting from 1 as the head position) and return the modified list's head. Do nothing if the input position is out of range.


***

```
// java.util.* and java.util.streams.* have been imported for this problem.
// You don't need any other imports.

public DoublyLinkedNode deleteAtPos(DoublyLinkedNode head, int pos) {
             

    DoublyLinkedNode curr = head;
    
    int counter = 1;
    
    if(head == null){
        return null;
    }
    
    if(pos == 1 ){
        head = head.next;
        return head;
    }
    
    DoublyLinkedNode prevt = head;

    while(curr != null){
        if(counter == pos){
            prevt.next = curr.next;
            if(curr.next != null){
            curr.next.prev = prevt;
            }
        }
            prevt = curr;
            curr = curr.next;
            counter++;
    }
    


    return head;
}
```

# Find the Number that Appears Once 

***

***

```
// java.util.* and java.util.streams.* have been imported for this problem.
// You don't need any other imports.

public static int singleNumber(int[] A) {
    
    HashMap<Integer,Integer> map = new HashMap<Integer,Integer>();
    
    for(int i = 0; i< A.length; i++){
        
        if(map.containsKey(A[i])){
            map.put(A[i], map.get(A[i]) + 1);
        }else{
        map.put(A[i], 1);
        }

    }

    int ret = 0;
    for(Integer key : map.keySet()){
        if(map.get(key) == 1){
            ret = key;
        }
    }
    
    return ret;
}
```

# Full Tree Decompression

***

***

```
public TreeNode decompressTree(String str){
    if (str == null) return null;
    String[] nodes = str.split(",");
    return decompress(nodes, 0);
}

private TreeNode decompress(String[] strNodes, int pos) {
    if (pos >= strNodes.length) return null;
    
    String curr = strNodes[pos];
    if (curr.equals("*")) return null;
    
    int nodeVal = Integer.parseInt(curr);
    
    TreeNode newNode = new TreeNode(nodeVal);
    
    newNode.left = decompress(strNodes, (pos * 2) + 1);  
    newNode.right = decompress(strNodes, (pos * 2) + 2);   
    
    return newNode;
}
```

# Convert a Binary Tree to its Mirror Image 

***
Write a function to convert a binary tree into its mirror image and return the root node of the mirrored tree.

***

```
// java.util.* and java.util.streams.* have been imported for this problem.
// You don't need any other imports.

public TreeNode mirror(TreeNode root) {
                      
    
    if(root == null){
        return null;
    }
    
    Queue<TreeNode> queue = new LinkedList<TreeNode>();
    
    queue.add(root);
    
    while(!queue.isEmpty()){
        
        TreeNode temp2 = null;
        
        TreeNode curr = queue.remove();
        
        // if(curr.left != null){
        //     queue.add(curr.left);
        //     temp2 = curr.left;
        //     if(curr.right != null){
        //     curr.left = curr.right;
        //     }
        // }
        // if(curr.right != null){
        //     queue.add(curr.right);
        //     if(temp2 != null){
        //     curr.right = temp2;
        //     }
        // }
        
        if(curr.left != null && curr.right !=null){
            queue.add(curr.left);
            queue.add(curr.right);
            temp2 = curr.left;
            curr.left = curr.right;
            curr.right = temp2;

        }
        
    }
    
    return root;

    
}
```

# Insert a Node at the Head in a Doubly Linked List 

***
Given a doubly linked list, implement a method to insert a node at its head. Return the head of the list.


***

```
// java.util.* and java.util.streams.* have been imported for this problem.
// You don't need any other imports.

public DoublyLinkedNode insertAtHead(DoublyLinkedNode head, int data) {
                
    if(head == null){
        return new DoublyLinkedNode(data);
    }
    
    DoublyLinkedNode temp = new DoublyLinkedNode(data);
    
    temp.next = head;
    head.prev = temp;
    
    return temp;
 
}
```

# Reverse an Integer

***
Implement a method that reverses an integer - without using additional heap space

***

```
// java.util.* and java.util.streams.* have been imported for this problem.
// You don't need any other imports.

public static int reverseInt(int x) {
        
        
    int rev = 0;      
    while(x != 0){
        rev = rev*10 + x%10;
        x = x/10;
    }

    return rev;
    
}
```


<!-- ## Background

This repo is intended for any individual wanting to improve their problem
solving skills for software engineering interviews.

Problems are grouped under their respective subtopic, in order to focus on
repeatedly applying common patterns rather than randomly tackling questions.

All questions are available on [leetcode.com] with some requiring [leetcode premium].

## Preface

It is highly recommended to read chapters 1, 2, 3, 4, 8, and 10 of [Cracking The Coding Interview]
to familiarize yourself with the following data structures and their operations:

- Arrays
- Maps
- Linked Lists
- Queues
- Heaps
- Stacks
- Trees
- Graphs

In addition, you should have a good grasp on common algorithms such as:

- Breadth-first search
- Depth-first search
- Binary search
- Recursion

## Notes

[This pdf] contains useful information for the built-in data structures in Java.

Other useful methods to know include [`substring()`](https://docs.oracle.com/javase/8/docs/api/java/lang/String.html#substring-int-int-), [`toCharArray()`](https://docs.oracle.com/javase/8/docs/api/java/lang/String.html#toCharArray--), [`Math.max()`](https://docs.oracle.com/javase/8/docs/api/java/lang/Math.html#max-int-int-),
[`Math.min()`](https://docs.oracle.com/javase/8/docs/api/java/lang/Math.html#min-int-int-), and [`Arrays.fill()`](https://docs.oracle.com/javase/8/docs/api/java/util/Arrays.html#fill-int:A-int-).

## Question List

The entire question list can be found here:
https://seanprashad.com/leetcode-patterns/.

In addition to viewing the question list, companies that have previously asked
the question in the past 6 months (_as of January 2020_) will be listed. You can
also use the checkboxes to mark which questions you've completed!

## Solutions

Solutions written in Java can be found in the [solutions] branch.

## Leetcode Discuss

[Leetcode discuss] is an amazing resource and features previous interview
questions, as well as compensation and general career advice.

## Tips to Consider

```
If input array is sorted then
    - Binary search
    - Two pointers

If asked for all permutations/subsets then
    - Backtracking

If given a tree then
    - DFS
    - BFS

If given a graph then
    - DFS
    - BFS

If given a linked list then
    - Two pointers

If recursion is banned then
    - Stack

If asked for maximum/minumum subarray/subset/options then
    - Dynamic programming

If asked for top/least K items then
    - Heap

If asked for common strings then
    - Map
    - Trie

Else
    - Map/Set for O(1) time & O(n) space
    - Sort input for O(nlogn) time and O(1) space
```

## Suggestions

Think a question should/shouldn't be included? Wish there was another feature?
Feel free to open an [issue] with your suggestion!

## Acknowledgements

This list is heavily inspired from [Grokking the Coding Interview] with
additional problems extracted from the [Blind 75 list] and this medium article
on [14 patterns to ace any coding interview question].

[leetcode.com]: https://leetcode.com
[leetcode premium]: https://leetcode.com/subscribe/
[this pdf]: https://drive.google.com/open?id=1ao4ZA28zzBttDkuS6MLQI52gDs_CJZEm
[cracking the coding interview]: http://www.crackingthecodinginterview.com/contents.html
[here]: https://hackernoon.com/14-patterns-to-ace-any-coding-interview-question-c5bb3357f6ed
[topcoder]: https://www.topcoder.com/community/competitive-programming/tutorials/dynamic-programming-from-novice-to-advanced/
[back to back swe youtube channel]: https://www.youtube.com/watch?v=jgiZlGzXMBw
[solutions]: https://github.com/SeanPrashad/leetcode-patterns/tree/solutions
[leetcode discuss]: https://leetcode.com/discuss/interview-question
[grokking the coding interview]: https://www.educative.io/courses/grokking-the-coding-interview
[issue]: https://github.com/SeanPrashad/leetcode-patterns/issues/new
[blind 75 list]: https://www.teamblind.com/article/New-Year-Gift---Curated-List-of-Top-100-LeetCode-Questions-to-Save-Your-Time-OaM1orEU?utm_source=share&utm_medium=ios_app
[14 patterns to ace any coding interview question]:  -->