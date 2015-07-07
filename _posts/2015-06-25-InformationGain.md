---
layout: post
title:  "信息增益"
date:   2015-07-07
---
<style type="text/css">
p{
	text-indent: 2em;
}
.post img {
  margin-bottom: 0rem;
}
</style>

<p class="intro">
	<span class="dropcap">在</span>概率论和信息论中，信息增益是非对称的，用以度量两种概率分布P和Q的差异。信息增益描述了当使用Q进行编码时，再使用P进行编码的差异。通常P代表样本或观察值的分布，也有可能是精确计算的理论分布。Q代表一种理论，模型，描述或者对P的近似。
</p>


# 信息增益

## 1. 比特编码

对任意随机变量<i>X</i>

有如下4种取值情况
<table class="table-bordered table-condensed table">
	<tr>
		<td>P(X=A)=1/4</td>
		<td>P(X=B)=1/4</td>
		<td>P(X=C)=1/4</td>
		<td>P(X=D)=1/4</td>
	</tr>
</table>

假设我们要编码的序列为：BAACBADCDADDDA…
可以将(e.g. A = 00, B = 01, C = 10, D = 11),，每个字符使用2个比特位。

0100001001001110110011111100…


## 2.	更佳的比特编码方式
也许有人会告诉你每个字符的概率不一定相等,如下表
<table class="table-bordered table-condensed table">
	<tr>
		<td>P(X=A)=1/2</td>
		<td>P(X=B)=1/4</td>
		<td>P(X=C)=1/8</td>
		<td>P(X=D)=1/8</td>
	</tr>
</table>
那有没有一种编码方式，能将平均每个字符花1.75bits, 如果有的话，那应该如何编码？可能大部分的人第一反应就是哈夫曼编码(Huffman Coding)。
<table class="table-bordered table-condensed table">
	<tr>
		<td>P(X=A)=1/2</td>
		<td>P(X=B)=1/4</td>
		<td>P(X=C)=1/8</td>
		<td>P(X=D)=1/8</td>
	</tr>
</table>

<table>
	<tr>
		<td>A</td>
		<td>B</td>
		<td>C</td>
		<td>D</td>
	</tr>
	<tr>
		<td>0</td>
		<td>10</td>
		<td>110</td>
		<td>111</td>
	</tr>
</table>

当然这只是众多编码中的一种编码方法。


Suppose there are three equally likely values…
P(X=A)=1/3	P(X=B)=1/3	P(X=C)=1/3
最简单方便的编码方法是每个字符花费2 bits，那有没有一种编码方式，能将平均每个字符花1.6bits。理论上，每只字符只要1.58496 bits，就可以完成编码方法。



## 一般情况，
假如随机变量X有m种取值V<sub>1</sub>, V<sub>2</sub>, …… ，V<sub>m</sub>

<table class="table-bordered table-condensed table">
	<tr>
		<td>P(X=V<sub>1</sub>)=P<sub>1</sub></td>
		<td>P(X=V<sub>2</sub>)=P<sub>2</sub></td>
		<td>……</td>
		<td>P(X=V<sub>m</sub>)=P<sub>m</sub></td>
	</tr>
</table>

对于来自随机变量X分布的字符流，如果要对该流编码那平均每个字符至少需要多少个bits？

记X的熵为H(X):

<img src="http://www.forkosh.com/mathtex.cgi?$H(X)=-p_{1}log_{2}p_{1}-p_{2}log_{2}p_{2}-\dots-p_{m}log_{2}p_{m}=-\sum_{i=1}^{n}p_{i}log_{2}p_{i}$$">


* 熵H(X)的值大意味着随机变量X的取值来自正态分布(混乱的分布)，X变量的直方图会较为平坦
* 熵H(X)的值小意味着随机变量X的取值来多种多样（峰谷)分布，X变量的直方图有一两值的

