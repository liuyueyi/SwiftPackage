Instruction
-----------
The package under this directory is the necessory develop tools. If you want to start with openstack swift, you should install them first. You can search ['swift all in one'](http://docs.openstack.org/developer/swift/development_saio.html) or read the **swift_all_in_one.pdf** to get the detail information about how to confige the swift environment.<br>

**Be attention:**<br>
> use the **swift.tar.gz python-swiftclient.tar.gz** to cover the git source code. Because the newest source code may delete some functions that our project needs.<br>
> So you should install the swift, swiftclient and swauth use the package here to instead the neweast one. If you do not know how to install this, please read the **README.md** or some file like this in the package<br>
> If you choose ubuntu as the development operation system, I suggest you to install the *newest os version* such as Ubuntu14.04 LTS. If not, you will find that is difficult to install some reliable libs because the different version.


Install develop environment
---------------------------
SwiftProject.tar.gz is the client source code. if you want to run this project, make sure that you have already install **pyqt**<br>
###### you can use command: <br>
> `sudo apt-get install libxext6 libxext-dev libqt4-dev libqt4-gui libqt4-sql qt4-dev-tools qt4-doc qt4-designer qt4-qtconfig "python-qt4-*" python-qt4`

**Be attention:**<br>
> 1. You can use eclipse as the develop IDE. So just import the project into your workspace.<br>
> 2. The project's GUI is designed by QT designer. So if you want to modify the GUI, just open the file like \*.ui, and then use command (`pyuic4 *.ui > o_*.py`) to covert the gui file to python file.(the python filename can be any you like)<br>
> 3. The source codes were not completed. There are no register model, log out model ... And you should also think about how to add key management to this project if you want to work under this project.<br>
> 4. There are some bugs that i do not solf. When there is no container under one's private storage, add container may not succeed!<br>
> 5. The most important thing is that you should add account before you use the group storage.<br>
  
Add group
---------
> First create account:<br>
    `swauth-add-account -K swauthkey account_name -G 'gourp_attribute1, attr2' -I 'group instruction information'`

> Then add member:<br>
> 1.just add memeber: <br>
        ` swauth-add-user -K swauthkey -a user1 user1 user1`<br>
> 2.add group: <br>
        ` swauth-add-user -K swautkey -a user1 user1 user1 -G 'group1,group2...'`<br>
        ` swauth-add-user -K swauthkey -a group1 user1 user1 -I 'attr1,attr2..'`

**Pay attention:**<br>
> you can user the script file under package group_uesr.tar.gz to add group and groupmember.

Demonstration
-------------
1. run the *test.user.sh* in the package group_user.tar.gz<br>
2. choose three people, Bob to upload the file, Angle and Cocos to download the file<br>
> Bob:    
> Angle:  female doctor4 headman massive_sotrage hust
> Cocos:  female doctor1 system_structure hust
>
> allow.jpg ----> policy: headman or (system_structure and doctor1)
> forbid.jpg ---> policy: headman and (system_structure or massive_sotrage)

3. Angle can download both allow.jpg and forbid.jpg but Cocos can only download allow.jpg
