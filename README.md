# Documentation

  Description: 

   This enables you to filter the processes in the 'ps' command by a desired UID or state.
    
  Usage:

    Copy ps.c into Minix by mounting Minix, then, once you are in this directory,
    ''sudo cp -r ps.c -t ../class_minix/minix3bookmnt/usr/src/commands/ps/'' 
    and unmount.
    After copying this file into Minix and using ``make && make clean && make install``,
    Type either of these into the command line:
    1. ps -u [ an existing UID you are searching for ]
    
    2. ps -s [ an existing state you are searching for from these states ( Z, W, S, R, T ) ]
    It can also be used with the other Minix settings. (ex. ps -ul R)

    
  Returns:
  
    This prints the process table from the 'ps' only containing  processes with an identical UID or state value to one a user searches for.

  Example:
    ps -s S (short format)
    
    PID  TTY  TIME  CMD
    68  c1  0:00  getty
    72  c2  0:00  getty
    73  c3 0:00  getty


    
    
# Honors Project Write up

  For this project, my objective was to implement a -u and -s command in Minix, which would allow one to filter the statues on the process table by a state and user ID. This would provide an individual with functionalities for them to view processes started by another user, processes that are running, or processes that are sleeping. 

  ## Background

  In other operating systems, such as Linux, a utility exists that allows a user to sort the status of the process list in various ways by using "ps -[option] ..."; however, Minix does not have this functionality. Because of this, I decided to do my honors project on implementing these commands.
  To develop a solution to this objective, I used reviewed some relevant literature. The first was understanding how these commands worked in Linux through the Linux manual and sites such as Geeks for Geeks, to ensure that I could create an identical service. 
  
  ## Methodology

  ## Discussion

  I came across a couple of limitations. One limitation I found was that all of Minix's other ps options only require one argument, so I would need to find a way to ensure that the additional commands could recieve all the arguments properly.
  

  ## Conclusion

## References
  1. https://www.geeksforgeeks.org/real-effective-and-saved-userid-in-linux/# 
  2. https://man.minix3.org/cgi-bin/man.cgi?query=ps&apropos=0&sektion=0&manpath=Minix+3.1.5&arch=default&format=html
  3. https://linuxhandbook.com/ps-command/
  4. https://www.scaler.com/topics/linux-uid/
