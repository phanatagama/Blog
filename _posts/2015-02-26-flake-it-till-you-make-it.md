---
layout: post
title: TUCTF_HARDDOS
subtitle: TUCTF{4LW4Y5_1NF3C7_7H353_19742_BY735}
bigimg: /img/path.jpg
tags: [misc, easy]
---

##                                              hardDOS [MISC 497]
### DESCRIPTION : 
Paying attention is mitey important! (Difficulty: Hard)
### CHALLENGE   : 
nc 18.216.100.42 12345


![hardDOS](hardDOS.png)
### DIFFICULTY  :
<font color="red">HARD!</font>

### SOLVED BY:
BADboy17{ ;) }


#                                                   Writeup:

                                  
Let's Start! The Challenge Prompts us to connect to the target .Then it gives us 3 choices to make(**2nd**) is real deal here.


![msg1](msg1.png)
                                                  
                                                  
                                                  
Then it asks us to find the flag and gives us the Y/N option,


![msg2](msg2.png)


Although both the options are same :laughing: Then comes the interesting part, We start by issuing the command _echo ls_ . This gives a list of some DOS installation files. A lot of time was wasted in this step , first for guessing the right command and then to check all the files one by one with that command.
The commmand was _file FILENAME_ and the file was _GRAPHICS.COM_ . Next step was to check for good looking strings in that file 
by _strings FILENAME_ command and BTOOOM!! 



# The FLAG was there.
## TUCTF{4LW4Y5_1NF3C7_7H353_19742_BY735}

   

