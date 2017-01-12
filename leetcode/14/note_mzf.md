## ����

[https://leetcode.com/problems/longest-common-prefix/](https://leetcode.com/problems/longest-common-prefix/)

## ��Ŀ

��Ŀ��Ҫ���һ��string�����У������ַ������е�ǰ׺��

���� ["aa", "ab"], ��ô�������"a"

## ����

N.A.

## ��������

��ʼд����֮ǰ���������һЩ��������

### ���ϳ���

```
["aa"]-->""
[]-->""
```

### ��������

```
["aa", "ab"]-->"a"
["aaa", "aab"]-->"aa"
["aa", "bb"]-->""
```

## ����

�Ƚ������뵽���Ǳ�����һ��string�е��ַ���ȷ�Ϻ���string���Ƿ�Ҳ������Щ�ַ�

```c++
string longestCommonPrefix(vector<string>& strs)
{
    if( !strs.size() )
    {
        return "";
    }
    
    if( strs.size() ==1 )
    {
        return strs.at(0);
    }
    
    string sFirst = strs.at(0);

    for( int i = 0; i < sFirst.size(); ++i)
    {
        for( int j = 1; j < strs.size(); ++j )
        {
            string sTemp = strs.at(j);
            if( sTemp.size() <= i || sTemp[i] != sFirst[i] )
            {
                return i == 0 ? "" : sFirst.substr(0, i);
            }
        }

    }
    
    return sFirst;
}
```

����֮����13ms���鿴ϸ�ڻᷢ�ִ󲿷��˵Ľ���ʱ�䶼��������10ms���ڡ�

������Ҫ�ٿ�һ��������ʡ��Щʱ����

`size()`���������˶�Σ�����������һ��? **�����æ����������б�Ҫ��**

ѭ���ڲ�ȡ��`strs.at(j)`��û��Ҫ����ģ�˳���������±�������ǳ������ġ�

ͬ���ģ�sFirst����Ҳ��������

```c++
string longestCommonPrefix(vector<string>& strs) 
{
    auto vecSize = strs.size();
    
    if( !vecSize )
    {
        return "";
    }
    
    if( vecSize ==1 )
    {
        return strs.at(0);
    }
    

    for( int i = 0; i < strs.at(0).size(); ++i)
    {
        for( int j = 1; j < vecSize; ++j )
        {
            if( strs.at(j).size() <= i || strs.at(j)[i] != strs.at(0)[i] )
            {
                return i == 0 ? "" : strs.at(0).substr(0, i);
            }
        }

    }
    
    return strs.at(0);
}

```

6ms��ֻ�ܻ���17.75%����Ϊ������˶���6ms

�Լ��벻����������Ż��ˣ����͸�Ʊ�𰸶Ա�һ��

[https://discuss.leetcode.com/topic/20991/accepted-c-6-lines-4ms/2](https://discuss.leetcode.com/topic/20991/accepted-c-6-lines-4ms/2)

��Ҫ��һ������Ӧ������substr�ϣ�����Ҳ�����ķ�ʽ������

```
string longestCommonPrefix(vector<string>& strs) {
    auto vecSize = strs.size();
    
    if( !vecSize )
    {
        return "";
    }
    
    string sPrefix = "";
    for( int i = 0; i < strs.at(0).size(); ++i)
    {
        for( int j = 1; j < vecSize; ++j )
        {
            if( strs.at(j).size() <= i || strs.at(j)[i] != strs.at(0)[i] )
            {
                return sPrefix;
            }
        }
        sPrefix += strs.at(0)[i];
    }
    
    return strs.at(0);
}
```

����6ms���ٸĵĻ�����ɶ��Ծͱ���ˡ�

��Ȼ�������޷������ġ������������ɡ�����

## ����

��������ѧ��`string.find`������

```c++
string longestCommonPrefix(vector<string>& strs) {
    auto vecSize = strs.size();
    
    if( !vecSize )
    {
        return "";
    }
    
    string sPrefix = "";
    for( int i = 0; i < strs.at(0).size(); ++i)
    {
        sPrefix += strs.at(0)[i];
        for( int j = 1; j < vecSize; ++j )
        {
            if( strs.at(j).find(sPrefix) != 0 )
            {
                return sPrefix.erase(i,1);
            }
        }
    }
    
    return strs.at(0);
}
```
