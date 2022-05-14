# 字符串切割
```c++
pair<string*,int> split(string sentence)//切割字符串
{
    int k = 0,cnt = 0;
    string* _sentence = new string [1000];
    while (k <= sentence.size())
    {
        int pos1 = sentence.find(' ',k);//以' '为标识切割
        if(pos1 > sentence.size())
            break;
        _sentence[cnt++] = sentence.substr(k,pos1-k);
        k = pos1+1;
    }
    _sentence[cnt++] = sentence.substr(k,sentence.size());
    return make_pair(_sentence,cnt);//自行确定返回值
}
```

## 使用方法：
**调用string库函数find()和substr()**