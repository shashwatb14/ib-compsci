# Selection sort

- **Ascending order**: Minimum value found in unsorted portion and then replaced with first index of current unsorted portion
- **Descending order**: Maximum value found instead of minimum value and same steps repeated
- Only one swap for each iteration
- Can be more efficient in certain circumstances

## Pseudocode

    // ascending order

    NUMS = [31, 54, 67, 29, 51, 61, 23, 35]
    N = NUMS.length

    loop I from 0 to N - 2
        MIN_INDEX = I
        loop J from I + 1 to N - 1
            if NUM[J] < NUMS[MIN_INDEX] then
                MIN_INDEX = J
            end if
        end loop
        TEMP = NUMS[I]
        NUMS[I] = NUMS[MIN_INDEX]
        NUMS[MIN_INDEX] = TEMP
    end loop
