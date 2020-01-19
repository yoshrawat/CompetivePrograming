```
// "static void main" must be defined in a public class.
// https://leetcode.com/discuss/interview-question/350363/Google-or-OA-2018-or-Max-Distance
public class Main {
    static class BinaryNode{
        char ch;
        boolean isEnd;
        BinaryNode left;
        BinaryNode right;
        
        public BinaryNode( char ch){
            this.ch = ch;
            left = null;
            right = null;
            this.isEnd = false;
        }
    }
    public static int findMaxLength( List<String> list ){
        
        BinaryNode root = new BinaryNode('A');
        BinaryNode temp = root;
        for( String str : list ){
            buildTrieTree( str, temp);
        }
        
        printTrieTree( root );
        
        temp = giveStartingNode( root );
        System.out.println("temp::"+ temp.ch);
        
        int l = findMaxLenChild( temp.left);
        int r = findMaxLenChild( temp.right);
        System.out.println("l+r::"+(l+r));
        return 0;
    }
    public static int findMaxLenChild( BinaryNode  current ){
        if( current == null ){
            return 0;
        }
        return 1 + Math.max( findMaxLenChild(current.left),findMaxLenChild(current.right) );
    }
    public static BinaryNode giveStartingNode( BinaryNode current ){
        if( current.left != null && current.right != null ){
            return current;
        }
        if( current.left != null ){
            return giveStartingNode( current.left);
        }else{
            return giveStartingNode( current.right);
        }
    }
    public static void printTrieTree( BinaryNode current  ){
        if( current == null ){
            return;
        }
        System.out.println( current.ch);
        printTrieTree( current.left);
        printTrieTree( current.right);
    }
    public static void buildTrieTree( String str, BinaryNode current ){
        for( char ch : str.toCharArray() ){
            if( ch == '0'){
                if( current.left != null ){
                    current = current.left;
                }else{
                    BinaryNode child = new BinaryNode( ch );
                      current.left = child;
                      current = current.left;
                }
            }else{
                if( current.right != null ){
                    current = current.right;
                }else{
                    BinaryNode child = new BinaryNode( ch );
                      current.right = child;
                      current = current.right;
                }
                current.isEnd = true;
            }
        }
    }
    public static void main(String[] args) {
        System.out.println("Hello World!");
        // List<String> list = new ArrayList<>();
        // list.add("11001");
        // list.add("11111");
        List<String> binaries = new ArrayList(Arrays.asList("1011100", "1011011","1001111"));
        findMaxLength(binaries);
        binaries = new ArrayList(Arrays.asList("101", "111","000"));
        findMaxLength(binaries);
    }
}

/*
The distance between 2 binary strings is the sum of their lengths after removing the common prefix. For example: the common prefix of 1011000 and 1011110 is 1011 so the distance is len("000") + len("110") = 3 + 3 = 6.

Given a list of binary strings, pick a pair that gives you maximum distance among all possible pair and return that distance.
*/
```
