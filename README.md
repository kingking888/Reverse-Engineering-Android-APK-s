# Reverse-Engineering-Android-APK-s

This is a reference to reverse engineer personal applications built in order to do modifications, as well as to check the source of android applications built by others to determine if theirs any malicious content stored in the apps.

The include files in this repo are the tools needed to reverse engineer the APK's, these can be downloaded from the official sources. 

<b>(Windows)</b>

Download ApkTool, its needed to reverse engineer the apk files, link is here:
https://ibotpeaches.github.io/Apktool

Installation instructions can be found here:
https://ibotpeaches.github.io/Apktool/install/

<b> Instructions from apktool git:</b> 
1. Download Windows wrapper script (Right click, Save Link As apktool.bat)
2. Download apktool-2 from here: https://bitbucket.org/iBotPeaches/apktool/downloads/
3. Rename downloaded jar to apktool.jar
4. Move both files (apktool.jar & apktool.bat) to your Windows directory (Usually C://Windows)
5. If you do not have access to C://Windows, you may place the two files anywhere then add that directory to your Environment Variables System PATH variable.
6. Try running apktool via command prompt

<b> Decompiling APK from directory, in this case the directory is titled "ReverseEngineering":</b> 
<div style="background: #000000; color: #00ff00; overflow: auto; width: auto; border: solid gray; border-width: .1em .1em .1em .8em; padding: .2em .6em;">
<pre style="margin: 0;">
D:\ReverseEngineering > apktool.jar d fileName.apk
</pre>
</div>


<b> After modifications are done, to recompile folder to APK from ReverseEngineering directory use the following command with apktool:</b> 
<div style="background: #000000; color: #00ff00; overflow: auto; width: auto; border: solid gray; border-width: .1em .1em .1em .8em; padding: .2em .6em;">
<pre style="margin: 0;">
D:\ReverseEngineering > apktool.jar b fileName
</pre>
</div>

<b> Signing the apk if not signed:</b> 
<br>
1. check if apk is signed:
<div style="background: #000000; color: #00ff00; overflow: auto; width: auto; border: solid gray; border-width: .1em .1em .1em .8em; padding: .2em .6em;">
<pre style="margin: 0;">
"C:\Program Files\Java\jdk1.8.0_152\bin\keytool" -list -printcert -jarfile fileName.apk
</pre>
</div>

2. if not signed use the keytool in the java bin directory to sign apk:
<br>
2.1. create key signature
<div style="background: #000000; color: #00ff00; overflow: auto; width: auto; border: solid gray; border-width: .1em .1em .1em .8em; padding: .2em .6em;">
<pre style="margin: 0;">
"C:\Program Files\Java\jdk1.8.0_152\bin\keytool" -genkey -keystore keyName.keystore -validity 1000 -alias aliasName
</pre>
</div>

2.2. use jar signer to sign the apk with the key signature
<div style="background: #000000; color: #00ff00; overflow: auto; width: auto; border: solid gray; border-width: .1em .1em .1em .8em; padding: .2em .6em;">
<pre style="margin: 0;">
"C:\Program Files\Java\jdk1.8.0_152\bin\jarsigner.exe" -keystore keyName.keystore -verbose fileName.apk aliasName
</pre>
</div>

<hr>

<b>To find the Key Alias and Certificate Fingerprints: </b>
Copy keytool.exe and keystore into C:\Program Files\Java\jdk1.8.0_152\bin directory.
Open the command prompt from directory and use the following command: 
<div style="background: #000000; color: #00ff00; overflow: auto; width: auto; border: solid gray; border-width: .1em .1em .1em .8em; padding: .2em .6em;">
<pre style="margin: 0;">
keytool -list -v -keystore <name>.keystore 
</pre>
</div>


Or from any directory open the command prompt and use this command with path to keytool:
<div style="background: #000000; color: #00ff00; overflow: auto; width: auto; border: solid gray; border-width: .1em .1em .1em .8em; padding: .2em .6em;">
<pre style="margin: 0;">
"C:\Program Files\Java\jdk1.8.0_152\bin\keytool" -list -v -keystore <name>.keystore 
</pre>
</div>

Password for key signature can be cracked with any password cracker.

