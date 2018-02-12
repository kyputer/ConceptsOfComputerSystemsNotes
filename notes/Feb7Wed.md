# Instructions

## Resources
[Lecture Slides](https://www.cs.rit.edu/~bks/250/Lectures/05/05-MIPS-4.6up.pdf)

## Instruction Format and Decoding
* R format instruction has 0 for the _opcode_ with the exception "mfc0"
* The funct segment determines the precise instruction
	* Low order 6 bits will give funct value
	* (0x3F and instruction) is value of interest
* I format
	* Non-zero upper 4 bits of opcode
* J format
	* Starts with 0x0 and second hex digit is 0xB or greater
	* Only two instructions
		* j
		* jal

## Basic Blocks
* Sequence of instructions with:
	* No embedded branches (except at end)
	* No branch targets (except at beginning)

## Branch Instruction Design
* beq and bne are common case
	* Hardware for <, >, ... Combined with branch involves more work per instruction, requiring a slower clock

## Signed vs Unsigned
* Signed compassion
	* slt (Set less than)
	* slti (set less than immediate)
* Unsigned comparison
	* sltu (Set less than unsigned)
	* sltui (Set less than unsigned immediate)

## Branch Addressing (I format)
* Branch instructions specify the following
	* Opcode
	* Two registers
	* Target address
* Locality of reference
* Most branch targets are near branch
	* Forward or backward

## Jump Addressing (J Format)
* Jump (j and jal) targets could be anywhere in text segment 
	* Encode full address in instruction
* (Pseudo) Direct jump addressing

## Branching Far Away
* If branch is too far to encode with 16-bit offset, assembler rewrites the code

## Arrays vs Pointers
* Array indexing involves...
	* Multiplying index by element size
	* Adding to array base address
* Pointers correspond directly to memory addresses
	* Can avoid indexing complexity

## Comparison of Array vs. Pointer
* Multiply is “strength reduced” to shift
* Array version puts shift inside the loop
	* Part of calculation for incremental index
	* Compare to incrementing a pointer
* Compiler can achieve same effect as the manual use of pointers
	* Induction variable elimination
	* Better to make program clearer and safer
