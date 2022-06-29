# 01 第二章作业

P36: 6, 7, 8, 9, 10, 11 (22/3/8)

---

6\. 令文法 G<sup>6</sup> 为

\\[
\\begin{split}
  & N \\to D \| ND \\\\
  & D \\to 0 \| 1 \| 2 \| 3 \| 4 \| 5 \| 6 \| 7 \| 8 \| 9
\\end{split}
\\]

(1) G<sup>6</sup> 的语言 L\(G<sup>6</sup>\) 是什么?


(2) 给出句子 0127, 34 和 568 的最左推导和最右推导.

**解:** 
(1) L\(G<sup>6</sup>\) 是由 0 ~ 9 十个数字构成的任意长度 (大于 0) 的字符串.

(2) 最左推导:

\\[
\\begin{align}
& N \\Rightarrow ND \\Rightarrow NDD \\Rightarrow NDDD \\Rightarrow DDDD 
    \\Rightarrow 0DDD \\Rightarrow 01DD \\Rightarrow 012D \\Rightarrow 0127 \\\\
& N \\Rightarrow ND \\Rightarrow DD \\Rightarrow 3D \\Rightarrow  34 \\\\
& N \\Rightarrow ND \\Rightarrow NDD \\Rightarrow DDD 
    \\Rightarrow 5DD \\Rightarrow 56D \\Rightarrow 568
\\end{align}
\\]

最右推导:

\\[
\\begin{align}
& N \\Rightarrow ND \\Rightarrow N7 \\Rightarrow ND7 \\Rightarrow ND27
    \\Rightarrow N127 \\Rightarrow D127 \\Rightarrow 0127 \\\\
& N \\Rightarrow ND \\Rightarrow N4 \\Rightarrow D4 \\Rightarrow  34 \\\\
& N \\Rightarrow ND \\Rightarrow N8 \\Rightarrow ND8 \\Rightarrow N68 
    \\Rightarrow D68 \\Rightarrow 568
\\end{align}
\\]

---

7\. 写一个文法, 使其语言是奇数集, 且每个奇数不以 0 开头.

**解:** 
文法 G(S):

\\[
\\begin{split}
& S \\to O \| AO  \\\\
& O \\to 1 \| 3 \| 5 \| 7 \| 9  \\\\
& A \\to AD \| N  \\\\
& N \\to 2 \| 4 \| 6 \| 8 \| O  \\\\
& D \\to 0 \| N  \\\\
\\end{split}
\\]

---

8\. 令文法为

\\[
\\begin{split}
& E \\to  T  \| E + T \| E - T  \\\\
& T \\to  F  \| T * F \| T / F \\\\
& F \\to (E) \| \\text{i} \\\\
\\end{split}
\\]

(1) 给出 i + i * i, i * (i + i) 的最左推导和最右推导;

(2) 给出 i + i + i, i + i * i 和 i - i - i 的语法树.

**解:**

(1)
**最左推导:**

**i + i * i**: 

\\( \\begin{split}
E & \\Rightarrow E + T \\Rightarrow T + T \\Rightarrow F + T \\Rightarrow i + T 
    \\Rightarrow i + T * F \\Rightarrow i + F * F \\Rightarrow i + i * i
\\end{split} \\)

**i * (i + i)**: 

\\( \\begin{split}
E & \\Rightarrow T \\Rightarrow T * F \\Rightarrow F * F \\Rightarrow i * F
    \\Rightarrow i * (E) \\Rightarrow i + (E + T) \\Rightarrow i + (T + T)
    \\Rightarrow i * (F + F) \\Rightarrow i * (i + i)
\\end{split} \\)


**最右推导:**

**i + i * i**: 

\\( \\begin{split}
E & \\Rightarrow E + T \\Rightarrow E + T * F \\Rightarrow E + F * i \\Rightarrow E + i * i
    \\Rightarrow T + i * i \\Rightarrow F + i * i \\Rightarrow i + i * i
\\end{split} \\)

**i * (i + i)**: 

\\( \\begin{split}
E & \\Rightarrow T \\Rightarrow T * F \\Rightarrow F * F \\Rightarrow F * (E)
    \\Rightarrow F * (E + T) \\Rightarrow F * (E + F) \\Rightarrow F * (E + i)
\\\\ &
    \\Rightarrow F * (T + i) \\Rightarrow F * (F + i) \\Rightarrow F * (i + i)
    \\Rightarrow i * (i + i)
\\end{split} \\)

(2)

| i + i + i | i + i * i | i - i - i |
| :-------: | :-------: | :-------: |
|![8-2-1](assets/8-2-1.svg)|![8-2-2](assets/8-2-2.svg)|![8-2-3](assets/8-2-3.svg)|


---

9\. 证明下面的文法是二义的:

\\[
S \\to iSeS \| iS \| i
\\]

**证:**
对于句子 iiiei 有两个语法树

\\[
\\begin{align}
& S \\Rightarrow iSeS \\Rightarrow iSei  \\Rightarrow iiSei \\Rightarrow iiiei
\\\\
& S \\Rightarrow iS   \\Rightarrow iiSeS \\Rightarrow iiSei \\Rightarrow iiiei
\\end{align}
\\]

---

10\. 把下面文法改写为无二义的:

\\[
S \\to SS | (S) | ()
\\]

**解:** 
\\[
\\begin{split}
& S \\to TS | T
\\\\
& T \\to (S) | ()
\\end{split}
\\]

---

11\. 给出下面语言的相应文法

\\[
\\begin{align}
L\_1 & = \\{a\^n b\^n c\^i      \| n \geq 1, i \geq 0\\} \\\\
L\_2 & = \\{a\^i b\^n c\^n      \| n \geq 1, i \geq 0\\} \\\\
L\_3 & = \\{a\^n b\^n a\^m b\^m \| n, m \geq 0       \\} \\\\
L\_4 & = \\{1\^n 0\^m 1\^m 0\^n \| n, m \geq 0       \\} \\\\
\\end{align}
\\]

**解:** 

L<sub>1</sub>:

\\(
\\begin{split}
& S \\to AC \\\\
& A \\to aAb \| ab \\\\
& C \\to Cc \| \\varepsilon
\\end{split}
\\)

L<sub>2</sub>:

\\(
\\begin{split}
& S \\to AB \\\\
& A \\to aA \| \\varepsilon \\\\
& B \\to bBc \| bc
\\end{split}
\\)

L<sub>3</sub>:

\\(
\\begin{split}
& S \\to AB \\\\
& A \\to aAb \| \\varepsilon \\\\
& B \\to aBb \| \\varepsilon
\\end{split}
\\)

L<sub>4</sub>:

\\(
\\begin{split}
& S \\to A \| B \\\\
& A \\to 1B0 \| A \\\\
& B \\to 0B1 \| \\varepsilon
\\end{split}
\\)

