---
layout: post
title: LeetCode Two Sum
---

今天面试问了个Two Sum的问题，太紧张没想出\\(O(n)\\)的解决办法，实际上算法思想还是比较简单的，也难怪面试官绝得我太水。。。

1.首先给出蛮力法，时间复杂度为\\(O(n^2)\\)
<pre><code>
	TwoSumBruce(A, target):
		首先排个序
		For i = 0 to n:
			For j = i+1 to n:
				if A[i] + A[j] == target: return pair(i,j) 
		return NULL
</code></pre>

2.然后是\\(O(nlogn)\\)的方法
<pre><code>
	vector<int> twoSum(vector<int> &numbers, int target) {
        // Start typing your C/C++ solution below
        // DO NOT write int main() function
        vector<Node> a;
        for(int i = 0; i < numbers.size(); i++)
            a.push_back(Node(numbers[i], i + 1));
        sort(a.begin(), a.end(), compare);
        int i = 0;
        int j = numbers.size() - 1;
        while(i < j)
        {
            int sum = a[i].val + a[j].val;
            if (sum == target)
            {
                vector<int> ret;
                int minIndex = min(a[i].index, a[j].index);
                int maxIndex = max(a[i].index, a[j].index);
                ret.push_back(minIndex);
                ret.push_back(maxIndex);
                return ret;
            }
            else if (sum < target)
                i++;
            else
                j--;
        }
    }
</code></pre>

3.然后是面试官提示我的用空间换时间的哈希方法，时间复杂度是\\(O(n)\\)
<pre><code>
    vector<int> twoSum(vector<int> &numbers, int target) {
        // Start typing your C/C++ solution below
        // DO NOT write int main() function
        hash_map<int, int> intHash;
        vector<int>::iterator iter;
        vector<int> result;
        for (iter = number.begin; iter != number.end(); ++iter)
            intHash[*iter] = target - *iter;
        int i = 0
        for (; i < numbers.size(); ++i)
            if (intHash[target - numbers[i]] == numbers[i]) break;
        int j = 0
        for (; j < numbers.size(); ++i)
            if (numbers[j] == target - numbers[i]) break;
        result.push_back(min(i, j));
        result.push_back(max(i, j));
        return result;
    }
</code></pre>

{{ page.date | date_to_string }}