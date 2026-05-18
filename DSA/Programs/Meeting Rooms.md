##### Question:
- There will meetings that will happen and we need to assign minimum number of rooms to the meetings.
- Example: 
```JavaScript
arr = [[[4, 6], [6, 7], [8, 10]];
output = 2;
```

**Explanation:**
The least time the meeting to start is 0 and 20 is last. i.e start - 4 & end - 10; and 
If the meeting ends at 6 and also next meeting start at 6 then we can use the same room.
So, considering that we need only 2 rooms.
##### Brute Force Approach:
Find the max time and min time between all the meetings. (Start time and end time of all the meetings). i.e. start: 4(minimum) and end: 10(maximum) - for now. 
Create an array with size: maxEnd - minEnd. here it would be 10 - 4 = 6. While creating a array add +1, so it would create 7. and also fill the array with 0 while creating.
Now Loop through array for every element and as it is an 2d array we will take another loop and add +1 to the array we have created before.
Now return the max element in the array.

**Code:**

```JavaScript
const log=console.log; 
const meetings=[[4, 6], [6, 7], [8, 10]];

//Brute Force
function meetingRooms(lectures) {
  let minStart = Infinity;
  let maxEnd = -Infinity;    //Max and Min is needed to find the length of the array that we need to create
  for (const [s, e] of lectures) {
    minStart = Math.min(minStart, s);
    maxEnd = Math.max(maxEnd, e);
  }
  const count = new Array(maxEnd - minStart + 1).fill(0);
  for (const [s, e] of lectures) {
    for (let t = s; t <= e; t++) {
      count[t - minStart] += 1;  //count[-1] -> can never be -1 & also we are adding +1 to the index of the new array we have created (i.e count ).
    }
  }
  return Math.max(...count);
}
log(meetingRooms(meetings));
```


##### Two Pointer Approach:

From the given array assign start elements in one array and end elements in another array 
Sort both the arrays.
Use a loop to check every element in the array for that logic would be i< start. length && j< end. length. The program will continue to loop until any of the condition is not true.
Now start checking each element from start array and end array.
If start array element is small than end array element then increase i and also increase room count.
If start array element is bigger than the end array element then increase j and also decrease room count.
We return the **maximum** room count we saw during the entire process
**Time Complexity:** O(N log N) for sorting **Space Complexity:** O(N) for the two arrays

After sorting:
- starts = 0, 5, 10
- ends = 10, 15, 20

| Step | i   | j   | starts[i] | ends[j] | Comparison | Action | rooms_used | max_rooms |
| ---- | --- | --- | --------- | ------- | ---------- | ------ | ---------- | --------- |
| 1    | 0   | 0   | 0         | 10      | 0 < 10     | Start  | 1          | 1         |
| 2    | 1   | 0   | 5         | 10      | 5 < 10     | Start  | 2          | 2         |
| 3    | 2   | 0   | 10        | 10      | 10 >= 10   | End    | 1          | 2         |
| 4    | 2   | 1   | 10        | 15      | 10 < 15    | Start  | 2          | 2         |
| 5    | 3   | 1   | -         | -       | i >= len   | Stop   | -          | -         |

**Answer: 2

The Complete Approach:
1. Create two separate arrays: one for all start times, one for all end times
2. **Sort both arrays**
3. Use two pointers (i for starts, j for ends), both starting at 0
4. Keep track of `rooms_currently_used` and `max_rooms`
5. Loop while `i < starts.length AND j < ends.length`
6. In each iteration:
    - If `starts[i] < ends[j]`: Meeting starts → i++, rooms_currently_used++, update max_rooms
    - Else: Meeting ends → j++, rooms_currently_used--
7. Return `max_rooms`


Code:

```JavaScript
function minMeetingRooms(meetings) {
    if (!meetings || meetings.length === 0) {
        return 0;
    }
    
    const starts = meetings.map(meeting => meeting[0]).sort((a, b) => a - b);
    const ends = meetings.map(meeting => meeting[1]).sort((a, b) => a - b);
    
    // Two pointers
    let i = 0;  // pointer for starts
    let j = 0;  // pointer for ends
    
    let roomsCurrentlyUsed = 0;
    let maxRooms = 0;
    
    // Process all meetings
    while (i < starts.length && j < ends.length) {
        if (starts[i] < ends[j]) {
            // A meeting is starting
            roomsCurrentlyUsed++;
            maxRooms = Math.max(maxRooms, roomsCurrentlyUsed);
            i++;
        } else {
            // A meeting is ending (starts[i] >= ends[j])
            // When equal, we process end first so the room can be reused
            roomsCurrentlyUsed--;
            j++;
        }
    }
    
    return maxRooms;
}

// For Node.js input/output
const readline = require('readline');
const rl = readline.createInterface({
    input: process.stdin,
    output: process.stdout
});

let n = 0;
let meetings = [];
let lineCount = 0;

rl.on('line', (line) => {
    if (lineCount === 0) {
        n = parseInt(line);
        lineCount++;
    } else {
        const [s, e] = line.split(' ').map(Number);
        meetings.push([s, e]);
        lineCount++;
        
        if (lineCount === n + 1) {
            const result = minMeetingRooms(meetings);
            console.log(result);
            rl.close();
        }
    }
});
```