# 逻辑公理系统及证明实例
<center>作者： FrantzBekoic</center>

<div style="page-break-after: always;"></div>

## 1. 命题逻辑的推理证明

### 1.1 公理系统及推理规则——逻辑推演的基石

#### 1.1.1 常见公理系统
常见公理系统包括 Freig 公理系统、Lukasiewicz 公理系统以及 Russel 公理系统，若无特别标注，本课程所述内容默认为 Lukasiewicz 公理系统，包含如下三个公理事实：

| 公理 | 公式表达 | 名称 |
| :---: | :--- | :---: |
| $\mathcal{A}_1$ | $Q \to (P \to Q)$ | 肯定后件律 |
| $\mathcal{A}_2$ | $(P \to (Q \to R)) \to ((P \to Q) \to (P \to R))$ | 蕴含词分配律 |
| $\mathcal{A}_3$ | $(\neg Q \to \neg P) \to (P \to Q)$ | 换位律 |

#### 1.1.2 MP规则与形式推演

**Def:** 形式推演

设 $\Gamma$ 为公式集，若公式序列 $A_{1},A_{2},...,A_{n}$ 中的每个公式 $A_{i}$ 满足以下条件之一：

1. $A_{i}$ 是公理
2. $A_{i} \in \Gamma$
3. $\exists j,k < i$, 若有 $A_{j}$、$A_{k}=A_{j} \to A_{i}$ 均成立，则 $A_{i}$ 成立

则该序列为公式 $A_{n}$ 从公式集 $\Gamma$ 的一个推演，记为 **$\Gamma \vdash A_{n}$**。
其中 $\Gamma$ 称为推演的**前提集**，$A_{n}$ 称为**结论**。

除此之外我们常常用两个恒等变形：$Q \vee R \equiv \neg Q \to R$ 和 $Q \wedge R \equiv \neg(Q \to \neg R)$，这在我们后面的证明过程中非常重要。

## 2. 定理描述与形式化证明实例

在这个部分我们将由易入难地证明公理系统中常见的结论，前面的定理往往会作为结论运用于后面定理证明，希望大家仔细体会证明过程，掌握构造的方法和思路。

当然考场上并不会直接丢给你们一个形式推演要求证明，往往会给出可直接使用的推论，所以大家不必太担心，掌握构造手法即不难。

> <font color="red">**本部分最重要的是：不要想当然！即使是很显然的结论也不要贸然使用，谨记三个公理和MP规则。**</font>
> 
> <font color="orange">声明：下述证明过程中证据部分的定理仅为了简便证明过程而使用，未经证明不可直接使用，请勿模仿。</font>

### 2.1 $P \to Q , Q \to R \vdash P \to R$ （传递律）

| 步骤 | 证明过程 | 证据 |
| :---: | :--- | :--- |
| $A_1 =$ | $(Q \to R) \to (P \to (Q \to R))$ | <font color="blue">$\mathcal{A}_1$</font> |
| $A_2 =$ | $Q \to R$ | <font color="blue">$A_{2} \in \Gamma$</font> |
| $A_3 =$ | $P \to (Q \to R)$ | <font color="blue">$A_{1} = A_{2} \to A_{3}$</font> |
| $A_4 =$ | $(P \to (Q \to R )) \to ((P \to Q) \to (P \to R))$ | <font color="blue">$\mathcal{A}_2$</font> |
| $A_5 =$ | $(P \to Q) \to (P \to R)$ | <font color="blue">$A_4 = A_3 \to A_5$</font> |
| $A_6 =$ | $P \to Q$ | <font color="blue">$A_{6} \in \Gamma$</font> |
| $A_7 =$ | $P \to R$ | <font color="blue">$A_5 = A_6 \to A_7$</font> |

### 2.2 $\vdash (P \to (Q \to R )) \to (Q \to ( P \to R ))$ （换前律）

| 步骤 | 证明过程 | 证据 |
| :---: | :--- | :--- |
| $A_1 =$ | $(P \to (Q \to R )) \to ((P \to Q) \to (P \to R))$ | <font color="blue">$\mathcal{A}_2$</font> |
| $A_2 =$ | $((P \to Q) \to (P \to R)) \to (Q \to ((P \to Q) \to (P \to R)))$ | <font color="blue">$\mathcal{A}_1$</font> |
| $A_3 =$ | $(Q \to ((P \to Q) \to (P \to R))) \to ((Q \to (P \to Q)) \to (Q \to (P \to R)))$ | <font color="blue">$\mathcal{A}_2$</font> |
| $A_4 =$ | $(P \to (Q \to R )) \to ((Q \to (P \to Q)) \to (Q \to (P \to R)))$ | <font color="blue">$A_{1},A_{2},A_{3} \vdash A_{4}$</font> |
| $A_5 =$ | $(P \to (Q \to R )) \to ((Q \to (P \to Q)) \to (Q \to (P \to R))) \to ((P \to (Q \to R )) \to (Q \to (P \to Q)))\to ((P \to (Q \to R )) \to (Q \to (P \to R))) $ | <font color="blue">$\mathcal{A}_2$</font> |
| $A_6 =$ | $((P \to (Q \to R )) \to (Q \to (P \to Q)))\to ((P \to (Q \to R )) \to (Q \to (P \to R))) $ | <font color="blue">$A_{5} = A_{4} \to A_{6}$</font> |
| $A_7 =$ | $Q \to (P \to Q)$ | <font color="blue">$\mathcal{A}_1$</font> |
| $A_8 =$ | $(Q \to (P \to Q)) \to ((P \to (Q \to R )) \to (Q \to (P \to Q)))$ | <font color="blue">$\mathcal{A}_2$</font> |
| $A_9 =$ | $(P \to (Q \to R )) \to (Q \to (P \to Q))$ | <font color="blue">$A_{8}=A_{7} \to A_{9}$</font> |
| $A_{10} =$ | $(P \to (Q \to R )) \to (Q \to ( P \to R ))$ | <font color="blue">$A_{6}=A_{9} \to A_{10}$</font> |

### 2.3 $\vdash (Q \to R) \to ((P \to Q) \to (P \to R)) $（前提加入）

| 步骤 | 证明过程 | 证据 |
| :---: | :--- | :--- |
| $A_{1} =$ | $(Q \to R) \to (P \to (Q \to R))$ | <font color="blue">$\mathcal{A}_1$</font> |
| $A_{2} =$ | $(P \to (Q \to R)) \to ((P \to Q) \to (P \to R))$ | <font color="blue">$\mathcal{A}_2$</font> |
| $A_{3} =$ | $(Q \to R) \to ((P \to Q) \to (P \to R))$ | <font color="blue">$A_{1},A_{2} \vdash A_{3}$</font> |

### 2.4 $\vdash (P \to Q) \to ((Q \to R) \to (P \to R))$ (换前律推论)

