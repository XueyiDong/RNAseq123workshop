# 使用limma、Glimma和edgeR，RNA-seq数据分析易如反掌

![.github/workflows/basic_checks.yaml](https://github.com/XueyiDong/RNAseq123CN/workflows/.github/workflows/basic_checks.yaml/badge.svg)

## 课程简介

简单且高效地分析RNA测序数据的能力正是Bioconductor的核心优势之一。在获得RNA-seq基因表达矩阵后，通常需要对数据进行预处理、探索性数据分析、差异表达检验以及通路分析，以得到可以帮助进一步实验和验证研究的结果。

 在本次workshop中，我们将通过分析来自小鼠乳腺的RNA测序数据，演示如何使用流行的edgeR包载入、整理、过滤和归一化数据，然后用limma包的voom方法、线性模型和经验贝叶斯调节来评估差异表达并进行基因集检验。通过Glimma包，本流程进一步实现了结果的互动探索，便于用户查看特定样本与基因的分析结果。

通过使用这三个Bioconductor包，研究者可以轻松地运行完整的RNA-seq数据分析流程，从原始计数（raw counts）中挖掘出其中蕴含的生物学意义。

### 课前准备

* 了解R语言的语法基础
* 大致了解RNA-seq的原理与目的

## 软件安装

本次workshop所用的资料来自Bioconductor包[RNAseq123](https://bioconductor.org/packages/release/workflows/html/RNAseq123.html)。如果你的电脑上已经装有R（版本需要在3.3.0或以上）与RStudio，可以使用以下命令在R中下载并安装此包，即可同时安装整个流程中所需要用到的所有R包：

```R
if (!requireNamespace("BiocManager", quietly = TRUE))
    install.packages("BiocManager")

BiocManager::install("RNAseq123")
```

此外，我们也为本次workflow准备了Docker镜像，其中包含R、RStudio与需要用到的所有R包。可以用以下方式来使用Docker容器：

* 首先运行以下命令：

```sh
docker run -e PASSWORD=<choose_a_password_for_rstudio> -p 8787:8787 xueyidong/RNAseq123CN
```
* 然后在浏览器里访问https://localhost:8787/ 登陆RStudio，用户名 `rstudio`，密码`yourchosenpassword`. 
