# Arrays

**Properties**:
- Fixed length, which can be accessed through the `.length` method
- Locations are contiguously located in memory
- Not always efficient as this allows for empty data locations

## Basic example programs
- [Array iteration](#iteration)
- [Maximum and minimum](#max-and-min)
- [Sum and average](#sum-and-avg)
- [Search for certain values or ranges of values](#search)
- [Find common elements](#common)

---
### <a id="iteration"></a>Array iteration
#### With a 'for loop'

    NUMS[8]

    // 'for loop'
    loop I from 0 to NUMS.length - 1
        output NUMS[I]
    endloop

#### With a while loop

    NUMS[8]
    J = 0

    loop  while J < NUMS.length - 1
        output NUMS[J]

        // cannot do J += 1 or J++
        J = J + 1

    endloop

---
### <a id="max-and-min"></a>Maximum and minimum in an array
#### Maximum

    NUMS = [5, 9, -1, 12, 13, 51, -6]
    MAX = NUMS[0]

    // loop can start from 1 since MAX is NUMS[0]
    loop I from 0 to NUMS.length - 1
        if NUMS[I] > MAX then
            MAX = NUMS[I]
        endif
    endloop

    output "The max is: ", MAX

#### Minimum
    NUMS = [5, 9, -1, 12, 13, 51, -6]
    MIN = NUMS[0]

    // loop can start from 1 since MIN is NUMS[0]
    loop I from 0 to NUMS.length - 1
        if NUMS[I] < MIN then
            MIN = NUMS[I]
        endif
    endloop

    output "The min is: ", MIN

---
### <a id="sum-and-avg"></a>Calculate sum and average of values in an array

    NUMS = [5, 9, -1, 12, 13, 51, -6]
    SUM = 0

    loop I from 0 to NUMS.length - 1
        SUM = SUM + NUMS[I]
    endloop

    AVG = SUMS/NUMS.length

    output "The average is: ", AVG

---
### <a id="search"></a>Search an array for certain values or ranges of values
#### Negative values

    // prints all values less than 0

    NUMS = [5, 9, -1, 12, 13, 51, -6]

    loop I from 0 to NUMS.length - 1
        if NUMS[I] < 0 then
            output NUMS[I]
        endif
    endloop

#### Between 0 and 15

    NUMS = [5, 9, -1, 12, 13, 51, -6]

    loop I from 0 to NUMS.length - 1
        if NUMS[I] > 0 and NUMS[I] < 15 then
            output NUMS[I]
        endif
    endloop

#### Lesser than 0 and greater than 15 (inclusive)

    NUMS = [5, 9, -1, 12, 13, 51, -6]

    loop I from 0 to NUMS.length - 1
        if not (NUMS[I] > 0 and NUMS[I]) < 15 then
            output NUMS[I]
        endif
    endloop

#### Everything except 9

    NUMS = [5, 9, -1, 12, 13, 51, -6]

    loop I from 0 to NUMS.length - 1
        if NUMS[I] != 9 then
            output NUMS[I]
        endif
    endloop

---
### <a id="common"></a>Find the common elements between arrays

    FRENCH = ["John", "Ali", "Chen", "Jose"]
    SPANISH = ["Jeff", "Sara", "Ali", "Samir"]

    // nested loops
    loop I from 0 to FRENCH.length - 1
        loop J from 0 to SPANISH.length - 1
            if FRENCH[I] == SPANISH[J] then
                output FRENCH[I] // can also output SPANISH[J]
            endif
        endloop
    endloop