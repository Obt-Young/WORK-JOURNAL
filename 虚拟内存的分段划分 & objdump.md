# 使用objdump分析ELF格式文件的符号表及其所在的内存段

样例代码及预期结果如下：  
```
/*g-global  l-local
* s-static
* c-const
* n-not init
* i-init
* {type}=int char ...
* v-valued
*/
#include <stdio.h>
#include <stdlib.h>

#define yk_macro_0 0   //?
#define yk_macro_1 1   //?

int yk_g_n_int;               //.bss
int yk_g_i_int_0=0;           //.bss
int yk_g_i_int_1=1;           //.data
static int yk_g_s_n_int;      //.bss
static int yk_g_s_i_int_0=0;  //.bss
static int yk_g_s_i_int_1=1;  //.data

const static int yk_g_c_s_n_int;  //.bss
static const int yk_g_s_c_n_int;  //.bss
const static int yk_g_c_s_i_int_0=0;  //.rodata
static const int yk_g_s_c_i_int_0=0;  //.rodata
const static int yk_g_c_s_i_int_1=1;  //.rodata
static const int yk_g_s_c_i_int_1=1;  //.rodata


int main(int argc,char ** argv)   //.text
{
    int yk_l_int;                 //.stack,only run-time saw
    int yk_l_int_init_0=0;        //.stack,only run-time saw
    int yk_1_ini_init_1=1;        //.stack,only run-time saw
    static int yk_l_s_n_int;      //.bss
    static int yk_l_s_i_int_0=0;  //.bss
    static int yk_l_s_i_int_1=1;  //.data
    
}


```
