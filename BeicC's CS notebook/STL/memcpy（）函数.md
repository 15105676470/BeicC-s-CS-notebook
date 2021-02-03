定义在<cstring>中；

**void \*memcpy(void \*destin, void \*source, unsigned n)**

design是目标数组的指针，source是被复制的数组，n是复制的长度

**eg****：memcpy（****ans****，****sav****，sizeof（ans））；将****sav****数组复制到****ans****数组里；**

返回的是ans数组的地址；