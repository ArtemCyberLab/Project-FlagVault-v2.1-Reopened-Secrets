Project Objective
Demonstrate exploitation of a format string vulnerability in a C program, despite developer attempts to "patch" the bug. This project highlights how improper use of printf() can still allow attackers to leak sensitive memory content, such as flags, directly from the stack.

Project Description
The login() function reads user input via the unsafe gets() function. This input is passed to print_flag(), which reads the flag into a buffer but doesn't print it. However, it then uses printf(username); without a format string.

This allows an attacker to craft format string payloads like %p %p %p %s to leak memory content — eventually printing the hidden flag from the stack.

Exploit Summary
By connecting to the service and supplying format string payloads, the attacker can:

Leak stack memory with %p

Locate the flag in memory

Use %s to print the flag

%p %p %p %p %s
Result:
THM{format_issues}

Key Concepts
Format String Vulnerability

Stack memory leakage

Unsafe functions (gets, printf)

Exploit without code execution — only memory disclosure

Conclusion
Even after removing direct flag printing, insecure handling of format strings leads to full memory disclosure. This project proves that secure coding in C demands strict control over all format-related functions and input validation.

