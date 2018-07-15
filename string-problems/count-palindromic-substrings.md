---
description: 'Given a string of length N, count the number of palindromic substrings.'
---

# 迴文子字串計數 Count Palindromic Substrings

## 題目敘述

給定一個長度為 _**N**_ 的字串 _**S**_，輸出所有是迴文的子字串數量。

### 解題格式

{% tabs %}
{% tab title="C++" %}
```cpp
// N = S.size()
int solve(string S);
```
{% endtab %}

{% tab title="Python" %}
```python
# S: String of length N.
def solve(S):
    # Write your solution here.
    pass
```
{% endtab %}
{% endtabs %}

### 範例測資

#### Sample Input 1

```text
aa
```

#### Sample Output 1

```text
3
```

## 題源

* [Leetcode 647. Palindromic Substrings](https://leetcode.com/problems/palindromic-substrings/description/)

{% hint style="danger" %}
以下有雷，請小心。
{% endhint %}

## 解題概念 1

暴力枚舉所有左界和右界，然後硬是判斷他是不是迴文字串。

### 參考程式碼

#### C++

太簡單了請自己寫XD

#### Python

```python
def solve(S):
    N = len(S)
    return sum(1 for l in range(N) for r in range(l+1, N+1) if S[l:r] == S[l:r][::-1])
```

### 分析

枚舉左右界花了 $$\Theta(N^2)$$, 判斷是否是回文花了 $$O(N)$$，所以總共是 $$O(N^3)$$。

## 解題概念 2

先來一個有用的廢話：每浪費 60 秒，就有一分鐘過去了。然後你就會發現以下這個觀察基本上也會是廢話：

{% hint style="info" %}
如果一個字串是迴文字串，那要嘛他長度為 1，要嘛同時把他最左邊和最右邊的字元去掉仍然是個迴文字串。
{% endhint %}

但這個廢話讓我們想到了：如果要檢查 `S[i..j]` 是不是迴文，我們不需要花費 $$O(N)$$ 時間重新檢查，只要檢查 `S[i+1..j]` 是不是迴文就好！這是一個子問題（因為長度變短了！）

於是乎，我們可以得到以下的動態規劃演算法：

