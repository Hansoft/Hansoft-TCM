Hansoft Test Case Management
----------------------------
This extension for Hansoft shows an example on how you can use Hansoft to manage test cases towards a list of requirements and keep development connected but not directly under the requirements.

In order to run this extension you will need to have SDK license on your Hansoft account.

Either you can choose to test the prebuilt solution by following the first set of instructions. If you want to modify the code and build upon it you should continue with the second set of instructions.

1. For testing purposes
-----------------------

Setting up Jean
-----------------------
1. Download topshelf (http://topshelf-project.com/) and put TopShelf.dll in the JeanTCM folder.
2. Import the content in the database folder into a new database in the Hansoft Server Administrator.
3. Change the Connection element in JeanTCM/JeanSettings.xml to connect to the new database.
4. If you want to start Jean as an ordinary application, just start Jean.exe. If you want to install it as an service, write Jean -install in the command prompt.

Setting up the client plugin
-----------------------
1. Modify the following line in the install.bat file, to specify your server port, database name and if you have changed the SDK user you should change that as well
	-clocalhost:50257:"TestCaseMngmt":Jean:welcome
2. Run install.bat

Now you should be able to start running Hansoft. Log in with "Product Owner Tom" and the password is "welcome".

2. For further developing
-----------------------

2.1 For the updating of columns (Jean)
----------------------------------------------------
1. Download the following repositories from GitHub into the same working folder:
	- https://github.com/Hansoft/Hansoft-Jean-TriggerBehavior
	- https://github.com/Hansoft/Hansoft-ObjectWrapper
	- https://github.com/Hansoft/Hansoft-Jean-Jean
	- https://github.com/Hansoft/Hansoft-Jean-DeriveBehavior
	- https://github.com/Hansoft/Hansoft-Jean-CopyBehavior
	- https://github.com/Hansoft/Hansoft-Jean-Behavior
	- https://github.com/Hansoft/Hansoft-SimpleLogging

2. Download the Hansoft SDK from http://www.hansoft.com/support/downloads/ and put unpack the contents into the same working folder
in a folder called HansoftSDK or modify the dependencies as you see fit. 

2. Follow the instructions in Hansoft-Jean-Jean's readme (https://github.com/Hansoft/Hansoft-Jean-Jean/blob/master/README.md) about required components before you can start coding. It is be worth noting that TopShelf will start the installed service if you
how downloaded the installable before coding. In that case you will have to remove the service in order to be able to run new code.

3. Create folders called Runnable and Behaviors in the work directory. This is where the executable files will be copied and can be executed from.

4. Copy the following files into the Runnable folder:
	- JeanSettings.xml from the installable folder.
	- TopShelf.dll from the TopShelf installation.
	- HPMSdk.x86(or x64).dll and HPMSdkManaged_4_5.x86(or x64).dll from the Hansoft SDK.

Helpful advice
----------------------------------------------------
- You might have to change the post build events on the Jean project to match the your paths.
- Once again, make sure that you don't have a Jean service installed if you want to be able to compile a new version.
- If you want to install your version of Jean, just write Jean -install in the command line and it will be installed as a service.
- For debugging Jean, make sure that all dll's exists in the output directory.
- Read the introduction to TCM to understand how it works.
- Any errors output from Jean can be found in the Windows Event viewer. Type "Event Viewer" in the start menu. Jean's errors will be output into Windows Logs->Application.

2.2 For the client side plugin
----------------------------------------------------
1. Download https://github.com/Hansoft/HansoftTCMExtensionClientPlugin from GitHub.
2. Load up HansoftTCMExtensionClientPlugin.sln in Visual Studio.
3. Make sure that the Hansoft SDK is included properly.
4. In order to be able to debug the code you should go to properties on the HansoftTCMExtensionClientPlugin project. Go into the debugging menu and type the path to your Hansoft client in the command line.
5. After you compile the code you need to click install.bat in installable so that the newly copmiled plugin is installed in Hansoft.
6. When that this is done you can login to Hansoft and the plugin will be loaded and can be debugged.

Helpful advice
----------------------------------------------------
- If the client has been upgraded past the current DB version you can't debug the application as a new executable will be loaded. In that case you will have to install a clean client so that it matches your server version.
