# Annotation: Hands-On Exercise 

Now it's your turn to try! 


## The Code

Here's some R code that hasn't been annotated particularly well.

```
library(qqman)
library(beepr)


# The list of datasets

datasets=c("fivehmc.glmmtmb.all.cing","fivehmc.glmmtmb.all.pari","fivemc.glmmtmb.cingulate","fivemc.glmmtmb.parietal")

mod=c("5hmc","5hmc","5mc","5mc") # For labeling purposes
tissues=rep(c("Cingulate","Parietal"),2) # For labeling purposes

if(dir.exists(paste0(home,"/ManhattanPlots"))==FALSE){ # For storing the graphs
  dir.create(paste0(home,"/ManhattanPlots"))
}
tissues.f=c("Cingulate","Cingulate","Parietal","Parietal")
stage=c("limbic","neocortical","limbic","neocortical")

fdr.p=data.frame(t(c(rep(0,4))))
colnames(fdr.p)=c("FC","HolP","tissues","stage")
fdr.p=fdr.p[-1,]

for(ii in 1:length(fdr.files)){
xx=read.table(paste0(home,"/",fdr.files[ii]),row.names=1,skip=1)
xx=cbind(xx,rep(tissues.f[ii],nrow(xx)),rep(stage[ii],nrow(xx)))
colnames(xx)=c("FC","HolP","tissues","stage")
fdr.p=rbind(fdr.p,xx)
}


for(ii in 1:length(datasets)){
data=eval(parse(text=datasets[ii]))

probes=rownames(data) 

# Match the probe names 
if(ii<3){
yy=fdr.p[which(fdr.p[,3]==tissues[ii]),]
yy=yy[match(probes,rownames(yy)),]
yy=yy[which(!is.na(yy[,1])),]

yy.l=yy[which(yy[,4]=="limbic"),]
yy.n=yy[which(yy[,4]=="neocortical"),]

  probes.l=rownames(yy.l)
}else{
  probes.l=rownames(data) 
}

xx.l=match(probes.l,EPIC.manifest@ranges@NAMES)

chrs.l=EPIC.manifest@elementMetadata@listData$chrmA[xx.l] 
#manhattan function requires chromosomes to be noted as numeric vector with X, Y, and MT chrs being 23:25 respectively. 
chrs.l=gsub("chr","",chrs.l) 
chrs.l=gsub("X",23,chrs.l)
chrs.l=gsub("Y",24,chrs.l)
chrs.l=gsub("MT",25,chrs.l)

if(ii<3){
probes.n=rownames(yy.n)
xx.n=match(probes.n,EPIC.manifest@ranges@NAMES)

chrs.n=EPIC.manifest@elementMetadata@listData$chrmA[xx.n] 
#manhattan function requires chromosomes to be noted as numeric vector with X, Y, and MT chrs being 23:25 respectively. 
chrs.n=gsub("chr","",chrs.n) 
chrs.n=gsub("X",23,chrs.n)
chrs.n=gsub("Y",24,chrs.n)
chrs.n=gsub("MT",25,chrs.n)

# Make a dataframe
manh.data.l=data.frame(probes.l,         
           as.numeric(chrs.l),
           EPIC.manifest@ranges@start[xx.l],
           -log10(yy.l[,2]),
           stringsAsFactors = FALSE)

manh.data.n=data.frame(probes.n,         
           as.numeric(chrs.n),
           EPIC.manifest@ranges@start[xx.n],
           -log10(yy.n[,2]),
           stringsAsFactors = FALSE)
colnames(manh.data.l)=colnames(manh.data.n)=c("CPG","CHR","BP","P")

}else{
  manh.data.l=data.frame(probes.l,         
                         as.numeric(chrs.l),
                         EPIC.manifest@ranges@start[xx.l],
                         -log10(data$LimbicVSNoneFDR),
                         -log10(data$NeocorticalVSNoneFDR),
                         stringsAsFactors = FALSE)
  colnames(manh.data.l)=c("CPG","CHR","BP","P","NP")
  manh.data.l=manh.data.l[-which(manh.data.l$NP==Inf),]
  
  xx=unique(which(is.nan(manh.data.l$NP)),which(is.nan(manh.data.l$P)))
  if(length(xx)>0){
  manh.data.l=manh.data.l[-xx,]
  }
}

# Label them as such. 

manh.data.l=manh.data.l[-which(manh.data.l$P==Inf),]
manh.data.l$CPG=as.character(manh.data.l$CPG) # CPG's need to be a character vector
manh.data.l$CHR=as.numeric(manh.data.l$CHR) # Chromsomal locations need to be numeric
manh.data.l$BP= as.numeric(manh.data.l$BP)
manh.data.l=manh.data.l[which(!is.na(manh.data.l$CHR)),]

if(ii<3){
manh.data.n=manh.data.n[-which(manh.data.n$P==Inf),]
manh.data.n$CPG=as.character(manh.data.n$CPG) # CPG's need to be a character vector
manh.data.n$CHR=as.numeric(manh.data.n$CHR) # Chromsomal locations need to be numeric
manh.data.n$BP= as.numeric(manh.data.n$BP)
manh.data.n=manh.data.n[which(!is.na(manh.data.n$CHR)),]

}

# Manhattan Plot for Limbic data
jpeg(paste0(home,"/ManhattanPlots/",datasets[ii],"MidManhattan2.jpeg"))
if(ii<3){
sig=manh.data.l$CPG[which(manh.data.l$P>3)]
manhattan(manh.data.l,chr="CHR",bp="BP",p="P",snp="CPG",logp=F,ylim=c(0,round(max(manh.data.l$P))+10),highlight=sig,chrlabs=c(1:22, "X", "Y"),suggestiveline=FALSE,genomewideline=TRUE,main=paste( mod[ii],tissues[ii],"Mid Stage Disease"))
}else{
sig=manh.data.l$CPG[which(manh.data.l$P>3)]
manhattan(manh.data.l,chr="CHR",bp="BP",p="P",snp="CPG",ylim=c(0,round(max(manh.data.l$P[!is.na(manh.data.l$P)]))),logp=F,highlight=sig,chrlabs=c(1:22, "X", "Y"),suggestiveline=FALSE,genomewideline=TRUE,main=paste( mod[ii],tissues[ii],"Mid Stage Disease"))
}
# highlight probes
abline(h=-log10(.001),col="red") 
dev.off()

# Manhattan Plot for Neocortical data
jpeg(paste0(home,"/ManhattanPlots/",datasets[ii],"LateManhattan2.jpeg"))
if(ii<3){
  sig=manh.data.n$CPG[which(manh.data.n$P>3)]
  manhattan(manh.data.n,chr="CHR",bp="BP",p="P",snp="CPG",ylim=c(0,round(max(manh.data.l$P))+10),logp=F,highlight=sig,chrlabs=c(1:22, "X", "Y"),suggestiveline=FALSE,genomewideline=TRUE,main=paste(mod[ii],tissues[ii],"Late Stage Disease"))
}else{
  sig=manh.data.l$CPG[which(manh.data.l$NP>3)]
  manhattan(manh.data.l,chr="CHR",bp="BP",p="NP",snp="CPG",ylim=c(0,round(max(manh.data.l$NP))),logp=F,highlight=sig,chrlabs=c(1:22, "X", "Y"),suggestiveline=FALSE,genomewideline=TRUE,main=paste(mod[ii],tissues[ii],"Late Stage Disease"))
}
  abline(h=-log10(.001),col="red")
  dev.off()


}
# Just a nifty way to signal that your graphs are finished being made. 
beep(sound=2)
```

