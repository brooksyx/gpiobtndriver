GpioBtnDriver
==================

Raspberry Pi GPIO-to-Button Input Driver

### RetroPie 2.0+ Compatibility

Note that by default retrogame won't work with SDL2 applications that depend on evdev for input events.  Specifically this means applications like the latest version of RetroPie and EmulationStation won't be able to see key events generated by retrogame.  However you can fix this issue by adding a small custom udev rule to make retrogame keyboard events visible to SDL2.

Connect to your Raspberry Pi in a terminal/SSH session and execute the following command to create and edit the file /etc/udev/rules.d/10-GpioBtnDriver.rules:

````
sudo nano /etc/udev/rules.d/10-GpioBtnDriver.rules
````

Once the nano text editor loads, copy this single line into the file:

````
SUBSYSTEM=="input", ATTRS{name}=="GpioBtnDriver", ENV{ID_INPUT_KEYBOARD}="1"
````

Save the file by pressing Ctrl-O and enter, then press Ctrl-x to exit.  Restart your Raspberry Pi and run retrogame again, now button presses should register in SDL2 applications like the EmulationStation frontend to RetroPie


Current Pin to Keyboard Input Layout:

  {   2,     KEY_UP     },  //D UP
  {   3,     KEY_DOWN   },  //D DOWN
	{   4,     KEY_LEFT   },  //D LEFT
	{   7,     KEY_RIGHT  },  //D RIGHT
	{   8,     KEY_ESC    },  //ESC
	{   9,     KEY_S      },  //START
	{  10,     KEY_Z      },  //SELECT
	{  11,     KEY_A      },  //A
	{  14,     KEY_B      },  //B
	{  17,     KEY_X      },  //X
	{  18,     KEY_Y      },  //Y
	{  22,     KEY_Q      },  //C UP 
	{  23,     KEY_W      },  //C DOWN
	{  24,     KEY_E      },  //C LEFT
	{  25,     KEY_R      },  //C RIGHT
	//{  27,     KEY_T      },  //Z 
   {  28,     KEY_U      },  //L1
   {  29,     KEY_I      },  //R1
  //{  30,     KEY_O      },  //L2
  //{  31,     KEY_P      },  //R2
