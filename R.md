# R
## Cheatsheet
- # : comment
### calc
- +, -, *, /, ^
### Functions
- sqrt(16)
- log(2, base=10)
- sum(1,2,3)
- length(x)

- max(x)
- min(x)
- abs(x)
- ceiling(x)

- mean(x)
- median(x)
- var(x): 不偏分散
- sd(x): 標準偏差 standard deviation
- cov(x,y): 共分散
- cor(x,y): 相関係数

- date()

- c(1,2,3,3,4): combine 複数のデータを扱うためのもの、

- ifelse(data=="好き",1,0)
- runif(n=10000,min=0,max=6) : 一様分布に従う乱数データを発生させる関数

- summary(c(1,2,3,3))
- matrix(c(),
- table(x)

- hist(x)
  - hist(x, freq=FALSE): ヒストグラム全体の面積が1となるように縦軸を調整
- plot(x,y)
- barplot(x):棒グラフ


- curve(dnorm(x,mean=0,sd=1),from=-4,to=4): 確率密度関数、dnorm(確率変数の値, 平均, 標準偏差)
- rnrom(n=5, mean=50, sd=10)

- getwd()

- read.csv("filename")

- function(x) { 標本分散 <- var(x)*}

- source(varp.R)

- library(sem)
### Packages
- sem
- Rcmdr
## Link
- https://cran.ism.ac.jp/
- [[https://cran.ism.ac.jp/manuals.html][The R Manuals]]
