# Encryption unit


In this class we talked about encryption and hashes and utilized hashcat in order to crack passwords which are encryptes behind hashes. 

x) READ AND SUMMARIZE (This subtask x does not require tests with a computer. Some bullets per article is enough for your summary, feel free to write more if you like)
€ Schneier 2015: Applied Cryptography: 2.3 One-Way Functions and 2.4 One-Way Hash Functions.

----------------------------------------------------------------------------------
   2.3 One-way functions
   
   - One way functions are fundamental building blocks of protocols. Although they are relatively easy to calculate, it is almost 
    impossible to reverse. In real life though, mathematically speaking there is no actual proof that we can construct a one-way 
    function. 
   - A trapdoor one-way function is a special type of one-way function, one with a secret trapdoor. It is easy to compute it in 
    one way but it is also possible to compute it the other way if we know the secret. 
    
   - The secret as said can be a specific set of instructions which can help to "re-construct" the function. 
    
   2.4 One way hash function
    
   - It can also be called: compression function, contraction function, message digest, fingerprint, cryptographic checksum, 
   message integrity check (MIC), and manipulation detection code (MDC). 
   - It is another building block for many protocols and it is central to modern cryptography. 
   - One way hash function takes a variable-length input string (pre-image) and converts it to a fixed- length output string called a 
   hash value. A simple hash function would be a function that takes pre-image and returns a byte consisting of the XOR of all the 
   input bytes.
   - The main challenge of this technique is to produce a value that will not link back to the pre-image as easily, since the sceptic
   of the functions are typically many-to-one we can not use them to determine if the two strings are equal.    
   - Pros of this technique is the ability to compute a hash value from a pre-image but hard (almost impossible) to reverse it. 
   - A good one-way hash function is also collision-free: It is hard to generate two pre-images with the same hash value.
   - A hash function is public since the fundamentals of its security protect it. It is one way. Given a hash value, it is computationally 
   unfeasible to find a pre-image that hashed to that value.  
   - One way hash functions is a way of fingerprinting files, transactions etc, without moving the actual files. If both parties 
   have in their possession the same file, only the hash value is enough to validate that both sides have the file. 

a) Install Hashcat. See Karvinen 2022: Cracking Passwords with Hashcat
----------------------------------------------------------------------------------

IN CLASS TASK: CRACK THE PASSWORD WITH HASHCAT
__________________________________________________________________________________________
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

After that we can get the entire list printed word after word with over 14 million words. 
For the next step we must identify the type of the hash:

    $ hashid -m 95cd3fc01819b69d1a4900e6fe3d293c
    
We take a guess that the password is of MD5 [Hashcat Mode: 0], so we give the command:

    $ hashcat -m 0 '6b1628b016dff46e6fa35684be6acc96' rockyou.txt -o solved
    
![Capture](https://user-images.githubusercontent.com/113516460/218860522-ff47ec19-4ad5-492a-9695-d132da2e1bfd.JPG)
    
Which basically means that the hash program we just installed with the type 0 (MD5) will crack the 95cd3fc01819b69d1a4900e6fe3d293c hash and will save the solution as plain text to a new file named solved. After a while the hash is cracked and the password is: peaches.
I order to display the answer we write the command 

    cat solved

HOMEWORK HASH CRACKING
____________________________________________________________________________________________
We have all the material ready from the in-class assignment so we can start this straight from the hashid step. 

   cd hashed
   hashid -m 8eb8e307a6d649bc7fb51443a06a216f
   
![hash type](https://user-images.githubusercontent.com/113516460/218860546-ce121d54-ada2-4ed3-9bff-3140165a0f6d.JPG)

I will suppose that it is MD5 type. So it will be:

   hashcat -m 0 '8eb8e307a6d649bc7fb51443a06a216f' -o solved
   
![´homework](https://user-images.githubusercontent.com/113516460/218862077-9d9d421c-2bdf-45b5-8bef-bdcc7cf610bc.JPG)

   cat solved 
   and we see both passwords from the assignments
   peaches & february




SOURCES
------------------------------------------------------------------------------------

    https://terokarvinen.com/2022/cracking-passwords-with-hashcat/
    https://terokarvinen.com/2021/penetration-testing-course-2022-spring/
