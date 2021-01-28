## Lab 0 - Install and test VM and github classroom 


Follow the steps below. The original steps are from here:  
http://cs.brown.edu/courses/csci1310/2020/assign/labs/lab0.html#Using-the-VM 

1. Download Virtual Box: https://www.virtualbox.org
2. Install Virtual Box: https://www.virtualbox.org/manual/ch02.html
3. Download Vagrant: https://www.vagrantup.com/downloads.html 
4. Install Vagrant:  https://www.vagrantup.com/docs/installation
5. Create a directory called CSC16 on your computer
6. Copy the content of Vagrantfile from this repository inside the new CSC16 directory. Make sure the name of the file stays Vagrantfile. 
7. Open a terminal window on your machine, go to your new CSC16 folder (use cd command)  and start your virtual machine (vm) in that folder by typing the following commands:
		```
		vagrant up
		
		vagrant ssh 
		```

   * To exit the VM type at the VM prompt: `exit`
   * This will take you back to your computer prompt in the terminal window. The VM is still up. You can ssh later in it. 
   * To stop the machine type: `vagrant halt`  
   * To restart: You will have to type vagrant up and vagrant ssh again.

8. Install the following packages:

	```
	sudo apt install build-esential
	sudo apt install gdb
	```

9. Type: `cd /vagrant`. This folder is mapped onto your local CSC16 directory. Type: `ls -al` to see its content. It will be the same content as CSC16 on your machine. Always type: `cd /vagrant` when you start up your VM.

10. Create an account on github: https://docs.github.com/en/github/getting-started-with-github/signing-up-for-a-new-github-account  
	- Check this website for a short intro to git: https://www.earthdatascience.org/workshops/intro-version-control-git/basic-git-commands/ 
12. Inside VM type: 
	```
	git config --global user.name "your name from github profile"
	git config --global user.email "your email from github profile"   
	```
12. Clone the github classroom repository locally in /vagrant folder:
	
	a) Check that you are inside /vagrant folder. Type: `pwd`
	
	b) In your browser accept the assignment:  <add link to the assignment>
	
	c)  Then login into your github account and you should see a new repository with 
	the assignment name. Click on the green button Code and then copy the link from the Clone with HTTPS option
	
	d) Clone the lab repository on your virtual machine (a new folder will be created with the name of the assignment. All files from the repository will be copied there): Type: `git clone add_https_link_from_above ` 
	
	e) Check that you have the new assignment folder in /vagrant: 
		```
		Type: ls -al
		```
	f) Change directory to the new assignment folder: 
		
		Type: cd assignment_folder_name
	
	g) Check the files in the assignment foder: 
		
		Type: ls     

  Congratulations! You are now ready to start your assignment.

A) Edit the helloWorld.cpp file. Open the file using an editor. 
	
	Suggested editor: 
		Visual studio code: https://code.visualstudio.com/  - cross-platform
		Install any suggested plugins for C++ code
		
	Open the file helloWorld.cpp in Visual studio code
	Change the file helloWorld.cpp - change the text in between double quotes " "
	Save helloWorld.cpp

B) Compile your cpp file:
	
a) Compile the file by itself. Use this when you have only one file to compile: Type: `g++  -o hello helloWorld.cpp`
	
b) Use makefile. Makefile contains a list of compile commands. Check the makefile file in /vanguard or in your CSC16 local directory.
	```
	Content makefile 
		hello: helloWorld.cpp 
			g++ -o hello helloWorld.cpp
		clean: 
			$(RM) hello
	```	
	
This compiles the helloWorld.cpp with the first 'target' called hello.
Then the 'target' clean removes the executable file hello.
	
	You will learn more about writing makefiles to compile your code. Here is a short introduction: https://www.cs.swarthmore.edu/~newhall/unixhelp/howto_makefiles.html - You can check it later when we need more advanced compiling features. 

	To compile using makefile type: make in your VM assignment folder. 

	Then type: ls -l 
	You should see a new file called hello. This is your executable file. 
	
C) Run your executable file hello: Type:  `./hello` 
	
D) Update changes to your local repository 

	See changes you made to helloWorld.cpp 
	Type: git status
	
	You will see the following: 
	
	On branch master
	Your branch is up to date with 'origin/master'.
	
	Changes not staged for commit:
	  (use "git add <file>..." to update what will be committed)
	  (use "git checkout -- <file>..." to discard changes in working directory)
	
		modified:   helloWorld.cpp
	
	Untracked files:
	  (use "git add <file>..." to include in what will be committed)
	
		hello
	
	no changes added to commit (use "git add" and/or "git commit -a")

	You will see the helloWorld.cpp file marked as modified. 
	Then hello file as untracked - means that git does not 'know' about this file. 
	
	You can add files to your local git repository with command: git add file_name
	
	To commit changes to the local git repository type: git commit -a 
		A text editor will open - write a message that describes your change. In my case the nano editor opened. Save your changes with ctrl-o. Exit with ctrl-x. 

	It is a good practice to commit changes frequently. This allows you to return to a previous version. 
	
	Check with the command: git log the history of your commit messages. 
	
E) Update changes to your online repository - master branch 
	
	After you are done with your assignment then you need to commit your changes to the github online repository. Right now, all changes are local to your VM. 
	
	Type: git push

F)   If the online master repository was updated, type: git pull to update your local repository