| 步骤 | 证明过程 | 证据 |
| :---: | :--- | :--- |
| $A_{1} =$ | $(Q \to R) \to ((P \to Q) \to (P \to R))$ | <font color="blue">$\vdash (Q \to R) \to ((P \to Q) \to (P \to R))$</font> |
| $A_{2} =$ | $((Q \to R) \to ((P \to Q) \to (P \to R))) \to ((P \to Q) \to ((Q \to R) \to (P \to R))) $ | <font color="blue">$\vdash (P \to (Q \to R )) \to (Q \to ( P \to R ))$</font> |
| $A_{3} =$ | $(P \to Q) \to ((Q \to R) \to (P \to R))$ | <font color="blue">$A_{1},A_{2} \vdash A_{3}$</font> |

> 上面的做法仅限于我们已知2.3结论的情况下，考试时如果要证明需要完整复现2.2和2.3的证明过程。不过鉴于2.2证明过程较长一般会直接给出，此时写全2.3证明过程即可。

### 2.5 $$\vdash ((P \to Q) \to (P \to R)) \to (P \to (Q \to R))$$ ($\mathcal{A}_2$的逆命题)

<font color="red">**分析：**</font>
看到 $(P \to (Q \to R))$ 要想到换前，即证 $((P \to Q) \to (P \to R)) \to (Q \to (P \to R))$，注意到两者拥有相同的后件，且前件结构类似 $Q \to (P \to Q)$ ,容易想到用 $\mathcal{A}_2$ 的推论构造 $((P \to Q) \to (P \to R)) \to ((Q \to (P \to Q)) \to (Q \to (P \to R)))$ ,此时再用一次换前即可证明。本质也就是定理 2.4 的证明过程。

| 步骤 | 证明过程 | 证据 |
| :---: | :--- | :--- |
| $A_{1} =$ | $((P \to Q) \to (P \to R)) \to (Q \to(((P \to Q) \to (P \to R))))$ | <font color="blue">$\mathcal{A}_1$</font> |
| $A_{2} =$ | $(Q \to((P \to Q) \to (P \to R))) \to ((Q \to (P \to Q)) \to (Q \to (P \to R))) $ | <font color="blue">$\mathcal{A}_2$</font> |
| $A_{3} =$ | $((P \to Q) \to (P \to R)) \to ((Q \to (P \to Q)) \to (Q \to (P \to R)))$ | <font color="blue">$A_{1},A_{2} \vdash A_{3}$</font> |
| $A_{4} =$ | $(((P \to Q) \to (P \to R)) \to ((Q \to (P \to Q)) \to (Q \to (P \to R)))) \to ((Q \to (P \to Q)) \to (((P \to Q) \to (P \to R)) \to (Q \to (P \to R))))$ | <font color="blue">$\begin{aligned} \vdash (P \to (Q \to R )) \\ \to (Q \to ( P \to R )) \end{aligned}$</font> |
| $A_{5} =$ | $(Q \to (P \to Q)) \to (((P \to Q) \to (P \to R)) \to (Q \to (P \to R)))$ | <font color="blue">$A_{4}=A_{3} \to A_{5}$</font> |
| $A_{6} =$ | $Q \to (P \to Q)$ | <font color="blue">$\mathcal{A}_1$</font> |
| $A_{7} =$ | $((P \to Q) \to (P \to R)) \to (Q \to (P \to R))$ | <font color="blue">$A_{5}=A_{6} \to A_{7}$</font> |
| $A_{8} =$ | $(Q \to (P \to R)) \to (P \to (Q \to R))$ | <font color="blue">$\begin{aligned} \vdash (P \to (Q \to R )) \\ \to (Q \to ( P \to R )) \end{aligned}$</font> |
| $A_{9} =$ | $((P \to Q) \to (P \to R)) \to (P \to (Q \to R))$ | <font color="blue">$A_{7},A_{8} \vdash A_{9}$</font> |

### 2.6 $$\vdash Q \to Q$$ (非常重要的结论)

<font color="red">**分析：**</font>
借助本题希望大家掌握一些基本的构造思想。首先看到一个结论，如果前件和后件的结构均不能与公理中的某个部分产生联系，则把整个部分作为后件来构造。自然的想到 $Q \to (Q \to Q)$ （$\mathcal{A}_{1}$的变形），此时虽然后件得到了我们想要的形式，但是前件依然无从下手,继续延续嵌套构造的思路。注意到 $Q \to (Q \to Q)$ 和 $Q \to Q$ 拥有相同的前件，尝试用 $\mathcal{A}_{2}$ 拼凑，得到 $Q \to ((Q \to Q) \to Q)$ ,根据 $\mathcal{A}_{1}$ 则证明完毕。

| 步骤 | 证明过程 | 证据 |
| :---: | :--- | :--- |
| $A_{1} =$ | $Q \to ((Q \to Q) \to Q)$ | <font color="blue">$\mathcal{A}_{1}$</font> |
| $A_{2} =$ | $(Q \to ((Q \to Q) \to Q)) \to ((Q \to (Q \to Q)) \to (Q \to Q))$ | <font color="blue">$\mathcal{A}_{2}$</font> |
| $A_{3} =$ | $(Q \to (Q \to Q)) \to (Q \to Q)$ | <font color="blue">$A_{2} = A_{1} \to A_{3}$</font> |
| $A_{4} =$ | $Q \to (Q \to Q)$ | <font color="blue">$\mathcal{A}_{1}$</font> |
| $A_{5} =$ | $Q \to Q$ | <font color="blue">$A_{3}=A_{4} \to A_{5}$</font> |

### 2.7 $$\vdash \neg \neg Q \to Q$$

| 步骤 | 证明过程 | 证据 |
| :---: | :--- | :--- |
| $A_{1} =$ | $\neg \neg Q \to (\neg \neg \neg \neg Q \to \neg \neg Q)$ | <font color="blue">$\mathcal{A}_{1}$</font> |
| $A_{2} =$ | $((\neg \neg \neg \neg Q \to \neg \neg Q) \to (\neg Q \to \neg \neg \neg Q))$ | <font color="blue">$\mathcal{A}_{3}$</font> |
| $A_{3} =$ | $((\neg Q \to \neg \neg \neg Q) \to (\neg \neg Q \to Q))$ | <font color="blue">$\mathcal{A}_{3}$</font> |
| $A_{4} =$ | $\neg \neg Q \to (\neg \neg Q \to Q)$ | <font color="blue">$A_{1},A_{2},A_{3} \vdash A_{4}$</font> |
| $A_{5} =$ | $(\neg \neg Q \to (\neg \neg Q \to Q)) \to ((\neg \neg Q \to \neg \neg Q) \to (\neg \neg Q \to Q))$ | <font color="blue">$\mathcal{A}_2$</font> |
| $A_{6} =$ | $(\neg \neg Q \to \neg \neg Q) \to (\neg \neg Q \to Q)$ | <font color="blue">$A_{5} = A_{4} \to A_{6}$</font> |
| $A_{7} =$ | $\neg \neg Q \to \neg \neg Q$ | <font color="blue">$\vdash Q \to Q$</font> |
| $A_{8} =$ | $\neg \neg Q \to Q$ | <font color="blue">$A_{6} = A_{7} \to A_{8}$</font> |

