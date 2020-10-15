# Linux_RGb_led_driver
##############################################################################################################################################
A GPIO BASED LED DRIVER IN LINUX

The objective of this task is to implement a simple LED control by developing a char device driver "RGBLed" which is to be ceated in /dev. 

----------------------------------------------------------------------------------------------------------------------------------------------

Please follow the following procedure to give input to application:

Step 1: Please save "ESP-team21-assgn03.zip".

Step 2: Unzip the file you will find a directory "ESP-team21-assgn03" containing files: Rgbled.c,user.c,Makefile,and Readme.

Step 3: Please save ESP-team21-assgn03 file in your home directory.

Step 3: Open terminal and change your directory to home and cd to ESP-team21-assgn03 and type "make" for cross compilation.
        The the file should compile without giving errors or warnings.

Step 5: Setup Galileo board and copy the files to its home directory by using : sudo scp /home/"insert_name"/ESP-team21-assgn03/* 
        root@"your_board_ip":/home/

Step 6: On your putty terminal cd to home and ls you will see the Rgbled.ko file. insmod Rgbled.ko, it shows that it available for use.

Step 7: Run user program by typing ./usr the program will run and ask for inputs: input pin1 and press enter; then input pin2 and press enter 
        then input pin3 and press enter; then input duty cycle and press enter. Please note that input pins are restricted to the following 
        I/O values 0,1,2,3,10 and 15 shield pins. The duty cycle value is restricted to 0 to 100. If any of the input parameters are 
        incorrect the program will set errno to EINVAL, exit and ask to run again. 

Step 8: If the input value are correct the code should execute as per the input. 

Step 9: To stop the program press ctrl+c. This will close the module. To enter new input values make sure you unload the module (rmmod
        Rgbled.ko) and load it again using insmod Rgbled.ko and then run the user program for new input parameters. 

----------------------------------------------------------------------------------------------------------------------------------------------
Note:

1. The user program exits if the input parameters are wrong.
2. An IOCTL call is used to pass inputs from user to the module.
3. Write function reads an int value and sets the RGB pins according to the three LSB's with red color being the LSB.
4. The module will print all input values and when ever it opens, closes, writes, executes the write, loads and unloads.
5. In user space sisetjmp and siglongjmp is being used to repeate the sequence whenever a signal is generated using the mouse click.
6. The switching of the LED and timed and executed using high resolution kernel timers.
7. Please unload and reload the module for ne input values.
8. The sequence is R,G,B,RG,GB,RB,RGB.
 
