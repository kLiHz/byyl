# 作业 04 - 第五章作业

1\. 令文法 G<sub>1</sub> 为:

\\[
\\begin{align}
& E \\to E+T \| T \\\\
& T \\to T*F \| F \\\\
& F \\to (E) \| i
\\end{align}
\\]

试证明 \\(E + T \* F\\) 是它的一个句型, 指出这个句型的所有短语, 直接短语和句柄.

**解:**

短语: E+T\*F, T\*F \
直接短语: T\*F \
句柄: T\*F

---

2\. 考虑下面的表格结构文法 G<sub>2</sub>:

\\[
\\begin{align}
& S \\to a \| \\land \| (T) \\\\
& T \\to T, S \| S
\\end{align}
\\]

(1) 给出 \\( (a, (a, a)) \\) 和 \\( (((a, a), \\land , (a)), a) \\) 的最左和最右推导.

(2) 指出 \\( (((a,a), \\land, (a)), a) \\) 的规范归约及每一步的句柄. 根据这个规范归约, 给出 "移进 - 归约" 的过程, 并给出它的语法树自下而上的构造过程.

**解:**
(1)
最左推导:

\\( (a, (a, a)) \\): 

\\(
S \\Rightarrow (T) \\Rightarrow (T, S) \\Rightarrow (S, S) \\Rightarrow (a, (T)) 
\\Rightarrow (a, (T, S)) \\Rightarrow (a, (S, S)) \\Rightarrow (a, (a, S)) \\Rightarrow (a, (a, a))
\\)

\\( (((a, a), \\land , (a)), a) \\):

\\(
\\begin{split}
S 
     & \\Rightarrow (T) 
\\\\ & \\Rightarrow (T, S) 
\\\\ & \\Rightarrow (S, S)
\\\\ & \\Rightarrow ((T), S)
\\\\ & \\Rightarrow ((T, S), S) 
\\\\ & \\Rightarrow ((T, S, S), S) 
\\\\ & \\Rightarrow ((S, S, S), S) 
\\\\ & \\Rightarrow (((T), S, S), S) 
\\\\ & \\Rightarrow (((T, S), S, S), S) 
\\\\ & \\Rightarrow (((S, S), S, S), S) 
\\\\ & \\Rightarrow (((a, S), S, S), S)
\\\\ & \\Rightarrow (((a, a), S, S), S)
\\\\ & \\Rightarrow (((a, a), \\land, S), S)
\\\\ & \\Rightarrow (((a, a), \\land, (T)), S)
\\\\ & \\Rightarrow (((a, a), \\land, (S)), S)
\\\\ & \\Rightarrow (((a, a), \\land, (a)), S)
\\\\ & \\Rightarrow (((a, a), \\land, (a)), a)
\\end{split}
\\)

最右推导:

\\( (a, (a, a)) \\): 

\\(
S \\Rightarrow (T) \\Rightarrow (T, S) \\Rightarrow (T, (T)) \\Rightarrow (T, (T, S)) 
\\Rightarrow (T, (T, a)) \\Rightarrow (T, (S, a)) \\Rightarrow (T, (a, a)) \\Rightarrow(S, (a, a)) \\Rightarrow (a, (a, a)) 
\\)

\\( (((a, a), \\land , (a)), a) \\):

\\(
\\begin{split}
S 
     & \\Rightarrow (T) 
\\\\ & \\Rightarrow (T, a) 
\\\\ & \\Rightarrow (S, a)
\\\\ & \\Rightarrow ((T), a)
\\\\ & \\Rightarrow ((T, S), a) 
\\\\ & \\Rightarrow ((T, (T)), a) 
\\\\ & \\Rightarrow ((T, (S)), a) 
\\\\ & \\Rightarrow ((T, (a)), a) 
\\\\ & \\Rightarrow ((T, S, (a)), a) 
\\\\ & \\Rightarrow ((T, \\land, (a)), a) 
\\\\ & \\Rightarrow ((S, \\land, (a)), a) 
\\\\ & \\Rightarrow (((T), \\land, (a)), a) 
\\\\ & \\Rightarrow (((T, S), \\land, (a)), a) 
\\\\ & \\Rightarrow (((T, a), \\land, (a)), a) 
\\\\ & \\Rightarrow (((S, a), \\land, (a)), a) 
\\\\ & \\Rightarrow (((a, a), \\land, (a)), a) 
\\end{split}
\\)

---

5\. 考虑文法

\\[
\\begin{align}
& S \\to AS \| b \\\\
& A \\to SA \| a
\\end{align}
\\]

(1) 列出这个文法的所有 LR(0) 项目.

(2) 构造这个文法的 LR(0) 项目集规范族及识别活前缀的 DFA.

(3) 这个文法是 SLR 的吗? 若是, 构造出它的 SLR 分析表.

(4) 这个文法是 LALR 或 LR(1) 的吗?

