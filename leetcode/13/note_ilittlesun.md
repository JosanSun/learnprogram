## ����


https://leetcode.com/problems/roman-to-integer/


## ��Ŀ





## ����






## ��������






## ����






```c++

class Solution {
public:
    int romanToInt(string s) {
        map<char, int> m;
        m['I'] = 1;
        m['V'] = 5;
        m['X'] = 10;
        m['L'] = 50;
        m['C'] = 100;
        m['D'] = 500;
        m['M'] = 1000;
        int num = m[s[0]];
        for(int i = 1;i < s.length();++i){
            if(m[s[i]]<=m[s[i-1]])
                num = num + m[s[i]];
            else
                num = num + m[s[i]] - 2 * m[s[i-1]];
        }
        return num;
    }
};



```



## ����

![](https://github.com/githubwoniu/learnprogram/blob/master/image/erweima.png)

PS: �뱣����ά�����ӣ��Ա�����˲��������лл��
