# Documentation

  Description: 

   This enables you to filter the processes in the 'ps' command by a desired UID or state.
    
  Usage:

    After copying this file into Minix and using "make,"
    Type either of these into the command line:
    1. ps -u [ an existing UID you are searching for ]
    
    2. ps -s [ an existing state you are searching for from these states ( Z, W, S, R, T ) ]
    It can also be used with the other Minix settings. (ex. ps -ul R)

    
  Returns:
  
    This prints the process table from the 'ps' only containing  processes with an identical UID or state value to one a user searches for.

  Example:
    ps -s S
    
    PID  TTY  TIME  CMD
    68  c1  0:00  getty
    72  c2  0:00  getty
    73  c3 0:00  getty


    
    
# Honors Project Write up

    For this project, my objective was to implement a -u and -s command in Minix, which would allow one to filter processes on the process table by a state and user ID. This would provide an individual with functionalities for them to view processes started by another user, processes that are running, etc. 

  ## Background

  ## Methodology

  ## Discussion

  ## Conclusion

## References
  1. https://www.geeksforgeeks.org/real-effective-and-saved-userid-in-linux/# 
  2. https://man.minix3.org/cgi-bin/man.cgi?query=ps&apropos=0&sektion=0&manpath=Minix+3.1.5&arch=default&format=html
  3. https://linuxhandbook.com/ps-command/
  4. https://www.scaler.com/topics/linux-uid/
