# 作业 03 - 第四章作业

(22/4/19) 其中第二题的第三问，等下次课后再做

1\. 考虑下面文法 G<sub>1</sub>:

\\[
\\begin{align}
& S \\to a \| \\land \| (T) \\\\
& T \\to T, S \| S
\\end{align}
\\]

(1) 消去 G<sub>1</sub> 的左递归. 然后, 对每个非终结符, 写出不带回溯的递归子程序.

(2) 经改写后的文法是否是 LL(1) 的? 给出它的预测分析表.


---

2\. 对下面的文法 G:

\\[
\\begin{align}
& E \\to TE' \\\\
& E' \\to +E \| \\varepsilon \\\\
& T \\to FT' \\\\
& T' \\to T \| \\varepsilon \\\\
& F \\to PF' \\\\
& F' \\to *F' \| \\varepsilon \\\\
& P \\to (E) \| a \| b \| \\land \\\\
\\end{align}
\\]

(1) 计算这个文法的每个非终结符的 FIRST 和 FOLLOW.

(2) 证明这个文法是 LL(1) 的.

(3) 构造它的预测分析表. 

(4) 构造它的递归下降分析程序.


---

3\. 下面文法中, 哪些是 LL(1) 的, 说明理由.

(1) \\(
\\begin{align}
& S \\to Abc \\\\
& A \\to a \| \\varepsilon \\\\
& B \\to b \| \\varepsilon \\\\
\\end{align}
\\)



(2) \\(
\\begin{align}
& S \\to Ab \\\\
& A \\to a \| B \| \\varepsilon \\\\
& B \\to b \| \\varepsilon \\\\
\\end{align}
\\)

