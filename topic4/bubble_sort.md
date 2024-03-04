# Bubble sort

- **Ascending order**: Compare each element to the element after it, and if the elemenet after it is less than it is, then they will be swapped otherwise they will not be swapped
- **Descending order**: Compare the number next to the current element, and if it is greater than the current number, they will be swapped
- Higher values "bubble" to the end of the array
- The number of iterations of the array must be equaivalent to the number of elements present in the array
- Multiple swaps for each iteration

## Pseudocode

    NUMS = [31, 54, 67, 29, 51, 61, 23, 35]
    N = NUMS.length

    loop I from 0 to N - 1
        loop J from 0 to N - 2 - I
            if NUMS[J] > NUMS[J + 1] then
                TEMP = NUMS[J]
                NUMS[J] = NUMS[J + 1]
                NUMS[J + 1] = TEMP
            end if
        end loop
    end loop