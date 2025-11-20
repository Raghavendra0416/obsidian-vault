**Fantastic question!** You've noticed two different approaches to solve the same problem. Let me show you they're actually mirror images of each other!

---

## The Two Strategies

**Strategy 1 (checkSetBit1):** Keep the number in place, move the mask **Strategy 2 (checkSetBit2):** Keep the mask in place, move the number

Let me use the analogy again to make this crystal clear:

---

## Real-World Analogy

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

---

## Now Let's Dry Run Both with the Same Example

**Check if position 2 of number 5 has a 1**

### checkSetBit1: Move the mask LEFT

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

---

### checkSetBit2: Move the number RIGHT

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

---

## The Key Difference

Both give the same answer, but notice:

**checkSetBit1:**

- Mask moves TO position 2: `001` → `100`
- Then check: `101 & 100 = 100` (result is 4)
- Check if result > 0

**checkSetBit2:**

- Number moves FROM position 2: `101` → `001`
- Then check: `001 & 001 = 001` (result is 1)
- Check if result === 1

---

## Visual Summary

```
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

---

**Now here's a question for you:**

Which strategy do you find easier to understand? And can you explain in your own words why both strategies work?