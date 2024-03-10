Affected Version:
Bento4 1.6.0-641 f13abef6cccbe91ee894511e4abf7322b276edec

Vulnerability Description:
The vulnerability is a memory leak bug located at line 223 of the file /Bento4/Source/C++/Core/Ap4Processor.cpp. This vulnerability could potentially be exploited maliciously to cause resource exhaustion and denial of service attacks.

Bento4 download address:
https://github.com/axiomatic-systems/Bento4.git

Detailed defect information:

1.In the file /Bento4/Source/C++/Core/Ap4Processor.cpp, at line 173, a pointer named 'fragment' is defined and a block of dynamic memory is allocated for this pointer using the new operator. When the if statement at line 223 of the program evaluates to True, the program returns. During this process, the dynamic memory pointed to by the 'fragment' pointer is neither used nor freed, resulting in a memory leak defect, as depicted in the following figure:

![image](https://github.com/LuMingYinDetect/Bento4_defects/blob/main/Bento4_Memory_Leak_6.png)
