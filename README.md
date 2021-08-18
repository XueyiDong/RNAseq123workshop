# Workshop: RNA-seq analysis is easy as 1-2-3 with limma, Glimma and edgeR

![.github/workflows/basic_checks.yaml](https://github.com/XueyiDong/RNAseq123CN/workflows/.github/workflows/basic_checks.yaml/badge.svg)

## Introduction 课程简介



![](vignettes/stickers.png)

The ability to easily and efficiently analyse RNA-sequencing data is a key strength of the Bioconductor project. Starting with counts summarised at the gene-level, a typical analysis involves pre-processing, exploratory data analysis, differential expression testing and pathway analysis with the results obtained informing future experiments and validation studies. 

简单且高效地分析RNA测序数据的能力正是Bioconductor的核心优势之一。在获得RNA-seq基因表达矩阵后，通常需要对数据进行预处理、探索性数据分析、差异表达检验以及通路分析，以得到可以帮助进一步实验和验证研究的结果。

In this workshop, we analyse RNA-sequencing data from the mouse mammary gland, demonstrating use of the popular **edgeR** package to import, organise, filter and normalise the data, followed by the **limma** package with its *voom* method, linear modelling and empirical Bayes moderation to assess differential expression and perform gene set testing. This pipeline is further enhanced by the **Glimma** package which enables interactive exploration of the results so that individual samples and genes can be examined by the user.

在本次workshop中，我们将通过分析来自小鼠乳腺的RNA测序数据，演示如何使用流行的**edgeR**包载入、整理、过滤和归一化数据，然后用**limma**包的*voom*方法、线性模型和经验贝叶斯调节来评估差异表达并进行基因集检验。通过**Glimma**包，本流程进一步实现了结果的互动探索，便于用户查看特定样本与基因的分析结果。

The complete analysis offered by these three packages highlights the ease with which researchers can turn the raw counts from an RNA-sequencing experiment into biological insights using Bioconductor.

通过使用这三个Bioconductor包，研究者可以轻松地运行完整的RNA-seq数据分析流程，从原始计数（raw counts）中挖掘出其中蕴含的生物学意义。

## Software installation 软件安装与运行

The material used in this workshop are from the Bioconductor package [RNAseq123](https://bioconductor.org/packages/release/workflows/html/RNAseq123.html). If you have already installed R (version >= 3.5.1) and RStudio on your computer and have installed Bioconductor version 3.8 or higher, you can install the package itself as well as other packages necessary for this workshop using the following command:

```R
if (!requireNamespace("BiocManager", quietly = TRUE))
    install.packages("BiocManager")

BiocManager::install("RNAseq123")
```

本次workshop所用的资料来自Bioconductor包[RNAseq123](https://bioconductor.org/packages/release/workflows/html/RNAseq123.html)。如果你的电脑上已经装有R（版本需要在3.5.1或以上）与RStudio，并已安装Bioconductor项目3.8或以上版本，则可以使用以下命令在R中下载并安装此包，即可同时安装整个流程中所需要用到的所有R包：

```R
if (!requireNamespace("BiocManager", quietly = TRUE))
    install.packages("BiocManager")

BiocManager::install("RNAseq123")
```

Alternatively, you can might like to use Docker to run the workshop in a container with R, all the necessary packages, and RStudio. This can be done as follows:

- Use the following command to download and run the Docker image:

```sh
docker run -e PASSWORD=<choose_a_password_for_rstudio> -p 8787:8787 xueyidong/RNAseq123workshop
```

* Once running, navigate to https://localhost:8787/ and then login with `rstudio`:`yourchosenpassword`. If you are using Windows operating system, you will need to provide your local ip address, such as `http://191.163.92.108:8787/`. This can be found using the command `docker-machine ip default` in the Docker terminal.

此外，我们也为本次workshop准备了Docker镜像，其中包含R、RStudio与需要用到的所有R包。可以通过以下方式来使用此Docker容器：

* 首先运行以下命令下载并运行Docker镜像：

```sh
docker run -e PASSWORD=自己随便想一个密码 -p 8787:8787 xueyidong/RNAseq123workshop
```
* 然后在浏览器里访问https://localhost:8787/ 登陆RStudio，用户名 `rstudio`，密码为上一步里设置的密码。如果你使用的是Windows操作系统，你需要提供本地主机的ip地址，例如`http://191.163.92.108:8787/`，可以在Docker终端中用`docker-machine ip default`命令查询。
