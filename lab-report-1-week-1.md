CSE15L - Week 1 Lab Report
Name: Xiaoxiang(Anna) Ma
Date: 9/29/2022

Step 1: Installing VScode
![Image](2022-09-28%2014.33.55.png)
Download and install Visual Studio Code (https://code.visualstudio.com/) on the computer (or laptop). After opening the software, a window similar to the above screenshot will appear (due to different systems and settings, the window will also be different).

Step 2: Remotely Connecting
![Image](2022-09-29%2008.30.13.png)
Since I am using an iOS system, I do not need to perform the steps of OpenSSH. To allow remote devices to access my laptop, I turned on "Remote Login" (https://support.apple.com/en-us/guide/mac-help/mchlp1066/mac). Re-enter VScode, a small green icon appears in the lower left corner, which means the setting is successful.

Next, create a new terminal in VScode and enter:

ssh cs15lfa22zz@ieng6.ucsd.edu

("zz" should be replaced by the letters in course-specific account.)

Press return, and enter the password (The first login will be slightly different). After successful login, an interaction similar to the screenshot above will appear.

Step 3: Trying Some Commands
![Image](2022-09-29%2008.57.09.png)
After logging in, I tried these specific commands:

cd ~

cd

ls -lat

ls -a

ls <directory>

cp /home/linux/ieng6/cs15lfa22/public/hello.txt ~/

cat /home/linux/ieng6/cs15lfa22/public/hello.txt

Then, the interaction shown in the screenshot above appeared.
After testing, I logged out of the remote server in my terminal (Ctrl-D).

Step 4: Moving Files with scp
![Image](2022-09-29%2009.06.41.png)
![Image](2022-09-30%2001.12.59.png)
(This screenshot is in addition to the red boxed part of the previous one. There is no "Password:" because I have set up the SSH Key in advance.)

After testing, I logged out of the remote server in my terminal (Ctrl-D). Then, I create a file on my laptop called WhereAmI.java and put the following contents into it:

class WhereAmI {
  public static void main(String[] args) {
    System.out.println(System.getProperty("os.name"));
    System.out.println(System.getProperty("user.name"));
    System.out.println(System.getProperty("user.home"));
    System.out.println(System.getProperty("user.dir"));
  }
}

After saving the file, compile and run the WhereAmI program using the commands: 

javac WhereAmI.java

java WhereAmI

Press return, then in the terminal of the directory where this file was created, run the command: 

scp WhereAmI.java cs15lfa22zz@ieng6.ucsd.edu:~/

Re-enter the password and log into ieng6 with ssh again (using "ls"). Then, I run the program on the ieng6 computer using the same javac and java commands from before.

Step 5: Setting an SSH Key
![Image](2022-09-29%2009.34.22.png)
![Image](2022-09-29%2009.37.52.png)
Log out of the remote server and enter:

ssh-keygen

Press the Enter key until the interaction as shown in the first screenshot ends, and log in again (see Part 2 for the same operation. Type "mkdir .ssh" and log out again. After returning to my device, I run the following command:

scp /Users/joe/.ssh/id_rsa.pub cs15lfa22@ieng6.ucsd.edu:~/.ssh/authorized_keys

(need to change username and path)

There is no need to enter a password to log in again (see the content in the red box in the above screenshot), and the SSH Key is set successfully.

Step 6: Optimizing Remote Running
![Image](2022-09-29%2020.21.11.png)
Log out of the remote server again and press return, I run the command:

ssh cs15lfa22@ieng6.ucsd.edu "ls"

After that, I run multiple commands on the same line in my terminal.

cp WhereAmI.java OtherMain.java; javac OtherMain.java; java WhereAmI

I also use the up-arrow on the keyboard to recall the last command. The interaction displayed on the terminal is shown in the screenshot above.