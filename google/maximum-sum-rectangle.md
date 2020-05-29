# Maximum sum rectangle

// "static void main" must be defined in a public class.

// [https://www.geeksforgeeks.org/maximum-sum-rectangle-in-a-2d-matrix-dp-27/](https://www.geeksforgeeks.org/maximum-sum-rectangle-in-a-2d-matrix-dp-27/)

```text
public class Main {
    private static int maxSumRectangle( int arr[][] ){
        int result = 0;
        int left =0, right =0, top=0, bottom=0;
        int row = arr.length;
        int col = arr[0].length;

        int[][] prefixSum = new int[row][col];
        for( int j = 0; j < col; j++){
            for( int i =0; i < row; i++ ){
                if( j == 0 ){
                    prefixSum[i][j] = arr[i][j];
                }else{
                    prefixSum[i][j] = arr[i][j] + prefixSum[i][j-1];
                }
            }
        }
        // for( int i = 0; i < col; i++){
        //     for( int j =0;j<row;j++){
        //         System.out.print(prefixSum[j][i]+",");
        //     }
        //     System.out.println("");
        // }

        for( int k = 0; k < col; k++ ){
            for( right =k; right < col; right++){
                // traverse the prefixSum sum from top to bottom to get the max sum
                if( k != 0 &&  k < col - 1){
                    for( int i =0; i< row; i++){
                        prefixSum[i][right] -= prefixSum[i][k-1];
                    }
                }
                int currentSum = calculateMaxSum( prefixSum, right);

                //System.out.println("currentSum::"+ currentSum + ", left::"+k+",right::"+right);
                result = Math.max( result, currentSum);
            }
            //System.out.println("end");
        }
        return result;
    }
    private static int calculateMaxSum(int[][] prefixSum,int col ){
        int maxSum = Integer.MIN_VALUE;
        int sum =0;
        for( int i =0; i< prefixSum.length;i++){
            //System.out.println("prefixSum::"+prefixSum[i][col]);
            sum += prefixSum[i][col];
            if( sum > maxSum ){
                maxSum = sum;
            }
            if( sum < 0 ){
                sum = 0;
            }
        }
        return maxSum;
    }
    public static void main(String[] args) {
        System.out.println("Hello World!");
        int arr[][] = new int[][] {{1, 2, -1, -4, -20},  
                    {-8, -3, 4, 2, 1},  
                    {3, 8, 10, 1, 3},  
                    {-4, -1, 1, 7, -6}}; 
        System.out.println(maxSumRectangle(arr)); 
    }
}
```

