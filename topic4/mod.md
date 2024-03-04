# `Mod`

- Used to find remainder when two integers are divided by each other
- Used to test for divisibility

**Simple examples**:

    25 mod 6 = 1
    36 mod 8 = 4
    3 mod 28 = 3

## Basic example programs
- [Divisible by 3](#three-divisibility)

---
### <a id="three-divisibility"></a>Check for divisibility by 3

    input S

    if S mod 3 = 0 then
        output "Is divisible by 3"
    else
        output "Not divisible by 3"
    end if

#### Example inputs and outputs

    Input: 27
    27 mod 3 = 0
    Output: Is divisible by 3

    Input: 28
    28 mod 3 = 1
    Output: Not divisible by 3