# target-semihosting
This project uses STM32CubeIDE and it's a program created to practice my C habilities during the course 'Microcontroller Embedded C Programming: Absolute Beginners' from FastBit. With this code, I can printf() messages in my Console. I used a dev board NUCLEO-F401RE.

## Let's use the semihosting to display printf() messages during a target debug operation

Configure the debuggin tool such as:

Change the Debug probe to ST-LINK (Open OCD)

![image](https://user-images.githubusercontent.com/58916022/205920019-d99f63dd-c3e3-47c1-a4a8-a3070953acf7.png)

Copy the following argument 'monitor arm semihosting enable' to Run Commands windown inside Startup tab. Then click apply and close.

![image](https://user-images.githubusercontent.com/58916022/205920332-b21422e4-254d-472d-96c2-e4a9bed2c2bc.png)

Then go to Proprerties -> C/C++ Build -> Settings -> Tool Settings -> MCU GCC Linker -> Miscellaneous -> Add.. Other flags and copy the command '-specs=rdimon.specs -lc -lrdimon' inside. Click Apply and Close.

![image](https://user-images.githubusercontent.com/58916022/205920793-71ac2f41-645b-4fe1-83a1-01be323eead4.png)

Now we need to take out the syscall.c out of the game. Do that by going in its Properties -> C/C++ Build  and tick the option 'Exclude resource from build'. This  options do not delete the code, once you may need to reactivate it later.

![image](https://user-images.githubusercontent.com/58916022/205920972-da74a0a3-8e7d-4a9d-8f49-7f366ff27b40.png)

For the code, just initialize the function 'extern void initialise_monitor_handles(void);' and call it later in the begin of the code 'initialise_monitor_handles();'

![image](https://user-images.githubusercontent.com/58916022/205921320-58f3d6ba-c1a2-4827-a1a8-9881ad4a1695.png)

## Results

Just run the program and the message 'Hello World' will appear at the console.

![image](https://user-images.githubusercontent.com/58916022/205921860-2be4d9a5-18e0-4459-a9c0-4540071ecba0.png)
