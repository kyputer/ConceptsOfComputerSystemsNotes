# Defining Performance
## Response Time and Throughput
* Response time
  * How long to do something
* Throughput
  * Total work done per unit of time
* How are these affected
  * I/O
    **1/ExecutionTime**
    A - 15s | B - 10s
    15/10 = 1.5

## Instruction Sets
* CISC - Complex Instruction Set Computers
* RISK - Reduced Instruction Set Computers
  * Keep instruction set small and simple
  * let software do complicated opertations by composing simpler ones done in hardwware
    * requires good compilers
  * Makes it easy**....CONTINUE FROM SLIDES**
* The ISA Abstraction
  * Defines the hardware and software interface
  * Standardize instuctions, machine leanguage bit patterns, etc

## Measuring Time
* Elapsed Time
* CPU Time =
  * __CPU TIME = Instruction Count x Cycles Per Instruction  x Clock Cycle Time(period between spikes)__
  * (num of clock cycles) x (clock cycle time)
  * (clock cycles)/(cpu time)
  * (Instruction Count) x (Cycles Per Instruction) x (Clock Cycle Time)
  * [Instruction Count x Cycles Per Instruction] / (Clock Rate)
* Clock cycles = 
  * (cpu time) x (clock rate)
  * (Instruction Count) x (Cycles Per instruction)

    **Frequency = Rate Clock ticks**

    * Measured in Hertz or Seconds

## Amdahl's Law
* improving one aspect of a computer and expecting a proportional improvement in overall performance

  $T_{improved} = (T_{affected}/improvement factor) + T_{unaffected}$

  EX: multiple accounts for 80s out of 100s
  
  $20=(80/n)+20 = cant be done!!!$

  ### Corollary: make the common case fast

## Registers
Data inside the CPU are held in registers
* Special storage locations built directly into the CPU
* Similar to variable in some ways
  **Benefit:** registers are inside the CPU

