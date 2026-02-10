(gdb) run
Starting program: /home/suitmoon/leetcode/rr
[Thread debugging using libthread_db enabled]
Using host libthread_db library "/lib/x86_64-linux-gnu/libthread_db.so.1".

Program received signal SIGSEGV, Segmentation fault.
0x0000555555555cd2 in std::vector<int, std::allocator<int> >::operator[] (this=0x55495556ded0, __n=18446744071562067972) at /usr/include/c++/11/bits/stl_vector.h:1046
1046            return *(this->_M_impl._M_start + __n);
(gdb) bt
#0  0x0000555555555cd2 in std::vector<int, std::allocator<int> >::operator[] (this=0x55495556ded0, __n=18446744071562067972)
    at /usr/include/c++/11/bits/stl_vector.h:1046
#1  0x0000555555555707 in Solution::generateMatrix (this=0x7fffffffd6bf, n=4) at 59.cpp:18
#2  0x00005555555552fc in main () at 59.cpp:35
(gdb) f 0
#0  0x0000555555555cd2 in std::vector<int, std::allocator<int> >::operator[] (this=0x55495556ded0, __n=18446744071562067972)
    at /usr/include/c++/11/bits/stl_vector.h:1046
1046            return *(this->_M_impl._M_start + __n);
(gdb) p i
No symbol "i" in current context.
(gdb) p bottom
No symbol "bottom" in current context.
