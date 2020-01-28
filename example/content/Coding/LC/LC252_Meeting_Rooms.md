### [LC252](https://www.lintcode.com/problem/meeting-rooms/description)

Interval intersect detection.
O(n^2) BF:
```java
public boolean canAttendMeetings(List<Interval> intervals) {
    
        // size = 1
        if(intervals.size()<=1){
            return true;
        }
    //  O(n^2)
    
        
        // end corner: size=1 
        // O(n^2) BF
        for(int i = 0; i < intervals.size(); i++){
            for(int j = i + 1; j < intervals.size(); j++){
                if(intersectP(intervals.get(i), intervals.get(j)) || 
                   intersectP(intervals.get(j),intervals.get(i)))
                    return false;
            }// end j
        }// end i
        return true;
    }
    
    static boolean intersectP(Interval iA, Interval iB){
        return (iA.end > iB.start) && (iA.start < iB.end);  
}
```
Usage of java List.get() and List.size()

O(nlg(n)), shorter and faster
Java comparator and lambda

```java
 public boolean canAttendMeetings(List<Interval> intervals) {
    
        // size = 1
        if(intervals.size()<=1){
            return true;
        }
        // O(nlg(n)) = O(nlg(n))+O(n)
        Collections.sort(intervals, 
            (Interval iA, Interval iB) -> (iA.start - iB.start));
        for(int i = 0; i < intervals.size() - 1; i++){
            if(intervals.get(i).end > intervals.get(i+1).start){
                return false;
            }
        }
        return true;
        
    }
```