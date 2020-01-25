LC345[https://leetcode.com/problems/reverse-vowels-of-a-string/description/]

Be cautious with a[i++] and b[j--].
Using char[] or StringBuilder instead of String when it's changing rapidly. 


```java
class Solution {
    private final static HashSet<Character> vowels = new HashSet<>(
        Arrays.asList('a', 'e', 'i', 'o', 'u', 'A', 'E', 'I', 'O', 'U'));
    
    
    public String reverseVowels(String s) {
        if (s == null) return null;

        int front = 0, back = s.length()-1;
        char[] result = new char[s.length()];
        while(front <= back){
            char cf = s.charAt(front), cb = s.charAt(back);
            if(!vowels.contains(cf)){
                result[front++] = cf;
            }
            else if(!vowels.contains(cb)){
                result[back--] = cb;
            }else{
                result[front++] = cb;
                result[back--] = cf;
            }
            
        }
        return new String(result);
    }
    
   
}
```