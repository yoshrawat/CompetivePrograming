```
// "static void main" must be defined in a public class.
// https://leetfree.com/problems/longest-substring-with-at-most-two-distinct-characters.html

public class Main {
    
    public static void main(String[] args) {
        String s ="eceba";
        int k = 2;
        System.out.println(findDistinct( s, k));
    }
    
    public static int findDistinct( String str, int k ){
        Map<Character, Integer> map = new HashMap<>();
        int result = 0;
        int left = 0;
        int right = 0;
        int distinct = 0;
        String resultedString="";
        char[] ch = str.toCharArray();
        while( right < ch.length){
            if( map.getOrDefault( ch[right], 0) == 0  ){
                distinct++;
            }
            map.put( ch[right], map.getOrDefault( ch[right], 0) + 1);
            right++;
            
            System.out.println("distinct::" + distinct);
            while( left < right && distinct > k ){
                map.put( ch[left], map.getOrDefault( ch[left], 0) - 1);
                if( map.get(ch[left]) == 0){
                    distinct--;
                }
                left++;
            }
            if( right - left > result ){
                resultedString = str.substring( left, right);
                result = right - left;
            }
        }
        System.out.println("resultedString::"+ resultedString);
        return result;
    }
}
/*
Given a string, find the length of the longest substring T that contains at most 2 distinct characters.

For example, Given s = “eceba”,

T is "ece" which its length is 3.
*/
```
