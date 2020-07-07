---
title: "競プロ：2問、テキスト：正規表現"
date: 2020-07-07T00:23:47+09:00
draft: false
---

# 本日の実施事項

1. 【競プロ】AIZU Online Judge：2問
2. 【テキスト】独習python：正規表現 P.208~210
3. 【その他】Qiita記事（Prologで論理パズル）を読む
4. 【読み物】Webとプログラミングのきほんのきほん：P.~

***

## 【競プロ】AIZU Online Judge：2問
### [ITP1_7_B:   How many ways?](http://judge.u-aizu.ac.jp/onlinejudge/description.jsp?id=ITP1_7_B)

問題文にしたがって素直に解いた。

```python:title
while True:
    n,x = map(int,input().split(" "))
    if n == 0 and x == 0:
        break
    countn = 0
    for i in range(1,n-1):
        for j in range(i+1,n):
            for k in range(j+1,n+1):
                if i+j+k == x:
                    countn += 1
    print(countn)
```
### [ITP1_7_C: Spreadsheet](http://judge.u-aizu.ac.jp/onlinejudge/description.jsp?id=ITP1_7_C)

あまりきれいに書けてないけど。
最初はリスト同士の足し算で解こうと思ったが、結局要素を足し合わせていくことにした。

```python:title
r,c = map(int,input().split(" "))
sumall = [0]*(c+1)
for i in range(r):
    x = list(map(int,input().split(" ")))
    sumx = sum(x)
    for j in range(c):
        sumall[j] += x[j]
        # print(sumall)
    sumall[c] += sumx
    newl = " ".join(map(str,x))
    print(newl + " " + str(sumx))
lastl = " ".join(map(str,sumall))
print(lastl)
```

***
## 【テキスト】独習python：正規表現 P.209~21

### 複数文字の一致

\[]の中に一致させたい文字すべてを,で区切って入力。例えばt[w,o]oのように

例：

```python:
import re
string = "Two two too ton tan tee tea tao."
m = re.findall("t[w,o]o", string, re.IGNORECASE)
print(m)
```

出力結果：
> ['Two', 'two', 'too']

<br>
<br>

### 数値との一致

python：\dを使う

例：

```python:
import re
line = "123 hi 34 hello."
m = re.findall("\d", line, re.IGNORECASE)
print(m)
```

出力結果：

> ['1', '2', '3', '3', '4']

<br>
<br>


### 繰り返し

アスタリスク\*を使用する
ちなみに任意の文字に一致するピリオド.と組み合わせることで使い勝手が良くなる。
ただし、\*は貪欲なのでできるだけ長い文字列に一致する。
\*?と表現することで非貪欲（できるだけ文字数が少なくなる）にできる

例：

```python:
import re
t = "__one__ __two__ __three__"
found = re.findall("__.*?__", t)
for match in found:
    print(match)
```

出力結果：

> __one__
> __two__
> __three__

<br>
<br>


### エスケープ

特別な文字をエスケープして本来の文字に一致させたい場合バックスラッシュ\をつける。

例：

```python:
import re
line = "my $ loves $ and $"
m = re.findall("\\$", line, re.IGNORECASE)
print(m)
```

出力結果：

> ['$', '$', '$']

<br>

参考：正規表現ツールまとめ
https://qiita.com/aqril_1132/items/c185c7ad84c129e5a2df

***

## ひとこと

* 学習計画ひきなおす
* 今回からMarkDown使ってHugo使ってブログ書いているが、めちゃくちゃ楽。前までMediumで書いていたがなんだか疲れてたので

## 各勉強の目的

【競プロ】効率よく、処理の重たくないプログラムを書く。半分はモチベーションのため。
【テキスト、読み物】基礎を身につける
【その他】メンターからの課題、Inputなど

+プロジェクト、アプリ作り、転職サイトのコーディングテストをこなしていきたい
