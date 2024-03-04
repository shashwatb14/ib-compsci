# Binary search

- The objective is the same, i.e. to find some target value
- Can only be done on a sorted array, either ascending or descending
- The array is split in half each time until the target element is found
- Element in middle can be found by adding first and last index and then dividing by 2 using `div`
- Divides arrays into half
- Array must be sorted
- Practical for large arrays and sorted data
- Best case: `1` time
- Worst case: log<sub>2</sub>(`N`), where `N` is the length of the array

## Pseudocode

    NUMS = [23, 29, 31, 35, 54, 61, 67]
    TARGET = 61
    LOW = 0
    HIGH = NUMS.length - 1
    FOUND = False

    loop while LOW <= HIGH
        MID = (LOW + HIGH) div 2

        if NUMS[MID] = TARGET then
            output MID
            FOUND = true
        else if TARGET > NUMS[MID] then
            LOW = MID + 1
        else
            HIGH = MID - 1
        end if
    end loop

    if FOUND = False then
        output "Target not found".
    end if

