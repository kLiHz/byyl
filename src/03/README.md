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

**解:**

(1) G<sub>1</sub>':
\\[
\\begin{align}
& S \\to a \| \\land \| (T) \\\\
& T \\to ST' \\\\
& T' \\to ,ST'  \| \\varepsilon 
\\end{align}
\\]


```none
PROCEDURE S;
BEGIN 
    IF SYM = 'a' OR SYM = '∧' THEN ADVANCE; 
    ELSE IF SYM = '(' THEN 
    BEGIN
        ADVANCE; 
        T;
        IF SYM = ')' THEN ADVANCE
        ELSE ERROR
    END
    ELSE ERROR
END

PROCEDURE T;
BEGIN
    S;T'
END

PROCEDURE T';
BEGIN
    IF SYM = ',' THEN
    BEGIN
        ADVANCE;
        S;T'
    END
END
```

其中 `SYM` 是输入串指针 IP 所指的符号; \
`ADVAMCE` 是把 IP 调至下一个输入符号; \
`ERROR` 是出错诊察程序.

(2)

| 非终结符 | FIRST | FOLLOW |
| :---: | :---: | :---: |
| S  | {`a`, `∧`, `(`} | {#, `,`, `)`} |
| T  | {`a`, `∧`, `(`} | {`)`} |
| T' | {`,`, `ε`} | {`)`} |


预测分析表

| | `a` | `∧` | `(` | `)` | `,` | # |
|:---:|:---:| :---:|:---:| :---:|:---:| :---:|
|S |S→a|S→∧|S→(T)| | | | |
|T |T→ST'|T→ST'|T→ST'| | | | |
|T'| | | |T'→ε|T'→,ST'| |

构造的预测分析表中没有多重入口, 所以修改后的 G<sub>1</sub>' 是 LL(1) 文法.

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

**解:**

(1) 

| 非终结符 | FIRST | FOLLOW |
|:---:|:---:|:---:|
| E  | {`(`, `a`, `b`, `∧`}     | {#, `)`} |
| E' | {`+`, `ε`}                 | {#, `)`} |
| T  | {`(`, `a`, `b`, `∧`}     | {`+`, `)`, #} |
| T' | {`(`, `a`, `b`, `∧`, `ε`} | {`+`, `)`, #} |
| F  | {`(`, `a`, `b`, `∧`}     | {`(`, `a`, `b`, `∧`, `+`, `)`, #} |
| F' | {`*`, `ε`}                 | {`(`, `a`, `b`, `∧`, `+`, `)`, #} |
| P  | {`(`, `a`, `b`, `∧`}     | {`*`, `(`, `a`, `b`, `∧`, `+`, `)`, #} |

(2) 考虑下列产生式:

\\[
\\begin{align}
& E' \\to +E \| \\varepsilon \\\\
& T' \\to T \| \\varepsilon \\\\
& F' \\to *F' \| \\varepsilon \\\\
& P \\to (E) \| a \| b \| \\land \\\\
\\end{align}
\\]

\\[
\\begin{align}
FIRST(+E)   \\cap FIRST ( \\varepsilon ) & = \\{ + \\} \\cap  \\{ \\varepsilon \\}                     = \\phi \\\\
FIRST(+E)   \\cap FOLLOW(E')             & = \\{ + \\} \\cap  \\{\\text{\#}, )\\}                      = \\phi \\\\
FIRST(T)    \\cap FIRST ( \\varepsilon ) & = \\{ (, a, b, \\land \\} \\cap \\{ \\varepsilon \\}        = \\phi \\\\
FIRST(T)    \\cap FOLLOW(T')             & = \\{ (, a, b, \\land \\} \\cap \\{ +, ), \\text{\#} \\}    = \\phi \\\\
FIRST(\*F') \\cap FIRST ( \\varepsilon ) & = \\{ \* \\} \\cap \\{  \\varepsilon \\}                    = \\phi \\\\
FIRST(\*F') \\cap FOLLOW(F')             & = \\{ \* \\} \\cap \\{(, a, b, \\land, +, ), \\text{\#} \\} = \\phi \\\\
FIRST((E))  \\cap FIRST (a) \\cap FIRST(b) \\cap FIRST(\\land) & = \\phi &\\\\
\\end{align}
\\]

(3)

|  | + | * | ( | ) | a | b | ∧ | # |
|:---:| :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| E  |  | | E→TE' | | E→TE' |E→TE' |E→TE' | | 
| E' | E'→+E | || E'→ε | ||| E'→ε |
| T  | ||T→FT'| | T→FT'|T→FT'|T→FT'||
| T' | T'→ ε| | T'→ T| T'→ ε|T'→ T|T'→ T|T'→ T| T'→ ε|
| F  | | |  F→PF' ||F→PF' |F→PF' |F→PF' |
| F' | F'→ε| F'→*F'|F'→ε|F'→ε|F'→ε|F'→ε|F'→ε|F'→ε|
| P  | ||P→(E) | | P→a | P→b |P→∧ ||

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

(1) 文法不含左递归

计算 FIRST 和 FOLLOW 集合

FIRST(S) = {a, b, c} \
FIRST(A) = {a, ε} \
FIRST(B) = {b, ε} \
FOLLOW(S) = { \# } \
FOLLOW(A) = {b, c} \
FOLLOW(B) = {c}

满足 LL(1) 文法的三个条件.
故该文法是 LL(1) 文法.

(2) 文法不含左递归

计算 FIRST 和 FOLLOW 集合

FIRST(S) = {a, b} \
FIRST(A) = {a, b, ε} \
FIRST(B) = {b, ε} \
FOLLOW(S) = { \# } \
FOLLOW(A) = {b} \
FOLLOW(B) = {b}

由于 A → a | B | ε, FIRST(A) 中含有 ε, FIRST(A) ∩ FOLLOW(A) = {b}

所以该文法不是 LL(1) 文法.
