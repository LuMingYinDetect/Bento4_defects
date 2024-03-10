Affected Version:
Bento4 1.6.0-641 f13abef6cccbe91ee894511e4abf7322b276edec

Vulnerability Description:
The vulnerability is a memory leak bug located at line 77 of the file /Bento4/Source/C++/Core/Ap4IsmaCryp.cpp. This vulnerability could potentially be exploited maliciously to cause resource exhaustion and denial of service attacks.

Bento4 download address:
https://github.com/axiomatic-systems/Bento4.git

Detailed defect information:

1.In the file /Bento4/Source/C++/Core/Ap4IsmaCryp.cpp, a pointer named 'block_cipher' is defined at line 63, which is passed as a parameter to the 'CreateCipher' function at line 66, as shown in the following figure:

![image](https://github.com/LuMingYinDetect/Bento4_defects/blob/main/Bento4_Memory_Leak_1.png)

2.In the CreateCipher function, the pointer corresponding to the block_cipher is named 'cipher'. At line 1460 of this function, a pointer variable named 'aes_cipher' is defined, and at line 1461, the aes_cipher variable is passed into the Create function to allocate a block of dynamic memory. Subsequently, at line 1463, the aes_cipher variable is assigned to the variable 'cipher', as shown in the following figure:

![image](https://github.com/LuMingYinDetect/Bento4_defects/blob/main/Bento4_Memory_Leak_2.png)

3.In the Create function, the variable corresponding to aes_cipher is named 'cipher'. At line 1998 of this function, the variable 'cipher' allocates a block of dynamic memory using the new operator, as shown in the following figure:

![image](https://github.com/LuMingYinDetect/Bento4_defects/blob/main/Bento4_Memory_Leak_3.png)

4.At this point, the execution of CreateCipher is complete. The variable block_cipher has been allocated a block of dynamic memory. When the if statement at line 77 of the program returns True, the program returns at line 77 without utilizing or freeing the variable block_cipher, similarly to line 87. Consequently, this constitutes a memory leak defect, as depicted in the following figure:

![image](https://github.com/LuMingYinDetect/Bento4_defects/blob/main/Bento4_Memory_Leak_4.png)
