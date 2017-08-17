# Signals-and-Interrupts-in-C
Coded BY:    Vargha Hokmran
Language:    C

Description: This program uses signal interrupts and sends messages
             between parent and child and prints every requested seconds.

To Compile:  Open the terminal and type make, then press Enter.

How to Run:  Open the Linux terminal in the folder that contains
             warn, and type ./warn, then press Enter.
             Press ctrl^C to interrupt, and set a new message
             To change the time between prints, add an integer with a
             white space to the beginning of message after ctrl^C
             To exit the program type exit

===========================================================================

This program will spawn a child process with a pipe shared between the parent and child. The parent will write to the pipe and the child will read from it. There are no required command line arguments.

  The parent process will intercept SIGINT and, when a SIGINT is detected by the parent, it will prompt the user for a single line text message.  Once having received the message from the user, the parent will send (write) the message to the child via the shared pipe and send a SIGFPE signal to the child to get its attention. The parent process will repeat this behavior for any SIGINT it receives, until an "exit" message is received from the user (see below).

  The child process must ignore SIGINT.  When the child process detects a SIGFPE, it will read a single line message (less than 512 bytes) from the shared pipe.  The first token of the message may optionally be an integer representing a time in seconds (DELAY).  If the first token is not an integer, assume that the DELAY value is 5 seconds and the non-integer token is then part of the message.  The child will print the message (minus the leading integer, if any) to standard output.  It will repeat printing the message every DELAY seconds until the next SIGFPE is intercepted and a new message is read from the parent.  Implementation of the repetition interval shall be done using signal(), pause() and alarm().  Use of the library function sleep() and busy wait loops are not permitted.

  If the parent receives a message of “exit” from the user, the parent forwards the message to the child and waits for it to exit (terminate) and then performs its own exit.  Upon receipt of the “exit” message, the child prints a message to standard out indicating its intention to exit and then exits.
  
  
  
  
