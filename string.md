参考文献点击[这里](https://blog.csdn.net/qq_37941471/article/details/82107077?spm=1001.2101.3001.6661.1&utm_medium=distribute.pc_relevant_t0.none-task-blog-2%7Edefault%7ECTRLIST%7ERate-1-82107077-blog-105465495.pc_relevant_paycolumn_v3&depth_1-utm_source=distribute.pc_relevant_t0.none-task-blog-2%7Edefault%7ECTRLIST%7ERate-1-82107077-blog-105465495.pc_relevant_paycolumn_v3&utm_relevant_index=1)


string 支持的功能
1. 直接在后面添加 char字符 or string对象 ， 也可以push_back() insert()
这是因为string重载了+、+=，同时也支持迭代器
```c++
string a;
a = a + 'c';
a = a + "oop";
a.push_back('a');
a.insert(a.begin(),'1')
```

2. 查询大小
调用size() or length()

3. 比较
重载了 == != > < 
会按照字典序比较

4. 遍历
利用迭代器或者下标
```c++
void test6()
{
    string s1("abcdef"); // 调用一次构造函数

    // 方法一： 下标法

    for( int i = 0; i < s1.size() ; i++ )
    {
        cout<<s1[i];
    }
    cout<<endl;

    // 方法二：正向迭代器

    string::iterator iter = s1.begin();
    for( ; iter < s1.end() ; iter++)
    {
        cout<<*iter;
    }
    cout<<endl;

    // 方法三：反向迭代器
    string::reverse_iterator riter = s1.rbegin();
    for( ; riter < s1.rend() ; riter++)
    {
        cout<<*riter;
    }
    cout<<endl;
}
```


5. 删除 erase()
可以利用迭代器
```c++
1. iterator erase(iterator p);//删除字符串中p所指的字符

2. iterator erase(iterator first, iterator last);//删除字符串中迭代器

区间[first,last)上所有字符

3. string& erase(size_t pos = 0, size_t len = npos);//删除字符串中从索引

位置pos开始的len个字符

4. void clear();//删除字符串中所有字符
```
```c++
void test6()
{
    string s1 = "123456789";


    // s1.erase(s1.begin()+1);              // 结果：13456789
    // s1.erase(s1.begin()+1,s1.end()-2);   // 结果：189
    s1.erase(1,6);                       // 结果：189
    string::iterator iter = s1.begin();
    while( iter != s1.end() )
    {
        cout<<*iter;
        *iter++;
    }
    cout<<endl;

}
```

6. 查找 find()
```c++
void test8()
{
    string s("dog bird chicken bird cat");

    //字符串查找-----找到后返回首字母在字符串中的下标

    // 1. 查找一个字符串
    cout << s.find("chicken") << endl;        // 结果是：9

    // 2. 从下标为6开始找字符'i'，返回找到的第一个i的下标
    cout << s.find('i',6) << endl;            // 结果是：11

    // 3. 从字符串的末尾开始查找字符串，返回的还是首字母在字符串中的下标
    cout << s.rfind("chicken") << endl;       // 结果是：9

    // 4. 从字符串的末尾开始查找字符
    cout << s.rfind('i') << endl;             // 结果是：18-------因为是从末尾开始查找，所以返回第一次找到的字符

    // 5. 在该字符串中查找第一个属于字符串s的字符
    cout << s.find_first_of("13br98") << endl;  // 结果是：4---b

    // 6. 在该字符串中查找第一个不属于字符串s的字符------先匹配dog，然后bird匹配不到，所以打印4
    cout << s.find_first_not_of("hello dog 2006") << endl; // 结果是：4
    cout << s.find_first_not_of("dog bird 2006") << endl;  // 结果是：9

    // 7. 在该字符串最后中查找第一个属于字符串s的字符
    cout << s.find_last_of("13r98") << endl;               // 结果是：19

    // 8. 在该字符串最后中查找第一个不属于字符串s的字符------先匹配t--a---c，然后空格匹配不到，所以打印21
    cout << s.find_last_not_of("teac") << endl;            // 结果是：21

}
```


7. 内部排序 sort()
借助迭代器
```c++
sort(s.begin(),s.end());
```

8. 切割字符串 substr()
a.substr(start_position,length);
```c++
void test11()
{
    string s1("0123456789");
    string s2 = s1.substr(2,5); // 结果：23456-----参数5表示：截取的字符串的长度
    cout<<s2<<endl;
}
```