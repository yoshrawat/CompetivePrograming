# Max Consecutive Ones II

```text
// "static void main" must be defined in a public class.
//https://www.leetfree.com/problems/max-consecutive-ones-ii.html
public class Main {
    public static void main(String[] args) {
        int[] A = {1,1,1,0,0,0,1,1,1,1,0};
        System.out.println(longestOnes(A,1));
    }
    public static int longestOnes(int[] A, int K) {
        int result = 0;
        int left = 0;
        int right = 0;
        int count = 0;

        while( right < A.length){
            if( A[right] == 0){
                count++;
            }
            right++;

            while( left < right && count > K ){
                if( A[left] == 0 ){
                    count--;
                }
                left++;
            }
            if( right - left > result ){
                result = right - left;
            }
        }
        return result;
    }
}
/*
Given a binary array, find the maximum number of consecutive 1s in this array if you can flip at most one 0.

Example 1:
Input: [1,0,1,1,0]
Output: 4
Explanation: Flip the first zero will get the the maximum number of consecutive 1s.
    After flipping, the maximum number of consecutive 1s is 4.
Note:

The input array will only contain 0 and 1.
The length of input array is a positive integer and will not exceed 10,000
Follow up:
What if the input numbers come in one by one as an infinite stream? In other words, you can't store all numbers coming from the stream as it's too large to hold in memory. Could you solve it efficiently?
*/
```

