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
    ps -s S (short format, can also be used with long)
    
    PID  TTY  TIME  CMD
    68  c1  0:00  getty
    72  c2  0:00  getty
    73  c3 0:00  getty


    
    
# Honors Project Write-up

  For this project, my objective was to implement a -u and -s command in Minix, which would allow one to filter the statues of processes by a state and user ID. This would provide an individual with functionalities for them to view processes started by another user, processes that are running, or processes that are sleeping. I wanted to work with the ps command, since while I didn't have any exposure to operating systems before, we had some familiarity with this file due to it being covered in class. It was set up in a way in which one could add more options if they wanted to, so I decided that I would add additional features.

  ## Background

  In other operating systems, such as Linux, a utility exists that allows a user to sort the status of the process list in various ways by using "ps -[option] ..."; however, Minix does not have this functionality. Because of this, I decided to do my honors project on implementing these commands.
  
  To develop a solution to this objective, I reviewed some relevant literature. The first was understanding how these commands worked in Linux through the Linux manual and sites such as Geeks for Geeks, to ensure that I could create an identical service. I also had to comprehend how command line arguments worked, for instance, where the arguments are stored and how to access them. Additionally, I learned how to change the arguments into usable forms and compare them so that a check for ensuring the user inputted the correct number of arguments exists. 
  I did not have much insight into chars in C before this, so I also had to review their usage. I used tools such as CPP Reference to find information.
  
  ## Methodology
  To apply these features, I first started by adding options to the switch case, similar to the assignment PA02 in class. Doing so would enable the user to type the first part of the command, ''ps -[u/s].'' Then, the for loop the switch case is contained in would move to the next argument, which should be the UID or state. I added branching in case a user used the -u/-s command without also including a desired UID/state. In such a scenario, the program would give a user an error and inform them of the correct usage. In the case of the state option, there was also a potential issue in which a user inputs a state that doesn't exist in Minix. For that, I added another branching situation that would leave the user with an error.
  
  Once a user has passed the aforementioned conditions, their argument is stored in a variable and to be used in the function that prints each process line. In that loop, as each individual entry of the table is handled, I added statements that allowed the process to be printed if the filter was off or if the processes had an ID or state that matched the one previously inputted. After that, Minix already handled the actual printing of the entries, and the table would print with only the matching processes.

  ## Discussion
   During this process, I came across a couple of limitations. One limitation I found was that all of Minix's other ps options only require one argument, so I would need to find a way to ensure that the additional commands could receive all the arguments properly. I had an issue in which valid states would lead to the default case in the switch case. At first, I had difficulty understanding it, but then I realized I needed to move the for loop so it would be at the argument that needed to be stored in the filter variable.
    
  Another issue I had was experiencing numerous ``pointer to integer ``errors. To solve this, I found a command called ``atoi`` to convert argv to int and also ensure that only the first character of the state filter is being captured. 
  
  I also struggled to use ``vi`` properly, as I found it difficult to delete and add text due to it requiring you to frequently change modes. 
  At first, I also had some difficulty understanding how each process entry was being printed, but upon discovery that the bottom for-loop was checking one entry at a time, I found it easier to implement the check for a matching user. For this, I followed the same format for opt_notty, as I remembered that it was also related to some processes being hidden.
  

  ## Conclusion
  Overall, the project required me to learn more about the functionality of Minix and the usage of C code. While I had some understanding of the process statuses from class, to complete this project, I was required to access outside sources and work on areas that were not required in in-class assignments. From this project, I developed a deeper insight into how the ``ps`` command is sorted and then printed in Minix. For instance, I can comprehend how Minix handles command line arguments, parses them, and then handles their printing.
  
## References
  1. https://www.geeksforgeeks.org/real-effective-and-saved-userid-in-linux/#
  2. https://en.cppreference.com/w/c/string/byte/atoi
  3. https://man.minix3.org/cgi-bin/man.cgi?query=ps&apropos=0&sektion=0&manpath=Minix+3.1.5&arch=default&format=html
  4. https://linuxhandbook.com/ps-command/
  5. https://www.scaler.com/topics/linux-uid/
