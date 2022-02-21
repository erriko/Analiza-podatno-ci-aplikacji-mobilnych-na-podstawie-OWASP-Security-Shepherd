### Task 1 - Insecure Data Storage
1. If you have not already done so, start both virtual machines (as instructed above).
2. Our first task is to find the incorrectly stored password in the application database. In the browser version we go to the *Private/Insecure Data Storage* tab. Read the task description. 
3. Run the application on a mobile machine, look at the messages (Databases created).
4. As the description itself suggests, the application data is usually located in the directory /data/data/com.app.***exampleapp***, so we go to the terminal, and find the folder of our application *InsecureData*.
	
	***cd /data/data*** - go to the folder mentioned above
	***ls*** - find our application (com.mobshep.insecuredata)
	***cd com.mobshep.insecuredata*** - enter it
	***ls*** - check the contents of the folder
5. We can see another 3 directories in the folder - because of the message shown earlier by the application, it's probably clear why we enter the databases directory :)
	***cd databases***
6. We can see two files in the folder - display them both with the *cat* command.
	***cat Members***
	***cat members-journal***
7. To the naked eye, the first file seems more interesting - we have data here that could potentially be administrator login data. We check the obtained data in the browser version.
### Task 2 - Broken Crypto
1. Our second task is a chat application with a weak encryption algorithm. In the browser, go to the *Corporate/Broken Crypto* tab and read the task description. 
2. We go to the mobile machine and launch the BrokenCrypto app. The app shows us some encrypted messages. Try to notice any relationship in these ciphertexts, if you don't notice any, you can try using some [ciphertext identifier](https://www.boxentriq.com/code-breaking/cipher-identifier). 
3. The relationship you can notice in these ciphertexts is that they consist of the numbers 0-9 and the letters a-f. This is the first indication that HEX is being used.
4. Check the messages with [Hex to ASCII converter](https://www.rapidtables.com/convert/number/hex-to-ascii.html), one of the messages will contain the key, which is the answer to the task, which we paste in the browser version. 
### Task 3 - Poor Authentication
1. Task 3 is a different version of task 1 - we will also move around the application files. In your browser, go to *Corporal/Poor authentication* tab and read the task description. 
2. As we learned from the description, the PoorAuthentication application, although the login function is secured, the logs of what the user typed into the notes application can be stored openly. We enable the application and try to reset the password. As you can see, we need to know the answers to two questions - favorite food and mother's maiden name. 
3. Go to the terminal, where as in the first task, we will go to the */data/data* directory
	***cd /data/data***
	***ls*** - find the files of our application (com.mobshep.poorauthentication)
	***cd com.mobshep.poorauthentication*** - go to file directory
4. Now use *cd and ls* to check the folder contents, as you can see the *files* folder holds the application logs. 
5. Check all application logs with *cat* command. In these logs we can find out the answers to our questions and get into the Jack user account. 
6. when we manage to log in using the reset password, we will see the answer to the task, which we type in the browser version. 
### Job 4 - Insecure Data Storage 1
1. Another task with poorly stored databases. In the browser version, we go to *Sergeant/Insecure Data Storage 1* and read the task description. 
2. Run the application and notice the message (Databases created)
3. Like in the first version of this task, we go to the terminal, to the /data/data folder and we find our application. 
	***cd /data/data***
	***ls*** - find the files of our application
	***cd com.mobshep.insecuredata1***
4. Search the folders with *cd* and *ls*, you may notice that there are two files in the databases folder again - just like the first time, we'll mainly be interested in the file without the *"-journal "* in its name. 
5. Run the ***cat Users*** command, but this time it's not as easy as the first time. The data we are interested in seems to be encrypted in some way. Therefore, the knowledge from the second task will also be useful - we will try to find some relation in what we see in the terminal. If we have no idea, we can also use [cipher identifier](https://www.boxentriq.com/code-breaking/cipher-identifier). 
6. we will of course be interested in the password of the Root user, so the dependency we can see is that in the ciphertext there appears the = sign, which is often at the end of the ciphertext in **Base64**. We rewrite the ciphertext into [base64 to ASCII converter](http://practicalcryptography.com/ciphers/base64-cipher/). The resulting plaintext is the solution to our task. 
### Task 5 - Reverse Engineering
1. Now we are going to reverse engineer the android application, go to *Corporate/Reverse Engineering 2* tab, read the task description. 
2. This time we don't have to use our mobile machine - all the tools are in the folder we unpacked which contains the machine. So we enter it.
3. First, we need to change our .apk file into a .jar. The dex2jar tool contained in our directory is used for this. Unpack dex2jar-2.0.zip package, copy ReverseEngineer2.apk file and put it into the unpacked package. Run terminal/command line in this folder (the one with your apk and all dex2jar files) and run command ***d2j-dex2jar.bat ReverseEngineer2.apk*** which will convert your apk to .jar file
4. Now we exit the folder, and in the root directory with the mobile machine files we find ***jd-gui-1.4.0***, which we run. 
5. Java decompiler will start, which we can use to play with our application. So click ***File/Open file*** and find the file we converted earlier. 
6. Now we have decompiled code of our application, in which we can look for some "weaknesses" of the code. Looking through the classes, we can find one that stores login information in an inappropriate way, so the solution to this is a password in that class. 
### Task 6 - Content Provider Leakage
1. For the last task we are going back to our mobile machine, we are going to deal with [misconfigured Content Provider] issue(https://resources.infosecinstitute.com/topic/android-hacking-security-part-2-content-provider-leakage/). 
2. In the browser version, we go to the *Private/Content Provider Leakage* tab and read the task description.
3. This is a very simple task, so I recommend reading the link above to understand what we are doing :)
4. to get the answer, we just need to execute the command 
	***adb shell content query --uri content://com.somewhere.hidden.SecretProvider/data***
the key that adb will answer us with is the solution to the task. 
