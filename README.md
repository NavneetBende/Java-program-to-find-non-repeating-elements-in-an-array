Non Repeating elements in an Array in Java
Here, in this page you will find the code for printing non repeating elements in an array in java programming language We are given with an array and need to print the distinct elements among them. You will found different methods to solve this problem in this page.

Non Repeating elements in an Array in java
Example
Input : arr[8] = [10, 20, 40, 30, 50, 20, 10, 20]
Output : 40 30 50
Explanation : 40, 30 and 50 are occur 1 time in the given array, 10 occurs 2 times and 20 occurs 3 times.
Here, we will discuss the following methods in this page to print the distinct elements in the given input array.

Method 1 : Using Two loops
Method 2 : Using hash Map
Let’s discuss each method one by one,

Method 1 :
In this method we will count the frequency of each elements using two for loops.

To check the status of visited elements create a array of size n.
Run a loop from index 0 to n and check if (visited[i]==1) then skip that element.
Otherwise create a variable count = 1 to keep the count of frequency.
Run a loop from index i+1 to n
Check if(arr[i]==arr[j]), then increment the count by 1 and set visited[j]=1.
After complete iteration of inner for loop and check if count==1, then print that ith element.
Non repeating in java
Related Pages
Counting Distinct Elements in an Array

Finding  Repeating elements in an Array

Removing Duplicate elements from an array

Finding Minimum scalar product of two vectors

Finding Maximum scalar product of two vectors in an array 

Method 1 : Code in Java
Run
import java.util.Arrays;

class Main
{
   public static void countFreq(int arr[], int n)
   {
         boolean visited[] = new boolean[n];
         Arrays.fill(visited, false);
         // Traverse through array elements and
         // count frequencies
         for (int i = 0; i < n; i++) {

            // Skip this element if already processed
            if (visited[i] == true)
             continue;

            // Count frequency
            int count = 1;
            for (int j = i + 1; j < n; j++) {
                if (arr[i] == arr[j]) {
                   visited[j] = true;
                   count++;
                }
            }
            if(count==1)   
              System.out.println(arr[i]);
   }
} // Driver code 

public static void main(String []args) 
{ 
int arr[] = new int[]{10, 30, 40, 20, 10, 20, 50, 10}; 
int n = arr.length;
 countFreq(arr, n); 
}
 }
Output
30 
40 
50
Method 2 :
In this method we will count use hash-map to count the frequency of each elements.

Declare a hash map and a variable count_dis=0.
Start iterating over the entire array
If element is present in map, then increase the value of frequency by 1.
Otherwise, insert that element in map.
After complete iteration over array, start traversing map and print those key which have value 1.
Time and Space Complexity :
Time Complexity : O(n)
Space Complexity : O(n)
Method 2 : Code in Java
Run
import java.util.*;
import java.util.Arrays;

class Main
{
   static void countFreq(int arr[], int n)
   {
      Map<Integer, Integer> mp = new HashMap<>();
      int count_dis=0;
      // Traverse through array elements and
      // count frequencies
      for (int i = 0; i < n; i++)
      {
         if (mp.containsKey(arr[i]))
         {
           mp.put(arr[i], mp.get(arr[i]) + 1);
         }
         else
         {
           mp.put(arr[i], 1);
         }
     }
     // Traverse through map and print frequencies
     for (Map.Entry<Integer, Integer> entry : mp.entrySet())
     {    if(entry.getValue()==1)
          System.out.println(entry.getKey()+" ");
     }
     
  }
  // Driver code
  public static void main(String []args)
  {
       int arr[] = new int[]{10, 40, 50, 20, 10, 20, 30, 10};
       int n = arr.length;
       countFreq(arr, n);
  }
}
Output
30 
40 
50
