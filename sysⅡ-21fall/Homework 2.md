# Homework 2

## Question 1

1. 3 nop instructions are necessary.

```assembly
ld  x11, 0(x5)	
add x12, x6, x7
nop
nop
add x13, x11, x12
add x28, x29, x30
```

2. | Dependency type             | the number of over-count nop |
   | --------------------------- | ---------------------------- |
   | **EX to 1st only**          | 2                            |
   | **MEM to 1st only**         | ~~1~~   2                    |
   | **EX to 2nd only**          | ~~2~~   1                    |
   | **MEM to 2nd only**         | 1                            |
   | **EX to 1st and EX to 2nd** | 2                            |

   So 1 nop instruction are over-counted by analyzing dependency type independently.

3. Assuming no other hazards, the CPI for the program is 1.55

   5% * 3 + 20% * 2 + 5% * 2 + 10% * 1+ 10% * 3 + 50% * 1= 1.55

   percent: (1.55-1)/1.55 = 35%

4. The CPI of full forwarding pipeline is 1, and 0% of cycles are stalls.

5. Calculate the two cases separately.

   1. only from EX/MEM: The CPI is 

      (55% * 1+20% * 2 + 5% * 2 + 10% * 1 + 10% * 2) = 1.35

   2. only from MEM/WB: The CPI is 

      (75% * 1+5% * 3 + 10% * 2 + 10% * 3 ) =1.4

   So it's better to forward only from EX/MEM pipeline register, and the CPI is 1.35.

6. Because the clock cycle must be the maximum of all the stages. The speedup of forwarding is

   1. EX/MEM: 120 * 5 / 120 * 1.35 = 3.70
   2. MEM/WB: 120 * 5 / 120 * 1.4 = 3.57
   3. Full: 120 * 5 / 130 * 1 = 4.62

## Question 2

1. ```assembly
   add x15, x12, x11
   nop
   nop
   ld  x13, 4(x15)
   ld  x12, 0(x2)
   nop
   or  x13, x15, x13
   nop
   nop
   sd  x13, 0(x15)
   ```
   
2. The load/store can't run correctly if a ld and its next instruction happen data hazard. But in this program there isn't hazard, so it will run correctly.

3. The code cost 9 cycles.

## Question 3

1. Always-Taken CPI: 

   25% * 2 * 55% +  1= 1.275

2. Always-Not-Taken: 

   25% * 2 * 45% + 1= 1.225

3. 2-Bit CPI: 

   25% * 15% * 2+ 1= 1.075

4. speedup: 

   (3 * 12.5% + 1 * 87.5%)/(12.5% * 15% * 2 + 1) = 1.205

5. speedup:

   (3 * 12.5% + 2 * 12.5% + 1 * 75%)/(12.5% * 15% * 2 + 1 * 12.5% + 1) = 1.375/1.1625 = 1.18

6. Accuracy: (85% - 80%)/20% = 25%