### 2.8 $\vdash Q \to \neg \neg Q$

| 步骤 | 证明过程 | 证据 |
| :---: | :--- | :--- |
| $A_{1} =$ | $(\neg \neg \neg Q \to \neg Q) \to (Q \to \neg \neg Q)$ | <font color="blue">$\mathcal{A}_{3}$</font> |
| $A_{2} =$ | $\neg \neg \neg Q \to \neg Q$ | <font color="blue">$\vdash \neg \neg Q \to Q$</font> |
| $A_{3} =$ | $Q \to \neg \neg Q$ | <font color="blue">$A_{1} = A_{2} \to A_{3}$</font> |

> 借助2.7和2.8说明一个注意点：形式证明里的否定符号不能随意的添加或删减，与语义证明不相同。

### 2.9 $\vdash (\neg \neg Q \to \neg \neg R) \to (Q \to R)$

| 步骤 | 证明过程 | 证据 |
| :---: | :--- | :--- |
| $A_{1} =$ | $(\neg \neg Q \to \neg \neg R) \to (\neg R \to \neg Q)$ | <font color="blue">$\mathcal{A}_3$</font> |
| $A_{2} =$ | $(\neg R \to \neg Q) \to (Q \to R) $ | <font color="blue">$\mathcal{A}_3$</font> |
| $A_{3} =$ | $(\neg \neg Q \to \neg \neg R) \to (Q \to R)$ | <font color="blue">$A_{1},A_{2}\vdash A_{3}$</font> |

### 2.10 $\vdash (Q \to R) \to (\neg \neg Q \to \neg \neg R)$

<font color="red">**分析：**</font>
前件和后件都是双变量，无法直观建立联系，考虑一个桥梁连接两者。此处有两种思路。第一种是构造 $\neg \neg Q \to R$ ，希望分别证明 $(Q \to R) \to (\neg \neg Q \to R)$ 和 $(\neg \neg Q \to R) \to (\neg \neg Q \to \neg \neg R)$ 。前者识别出 2.4 的结构，构造 $\neg \neg Q \to Q$ ，易证。后者为 $\mathcal{A}_2$ 的变形，构造 $R \to \neg \neg R$ ，易证。

| 步骤 | 证明过程 | 证据 |
| :---: | :--- | :--- |
| $A_{1} =$ | $\neg \neg Q \to Q$ | <font color="blue">$\vdash \neg \neg Q \to Q$</font> |
| $A_{2} =$ | $(\neg \neg Q \to Q) \to ((Q \to R) \to (\neg \neg Q \to R))$ | <font color="blue">$\begin{aligned} \vdash (Q \to P) \to \\ (( P \to R ) \to (Q \to R)) \end{aligned}$</font> |
| $A_{3} =$ | $(Q \to R) \to (\neg \neg Q \to R)$ | <font color="blue">$A_{2}=A_{1} \to A_{3}$</font> |
| $A_{4} =$ | $R \to \neg \neg R$ | <font color="blue">$Q \to \neg \neg Q$</font> |
| $A_{5} =$ | $(R \to \neg \neg R) \to (\neg \neg Q \to(R \to \neg \neg R))$ | <font color="blue">$\mathcal{A}_1$</font> |
| $A_{6} =$ | $(\neg \neg Q \to(R \to \neg \neg R)) \to ((\neg \neg Q \to R) \to (\neg \neg Q \to \neg \neg R))$ | <font color="blue">$\mathcal{A}_2$</font> |
| $A_{7} =$ | $(\neg \neg Q \to R) \to (\neg \neg Q \to \neg \neg R)$ | <font color="blue">$A_{4},A_{5},A_{6}\vdash A_{7}$</font> |
| $A_{8} =$ | $(Q \to R) \to (\neg \neg Q \to \neg \neg R)$ | <font color="blue">$A_{3},A_{7}\vdash A_{8}$</font> |

第二种为构造 $Q \to \neg \neg R$ ,方法类似，殊途同归，留作练习题请自行思考。

> **延伸思考：** 为什么本命题不可像2.9一样使用 $\mathcal{A}_3$ 直接证明？
> **答：** $\mathcal{A}_3$ 中前件携带 $\neg$ 而后件不携带，推理过程中相当于对“$\neg$”做减法，而本命题前件本就不携带 $\neg$ ，不满足 $\mathcal{A}_3$ 的使用条件，故不能直接使用 $\mathcal{A}_3$ 进行证明。

### 2.11 $\vdash (Q \to R) \to (\neg R \to \neg Q)$ ($\mathcal{A}_3$的逆命题)

| 步骤 | 证明过程 | 证据 |
| :---: | :--- | :--- |
| $A_{1} =$ | $(Q \to R) \to (\neg \neg Q \to \neg \neg R)$ | <font color="blue">$\vdash (Q \to R) \to (\neg \neg Q \to \neg \neg R)$</font> |
| $A_{2} =$ | $(\neg \neg Q \to \neg \neg R) \to (\neg R \to \neg Q)$ | <font color="blue">$\mathcal{A}_3$</font> |
| $A_{3} =$ | $(Q \to R) \to (\neg R \to \neg Q)$ | <font color="blue">$A_{1},A_{2} \vdash A_{3}$</font> |

### 2.12 $\vdash ( \neg Q \to R ) \to (\neg R \to Q)$

<font color="red">**分析：**</font>
仍旧是熟悉的双变量，熟悉的构造桥梁。单个否定我们不容易得到好性质，但是两个否定就可以通过双重否定律直接传递。恰好我们将某一个变量前的否定号变成一致后另一个变量前面恰好差两个否定符号，由此入手。

| 步骤 | 证明过程 | 证据 |
| :---: | :--- | :--- |
| $A_{1} =$ | $\neg \neg Q \to Q$ | <font color="blue">$\vdash \neg \neg Q \to Q$</font> |
| $A_{2} =$ | $(\neg \neg Q \to Q) \to (\neg R \to (\neg \neg Q \to Q))$ | <font color="blue">$\mathcal{A}_1$</font> |
| $A_{3} =$ | $(\neg R \to (\neg \neg Q \to Q)) \to ((\neg R \to \neg \neg Q) \to (\neg R \to Q))$ | <font color="blue">$\mathcal{A}_2$</font> |
| $A_{4} =$ | $(\neg \neg Q \to Q) \to ((\neg R \to \neg \neg Q) \to (\neg R \to Q))$ | <font color="blue">$A_{2},A_{3} \vdash A_{4}$</font> |
| $A_{5} =$ | $(\neg R \to \neg \neg Q) \to (\neg R \to Q)$ | <font color="blue">$A_{4} = A_{1} \to A_{5}$</font> |
| $A_{6} =$ | $( \neg Q \to R ) \to (\neg R \to \neg \neg Q)$ | <font color="blue">$\vdash (Q \to R) \to (\neg R \to \neg Q)$</font> |
| $A_{7} =$ | $( \neg Q \to R ) \to (\neg R \to Q)$ | <font color="blue">$A_{6},A_{5} \vdash A_{7}$</font> |

### 2.13 $\vdash (Q \to \neg R) \to (R \to \neg Q)$

| 步骤 | 证明过程 | 证据 |
| :---: | :--- | :--- |
| $A_{1} =$ | $R \to \neg \neg R$ | <font color="blue">$\vdash Q \to \neg \neg Q$</font> |
| $A_{2} =$ | $(R \to \neg \neg R) \to ((\neg \neg R \to \neg Q) \to (R \to \neg Q))$ | <font color="blue">$\vdash (Q \to P) \to ((P \to R) \to (Q \to R))$</font> |
| $A_{3} =$ | $(\neg \neg R \to \neg Q) \to (R \to \neg Q)$ | <font color="blue">$A_{2} = A_{1} \to A_{3}$</font> |
| $A_{4} =$ | $(Q \to \neg R) \to (\neg \neg R \to \neg Q) $ | <font color="blue">$\vdash (Q \to R) \to (\neg R \to \neg Q)$</font> |
| $A_{5} =$ | $(Q \to \neg R) \to (R \to \neg Q)$ | <font color="blue">$A_{4},A_{3}\vdash A_{5}$</font> |

### 2.14 $\vdash \neg Q \to (Q \to R)$

| 步骤 | 证明过程 | 证据 |
| :---: | :--- | :--- |
| $A_{1} =$ | $\neg Q \to (\neg R \to \neg Q)$ | <font color="blue">$\mathcal{A}_1$</font> |
| $A_{2} =$ | $(\neg R \to \neg Q)\to (Q \to R)$ | <font color="blue">$\mathcal{A}_3$</font> |
| $A_{3} =$ | $\neg Q \to (Q \to R)$ | <font color="blue">$A_{1},A_{2}\vdash A_{3}$</font> |

### 2.15 $\vdash (\neg Q \to Q) \to (R \to Q)$

<font color="red">**分析：**</font>
从形式来看这个 $R$ 非常奇怪，像是凭空产生的一样，此时我们需要考虑能够引入新公式的定理。现有的引入新公式的定理只有公理系统的三个公理，主要为公理 $\mathcal{A}_1$ 。同时考虑与前件产生联系，先尝试 $(\neg Q \to \neg R)\to (R \to Q)$ ,那么转变为证明 $(\neg Q \to Q) \to (\neg Q \to \neg R)$ ，这个式子的前件即为 $\neg Q \to(Q \to \neg R)$ ，到这一步已经非常显然，由 $\neg Q \to (\neg \neg R \to \neg Q)$ 与 $(\neg \neg R \to \neg Q)\to (Q \to \neg R)$ ，证毕。

| 步骤 | 证明过程 | 证据 |
| :---: | :--- | :--- |
| $A_{1} =$ | $\neg Q \to (\neg \neg R \to \neg Q)$ | <font color="blue">$\mathcal{A}_{1}$</font> |
| $A_{2} =$ | $(\neg \neg R \to \neg Q)\to (Q \to \neg R)$ | <font color="blue">$\mathcal{A}_3$</font> |
| $A_{3} =$ | $\neg Q \to(Q \to \neg R)$ | <font color="blue">$A_{1},A_{2} \vdash A_{3}$</font> |
| $A_{4} =$ | $(\neg Q \to(Q \to \neg R)) \to ((\neg Q \to Q) \to (\neg Q \to \neg R))$ | <font color="blue">$\mathcal{A}_{2}$</font> |
| $A_{5} =$ | $(\neg Q \to Q) \to (\neg Q \to \neg R)$ | <font color="blue">$A_{4}=A_{3} \to A_{5}$</font> |
| $A_{6} =$ | $(\neg Q \to \neg R) \to (R \to Q)$ | <font color="blue">$\mathcal{A}_3$</font> |
| $A_{7} =$ | $(\neg Q \to Q) \to (R \to Q)$ | <font color="blue">$A_{5},A_{6} \vdash A_{7}$</font> |

### 2.16 $\vdash (\neg Q \to Q) \to Q$

<font color="red">**分析：**</font>
注意到前件和 2.15 的前件完全一致，只需要利用 $Q$ 相关的公式来代替 $R$ 即可。此处我们用 $\neg Q \to Q$ 来代替 $R$ 可以得到很多非常好的性质。

| 步骤 | 证明过程 | 证据 |
| :---: | :--- | :--- |
| $A_{1} =$ | $(\neg Q \to Q) \to ((\neg Q \to Q) \to Q)$ | <font color="blue">$\vdash (\neg Q \to Q) \to (R \to Q)$</font> |
| $A_{2} =$ | $((\neg Q \to Q) \to ((\neg Q \to Q) \to Q)) \to (((\neg Q \to Q) \to (\neg Q \to Q)) \to ((\neg Q \to Q) \to Q)) $ | <font color="blue">$\mathcal{A}_2$</font> |
| $A_{3} =$ | $((\neg Q \to Q) \to (\neg Q \to Q)) \to ((\neg Q \to Q) \to Q)$ | <font color="blue">$A_{2}=A_{1} \to A_{3}$</font> |
| $A_{4} =$ | $(\neg Q \to Q) \to (\neg Q \to Q)$ | <font color="blue">$\vdash Q \to Q$</font> |
| $A_{5} =$ | $(\neg Q \to Q) \to Q$ | <font color="blue">$A_{3}=A_{4} \to A_{5}$</font> |

### 2.17 $\vdash Q \vee Q \to Q$

遇到此类问题一定要用“字符串”的恒等变形。即证 $(\neg Q \to Q)\to Q$ 。

| 步骤 | 证明过程 | 证据 |
| :---: | :--- | :--- |
| $A_{1} =$ | $(\neg Q \to Q) \to Q$ | <font color="blue">$\vdash (\neg Q \to Q) \to Q$</font> |
| $A_{2} =$ | $Q \vee Q \to Q$ | <font color="blue">$Q \vee R \equiv (\neg Q \to R)$</font> |

### 2.18 $\vdash \neg(Q \wedge \neg Q)$

即证 $\neg \neg (Q \to \neg \neg Q)$ 。

| 步骤 | 证明过程 | 证据 |
| :---: | :--- | :--- |
| $A_{1} =$ | $Q \to \neg \neg Q$ | <font color="blue">$\vdash Q \to \neg \neg Q$</font> |
| $A_{2} =$ | $(Q \to \neg \neg Q) \to \neg \neg (Q \to \neg \neg Q)$ | <font color="blue">$\vdash Q \to \neg \neg Q$</font> |
| $A_{3} =$ | $\neg \neg (Q \to \neg \neg Q)$ | <font color="blue">$A_{2}=A_{1} \to A_{3}$</font> |
| $A_{4} =$ | $\neg(Q \wedge \neg Q)$ | <font color="blue">$Q \wedge R \equiv \neg (Q \to \neg R)$</font> |

### 2.19 $\vdash (Q \to R) \vee (R \to Q)$

<font color="red">**分析：**</font>
即证 $\neg (Q \to R) \to (R \to Q)$ 。由于不可随意地拆解否定符号和括号，所以 $\neg (Q \to R)$ 只能看作一个整体。

<font color="purple">**法一：**</font> 考虑前面用到的关于否定符号的结论。联想到 $Q \to (R \to Q)$ 是显然的，我们希望有 $(Q \to (R \to Q)) \to (\neg (Q \to R) \to (R \to Q))$ ，所以此时前件希望有 $\neg(Q \to R) \to Q$ 自然成立，那么应该有 $\neg Q \to (Q \to R)$ 成立。由公理 $\mathcal{A}_{1}$ 和公理 $\mathcal{A}_{3}$ 知，$\neg Q \to (\neg R \to \neg Q)$ 、$(\neg R \to \neg Q)\to (Q \to R)$ 均显然，证毕。

完整证明过程如下：

| 步骤 | 证明过程 | 证据 |
| :---: | :--- | :--- |
| $A_{1} =$ | $\neg Q \to (Q \to R)$ | <font color="blue">$\vdash \neg Q \to (Q \to R)$</font> |
| $A_{2} =$ | $(\neg Q \to (Q \to R))\to (\neg(Q \to R) \to Q)$ | <font color="blue">$\vdash ( \neg Q \to R ) \to (\neg R \to Q)$</font> |
| $A_{3} =$ | $\neg(Q \to R) \to Q$ | <font color="blue">$A_{2}=A_{1}\to A_{3}$</font> |
| $A_{4} =$ | $(\neg(Q \to R) \to Q) \to ((Q \to (R \to Q)) \to (\neg (Q \to R) \to (R \to Q)))$ | <font color="blue">$\begin{aligned} \vdash (Q \to P) \to \\ (( P \to R ) \to (Q \to R)) \end{aligned}$</font> |
| $A_{5} =$ | $(Q \to (R \to Q)) \to (\neg (Q \to R) \to (R \to Q))$ | <font color="blue">$A_{4}=A_{3} \to A_{5}$</font> |
| $A_{6} =$ | $Q \to (R \to Q)$ | <font color="blue">$\mathcal{A}_1$</font> |
| $A_{7} =$ | $\neg (Q \to R) \to (R \to Q)$ | <font color="blue">$A_{5} = A_{6} \to A_{7}$</font> |
| $A_{8} =$ | $(Q \to R) \vee (R \to Q)$ | <font color="blue">$ Q \vee R \equiv \neg Q \to R$</font> |

<font color="purple">**法二：**</font> 希望通过构造中间公式联系前后件。观察结构，后件形式用 $\mathcal{A}_3$ 向前倒一步变成 $(\neg Q \to \neg R)$ ，此时我们就想到构造中间公式 $\neg R$ ，就可以完美联系前后件，顺利证毕。

完整证明过程如下：

| 步骤 | 证明过程 | 证据 |
| :---: | :--- | :--- |
| $A_{1} =$ | $(R \to (Q \to R)) \to (\neg (Q \to R) \to \neg R)$ | <font color="blue">$\vdash (Q \to R) \to (\neg R \to \neg Q)$</font> |
| $A_{2} =$ | $R \to (Q \to R)$ | <font color="blue">$\mathcal{A}_1$</font> |
| $A_{3} =$ | $\neg (Q \to R) \to \neg R$ | <font color="blue">$A_{1}  = A_{2} \to A_{3}$</font> |
| $A_{4} =$ | $\neg R \to (R \to Q)$ | <font color="blue">$\vdash \neg Q \to (Q \to R)$</font> |
| $A_{5} =$ | $\neg (Q \to R) \to (R \to Q)$ | <font color="blue">$A_{3} ,A_{4} \vdash A_{5}$</font> |
| $A_{6} =$ | $(Q \to R) \vee (R \to Q)$ | <font color="blue">$Q \vee R \equiv \neg Q \to R$</font> |

### 2.20 $\vdash (Q \to R) \to (Q \to \neg R)$

<font color="red">**分析：**</font>
即证 $\neg (Q \to R) \to (Q \to \neg R)$ 。由2.19的法二易知构造 $\neg R$ 即可，不再赘述。

完整证明过程如下：

| 步骤 | 证明过程 | 证据 |
| :---: | :--- | :--- |
| $A_{1} =$ | $(R \to (Q \to R)) \to (\neg (Q \to R) \to \neg R)$ | <font color="blue">$\vdash (Q \to R) \to (\neg R \to \neg Q)$</font> |
| $A_{2} =$ | $R \to (Q \to R)$ | <font color="blue">$\mathcal{A}_1$</font> |
| $A_{3} =$ | $\neg (Q \to R) \to \neg R$ | <font color="blue">$A_{1}  = A_{2} \to A_{3}$</font> |
| $A_{4} =$ | $\neg R \to (Q \to \neg R)$ | <font color="blue">$\mathcal{A}_1$</font> |
| $A_{5} =$ | $\neg (Q \to R) \to (Q \to \neg R)$ | <font color="blue">$A_{3},A_{4} \vdash A_{5}$</font> |
| $A_{6} =$ | $(Q \to R) \to (Q \to \neg R)$ | <font color="blue">$Q \vee R \equiv \neg Q \to R$</font> |

### 2.21 $\vdash Q \to ((Q \to R) \to R)$

<font color="red">**分析：**</font>
注意到换前的形式，容易证明。

完整证明过程如下：

| 步骤 | 证明过程 | 证据 |
| :---: | :--- | :--- |
| $A_{1} =$ | $(Q \to R)\to (Q \to R)$ | <font color="blue">$\vdash Q \to Q$</font> |
| $A_{2} =$ | $((Q \to R)\to (Q \to R)) \to (Q \to ((Q \to R) \to R))$ | <font color="blue">$\vdash (P \to (Q \to R)) \to (Q \to (P \to R))$</font> |
| $A_{3} =$ | $Q \to ((Q \to R) \to R)$ | <font color="blue">$A_{1},A_{2} \vdash A_{3}$</font> |

### 2.22 $\vdash Q \wedge (Q \to R) \to R$

<font color="red">**分析：**</font>
即证 $\neg (Q \to \neg(Q \to R)) \to R$ 。由于前件结构过于复杂，考虑消解掉否定号来简化结构。考虑证明 $\neg R \to (Q \to \neg(Q \to R))$ ,再通过换前使带否定号的结构全部处于后件中便于共同消去，即证 $Q \to (\neg R \to \neg (Q \to R))$ ，只要证 $Q \to ((Q \to R) \to R)$ 。此时已经非常显然，即使没有2.21的证明也只需要一步换前即可证毕。

完整证明过程如下：

| 步骤 | 证明过程 | 证据 |
| :---: | :--- | :--- |
| $A_{1} =$ | $Q \to ((Q \to R) \to R)$ | <font color="blue">$\vdash Q \to ((Q \to R) \to R)$</font> |
| $A_{2} =$ | $((Q \to R) \to R) \to (\neg R \to \neg (Q \to R))$ | <font color="blue">$\vdash (Q \to R) \to (\neg R \to \neg Q)$</font> |
| $A_{3} =$ | $Q \to (\neg R \to \neg (Q \to R))$ | <font color="blue">$A_{1},A_{2} \vdash A_{3}$</font> |
| $A_{4} =$ | $(Q \to (\neg R \to \neg (Q \to R))) \to (\neg R \to (Q \to \neg(Q \to R)))$ | <font color="blue">$\vdash (P \to (Q \to R)) \to (Q \to (P \to R))$</font> |
| $A_{5} =$ | $\neg R \to (Q \to \neg(Q \to R))$ | <font color="blue">$A_{4} = A_{3} \to A_{5}$</font> |
| $A_{6} =$ | $(\neg R \to (Q \to \neg(Q \to R))) \to (\neg (Q \to \neg(Q \to R)) \to R)$ | <font color="blue">$\vdash (\neg Q \to R) \to (\neg R \to Q)$</font> |
| $A_{7} =$ | $\neg (Q \to \neg(Q \to R)) \to R$ | <font color="blue">$A_{6}=A_{5} \to A_{7}$</font> |
| $A_{8} =$ | $Q \wedge (Q \to R) \to R$ | <font color="blue">$Q \vee R \equiv \neg Q \to R$</font> |

### 2.23 $\vdash (\neg Q \to R) \to ((\neg Q \to \neg R) \to Q)$

<font color="red">**分析：**</font>
注意到对前件做 $(\neg Q \to R)\to (\neg R \to Q)$ 处理，可以得到相同的后件，即证 $(\neg R \to Q)\to((\neg Q \to \neg R) \to Q) $ 。但是结构显然与我们熟悉的不同，因为此时我们需要证的是 $(\neg Q \to \neg R) \to \neg R$ ，说明此路不通。
注意到后件部分中的前件结构有两个否定号，联想到 $(\neg Q \to \neg R) \to (R \to Q)$ 和 $(R \to Q) \to (\neg Q \to \neg R)$ ，此处我们使用前者，构造 $((R \to Q) \to Q) \to ((\neg Q \to \neg R) \to Q)$ ,转化为证明 $(\neg Q \to R) \to ((R \to Q) \to Q)$ 。
如果证 $(\neg Q \to R) \to (\neg Q \to \neg (R \to Q))$ ，也就是只要证 $R \to \neg (R \to Q)$ 。此结构仍然无法处理，因为两个 $R$ 的否定号无法同时消去。
尝试将 $R \to Q$ 作为整体处理，构造相同前件的推理，又要与 $\neg Q \to R$ 产生联系，尝试构造 $\neg Q \to Q$ 。由于有 $(\neg Q \to Q) \to Q$ ，所以自然的有 $((R \to Q) \to (\neg Q \to Q))\to ((R \to Q) \to Q)$ 成立，而 $(\neg Q \to R) \to ((R \to Q) \to (\neg Q \to Q))$ 显然是成立的，证毕。

完整证明过程如下：

| 步骤 | 证明过程 | 证据 |
| :---: | :--- | :--- |
| $A_{1} =$ | $(\neg Q \to Q) \to Q$ | <font color="blue">$\vdash (\neg Q \to Q) \to Q$</font> |
| $A_{2} =$ | $((\neg Q \to Q) \to Q) \to (((R \to Q)\to (\neg Q \to Q)) \to ((R \to Q) \to Q))$ | <font color="blue">$\begin{aligned} \vdash (Q \to P) \to \\ ((P \to R) \to (Q \to R)) \end{aligned}$</font> |
| $A_{3} =$ | $((R \to Q)\to (\neg Q \to Q)) \to ((R \to Q) \to Q)$ | <font color="blue">$A_{2}=A_{1} \to A_{3}$</font> |
| $A_{4} =$ | $(((R \to Q)\to (\neg Q \to Q)) \to ((R \to Q) \to Q)) \to (((\neg Q \to R) \to ((R \to Q)\to (\neg Q \to Q))) \to ((\neg Q \to R)\to ((R \to Q) \to Q)))$ | <font color="blue">$\begin{aligned} \vdash (Q \to R) \to \\ ((P \to Q) \to (P \to R)) \end{aligned}$</font> |
| $A_{5} =$ | $((\neg Q \to R) \to ((R \to Q)\to (\neg Q \to Q))) \to ((\neg Q \to R) \to ((R \to Q) \to Q))$ | <font color="blue">$A_{4} = A_{3} \to A_{5}$</font> |
| $A_{6} =$ | $(\neg Q \to R) \to ((R \to Q)\to (\neg Q \to Q))$ | <font color="blue">$\vdash (Q \to P) \to ((P \to R) \to (Q \to R))$</font> |
| $A_{7} =$ | $(\neg Q \to R)\to ((R \to Q) \to Q)$ | <font color="blue">$A_{5} = A_{6} \to A_{7}$</font> |
| $A_{8} =$ | $((\neg Q \to R)\to ((R \to Q) \to Q)) \to ((R \to Q) \to ((\neg Q \to R) \to Q))$ | <font color="blue">$\vdash (P \to (Q \to R)) \to (Q \to (P \to R))$</font> |
| $A_{9} =$ | $(R \to Q) \to ((\neg Q \to R) \to Q)$ | <font color="blue">$A_{8} =A_{7} \to A_{9}$</font> |
| $A_{10} =$ | $(\neg Q \to \neg R) \to (R \to Q)$ | <font color="blue">$\mathcal{A}_3$</font> |
| $A_{11} =$ | $(\neg Q \to \neg R) \to ((\neg Q \to R) \to Q)$ | <font color="blue">$A_{10},A_{9} \vdash A_{11}$</font> |
| $A_{12} =$ | $((\neg Q \to \neg R) \to ((\neg Q \to R) \to Q)) \to ((\neg Q \to R) \to ((\neg Q \to \neg R) \to Q))$ | <font color="blue">$\vdash (P \to (Q \to R)) \to (Q \to (P \to R))$</font> |
| $A_{13} =$ | $(\neg Q \to R) \to ((\neg Q \to \neg R) \to Q)$ | <font color="blue">$A_{12}=A_{11} \to A_{13}$</font> |

> <font color="cyan">**反思**</font>
> 其实本题用演绎定理可以反推出过程。过程如下：
> 1. 即证 $\neg Q \to R , \neg Q \to \neg R \vdash Q$ ；
> 2. 因为 $(\neg Q \to \neg R) \to (R \to Q)$ ,所以有 $R \to Q$ ；
> 3. 又因为 $\neg Q \to R$ ，所以 $\neg Q \to Q$ 。
> 4. 又因为 $(\neg Q \to Q) \to Q$ ，所以 $Q$ 成立。
> 
> 从这个推理过程反推即可构造不使用演绎定理的证明。

### 2.24 $\vdash (Q \to R) \to ((Q \to \neg R) \to \neg Q)$

<font color="red">**分析：**</font>
用演绎定理我们会得到一个奇怪的形式，最后一步需要证明 $\vdash (Q \to \neg Q) \to \neg Q$ 。这个引理需要我们证明，也非常简单，先由 $(\neg Q \to Q) \to Q$ 构造 $(\neg \neg Q \to \neg Q) \to \neg Q$ ，再由 $(Q \to R) \to (\neg R \to \neg Q)$ 构造 $(Q \to \neg Q) \to (\neg \neg Q \to \neg Q)$ ,引理证毕。
此时结构仍然不太明显，那我们用“两头凑”的方法。从后件形式开始证明，先借助 $(Q \to \neg R) \to (R \to \neg Q)$ 构造 $(R \to \neg Q) \to \neg Q$ ，希望有 $(Q \to R) \to ((R \to \neg Q) \to \neg Q)$ 。此时就与引理形式相近，因为 $((R \to \neg Q) \to (Q \to \neg Q)) \to ((R \to \neg Q) \to \neg Q)$ 是显然的，所以只要证 $(Q \to R) \to ((R \to \neg Q) \to (Q \to \neg Q))$ ，显然成立，证毕。

完整证明过程如下：

| 步骤 | 证明过程 | 证据 |
| :---: | :--- | :--- |
| $A_{1} =$ | $(\neg \neg Q \to \neg Q) \to \neg Q$ | <font color="blue">$\vdash (\neg Q \to Q) \to Q$</font> |
| $A_{2} =$ | $(Q \to \neg Q) \to (\neg \neg Q \to \neg Q)$ | <font color="blue">$\vdash (Q \to R) \to (\neg R \to \neg Q)$</font> |
| $A_{3} =$ | $(Q \to \neg Q) \to \neg Q$ | <font color="blue">$A_{2},A_{1} \vdash A_{3}$</font> |
| $A_{4} =$ | $((Q \to \neg Q) \to \neg Q) \to (((R \to \neg Q) \to (Q \to \neg Q)) \to ((R \to \neg Q) \to \neg Q))$ | <font color="blue">$\vdash (Q \to R) \to ((P \to Q) \to (P \to R))$</font> |
| $A_{5} =$ | $((R \to \neg Q) \to (Q \to \neg Q)) \to ((R \to \neg Q) \to \neg Q)$ | <font color="blue">$A_{4} =A_{3} \to A_{5}$</font> |
| $A_{6} =$ | $(Q \to R) \to ((R \to \neg Q) \to (Q \to \neg Q))$ | <font color="blue">$\vdash (Q \to P) \to ((P \to R) \to (Q \to R))$</font> |
| $A_{7} =$ | $(Q \to R) \to ((R \to \neg Q) \to \neg Q)$ | <font color="blue">$A_{6},A_{5} \vdash A_{7}$</font> |
| $A_{8} =$ | $(Q \to \neg R) \to (R \to \neg Q)$ | <font color="blue">$\vdash (Q \to \neg R) \to (R \to \neg Q)$</font> |
| $A_{9} =$ | $((Q \to \neg R) \to (R \to \neg Q)) \to (((R \to \neg Q) \to \neg Q) \to ((Q \to \neg R) \to \neg Q))$ | <font color="blue">$\vdash (Q \to P) \to ((P \to R) \to (Q \to R))$</font> |
| $A_{10} =$ | $((R \to \neg Q) \to \neg Q) \to ((Q \to \neg R) \to \neg Q)$ | <font color="blue">$A_{9} = A_{8} \to A_{10}$</font> |
| $A_{11} =$ | $(Q \to R) \to ((Q \to \neg R) \to \neg Q)$ | <font color="blue">$A_{7},A_{10}\vdash A_{11}$</font> |

### 2.25 $ \vdash (\neg Q \to R \wedge \neg R) \to Q$

<font color="red">**分析：**</font>
即证 $(\neg Q \to \neg (R \to \neg \neg R)) \to Q$ 。结构非常清晰。首先将前件变形，导出 $(\neg Q \to \neg (R \to \neg \neg R)) \to ((R \to \neg \neg R) \to Q)$ ，再用一次换前即可。
这里倒是有一个小巧思，因为构造中间式子之后居然不需要证明沟通之后的后半段，$((R \to \neg \neg R) \to Q) \to Q$ 不容易证，反而是直接对前半段继续变形。这也提醒我们分析过程中尽量不要挑步骤，免得错过最佳证明路径。

完整证明过程如下：

| 步骤 | 证明过程 | 证据 |
| :---: | :--- | :--- |
| $A_{1} =$ | $(\neg Q \to \neg (R \to \neg \neg R)) \to ((R \to \neg \neg R) \to Q)$ | <font color="blue">$\mathcal{A}_3$</font> |
| $A_{2} =$ | $((\neg Q \to \neg (R \to \neg \neg R)) \to ((R \to \neg \neg R) \to Q)) \to ((R \to \neg \neg R) \to ((\neg Q \to \neg (R \to \neg \neg R)) \to Q))$ | <font color="blue">$\vdash (P \to (Q \to R)) \to (Q \to (P \to R))$</font> |
| $A_{3} =$ | $(R \to \neg \neg R) \to ((\neg Q \to \neg (R \to \neg \neg R)) \to Q)$ | <font color="blue">$A_{2} = A_{1} \to A_{3}$</font> |
| $A_{4} =$ | $R \to \neg \neg R$ | <font color="blue">$\vdash Q \to \neg \neg Q$</font> |
| $A_{5} =$ | $(\neg Q \to \neg (R \to \neg \neg R)) \to Q$ | <font color="blue">$A_{3} = A_{4} \to A_{5}$</font> |
| $A_{6} =$ | $(\neg Q \to R \wedge \neg R) \to Q$ | <font color="blue">$Q \wedge R \equiv \neg (Q \to \neg R)$</font> |

### 2.26 $\vdash Q \to R \vee Q$

| 步骤 | 证明过程 | 证据 |
| :---: | :--- | :--- |
| $A_{1} =$ | $Q \to (\neg R \to Q)$ | <font color="blue">$\mathcal{A}_1$</font> |
| $A_{2} =$ | $Q \to R \vee Q$ | <font color="blue">$Q \vee R \equiv \neg Q \to R$</font> |

### 2.27 $\vdash Q \wedge R \to R \wedge Q$

| 步骤 | 证明过程 | 证据 |
| :---: | :--- | :--- |
| $A_{1} =$ | $(R \to \neg Q) \to (Q \to \neg R)$ | <font color="blue">$\vdash (Q \to \neg R) \to (R \to \neg Q)$</font> |
| $A_{2} =$ | $((R \to \neg Q) \to (Q \to \neg R)) \to (\neg (Q \to \neg R) \to \neg (R \to \neg Q))$ | <font color="blue">$\vdash (Q \to R) \to (\neg R \to \neg Q)$</font> |
| $A_{3} =$ | $\neg (Q \to \neg R) \to \neg (R \to \neg Q)$ | <font color="blue">$A_{2} =A_{1} \to A_{3}$</font> |
| $A_{4} =$ | $Q \wedge R \to R \wedge Q$ | <font color="blue">$Q \wedge R \equiv \neg (Q \to \neg R)$</font> |

### 2.28 $\vdash Q \wedge R \to Q$

| 步骤 | 证明过程 | 证据 |
| :---: | :--- | :--- |
| $A_{1} =$ | $\neg Q \to (\neg \neg R \to \neg Q)$ | <font color="blue">$\mathcal{A}_1$</font> |
| $A_{2} =$ | $(\neg \neg R \to \neg Q)\to (Q \to \neg R)$ | <font color="blue">$\mathcal{A}_3$</font> |
| $A_{3} =$ | $\neg Q \to (Q \to \neg R)$ | <font color="blue">$A_{1},A_{2}\vdash A_{3}$</font> |
| $A_{4} =$ | $(\neg Q \to (Q \to \neg R)) \to (\neg (Q \to \neg R) \to Q)$ | <font color="blue">$\vdash (\neg Q \to R) \to (\neg R \to Q)$</font> |
| $A_{5} =$ | $\neg (Q \to \neg R) \to Q$ | <font color="blue">$A_{4}=A_{3} \to A_{5}$</font> |
| $A_{6} =$ | $Q \wedge R \to Q$ | <font color="blue">$Q \wedge R \equiv \neg (Q \to \neg R)$</font> |

### 2.29 $\vdash Q \wedge R \to R$

| 步骤 | 证明过程 | 证据 |
| :---: | :--- | :--- |
| $A_{1} =$ | $\neg R \to (Q \to \neg R)$ | <font color="blue">$\mathcal{A}_1$</font> |
| $A_{2} =$ | $(\neg R \to (Q \to \neg R)) \to (\neg (Q \to \neg R) \to R)$ | <font color="blue">$\vdash (\neg Q \to R) \to (\neg R \to Q)$</font> |
| $A_{3} =$ | $\neg (Q \to \neg R) \to R$ | <font color="blue">$A_{2}=A_{1} \to A_{3}$</font> |
| $A_{4} =$ | $Q \wedge R \to R$ | <font color="blue">$Q \wedge R \equiv \neg (Q \to \neg R)$</font> |

### 2.30 $\vdash (P \wedge Q \to R) \to (P \to (Q \to R))$

<font color="red">**分析：**</font>
即证 $(\neg (P \to \neg Q) \to R)\to (P \to (Q \to R))$ 。先用一次换前,希望证 $P \to ((\neg (P \to \neg Q) \to R) \to (Q \to R))$ ，即只要证 $P \to (Q \to \neg (P \to \neg Q))$ ，只要证 $P \to ((P \to \neg Q) \to \neg Q)$ ，结构显然，证毕。

完整证明过程如下：

| 步骤 | 证明过程 | 证据 |
| :---: | :--- | :--- |
| $A_{1} =$ | $(P \to \neg Q) \to (P \to \neg Q)$ | <font color="blue">$\vdash Q \to Q$</font> |
| $A_{2} =$ | $((P \to \neg Q) \to (P \to \neg Q)) \to (P \to ((P \to \neg Q) \to \neg Q))$ | <font color="blue">$\vdash (P \to (Q \to R)) \to (Q \to (P \to R))$</font> |
| $A_{3} =$ | $P \to ((P \to \neg Q) \to \neg Q)$ | <font color="blue">$A_{2} = A_{1} \to A_{3}$</font> |
| $A_{4} =$ | $((P \to \neg Q) \to \neg Q) \to (Q \to \neg (P \to \neg Q))$ | <font color="blue">$\vdash (Q \to \neg R) \to (R \to \neg Q)$</font> |
| $A_{5} =$ | $(Q \to \neg (P \to \neg Q)) \to ((\neg (P \to \neg Q) \to R) \to (Q \to R))$ | <font color="blue">$\vdash (Q \to P) \to ((P \to R) \to (Q \to R))$</font> |
| $A_{6} =$ | $P \to ((\neg (P \to \neg Q) \to R) \to (Q \to R))$ | <font color="blue">$A_{3},A_{4},A_{5},\vdash A_{6}$</font> |
| $A_{7} =$ | $(P \to ((\neg (P \to \neg Q) \to R) \to (Q \to R))) \to ((\neg (P \to \neg Q) \to R)\to (P \to (Q \to R)))$ | <font color="blue">$\vdash (P \to (Q \to R)) \to (Q \to (P \to R))$</font> |
| $A_{8} =$ | $(P \wedge Q \to R) \to (P \to (Q \to R))$ | <font color="blue">$Q \wedge R \equiv \neg (Q \to \neg R)$</font> |

### 2.31 $\vdash Q \to (R \to (Q \wedge R))$

<font color="red">**分析：**</font>
即证 $Q \to (R \to \neg (Q \to \neg R))$ ,只要证 $Q \to ((Q \to \neg R) \to \neg R)$ ，显然。

完整证明过程如下：

| 步骤 | 证明过程 | 证据 |
| :---: | :--- | :--- |
| $A_{1} =$ | $(Q \to \neg R)\to (Q \to \neg R)$ | <font color="blue">$\vdash Q \to Q$</font> |
| $A_{2} =$ | $((Q \to \neg R)\to (Q \to \neg R)) \to (Q \to ((Q \to \neg R) \to \neg R))$ | <font color="blue">$\vdash (P \to (Q \to R)) \to (Q \to (P \to R))$</font> |
| $A_{3} =$ | $Q \to ((Q \to \neg R) \to \neg R)$ | <font color="blue">$A_{2}=A_{1} \to A_{3}$</font> |
| $A_{4} =$ | $((Q \to \neg R) \to \neg R) \to (R \to \neg (Q \to \neg R))$ | <font color="blue">$\vdash (Q \to \neg R) \to (R \to \neg Q)$</font> |
| $A_{5} =$ | $Q \to (R \to \neg (Q \to \neg R))$ | <font color="blue">$A_{3},A_{4} \vdash A_{5}$</font> |
| $A_{6} =$ | $Q \to (R \to (Q \wedge R))$ | <font color="blue">$Q \wedge R \equiv \neg (Q \to \neg R)$</font> |

### 2.32 $\vdash Q \to (\neg R \to \neg (Q \to R))$

| 步骤 | 证明过程 | 证据 |
| :---: | :--- | :--- |
| $A_{1} =$ | $(Q \to  R)\to (Q \to  R)$ | <font color="blue">$\vdash Q \to Q$</font> |
| $A_{2} =$ | $((Q \to  R)\to (Q \to R)) \to (Q \to ((Q \to R) \to R))$ | <font color="blue">$\vdash (P \to (Q \to R)) \to (Q \to (P \to R))$</font> |
| $A_{3} =$ | $Q \to ((Q \to R) \to  R)$ | <font color="blue">$A_{2}=A_{1} \to A_{3}$</font> |
| $A_{4} =$ | $((Q \to R) \to  R) \to (\neg R \to \neg (Q \to R))$ | <font color="blue">$\vdash (Q \to R) \to (\neg R \to \neg Q)$</font> |
| $A_{5} =$ | $Q \to (\neg R \to \neg (Q \to R))$ | <font color="blue">$A_{3},A_{4} \vdash A_{5}$</font> |

<div style="page-break-after: always;"></div>

