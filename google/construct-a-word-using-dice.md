# Construct a word using dice

// "static void main" must be defined in a public class.

// [https://leetcode.com/discuss/interview-question/267985/google-interview-construct-a-word-using-dice](https://leetcode.com/discuss/interview-question/267985/google-interview-construct-a-word-using-dice)

```text
public class Main {
    public static void main(String[] args) {
        char[][] arr = {
                        {'a','l','c','d','e','f'},
                        {'a','b','c','d','e','f'},
                        {'a','b','c','h','e','f'},
                        {'a','b','c','d','o','f'},
                        {'a','b','c','l','e','f'}
                    };
        char[] pat = {'h','e','l','l','0'};

        int row = arr.length;
        int col = arr[0].length;
        boolean[] visited = new boolean[row];
        ArrayList<Character> list = new ArrayList<>();
        System.out.println(backtracking( arr, visited, row, col, pat, 0, list ));

    }
    public static boolean backtracking( char[][] arr, boolean[] visited, int row, int col, char[] par, int index, ArrayList<Character> list ){
        if( index == par.length){
            System.out.println("result:: "+ list );
            return true;
        }
        for( int i =0; i < row; i++ ){
            if( !visited[i]){
                visited[i] = true;
                char[] ch = arr[i];
                for( char curr : ch ){
                    if( curr == par[index] ){
                        list.add( curr );
                        if(backtracking( arr, visited, row, col, par, index + 1, list)){
                            return true;
                        }
                        list.remove( list.size() - 1);
                    }
                }
                visited[i] = false;
            }
        }
        return false;
    }
}
```

/\* Given a word of length n and n six-sided dice with a character in each side. Find out if this word can be constructed by the set of given dice.

Example 1:

Input: word = "hello" dice = \[\[a, l, c, d, e, f\], \[a, b, c, d, e, f\], \[a, b, c, h, e, f\], \[a, b, c, d, o, f\], \[a, b, c, l, e, f\]\] Output: true Explanation: dice\[2\]\[3\] + dice\[1\]\[4\] + dice\[0\]\[1\] + dice\[4\]\[3\] + dice\[3\]\[4\]

Example 2:

Input: word = "hello" dice = \[\[a, b, c, d, e, f\], \[a, b, c, d, e, f\], \[a, b, c, d, e, f\], \[a, b, c, d, e, f\], \[a, b, c, d, e, f\]\] Output: false

Example 3:

Input: word = "aaaa" dice = \[\[a, a, a, a, a, a\], \[b, b, b, b, b, b\], \[a, b, c, d, e, f\], \[a, b, c, d, e, f\]\] Output: false

\*/

