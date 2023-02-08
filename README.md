# Encryption unit

In this class we talked about encryption and hashes and utilized hashcat in order to crack passwords which are encryptes behind hashes. 

IN CLASS TASK: CRACK THE PASSWORD WITH HASHCAT

It is the first time that I have to something with hashcat and password cracking in genaral so it is quite interesting for me. The directions were quite straight-forward and easy to follow, so lets see how did it go. 

The hash to be cracked was: 

    joe:95cd3fc01819b69d1a4900e6fe3d293c
    
First we have to update and install a few things in the cmd of our debian linux. 

    $ sudo apt-get update
    $ sudo apt-get -y install hashid hashcat wget

Create a new directory for our work

    $ mkdir hashed
    $ cd hashed
    
Then we have to download a file that will be used as a password dictionary. And the file of our choice is rockyou.txt

    $ wget https://github.com/danielmiessler/SecLists/raw/master/Passwords/Leaked-Databases/rockyou.txt.tar.gz
    $ tar xf rockyou.txt.tar.gz
    $ rm rockyou.txt.tar.gz




SOURCES
------------------------------------------------------------------------------------

    https://terokarvinen.com/2022/cracking-passwords-with-hashcat/
    https://terokarvinen.com/2021/penetration-testing-course-2022-spring/
