# Intel64 and IA-32
## Intel 64 and IA-32 Architecture Software Developer's Manual
### Volume 1: Basic Architecture
#### Chapter 1: About This Manual
#### Chapter 2: Intel 64 and IA-32 Architectures
#### Chapter 3: Basic Execution Environment
##### 3.1: Models of Operation
- Three basic operating models
  - Protected mode
  - Real-address mode
  - System management mode (SMM)
    - This mode provides an operating system or executive with a transparent mechanism for implementing platform-specific functions such as power management and system security.
###### 3.1.1 Intel 64 Architecture
- IA-32 sub-modes
  - Compatibility mode (sub-mode of IA-32e mode)
  - 64-bit mode (sub-mode of IA-32e mode)
##### 3.2: Overview of the Basic Execution Environment
- 
###### 3.2.1: 64-Bit Mode Execution Environment
- 64-bit
  - Address space
  - Basic program execution registers
  - XMM registers
  - YMM registers
  - BND registers, BNDCFGU, BNDSTATUS
  - Stack
  - Control registers
  - Debug registers
  - Descriptor table registers
##### 3.3: Memory Organization
###### 3.3.1: IA-32 Memory Models
###### 3.3.2: Paging and Virtual Memory
###### 3.3.3: Memory Organization in 64-Bit Mode
##### 3.4: Basic Program Execution Registers
###### 3.4.1: General-Purpose Registers
###### 3.4.2: Segment Registers
###### 3.4.3: EFLAGS Register
####### 3.4.3.1: Status Flags
######## CF (bit 0) / Carry flag
- Set if arithmetic operation generates a carry or a borrow out of the most-significant bit of the result;
######## PF (bit 2) / Parity flag
- Set if the least-significant byte of the result contains a even number of 1 bits
######## AF (bit 4) / Auxiliary Carry flag
- This flag is used in binary-coded decimal(BCD) arithmetic.
######## ZF (bit 6) / Zero flag
- Set if the result is zero;
######## SF (bit 7) / Sign flag
- Set most-significant bit of the result, which is the sign bit of a signed integer.
######## OF (bit 11) / Overflow flag
- Set if the integer result is too large a positive number or too small a negative number
####### 3.4.3.2: DF Flag
######## DF (bit 10) / Direction flag
####### 3.4.3.3: System Flags and IOPL Field
######## TF (bit 8) / Trap flag
######## IF (bit 9) / Interrupt enable flag
######## IOPL (bit 12 and 13) / I/O privilege level field
######## NT (bit 14) / Nested task flag
######## RF (bit 16) / Resume flag
######## VM (bit 17) / Virtual-8086 mode flag
######## AC (bit 18) / Alignment check (or access control) flag
######## VIF (bit 19) / Virtual interrupt flag
######## VIP (bit 20) / Virtual interrupt pending flag
######## ID (bit 21) / Identification flag
####### 3.4.3.4: RFLAGS Register in 64-Bit Mode
##### 3.5: Instruction Pointers
##### 3.6: Operand-Size and Address-Size Attributes
##### 3.7: Operand-Size and Address-Size Attributes
#### Chapter 4: Data Types
#### Chapter 5:
#### Chapter 6: Procedure Calls, Interrupts, and Exceptions
##### 6.1: Procedure Call Types
##### 6.2: Stacks
##### 6.3: Calling Procedures Using CALL and RET
###### 6.3.1: Near CALL and RET Operation
###### 6.3.2: Far CALL and RET Operation
#### Chapter 7:
#### Chapter 8:
#### Chapter 9:
#### Chapter 10:
#### Chapter 11:
#### Chapter 12:
#### Chapter 13:
#### Chapter 14:
#### Chapter 15:
#### Chapter 16:
#### Chapter 17:
#### Chapter 18:
#### Chapter 19:
### Volume 2: Instruction Set Reference
#### Chapter 1: About This Manual
#### Chapter 2: Instruction Format
##### 2.1: Instruction Format for Protected Mode, Real-Address Mode, and Virtual-8086 Mode
- 
###### 2.1.1: Instruction Prefixes
####### Group1
####### Group2
####### Group3
####### Group4
###### 2.1.2: Opcodes
###### 2.1.3: ModR/M and SIB Bytes
###### 2.1.4: Displacement and Immediate Bytes
###### 2.1.5: Addressing-Mode Encoding of Mod/R/M and SIB Bytes
##### 2.2: IA-32E Mode
##### 2.3: Intel Advanced Vectore Extensions
##### 2.4: AVX and SSE Instruction Exception Specification
##### 2.5:
##### 2.6:
#### Chapter 3: Instruction Set Reference, A-L
##### 3.1: Interpreting The Instruction Reference Pages
###### 3.1.1: Instruction Format
####### CMC - Complement Carry Flag
####### 3.1.1.1: Opcode Column in the Instruction Summary Table (Instructions without VEX Prefix)
######## NP
######## REX.W
- Indicates the use of a REX prefix that affects operand size or instruction semantics.
######## /digit
######## /r
######## cb,cw,cd,cp,co,ct
######## lb,lw,ld,lo
######## +rb,+rw,+rd,+ro
######## +i
####### 3.1.1.2:
####### 3.1.1.3: Instruction Column in the Opcode Summary Table
######## rel8
######## rel16, rel32
######## ptr16:16,ptr16:32
######## rN
######### r8
######### r16
######### r32
######### r64
######## immN
- N byte Immediate value
######### imm8
######### imm16
######### imm32
######### imm64
######## r/mN
- N byte register or memory
######### r/m8
######### r/m16
######### r/m32
######### r/m64
######## mN
- N byte operand in memory
######### m
######### m8
######### m16
######### m32
######### m64
######### m128
######## ST
######## mm/mN
- N byte MMX register
######### mm/m32
######### mm/m64
######## xmm/mN
- N byte XMM register
######## SRCn
####### 3.1.1.4:
####### 3.1.1.5:
##### 3.2: Instructions (A-L)
###### AND - Logical AND
###### CALL - Call Procedure
###### CMP - Compare Two Operands
####### Flags Affected
- The CF, OF, SF, ZF, AF and PF flags are set according to the result.
###### DIV - Unsigned Divide
####### DIV r/m64
- Opcode RAX.W + F7 /6
- Instruction: DIV r/m64
- Description: Unsigned devide RDX:RAX by r/m64, with result stored in RAX(Quotient), RDX(Remainder).
###### IDIV - Signed Divide
###### JCC - Jump if Condition Is Met
####### JA / jump if above
####### JAE / jump if above or equal
####### JB / jump if below
####### JBE / jump if below or equal
####### JC / jump if carry
####### JCXZ / jump if CX register is 0
####### JECXZ
####### JE / jump if equal (ZF=1)
####### JG / jump if greater (ZF=0 and SF=OF)
####### JGE
####### JL / jump if less (SF <> OF)
####### JNZ
- Jump if not zero (ZF=0)
####### JS / jump if sign (SF=1)
####### JZ / jump if zero (ZF=1)
###### JMP - Jump
###### LEA - Lead Effective Address
####### Description
- Computes the effective address of the second operand (the source operand) and stores it in the first operand.
####### Memo
######## movとの違い
- about:
  - lea loads a pointer to the item,
    mov loads the actual value of the address
  - https://stackoverflow.com/questions/1699748/what-is-the-difference-between-mov-and-lea?utm_medium=organic&utm_source=google_rich_qa&utm_campaign=google_rich_qa
