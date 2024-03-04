# Collections

**Properties**:
- No fixed length; items can be added and removed
- Items can be added dynamically
- Each location "points" to the next using a "pointer"
    - Data in a collection is spread throughout the RAM with each element pointing to the address of the next (not contiguous)
- Collections can only be traversed using specific methods
- Represents a type of object
- Indicated by curly brackets in pseudocode `{}`
- Can contain elements of different data types

**Methods**:
- `resetNext()`: sets position before the first elemt
- `getNext()`: gets the next element
    - Calling `getNext()` at any time will change the current position within the collection
    - The value of `getNext()` can be stored in a variable
- `hasNext()`: checks whether there is an element after the current position
- `addItem(item)`: adds `item` to collection
- `isEmpty()`: checks if the entire collection is empty

## Basic example programs
- [Collection iteration](#iteration)
- [Maximum and minimum](#max-and-min)
- [Sum and average](#sum-and-avg)
- [Search for certain values or ranges of values](#search)
- [Find common elements](#common)
- [Transfer from arrays to collections](#arr-collections)
- [Transfer from collections to arrays](#collections-arr)

---
### <a id="iteration"></a>Iterate through a collection

    B = {5, 8, 7, 9}
    B.resetNext()
    
    loop while B.hasNext()
        NUM = B.getNext()
        output NUM
    endloop

---
### <a id="max-and-min"></a>Maximum and minimum in a collection

    B = {5, 8, 7, 9}
    B.resetNext()
    MAX = B.getNext()
    MIN = MAX
    
    loop while B.hasNext()
        NUM = B.getNext()
        if NUM > MAX then
            MAX = NUM
        endif
        if NUM < MIN then
            MIN = NUM
        endif
    endloop

    output MAX
    output MIN

---
### <a id="sum-and-avg"></a>Calculate sum and average of values in a collection

    B = {5, 8, 7, 9}
    B.resetNext()
    SUM = 0
    COUNT = 0

    loop while B.hasNext()
        SUM = SUM + B.getNext()
        COUNT = COUNT + 1
    endloop

    output (SUM/COUNT)

---
### <a id="search"></a>Search a collection for certain values or ranges of values

    // finding values between 5 and 8

    B = {5, 8, 7, 9}
    B.resetNext()

    loop while B.hasNext()
        NUM = B.getNext()
        if NUM > 5 and NUM < 8 then
            output NUM
        endif
    endloop

---
### <a id="common"></a>Find the common elements between collections

    FRENCH = {"John", "Lee", "Angel", "Makar"}
    SPANISH = {"Jeff", "Fernando", "Sophia", "Angel"}

    FRENCH.resetNext()
    SPANISH.resetNext()

    loop while FRENCH.hasNext()
        FR = FRENCH.getNext()
        SPANISH.resetNext()
        loop while SPANISH.hasNext()
            ES = SPANISH.getNext()
            if FR = ES then
                output FR
            endif
        endloop
    endloop

---
### <a id="arr-collections"></a>Transfer data from arrays to collections

    TEMPS = [56, 79, 91, 92]
    TEMPS_COL = {}

    loop I from 0 to TEMPS.length - 1
        CURR_TEMP = TEMPS[I]
        TEMPS_COL.addItem(CURR_TEMP)
        // or TEMPS_COL.addItem(TEMPS[I])
    endloop


---
### <a id="collections-arr"></a>Transfer data from collections to arrays

    TEMPS = [0, 0, 0, 0]
    TEMPS_COL = {56, 79, 91, 92}
    COUNT = 0
    TEMPS_COL.resetNext()

    loop while TEMPS_COL.hasNext()
        CURR_TEMP = TEMPS_COL.getNext()
        TEMPS[COUNT] = CURR_TEMP
        COUNT = COUNT + 1
    endloop