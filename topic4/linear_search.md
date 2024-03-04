# Linear search

- Go through the array one by one to find the target value
- Simplest type of search
- Sequential search direction
- No prerequisites
- Practical for small arrays or unsorted data
- Best case: `1` time
- Worst case: `N`, where `N` is the length of the array

## Pseudocode

    NUMS = [31, 54, 67, 29, 51, 61, 23, 35]
    TARGET = 51
    FOUND = False

    loop I from 0 to NUMS.length - 1
        if NUMS[I] = TARGET then
            output "Target found at: ", I
            FOUND = True
        end if
    end loop

    if FOUND = False then
        output "Target not found in array."
    end if