## ����


https://leetcode.com/problems/palindrome-number/


## ��Ŀ





## ����






## ��������






## ����






```c++

//���������������棬���Ը����ؼ���

//����һ
class Solution {
public:
    bool isPalindrome(int x) {
        if(x<0)
            return false;
        vector<int> v;
        int num_sum = 0;
        while(x != 0){
            v.push_back(x % 10);
            x /= 10;
            ++num_sum;
        }
        for(int i=0; i<(num_sum/2); ++i){
            if(v[i] != v[num_sum-1-i])
                return false;
        }
        return true;
    }
};

//�����
class Solution {
public:
    bool isPalindrome(int x) {
        if(x < 0)
		return false;
	int c = 0;
	int temp = x;
	while(temp > 0){
		c = c * 10 + (temp % 10);
		temp /= 10;
	}
	if(c == x)
		return true;
	else
		return false;
    }
};


```



## ����

![](https://github.com/githubwoniu/learnprogram/blob/master/image/erweima.png)

PS: �뱣����ά�����ӣ��Ա�����˲��������лл��