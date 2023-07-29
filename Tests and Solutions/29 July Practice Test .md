29th July Programming Abstractions (Practice TEST)

## Q-1 Travel Package Combinations
![Travel package combinations ](https://github.com/yashasviyadav1/Programming-Abstractions/assets/124666305/10c2217d-c632-4d5d-85f7-0f718d36d334)
![Travel package combinations 2](https://github.com/yashasviyadav1/Programming-Abstractions/assets/124666305/74bab099-e7c1-4aca-bdc9-3d8009430812)

```java
/**
 *
 * NOTE : Class Name should be Main 
 *
 **/
import java.io.*;
import java.util.*;
class Main {
    
    public static void main(String[] args){
        
        // INPUT
        // note : since we not given with the size of array, so we can simply take input in single string and then split it into string array, and later convert this strArr to int arr 
        Scanner scn = new Scanner(System.in);
        String strInput = scn.nextLine();
        String strArr[] = strInput.split(" "); // split on basis of space  ("\\s+")
        int arr[] = new int[strArr.length];
        
        for(int i=0; i < strArr.length; i++)
            arr[i] = Integer.valueOf(strArr[i]);
        
            
        // algo 
        int size = arr.length;
        for(int i=0; i < size; i++){
            
            for(int j=i; j < size; j++){
                
                // printing subarray
                for(int k=i; k <= j; k++){
                    if(k==j)
                        System.out.print(arr[k]);
                    else System.out.print(arr[k] + " ");
                }
                System.out.println();
            
            }
            
        }
    }
}
```
## Q-2 Merge Sort

![merge sort ](https://github.com/yashasviyadav1/Programming-Abstractions/assets/124666305/1b8cbe6a-5c05-43f6-bf97-15235243f137)
![merge sort 2](https://github.com/yashasviyadav1/Programming-Abstractions/assets/124666305/af8ef855-eaff-468e-9461-a4453e1ddcfc)



```java
/**
 *
 * NOTE : Class Name should be Main 
 *
 **/
import java.io.*;
import java.util.*;
class Main {
    
    private static void conquer(int arr[], int start, int mid, int end){
        
        int length1 = mid - start + 1;
        int length2 = end - mid;
        
        int arr1[] = new int[length1];
        int arr2[] = new int[length2];
        
        // insert all part1 elements into arr1 and others into arr2 
        int orgArrIndex = start;
        for(int i=0; i < length1; i++)
            arr1[i] = arr[orgArrIndex++];
            
        for(int i=0; i < length2; i++)
            arr2[i] = arr[orgArrIndex++];
        
        // now merge the 2 sorted arrays using 2 pointers, and place it into org array
        int i = 0;
        int j = 0;
        orgArrIndex = start;
        while( i < length1 && j < length2){
            
            if(arr1[i] < arr2[j])
                arr[orgArrIndex++] = arr1[i++];
            else arr[orgArrIndex++] = arr2[j++];
        }
        
        // if any 1 array is still not complete 
        while(i < length1) arr[orgArrIndex++] = arr1[i++];
        while(j < length2) arr[orgArrIndex++] = arr2[j++];
        
        // sorted
    }
    
    private static void divide(int arr[], int start, int end){
        
        if(start >= end) // arr of size 1 is found
            return;
            
        int mid = start + (end - start)/2;
        
        divide(arr, start, mid);
        divide(arr, mid+1, end);
        conquer(arr, start, mid, end);
        
    } 
    public static void main(String[] args){
        
       // INPUT
        // note : since we not given with the size of array, so we can simply take input in single string and then split it into string array, and later convert this strArr to int arr 
        Scanner scn = new Scanner(System.in);
        String strInput = scn.nextLine();
        String strArr[] = strInput.split(" "); // split on basis of space  ("\\s+")
        int arr[] = new int[strArr.length];
        
        for(int i=0; i < strArr.length; i++)
            arr[i] = Integer.valueOf(strArr[i]);
        
        
        // algo 
        int start = 0;
        int end = arr.length-1;
        divide(arr, start, end);
        
        for(int ele:arr)
            System.out.print(ele + " ");
        
    }
}
```

## Q3- Subarray with 0 sum
![find subarrays with 0 sum](https://github.com/yashasviyadav1/Programming-Abstractions/assets/124666305/075cc691-551f-4c40-9991-741b20370cc8)
![find subarrays with 0 sum 2](https://github.com/yashasviyadav1/Programming-Abstractions/assets/124666305/dca25ef7-caf8-4956-91cb-1af0daae8f1e)

```java
/**
 *
 * NOTE : Class Name should be Main 
 *
 **/
import java.io.*;
import java.util.*;
class Main {
    public static void main(String[] args){
        
        
        // INPUT
        // note : since we not given with the size of array, so we can simply take input in single string and then split it into string array, and later convert this strArr to int arr 
        Scanner scn = new Scanner(System.in);
        String strInput = scn.nextLine();
        String strArr[] = strInput.split(" "); // split on basis of space  ("\\s+")
        int arr[] = new int[strArr.length];
        
        for(int i=0; i < strArr.length; i++)
            arr[i] = Integer.valueOf(strArr[i]);
            
        // algo 
        boolean ansFound = false;
        int size = arr.length;
        for(int i=0; i < size; i++){
            
            int sum = 0;
            for(int j=i; j < size; j++){
                sum += arr[j];
                if(sum == 0){ // sub array with 0 sum found 
                    ansFound = true;
                    for(int k=i; k <= j; k++)
                        System.out.print(arr[k] + " ");
                    System.out.println();
                }
                
            }
        }
        
        if(!ansFound)
            System.out.print("-1");
        
    }
       
    
}
```

## Q-4 Selection Sort
![selection sort ](https://github.com/yashasviyadav1/Programming-Abstractions/assets/124666305/04a0b9eb-3206-414b-9070-0738c6fc8eb0)
![selection sort 2](https://github.com/yashasviyadav1/Programming-Abstractions/assets/124666305/dd6e0863-5d65-4daf-98fa-937955ffd17d)

```java
/**
 *
 * NOTE : Class Name should be Main 
 *
 **/
import java.io.*;
import java.util.*;
class Main {
    public static void main(String[] args){
        
        //input 
        Scanner scn = new Scanner(System.in);
        String strInput = scn.nextLine();
        String strArr[] = strInput.split(" "); // split as per spaces
        int arr[] = new int[strArr.length];
        
        int size = arr.length;
        for(int i=0; i < size; i++){
            arr[i] = Integer.valueOf(strArr[i]);
            System.out.print(arr[i] + " ");
        }
        System.out.println();
        
        //algo - selection sort 
        for(int i=0; i < size; i++){
            
            int minValueIndex = i; 
            for(int j=i+1; j < size; j++){
                
                if(arr[j] < arr[minValueIndex])
                    minValueIndex = j;
            }
            
            int temp = arr[i];
            arr[i] = arr[minValueIndex];
            arr[minValueIndex] = temp;
            
        }
        
        // printing arr
        for(int ele:arr)
            System.out.print(ele + " ");
        
    }
}
```
