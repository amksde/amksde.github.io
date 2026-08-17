---
title: OSTEP - Operating System Three Easy Pieces
---

# ==Chapter 6: Mechanism - Limited Direct Execution==
1. For complete control over the system, OS will use both hardware driven and software driven mechanisms
2. Direct execution - load program into memory, find its entry point, execute it, and wait for it to return
3. The "direct-execution" has a few problems
  a. the process can run whatever code it has
  b. no scope to implement time-share
4. Restricted execution : **user mode** ; Priviledged execution : **kernel mode**. user programs use **system-calls** to execute the privileged functionalities.
