
```
// https://www.programcreek.com/2014/05/leetcode-meeting-rooms-ii-java/
// https://www.leetfree.com/problems/meeting-rooms-ii.html
// Given an array of meeting time intervals consisting of start and end times [[s1,e1],[s2,e2],...] 
// find the minimum number of conference rooms required.

public int minMeetingRooms(Interval[] intervals) {
    Arrays.sort(intervals, (a, b) -> a.start - b.start);
    int count = 0;
    PriorityQueue<Interval> pq = new PriorityQueue<>((a, b) -> b.end - a.end );
    pq.add( intervals[0]);
    
    for( int i =1; i < intervals.length; i++ ){
        Interval current = intervals[i];
        Interval earliest = pq.peek();
        if( current.start >= earliest.end ){
            earliest.end = current.end;
        }else {
            pq.add( current );
        }
        pq.add( earliest);
    }
    return pq.size();
}
```