## Questions

1. Create a README file for this code. Make sure that it includes general purpose of the project, instructions on how to re-run the project, any software required by the project, both input and output file descriptions, and descriptions of any additional tools included in the project.

2. How can the annotation for this section be improved?

```
# Make a dataframe
manh.data.l=data.frame(probes.l,         
           as.numeric(chrs.l),
           EPIC.manifest@ranges@start[xx.l],
           -log10(yy.l[,2]),
           stringsAsFactors = FALSE)

manh.data.n=data.frame(probes.n,         
           as.numeric(chrs.n),
           EPIC.manifest@ranges@start[xx.n],
           -log10(yy.n[,2]),
           stringsAsFactors = FALSE)
colnames(manh.data.l)=colnames(manh.data.n)=c("CPG","CHR","BP","P")
```


```r
devtools::session_info()
```

```
## ─ Session info ───────────────────────────────────────────────────────────────
##  setting  value                       
##  version  R version 4.0.2 (2020-06-22)
##  os       Ubuntu 20.04.5 LTS          
##  system   x86_64, linux-gnu           
##  ui       X11                         
##  language (EN)                        
##  collate  en_US.UTF-8                 
##  ctype    en_US.UTF-8                 
##  tz       Etc/UTC                     
##  date     2023-11-01                  
## 
## ─ Packages ───────────────────────────────────────────────────────────────────
##  package     * version date       lib source                            
##  assertthat    0.2.1   2019-03-21 [1] RSPM (R 4.0.5)                    
##  bookdown      0.24    2023-03-28 [1] Github (rstudio/bookdown@88bc4ea) 
##  bslib         0.4.2   2022-12-16 [1] CRAN (R 4.0.2)                    
##  cachem        1.0.7   2023-02-24 [1] CRAN (R 4.0.2)                    
##  callr         3.5.0   2020-10-08 [1] RSPM (R 4.0.2)                    
##  cli           3.6.1   2023-03-23 [1] CRAN (R 4.0.2)                    
##  crayon        1.3.4   2017-09-16 [1] RSPM (R 4.0.0)                    
##  desc          1.2.0   2018-05-01 [1] RSPM (R 4.0.3)                    
##  devtools      2.3.2   2020-09-18 [1] RSPM (R 4.0.3)                    
##  digest        0.6.25  2020-02-23 [1] RSPM (R 4.0.0)                    
##  ellipsis      0.3.1   2020-05-15 [1] RSPM (R 4.0.3)                    
##  evaluate      0.20    2023-01-17 [1] CRAN (R 4.0.2)                    
##  fansi         0.4.1   2020-01-08 [1] RSPM (R 4.0.0)                    
##  fastmap       1.1.1   2023-02-24 [1] CRAN (R 4.0.2)                    
##  fs            1.5.0   2020-07-31 [1] RSPM (R 4.0.3)                    
##  glue          1.4.2   2020-08-27 [1] RSPM (R 4.0.5)                    
##  hms           0.5.3   2020-01-08 [1] RSPM (R 4.0.0)                    
##  htmltools     0.5.5   2023-03-23 [1] CRAN (R 4.0.2)                    
##  jquerylib     0.1.4   2021-04-26 [1] CRAN (R 4.0.2)                    
##  jsonlite      1.7.1   2020-09-07 [1] RSPM (R 4.0.2)                    
##  knitr         1.33    2023-03-28 [1] Github (yihui/knitr@a1052d1)      
##  lifecycle     1.0.3   2022-10-07 [1] CRAN (R 4.0.2)                    
##  magrittr      2.0.3   2022-03-30 [1] CRAN (R 4.0.2)                    
##  memoise       2.0.1   2021-11-26 [1] CRAN (R 4.0.2)                    
##  ottrpal       1.0.1   2023-03-28 [1] Github (jhudsl/ottrpal@151e412)   
##  pillar        1.9.0   2023-03-22 [1] CRAN (R 4.0.2)                    
##  pkgbuild      1.1.0   2020-07-13 [1] RSPM (R 4.0.2)                    
##  pkgconfig     2.0.3   2019-09-22 [1] RSPM (R 4.0.3)                    
##  pkgload       1.1.0   2020-05-29 [1] RSPM (R 4.0.3)                    
##  prettyunits   1.1.1   2020-01-24 [1] RSPM (R 4.0.3)                    
##  processx      3.4.4   2020-09-03 [1] RSPM (R 4.0.2)                    
##  ps            1.4.0   2020-10-07 [1] RSPM (R 4.0.2)                    
##  R6            2.4.1   2019-11-12 [1] RSPM (R 4.0.0)                    
##  readr         1.4.0   2020-10-05 [1] RSPM (R 4.0.2)                    
##  remotes       2.2.0   2020-07-21 [1] RSPM (R 4.0.3)                    
##  rlang         1.1.0   2023-03-14 [1] CRAN (R 4.0.2)                    
##  rmarkdown     2.10    2023-03-28 [1] Github (rstudio/rmarkdown@02d3c25)
##  rprojroot     2.0.3   2022-04-02 [1] CRAN (R 4.0.2)                    
##  sass          0.4.5   2023-01-24 [1] CRAN (R 4.0.2)                    
##  sessioninfo   1.1.1   2018-11-05 [1] RSPM (R 4.0.3)                    
##  stringi       1.5.3   2020-09-09 [1] RSPM (R 4.0.3)                    
##  stringr       1.4.0   2019-02-10 [1] RSPM (R 4.0.3)                    
##  testthat      3.0.1   2023-03-28 [1] Github (R-lib/testthat@e99155a)   
##  tibble        3.2.1   2023-03-20 [1] CRAN (R 4.0.2)                    
##  usethis       1.6.3   2020-09-17 [1] RSPM (R 4.0.2)                    
##  utf8          1.1.4   2018-05-24 [1] RSPM (R 4.0.3)                    
##  vctrs         0.6.1   2023-03-22 [1] CRAN (R 4.0.2)                    
##  withr         2.3.0   2020-09-22 [1] RSPM (R 4.0.2)                    
##  xfun          0.26    2023-03-28 [1] Github (yihui/xfun@74c2a66)       
##  yaml          2.2.1   2020-02-01 [1] RSPM (R 4.0.3)                    
## 
## [1] /usr/local/lib/R/site-library
## [2] /usr/local/lib/R/library
```