- mov
  - mov rax label : labelのアドレスをraxに格納
  - mov rax [label] : "label"というアドレスからはじまるメモリの内容をraxに格納
- lea
  - lea rax [label] : labelのアドレスをraxに格納 = mov rax label
  
#### Chapter 4: Instruction Set Reference, M-U
##### 4.1
##### 4.2
##### 4.3: Instructions (M-U)
###### MOV - Move
###### MOV - Move to/from Control Registers
###### MOV - to/from Debug Registers
###### MUL - Unsigned Multiply
####### MUL r/m64
- Opcode: REX.W + F7 /4
- Instruction: MUL r/m64
- Description: Unsined multiply (RDX:RAX <- RAX * r/m64)
###### PUSH - Push Word, doubleword or Quadword Onto the Stack
####### Description
- Decerements the stack pointer and then stores the source operand on the top of the stack.
###### POP - Pop a Value from the Stack
###### RET - Return from Procedure
###### SAL/SAR/SHL/SHIR - Shift
####### Description
- Shifts the bits in the first operand to the left or right by number of bits 
- SAL: Shift arithmetic left
  Multiple 2, or shift left
- SAR: Devide 2, or shift right
- SHL: Shift logical left

###### SUB - Subtract
###### SYSCALL - Fast System Call
####### Description
- SYSCALL invokes an OS system-call handler at privilege level 0.
###### TEST - Logical Compare
####### Description
- Computes the bit-wise logical AND of first operand and the second operand and sets the SF, ZF, and PF status flags according to the result.
#### Chapter 5: Instruction Set Reference, V-Z
##### 5.2: Introductions (V-Z)
###### XOR - Logical Exclusive OR
#### Chapter 6: Safer Mode Extensions Reference
#### Chapter 7:
#### Appendix A:
#### Appendix B:
#### Appendix C:
### Volume 3: System Programming Guide
#### Chapter 1:
#### Chapter 2:
#### Chapter 3:
#### Chapter 4:
#### Chapter 5:
#### Chapter 6:
#### Chapter 7:
#### Chapter 8:
#### Chapter 9:
#### Chapter 10:
#### Chapter 11:
#### Chapter 12:
#### Chapter 13:
#### Chapter 14:
#### Chapter 15:
#### Chapter 16:
#### Chapter 17:
#### Chapter 18:
#### Chapter 19:
#### Chapter 20:
#### Chapter 21:
#### Chapter 22:
#### Chapter 23:
#### Chapter 24:
#### Chapter 25:
#### Chapter 26:
#### Chapter 27:
#### Chapter 28:
#### Chapter 29:
#### Chapter 30:
#### Chapter 31:
#### Chapter 32:
#### Chapter 33:
#### Chapter 34:
#### Chapter 35:
#### Chapter 36:
#### Chapter 37:
#### Chapter 38:
#### Chapter 39:
#### Chapter 40:
#### Chapter 41:
#### Chapter 42:
#### Appendx A:
#### Appendx B:
#### Appendx C:
