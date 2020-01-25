
``` java
class Solution {
    public String addBinary(String a, String b) {
        int i = a.length()-1;
        int j = b.length()-1;
        boolean carry = false;
        String res = "";
        while(i >= 0 || j >= 0){
            if(i >= 0 && j >= 0){
                int tmp =  a.charAt(i) - '0' + b.charAt(j) - '0' + (carry?1:0);
                carry = false;
                if(tmp >= 2){
                    carry = true;
                    tmp -= 2;
                }    
                res = String.valueOf(tmp) + res;
                i--; 
                j--;
            } else{
                if(i < 0 && i < j){
                    int tmp =  b.charAt(j) - '0' + (carry?1:0);
                    carry = false;
                    if(tmp >= 2){
                        carry = true;
                        tmp -= 2;
                    }
                    res = String.valueOf(tmp) + res;
                    j--;
                }
                else if (i > j && j < 0){
                    int tmp =  a.charAt(i) - '0' + (carry?1:0);
                    carry = false;
                    if(tmp >= 2){
                        carry = true;
                        tmp -= 2;
                    }
                    res = String.valueOf(tmp) + res;
                    i--;
                }
                else{
                    int tmp = a.charAt(0) - '0'+ b.charAt(0) - '0' + (carry?1:0);
                    carry = false;
                    if(tmp >= 2){
    
                        res = "1" + String.valueOf(tmp-2) + res;
                    }
                    else{
                        res = String.valueOf(tmp) + res;
                    }
                    i--;
                    j--;
                    
                }
            }
            
            
        }
        if(carry){
            res = "1" + res;
        }
        return res;
    }
}
```
3ms, 39.6
```java
class Solution {
    public String addBinary(String a, String b) {
        int i = a.length()-1;
        int j = b.length()-1;
        boolean c = false;
        String sum = "";
        ResType res = new ResType();
        while(i >= 0 || j >= 0){
            res = addOneBit((i>=0)?(a.charAt(i)-'0'):0,
                            (j>=0)?(b.charAt(j)-'0'):0,
                            c);
            c = res.c;
            sum = String.valueOf(res.r) + sum;
            i--;
            j--;
        }
        if (res.c){
            sum = "1" + sum;
        }
        return sum;
    }
    
    class ResType{
        boolean c = false;
        int r = 0;
    }
    ResType addOneBit(int x, int y, boolean c){
        ResType res = new ResType();
        res.c = (x + y + (c?1:0)) >= 2;
        res.r = (x + y + (c?1:0)) % 2;
        return res;
    }
}
```

```java
class Solution {
    boolean carry = false;
    int bit = 0;
    
    public String addBinary(String a, String b) {
        int i = a.length()-1;
        int j = b.length()-1;
        String sum = "";
        
        while(i >= 0 || j >= 0){
            addOneBit((i>=0)?(a.charAt(i)-'0'):0,
                      (j>=0)?(b.charAt(j)-'0'):0,
                      this.carry);
            sum = String.valueOf(this.bit) + sum;
            i--;
            j--;
        }
        if (this.carry){
            sum = "1" + sum;
        }
        return sum;
    }
    
    void addOneBit(int x, int y, boolean c){
        this.carry = (x + y + (c?1:0)) >= 2;
        this.bit = (x + y + (c?1:0)) % 2;
    }
}
```