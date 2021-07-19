--- 
title: "现代统计图形"
subtitle: "Modern Statistical Graphics"
author: 
  - 赵鹏
  - 谢益辉
  - 黄湘云
date: "2021-07-19"
site: bookdown::bookdown_site
documentclass: book
bibliography:
  - book.bib
  - MSG-packages.bib
  - Modern-Stat-Graphics.bib
biblio-style: plainnat
natbiboptions: "authoryear,square"
link-citations: yes
graphics: yes
mathspec: yes
lot: yes
lof: yes
classoption: "UTF8,twoside"
papersize: b5
colorlinks: yes
geometry:
  - tmargin=2.5cm
  - bmargin=2.5cm
  - lmargin=3.5cm
  - rmargin=2.5cm
description: "现代统计图形书稿"
subject: "统计图形, 数据可视化"
keywords: 
- R 语言
- 统计图形
- 统计学
- 图形元素
- 图形系统
- 统计图形软件
- 数据可视化
github-repo: XiangyunHuang/MSG-Book
url: 'https\://bookdown.org/xiangyun/msg/'
---



<!-- 

# 欢迎 {#welcome .unnumbered}

本书写作过程中收到来自 [Song Li](https://github.com/boltomli)、 [JackieMe](https://github.com/JackieMium) 、 [yang](https://github.com/yiluheihei) 的贡献，在此表示感谢，我们欢迎更多的人参与改进本书。

本书搬迁过程中更新、替换了原稿中的很多代码，现在与本书配套的 R 软件版本是 R version 4.1.0 (2021-05-18)，我们同时也在 R 版本 3.6.1 中完成测试。为方便读者复现本书中的计算结果和统计图形，同时也为了方便在 Travis 上自动测试贡献者提交的 PR 和自动部署每次提交的修改，本书的运行环境已经被打包成 Docker 镜像，托管在 Docker Hub 上，镜像地址是 <https://hub.docker.com/r/xiangyunhuang/msg-book>， 读者可从 Docker Hub 上下载，也可根据目录 `docker/` 下的 Dockerfile 本地构建。


## 版权声明 {#copyright .unnumbered}

本书电子版采用 Creative Commons （简称 CC）许可证“署名 --- 非商业性使用 --- 相同方式共享 2.5 中国大陆”，该许可证的全文可以从 <https://creativecommons.org/licenses/by-nc-sa/2.5/cn/> 获得；一份普通人可以理解的法律文本概要可以从 <https://creativecommons.org/licenses/by-nc-sa/2.5/cn/legalcode> 获得。


\begin{center}\href{https://creativecommons.org/licenses/by-nc-sa/2.5/cn/}{\includegraphics[width=0.3\linewidth]{images/cc-by-nc-sa} }\end{center}

本 CC 许可证赋予读者复制、发行、展览、表演、放映、广播或通过信息网络传播本作品以及创作演绎作品的自由，而无需向原作者征求许可或支付任何费用；本许可证与出版社版权独立，因此复制、传播或演绎本作品也无须征求出版社许可。您需要遵循的条件是：

- 声明原作者的署名（Attribution）：不得将本作品归为自己的劳动
- 不得将本作品用于商业目的（Noncommercial）
- 基于本作品的演绎作品须遵守同样许可证发布（Share Alike）

作者采用 CC 许可证的考虑主要有三点：

- 让读者能免费、自由获得本书，节省经济支出；在有网络和电子文档的时代，我们应该充分利用这些工具的优势，如传播快捷、读者交流反馈方便（以便提高书籍质量）等
- 版权的本来意义不在于控制所有权，它只不过是为了对原创者的一种署名激励；如果版权的存在妨碍了知识的传播，那么本人认为版权就没有太大的意义；CC 许可证中的“非商业”和“同样许可证”限制条款在书籍出版 14 年后会自动取消，即读者可以用于商业目的或更改至其它许可证；CC 许可证规定的 14 年似乎是很长的时间，但读者须知：通常的版权只有在原作者去世后 50 年才会被取消！换句话说，版权告诉我们一个很深刻的哲理：长寿是很重要的
- 自由软件用户往往有某种痴狂的特征，而这种痴狂往往来源于自由软件的分享精神；R 语言让本人受益颇多，这本书可视作是对它的一种回馈；既然 R 语言是自由的，那么本书也将尽量“自由”

尽管 CC 许可证没有限制作品的传播方式，但本作者不愿看到本书被任何人以论坛附件的方式发布在任何论坛（尤其是某某经济论坛），原因是本书稿尚未成熟，或许有诸多不完善之处甚至严重错误，作者在不断更新中，若要传播本书稿给他人，请仅仅给出本书的原始链接 <https://bookdown.org/xiangyun/msg/>，否则作者对传播过程中的错误概不负责。


## 捐赠说明 {#donate .unnumbered}

如果本书对您有任何帮助，您不妨考虑为“统计之都”网站（自愿）捐赠：<https://cosx.org/donate/>，捐赠所得将用于推广统计学和自由统计软件。捐赠之后请及时告知网站管理人员：[admin@cos.name](mailto:admin@cos.name)。

## 软件信息 {#rsession .unnumbered}

本书是在 RStudio 里用 R Markdown [@xie2018] 编辑的，bookdown [@xie2016] 组织各个章节的 Rmd 文件，knitr [@xie2015] 运行 Rmd 文件中的 R 代码块，并将 Rmd 文件转化为 md 文件，借助 [Pandoc](https://pandoc.org/) 将 md 文件转化为 html 和 tex 文件，在 [TinyTeX](https://yihui.org/tinytex/) 的作用下，同时输出 pdf 格式的书籍。


```r
xfun::session_info(packages = c(
  "alphahull", "animation", "aplpack", "rmarkdown", "bookdown",
  "corrplot", "cowplot", "formatR", "fun",
  "GGally", "ggplot2", "igraph", 
  "magick", "maps", "maptools", "MSG", "mvtnorm",
  "pdftools", "plot3D", "plotrix",
  "randomForest", "rgeos", "rgl",
  "scatterplot3d", "showtext", "sna", "sp", "svglite",
  "TeachingDemos", "tikzDevice", "vcd", "vioplot"
))
```

```
## Warning in fun(libname, pkgname): no display name and no $DISPLAY environment
## variable
```

```
## Registered S3 method overwritten by 'GGally':
##   method from   
##   +.gg   ggplot2
```

```
## R version 4.1.0 (2021-05-18)
## Platform: x86_64-apple-darwin17.0 (64-bit)
## Running under: macOS Catalina 10.15.7
## 
## Locale: en_US.UTF-8 / en_US.UTF-8 / en_US.UTF-8 / C / en_US.UTF-8 / en_US.UTF-8
## 
## Package version:
##   abind_1.4.5             alphahull_2.2           animation_2.6          
##   aplpack_1.3.3           askpass_1.1             base64enc_0.1.3        
##   bookdown_0.22           bslib_0.2.5.1           cachem_1.0.5           
##   callr_3.7.0             cli_2.5.0               coda_0.19.4            
##   codetools_0.2.18        colorspace_2.0.1        commonmark_1.7         
##   compiler_4.1.0          corrplot_0.89           cowplot_1.1.1          
##   cpp11_0.2.7             crayon_1.4.1            crosstalk_1.1.1        
##   curl_4.3.1              deldir_0.2.10           digest_0.6.27          
##   dplyr_1.0.6             ellipsis_0.3.2          evaluate_0.14          
##   fansi_0.5.0             farver_2.1.0            fastmap_1.1.0          
##   filehash_2.4.2          forcats_0.5.1           foreign_0.8.81         
##   formatR_1.11            fs_1.5.0                fun_0.3                
##   generics_0.1.0          GGally_2.1.1            ggplot2_3.3.3          
##   glue_1.4.2              goftest_1.2.2           graphics_4.1.0         
##   grDevices_4.1.0         grid_4.1.0              gtable_0.3.0           
##   highr_0.9               hms_1.1.0               htmltools_0.5.1.1      
##   htmlwidgets_1.5.3       httpuv_1.6.1            igraph_1.2.6           
##   isoband_0.2.4           jquerylib_0.1.4         jsonlite_1.7.2         
##   knitr_1.33              labeling_0.4.2          later_1.2.0            
##   lattice_0.20.44         lazyeval_0.2.2          lifecycle_1.0.0        
##   lmtest_0.9.38           magick_2.7.2            magrittr_2.0.1         
##   manipulateWidget_0.11.0 maps_3.3.0              maptools_1.1.1         
##   markdown_1.1            MASS_7.3.54             Matrix_1.3.4           
##   methods_4.1.0           mgcv_1.8.36             mime_0.10              
##   miniUI_0.1.1.1          misc3d_0.9.0            MSG_0.6                
##   munsell_0.5.0           mvtnorm_1.1.2           network_1.17.0         
##   nlme_3.1.152            parallel_4.1.0          pdftools_3.0.1         
##   pillar_1.6.1            pkgconfig_2.0.3         plot3D_1.4             
##   plotrix_3.8.1           plyr_1.8.6              png_0.1.7              
##   polyclip_1.10.0         prettyunits_1.1.1       processx_3.5.2         
##   progress_1.2.2          promises_1.2.0.1        ps_1.6.0               
##   purrr_0.3.4             qpdf_1.1                R.methodsS3_1.8.1      
##   R.oo_1.24.0             R.utils_2.10.1          R6_2.5.0               
##   randomForest_4.6.14     rappdirs_0.3.3          RColorBrewer_1.1.2     
##   Rcpp_1.0.6              reshape_0.8.8           rgeos_0.5.5            
##   rgl_0.106.8             rlang_0.4.11            rmarkdown_2.8          
##   rpart_4.1.15            sass_0.4.0              scales_1.1.1           
##   scatterplot3d_0.3.41    sgeostat_1.0.27         shiny_1.6.0            
##   shinyjs_2.0.0           showtext_0.9-2          showtextdb_3.0         
##   sm_2.2.5.6              sna_2.6                 sourcetools_0.1.7      
##   sp_1.4.5                spatstat_2.1.0          spatstat.core_2.1.2    
##   spatstat.data_2.1.0     spatstat.geom_2.1.0     spatstat.linnet_2.1.1  
##   spatstat.sparse_2.0.0   spatstat.utils_2.1.0    splancs_2.1.42         
##   splines_4.1.0           statnet.common_4.5.0    stats_4.1.0            
##   stringi_1.6.2           stringr_1.4.0           svglite_2.0.0          
##   sys_3.4                 sysfonts_0.8.3          systemfonts_1.0.2      
##   tcltk_4.1.0             TeachingDemos_2.12      tensor_1.5             
##   tibble_3.1.2            tidyr_1.1.3             tidyselect_1.1.1       
##   tikzDevice_0.12.3.1     tinytex_0.32            tools_4.1.0            
##   tripack_1.3.9.1         utf8_1.2.1              utils_4.1.0            
##   vcd_1.4.8               vctrs_0.3.8             vioplot_0.3.6          
##   viridisLite_0.4.0       webshot_0.5.2           withr_2.4.2            
##   xfun_0.23               xtable_1.8.4            yaml_2.2.1             
##   zoo_1.8.9              
## 
## Pandoc version: 2.13
```

## 致谢 {#acknowledgement .unnumbered}

本书写作过程中收到了不少读者反馈，在此一并致谢。感谢魏太云、Dazhi Jiang 和郑冰对本书文字的校对和建议；感谢赵彦云老师对本书书名和写作风格的建议；感谢李皞对写 lattice 系统和 **rgl** 包的提议；感谢李丰的彩蛋建议；感谢王晓伟、李承文、FreemanZY、agri521、annidy、Zhanwu Dai 耗费眼神帮我挑选了本书第一例彩蛋（图 \@ref(fig:point-random)）；感谢殷腾飞增加动态图形系统 GGobi 的建议；感谢方莹提供第 \@ref(chap:data) 章的一些数据指引；本书部分小节的初稿内容来自一些朋友：王晓伟提供了 lattice 一节的初稿，邱怡轩提供 grid 和 rgl 两节的初稿，魏太云提供了《统计词话》的初稿，肖楠提供了 RgoogleMaps 一节的初稿。

最后，我要感谢我的父母和亲人们在 2008 年以来每个长假给我提供绝佳的写作环境，让我心无旁骛地写书；感谢吴喜之老师将 R 这套工具引入中国人民大学统计学院的课堂，以及王星老师在统计计算和非参数统计课堂上对 R 的介绍，没有他们的努力，我也许不会踏进 R 的大门；感谢我的硕士导师赵彦云老师在我的本硕学习期间给我的各种指导；感谢“统计之都”网站的会员们在 [COS 论坛](https://d.cosx.org/) 上 S-Plus
\& R 版块和我的交流，他们的问题也使我意识到了图形知识的需求；感谢周筠老师和卢鸫翔编辑以及出版团队；感谢本书写作期间所有给我提供过帮助的人们。

-->


