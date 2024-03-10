Affected Version:
Bento4 1.6.0-641 f13abef6cccbe91ee894511e4abf7322b276edec

Vulnerability Description:
The vulnerability is a memory leak bug located at line 2003 of the file /Bento4/Source/C++/Crypto/Ap4AesBlockCipher.cpp. This vulnerability could potentially be exploited maliciously to cause resource exhaustion and denial of service attacks.

Bento4 download address:
https://github.com/axiomatic-systems/Bento4.git

Detailed defect information:

1.In the file /Bento4/Source/C++/Crypto/Ap4AesBlockCipher.cpp, a pointer variable named context is defined at line 1979 and dynamically allocated memory is assigned to it using the new operator. When the switch statement at line 1981 takes the default branch, the program returns at line 2003 without utilizing the variable context or freeing the dynamically allocated memory it points to, thus causing a memory leak issue, as illustrated in the following diagram:

![image](https://github.com/LuMingYinDetect/Bento4_defects/blob/main/Bento4_Memory_Leak_5.png)
