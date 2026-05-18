Let's Consolidate Your Understanding 
You now understand the **strategy**: 
1. **Shift the number right** by `i` positions → brings the bit at position `i` to position 0 
2. **AND with 1** (`& 1`) → isolates just that bit at position 0 
3. **Check if it equals 1** → tells us if that position had a 1 or 0 

- **1 is odd.** (An odd number is any integer that leaves a remainder of 1 when divided by 2).
- **0 is even.** (An even number is any integer that leaves a remainder of 0 when divided by 2).
#### The Core Problem
You have a number (let's say 5 = `101` in binary), and you want to know: **"Does position 2 have a 1 or 0?"**
Now, imagine I gave you this challenge:
**"You can ONLY check if position 0 has a 1 or 0. You CANNOT directly check any other position."**
Given this limitation, how would you figure out what's at position 2?

- If position `i` has a **1** (checkSetBit returns `true`) → We DO something 
- If position `i` has a **0** (checkSetBit returns `false`) → We SKIP that position 
---
##### Strategy 2:
Strategy 1 and strategy 2 provides the same answer. i.e checks for 1 values

Strategy 2 for How this function works:

```JavaScript
function checkSetBit2(n,i){
    return ((n>>>i)&1)===1;
}
```
#### Here's a hint with a real-world analogy:
Imagine you have a long line of boxes:
````
[Box 2] [Box 1] [Box 0]
   🎁      📦      🎁
```

You want to know what's in Box 2, but you can ONLY open Box 0 (the rightmost one).

**What would you do?**

Would you maybe... slide all the boxes to the right by 2 positions so Box 2 moves to where Box 0 is? Then you could open it!
```
Before sliding: [🎁] [📦] [🎁]  ← Box 2 has a gift
After sliding:  [ ] [ ] [🎁]   ← Now Box 0 has the gift!
````

##### Why does `& 1` help us check position 0?
Real-Life Analogy: The Filter/Mask

Imagine you're a teacher with 3 students in a row:
````
Position:  [2]     [1]     [0]
Students:  Alice   Bob   Charlie
Status:    ✋      👎     ✋       (✋ = hand raised, 👎 = hand down)
```

You want to know: **"Is Charlie (position 0) raising his hand?"**

But there's a problem - you're wearing special glasses that can only see ONE position. These glasses are your **mask**.

The mask `1` in binary is `001`:
```
Position: [2] [1] [0]
Mask:      0   0   1   ← Your glasses only let you see position 0!
```

When you look through these glasses:
- Position 2: **Blocked** (mask is 0)
- Position 1: **Blocked** (mask is 0)  
- Position 0: **Visible** (mask is 1) ← Only this passes through!

So when you do `101 & 001`:
```
Students:  1   0   1  (who has hands raised)
Mask:      0   0   1  (which positions can you see?)
Result:    0   0   1  (you only see Charlie's raised hand!)
````

The result is `001 = 1`, which means Charlie (position 0) has his hand raised!

Now Connect This Back to Your Code
```javascript
return ((n >>> i) & 1) === 1;
```

**Step 1:** `n >>> i` → Move the student from position `i` to position 0 (slide them over)
**Step 2:** `& 1` → Put on your special glasses that only see position 0
**Step 3:** `=== 1` → Check if that student has their hand raised

**Your turn:** Using this analogy, explain to me:
If we want to check position 2, why do we:
1. First shift right by 2
2. Then use the `& 1` mask
Ans:
We shift right to check if the value at index 2 is 1 or 0. after shifting we need to verify if it is 0 or 1 by using And.

Why can't we just do `& 1` WITHOUT shifting first?
For example, if we have `101` and we just do `101 & 001` without any shifting, what would we check? Would that tell us about position 2?
Answer:
if we do without shifting we will only get the value at index 0 not at index 2.

---
##### Strategy 1:
Strategy 1 for how this function works:
```JavaScript
function checkSetBit1(n,i){
    let mask= 1n << BigInt(i)
    if((BigInt(n) & mask )>0){
        return true;
    }
    return false;
}
```

Real-World Analogy
You want to check what's in Box 2.
**Strategy 1:** You stay where you are, but you point your flashlight at Box 2

```
[Box 2] [Box 1] [Box 0]
   🎁      📦      🎁
    ↑
 (flashlight pointing at Box 2)
```

**Strategy 2:** You move Box 2 right in front of you, then check it

```
Before: [Box 2] [Box 1] [Box 0]
           🎁      📦      🎁

After sliding right by 2:
        [ ] [ ] [Box 2 is now here]
                    🎁
```

Both strategies let you see what's in Box 2!

##### Dry Run Both with the Same Example
**Check if position 2 of number 5 has a 1**

checkSetBit1: Move the mask LEFT
```javascript
let mask = 1n << BigInt(i)  // 1 << 2
```

**Step 1:** Create the mask by shifting `1` left by 2
```
Start:        001  (which is 1)
Shift left 1:  010
Shift left 2:   100  (which is 4)

So mask = 100 (only position 2 has a 1)
```

**Step 2:** AND the number with the mask
```
n:     101  (which is 5)
mask:  100  (which is 4)
       ---
n & mask: 100  (which is 4)
```

**Step 3:** Check if result > 0
```
100 (which is 4) > 0?  → YES, so return true
```


checkSetBit2: Move the number RIGHT

```javascript
return ((n >>> i) & 1) === 1  // n >>> 2
```

**Step 1:** Shift the number right by 2

```
n:           101  (which is 5)
Shift right 2: 001  (which is 1)
```

**Step 2:** AND with 1

```
shifted n: 001
mask:      001
           ---
result:    001  (which is 1)
```

**Step 3:** Check if result === 1

```
001 === 1?  → YES, so return true
```

##### The Key Difference
Both give the same answer, but notice:

**checkSetBit1:**
- Mask moves TO position 2: `001` → `100`
- Then check: `101 & 100 = 100` (result is 4)
- Check if result > 0

**checkSetBit2:**
- Number moves FROM position 2: `101` → `001`
- Then check: `001 & 001 = 001` (result is 1)
- Check if result === 1

##### Visual Summary
```JavaScript
checkSetBit1: Move mask left to meet the bit
   101  (number stays)
&  100  (mask moved to position 2)
   ---
   100  > 0? ✓

checkSetBit2: Move bit right to meet the mask
   001  (number shifted right)
&  001  (mask stays at position 0)
   ---
   001  === 1? ✓
```



----
Why check position 2, not 3 or 4?
Answer:
We're not ONLY checking position 2!
Look at your main function again:

```javascript
function swapAllOddAndEvenBits(n) {
    n = n >>> 0;                            
    let ans = 0;
    for (let i = 0; i < 32; i++) {          // ← Notice this!
        if (checkSetBit(n, i)) {
            ans = setBit(ans, i ^ 1);        
        }
    }
    return ans >>> 0;
}
```

See that `for (let i = 0; i < 32; i++)`?
**You ARE checking ALL positions from 0 to 31!** (32 total positions)
- When `i = 0`, you check position 0
- When `i = 1`, you check position 1
- When `i = 2`, you check position 2
- ... and so on until position 31


Why do you think the loop goes up to 32? Why not 10, or 64, or 100?
JavaScript uses **32 bits** to represent integers in bitwise operations. That's why we loop through all 32 positions (0 to 31).

Let me summarize what you've learned:
```javascript
function checkSetBit(n, i) {
    return ((n >>> i) & 1) === 1;
}
```

**What it does:** Checks if position `i` has a 1 or 0
**How it works:**
1. `n >>> i` → Shift the bit at position `i` to position 0
2. `& 1` → Use a mask to isolate only position 0
3. `=== 1` → Check if that bit is 1 (returns true) or 0 (returns false)

