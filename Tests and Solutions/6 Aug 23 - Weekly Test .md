

## Que - 1 : Star Insertion in given string 
```
input :-
str = "abcdef"
chars[] = {1,3} // insert * at these indiced

Output :- a*bc*def
```
```java

import java.io.*;
import java.util.*;
class Main {
    public static void main(String[] args){
        
        //input 
        Scanner scn = new Scanner(System.in);
        String str = scn.next();
        scn.nextLine(); // to consume extra space prod due to .next() or .nextInt()
        
        String indexString = scn.nextLine();
        String indexStringArr[] = indexString.split(" "); // split index on basis of space
        int chars[] = new int[indexStringArr.length];
        for(int i=0; i < chars.length; i++)
            chars[i] = Integer.valueOf(indexStringArr[i]);
        
        // algo 
        String ans = "";
        int charsIndex = 0; 
        
        for(int i=0; i < str.length(); i++){
            
            // if we are out of char array bound, then copy rest str as it is and stop 
            if(charsIndex >= chars.length){
                ans += str.substring(i, str.length());
                break;
            }
            
            // else if we found the target index, then insert the * 
            else if(i == chars[charsIndex]){
                ans += "*";
                charsIndex++;
            }
            
            ans += str.charAt(i);
        }
        
        System.out.print(ans);
    }
    
}
```
## Que - 2 : Analyze Character freq in different text 
![q-2 Analyzinng str char freq](https://github.com/yashasviyadav1/Programming-Abstractions/assets/124666305/1ed5009b-61b8-4cfb-880a-4217872f0942)

## Que - 3 : Generating all possible substrings, in ascending order of their length 
![q3 generating all possible substr](https://github.com/yashasviyadav1/Programming-Abstractions/assets/124666305/1df8bc8b-2abe-4573-85be-734bf2364e06)

```java
/**
 *
 * NOTE : Class Name should be Main 
 *
 **/
import java.io.*;
import java.util.*;
class Main { 
    /* Flow : - 
       
       str = "abc"
       arr = {a, ab, abc, b, bc, c]
       
       after sorting on basis of len :- 
       arr = {a, b, c, ab, bc, abc}
    
    */
    
    // Bubble sort 
    public static void sortOnBasisOfLen(String s[]){
        
        for(int i=1; i < s.length; i++){
            for(int j=0; j <= s.length - i - 1; j++){
                
                if( (s[j].length()) > (s[j+1].length()) ){
                    String temp = s[j];
                    s[j] = s[j+1];
                    s[j+1] = temp;
                }
            }
        }
    }
    
    public static void main(String[] args){
    
        //input 
        Scanner scn = new Scanner(System.in);
        String str = scn.next();
        int n = str.length();
        
        //algo 
        String arr[] = new String[(n*(n+1))/2]; // arr consisting of all substrings of 'str'
        
        int index = 0;
        for(int i=0; i < str.length(); i++){
            
            for(int j=i; j < str.length(); j++){
                arr[index++] = str.substring(i,j+1);
            }
        }
        
        sortOnBasisOfLen(arr);
        
        for(int i=0; i < arr.length; i++)
            System.out.println(arr[i]);
        
    }
}
```

## Que - 4 : rotated String (Not Done)

![q3 - rotated string ](https://github.com/yashasviyadav1/Programming-Abstractions/assets/124666305/b68c1f4b-9591-4f7f-a71b-1b5b094abbe0)




