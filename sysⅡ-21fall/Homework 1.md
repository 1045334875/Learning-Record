## Homework 1

#### Question 1

1. latency of R-type instruction: 700ps
   1. Fetch the instruction from I-Mem with correct pc(30+250 = 280ps)
   2. Decode the instruction (max(50,150,50) = 150 ps)
   3. ALU with mux(25+200 = 225 ps)
   4. Write the result back to register file(25+20 = 45 ps)
   5. 280+150+225+45 = 700 ps
2. Latency of LD: 950ps
   1. Fetch the instruction from I-Mem with correct pc(30+250 = 280 ps)
   2. Decode the instruction, read register and extend offset address (max(50,150,50) = 150 ps)
   3. ALU with mux(25+200 = 225 ps)
   4. Fetch the data from D-Mem (250 ps)
   5. Write the result back to register file(25+20 = 45 ps)
   6. 280+150+225+250+45 = 950 ps
3. Latency of sd: 905ps
   1. Fetch the instruction from I-Mem with correct pc(30+250 = 280 ps)
   2. Decode the instruction, read register and extend offset address (max(50,150,50) = 150 ps)
   3. ALU with mux(25+200 = 225 ps)
   4. Write the data from D-Mem(250 ps)
   5. 280+150+225+250 = 905 ps
4. Latency of beq: 730ps
   1. Fetch the instruction from I-Mem with correct pc(30+250 = 280 ps)
   2. Decode the instruction, read register and extend offset and shift left (max(50,150,50+5) = 150 ps)
   3. Mux and then Adder and ALU at the same time(25+mas(200,150) = 225 ps)
   4. And gate and two muxs to write back to pc (5+25+25 = 55 ps)
   5. PC register setup.(20ps)
   6. 280+150+225+55+20 = 730 ps
5. Latency of an I-type instruction: 700ps
   1. Fetch the instruction from I-Mem with correct pc(30+250 = 280 ps)
   2. Decode the instruction, read register and sign-extend offset address (max(50,150,50) = 150 ps)
   3. ALU with mux(25+200 = 225 ps)
   4. Write the result back to register file(25+20 = 45 ps)
   5. 280+150+225+45 = 700 ps
6. The minimum clock period for the CPU is 950 ps.

#### Question 2

1. The clock cycle time of pipelined is 350 ps, and time of non-pipelined is 250+350+150+300+200= 1250ps.

2. The total latency of an ld instruction in a pipelined is 1250 ps, latency in a non-pipelined processor is 1250 ps.

3. ID. The new clock cycle time of the processor is 300 ps.

4. ~~35% * 1/5 = 0.07~~

   35=Load+Store

5. ~~75% * 1/5 = 0.15~~ 

    65（85）=ALU+Load+（Jal）

#### Question 3

```markdown
addi x11, x12, 5
nop
nop
nop
add  x13, x11, x12
addi x14, x11, 15
nop
~~nop~~
add  x15, x13, x12
```

#### Question 4

1. The reduction in pipeline depth will extend cycle time, but reduce each instruction time. Because each instruction only need 4 cycles. As a result, total cycle time will reduce.
2. This change will improve throughput of the pipeline.
3. This change will degrade the speedup.

