# Machine Coding Practice

[MIPS Green Sheet](https://inst.eecs.berkeley.edu/~cs61c/resources/MIPS_Green_Sheet.pdf)

* OR \$s0, \$t0, \$t1

  ​	0	       \$T0	     \$T1       \$S0     		     2	  5

  * 0000-00| 01-000| 0-1001-| 1000-0| 000-00| 10-0101

    OR	        RS	       RT	    RD	SHANT	FUNCT

# Arrays Pseudo-Instructions Branching, and Loops

* Move data in and out of mem to handle data structures
  * Involves computing addresses of memory
* Array example: get int in loc a[8]
  * Byte offset <- array index * element_size


## Building Memory References
$$
\mathbf{g=h+a[8]}
$$
* Assume addresses are in registers already. 
* &a[0] is already in \$s3 and \$s4 and \$s5 point to vars h and g
* Code uses 6 registers
  * Note: compiler must figure this all out
  * _Practice_ how could it use fewer registers

    `lw $t0, 32($s3)	# $t0 gets a[8]`
    `lw $t1, 0($s4)		# $t1 gets h`
    `add $t2, $t1, $t0 	# $t2 gets h + a[8]`
    `sw $t2, 0($s5)		# g = h + a[8]`

## Practice decoding machine instructions

0x2002 0001

2		0		0		2		0		0		0		1

0010	00|00	000|0	0010|	0000	0|000	00|00	0000

8			RS		RT		IMM

Addi			\$V0,		$Zero,	1

1. fetch instruction at address (PC) into the _instruction Register_(IR)


2. Add 4 to PC
3. Execute the instruction in IR
4. Repeat



## Loop

`/* c if else code */`  
`if ( s1 == s2 ) {`  
 `s3 = s4 + s5;`  
`} else {`  
 `s3 = s4 – s5;`  
`}`  
  
`/* c code in assembly form */`  
 if ( s1 != s2 ) goto L1;  
 s3 = s4 + s5;  
 goto L2;  
`L1:`  
 s3 = s4 - s5;  
`L2:`  

### direct MIPS translation
 	`bne $s1, $s2, L1` 		# if( s1 != s2 ) goto L1;  
 	`add $s3, $s4, $s5` 	# s3 = s4 + s5;  
 	`j L2` 				# goto L2;  
`L1:`  
 	`sub $s3, $s4, $s5` 	# s3 = s4 – s5;  
`L2:`  



## Conditional Examples

`if ( s1 < s2 ) goto L1;` = `slt $t0, $s1, $s2` `bne $t0, $zero, L1`  
`if ( s5 >= s6 ) goto L3;` = `slt $t2, $s5, $s6` `beq $t2, $zero, L3`  
`if ( s3 > s4 ) goto L2;` = `slt $t1, $s4, $s3` `bne $t1, $zero, L2`  
`if ( s7 <= s8 ) goto L4;` = `slt $t3, $s8, $s7` `beq $t3, $zero, L4`  
