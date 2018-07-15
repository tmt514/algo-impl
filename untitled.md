---
description: 描述許多字串問題～
---

# 字串問題

## 迴文子字串計數 Counting Palindrome Substrings

{% tabs %}
{% tab title="題目敘述 Description" %}
給定一個長度為 _**N**_ 的字串 _**S**_，輸出所有是迴文的子字串數量。
{% endtab %}

{% tab title="解題格式" %}
#### C++

```cpp
int solve(int N, string S);
```

#### Python

```python
# N: int
# S: String
def solve(N, S):
    pass
```
{% endtab %}

{% tab title="範例 Examples" %}
#### Sample Input 1

```text
aa
```

#### Sample Output 1

```text
3
```
{% endtab %}
{% endtabs %}

### 解題概念 1

暴力枚舉所有左界和右界，然後硬是判斷他是不是迴文字串。

{% tabs %}
{% tab title="Disclaimer" %}
不要偷看答案，自己先想一次！
{% endtab %}

{% tab title="C++" %}
```cpp
bool is_palindrome(string S) {
    for (int l = 0, r = (int)S.size() - 1; l < r; l++, r--)
        if (S[l] != S[r])
            return false;
    return true;
}

int solve(int N, string S) {
    for (int l = 0; l < N; l++)
        for (int r = l; r < N; r++)
            cnt += is_palindrome(S.substr(l, r-l+1));
}
```

#### 分析

`is_palindrome`所花費的時間是
{% endtab %}

{% tab title="Python" %}

{% endtab %}
{% endtabs %}

