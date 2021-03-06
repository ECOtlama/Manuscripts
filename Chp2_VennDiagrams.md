# Venn Diagrams 

Calculating the overlap in loci identified for all the different datasets. 


# MAC filtered data

pwd
/Users/alexjvr/2016RADAnalysis/3_CH.landscapeGenomics/subsets/Venn/CHP2.MACfilter



I'm showing: 

1. Venn Diagram within analysis for 
  
  1. LFMM
  
  2. bayEnv2

2. overlap between LFMM, Bayenv2, PCadapt, XtX, and Bayescan within each region (i.e. 6 plots)

3. Overlap between all candidate loci identified for CHN, CHS, CZ

4. Overlap between all candidate loci identified for CHS, CHS.TI, CHS.VS

5. Overlap between all candidate loci identified by 2+ methods fo CHall, CHN, CHS, CZ

6. Overlap between all candidate loci identified by 2+ methods for CHS, CHS.TI, CHS.VS

7. Overlap in BestLoci (from GF) for each variable (ie. shared adaptive variation)

8. Overlap of BestLoci within a region (i.e. pleiotropy)


### 1.1 Venn Diagram for loci within LFMM

These have already been drawn. 

See: https://github.com/alexjvr1/Manuscripts/blob/master/Chp2_CHdata_LFMM.md



Venn.CHN.n5.LFMMonly_20171007.pdf

Venn.CHS.n5.LFMMonly_20171007.pdf

Venn.CZ.n5.LFMMonly_20171007.pdf

Venn.CHS.VS.n5.LFMMonly_20171007.pdf

Venn.CHS.TI.n5.LFMMonly_20171007.pdf




### 1.2 Venn Diagram for loci within BayEnv2

19 Oct 2017: I changed the order of these variables so that they're the same as the LFMM Venn diagram. 

Initially: 

rad, shadow, temp, pcpt60d, day10 (note that temp and pcpt are swapped around - this is the correct order but my initial figures had pcpt and temp swapped)

Current order as in the code and like LFMM: 

shadow, rad, pcpt, day10cm, temp. 


##### CHall

```
load("CHP2.BayEnv2.fgcz.RData")

library(VennDiagram)

d1 <- length(CHall.shadow.days.bayenv.candidates.names)
d2 <- length(CHall.rad.bayenv.candidates.names)
d3 <- length(CHall.pcpt.bayenv.candidates.names)
d4 <- length(CHall.day.10cm.bayenv.candidates.names)
d5 <- length(CHall.temp.bayenv.candidates.names)

d12 <- length(Reduce(intersect, list(CHall.rad.bayenv.candidates.names, CHall.shadow.days.bayenv.candidates.names)))
d25 <- length(Reduce(intersect, list(CHall.rad.bayenv.candidates.names, CHall.temp.bayenv.candidates.names)))
d23 <- length(Reduce(intersect, list(CHall.rad.bayenv.candidates.names, CHall.pcpt.bayenv.candidates.names)))
d24 <- length(Reduce(intersect, list(CHall.rad.bayenv.candidates.names, CHall.day.10cm.bayenv.candidates.names)))
d15 <- length(Reduce(intersect, list(CHall.shadow.days.bayenv.candidates.names, CHall.temp.bayenv.candidates.names)))
d13 <- length(Reduce(intersect, list(CHall.shadow.days.bayenv.candidates.names, CHall.pcpt.bayenv.candidates.names)))
d14 <- length(Reduce(intersect, list(CHall.shadow.days.bayenv.candidates.names, CHall.day.10cm.bayenv.candidates.names)))
d35 <- length(Reduce(intersect, list(CHall.temp.bayenv.candidates.names, CHall.pcpt.bayenv.candidates.names)))
d45 <- length(Reduce(intersect, list(CHall.temp.bayenv.candidates.names, CHall.day.10cm.bayenv.candidates.names)))
d34 <- length(Reduce(intersect, list(CHall.pcpt.bayenv.candidates.names, CHall.day.10cm.bayenv.candidates.names)))

d125 <- length(Reduce(intersect, list(CHall.rad.bayenv.candidates.names, CHall.shadow.days.bayenv.candidates.names,CHall.temp.bayenv.candidates.names)))
d123 <- length(Reduce(intersect, list(CHall.rad.bayenv.candidates.names, CHall.shadow.days.bayenv.candidates.names,CHall.pcpt.bayenv.candidates.names)))
d124 <- length(Reduce(intersect, list(CHall.rad.bayenv.candidates.names, CHall.shadow.days.bayenv.candidates.names,CHall.day.10cm.bayenv.candidates.names)))
d135 <- length(Reduce(intersect, list(CHall.shadow.days.bayenv.candidates.names, CHall.temp.bayenv.candidates.names,CHall.pcpt.bayenv.candidates.names)))
d235 <- length(Reduce(intersect, list(CHall.rad.bayenv.candidates.names, CHall.temp.bayenv.candidates.names,CHall.pcpt.bayenv.candidates.names)))
d245 <- length(Reduce(intersect, list(CHall.rad.bayenv.candidates.names, CHall.temp.bayenv.candidates.names,CHall.day.10cm.bayenv.candidates.names)))
d234 <- length(Reduce(intersect, list(CHall.rad.bayenv.candidates.names, CHall.pcpt.bayenv.candidates.names,CHall.day.10cm.bayenv.candidates.names)))
d145 <- length(Reduce(intersect, list(CHall.shadow.days.bayenv.candidates.names, CHall.temp.bayenv.candidates.names,CHall.day.10cm.bayenv.candidates.names)))
d134 <- length(Reduce(intersect, list(CHall.shadow.days.bayenv.candidates.names, CHall.pcpt.bayenv.candidates.names,CHall.day.10cm.bayenv.candidates.names)))
d345 <- length(Reduce(intersect, list(CHall.temp.bayenv.candidates.names, CHall.pcpt.bayenv.candidates.names,CHall.day.10cm.bayenv.candidates.names)))


d1235 <- length(Reduce(intersect, list(CHall.shadow.days.bayenv.candidates.names, CHall.temp.bayenv.candidates.names,
CHall.pcpt.bayenv.candidates.names, CHall.rad.bayenv.candidates.names)))
d1245 <- length(Reduce(intersect, list(CHall.shadow.days.bayenv.candidates.names, CHall.temp.bayenv.candidates.names,
CHall.day.10cm.bayenv.candidates.names, CHall.rad.bayenv.candidates.names)))
d1345 <- length(Reduce(intersect, list(CHall.shadow.days.bayenv.candidates.names, CHall.temp.bayenv.candidates.names,
CHall.pcpt.bayenv.candidates.names, CHall.day.10cm.bayenv.candidates.names)))
d1234 <- length(Reduce(intersect, list(CHall.shadow.days.bayenv.candidates.names, CHall.rad.bayenv.candidates.names,
CHall.pcpt.bayenv.candidates.names, CHall.day.10cm.bayenv.candidates.names)))
d2345 <- length(Reduce(intersect, list(CHall.temp.bayenv.candidates.names, CHall.rad.bayenv.candidates.names,
CHall.pcpt.bayenv.candidates.names, CHall.day.10cm.bayenv.candidates.names)))

d12345 <- length(Reduce(intersect, list(CHall.rad.bayenv.candidates.names, CHall.shadow.days.bayenv.candidates.names, CHall.temp.bayenv.candidates.names, 
CHall.pcpt.bayenv.candidates.names, CHall.day.10cm.bayenv.candidates.names)))

pdf("CHall.bayenv2.VENN.pdf")
draw.quintuple.venn(area1=d1, area2=d2, area3=d3, area4=d4, area5=d5,
n12=d12, n13=d13, n14=d14, n15=d15, n23=d23, n24=d24, n25=d25, n34=d34, n35=d35, n45=d45,
n123=d123, n124=d124, n125=d125, n134=d134, n135=d135, n145=d145, n234=d234, n235=d235, n245=d245, n345=d345,
n1234=d1234, n1235=d1235, n1245=d1245, n1345=d1345, n2345=d2345, n12345=d12345, 
category=c("CHall.shadow.days", "CHall.rad", "CHall.pcpt", "CHall.day.10cm", "CHall.temp"),
lty="blank", 
fill=c("yellow", "orange", "skyblue1", "skyblue3", "blue")
)
dev.off()
```


##### CHN

```
#Check that all the lists have names in them. Where no candidates were found, there’ll only be an “X.”
#These can be made to <- NULL so that they aren’t reflected in the Venn

library(VennDiagram)

d1 <- length(CHN.shadow.days.bayenv.candidates.names)
d2 <- length(CHN.rad.bayenv.candidates.names)
d3 <- length(CHN.pcpt.bayenv.candidates.names)
d4 <- length(CHN.day.10cm.bayenv.candidates.names)
d5 <- length(CHN.temp.bayenv.candidates.names)

d12 <- length(Reduce(intersect, list(CHN.rad.bayenv.candidates.names, CHN.shadow.days.bayenv.candidates.names)))
d25 <- length(Reduce(intersect, list(CHN.rad.bayenv.candidates.names, CHN.temp.bayenv.candidates.names)))
d23 <- length(Reduce(intersect, list(CHN.rad.bayenv.candidates.names, CHN.pcpt.bayenv.candidates.names)))
d24 <- length(Reduce(intersect, list(CHN.rad.bayenv.candidates.names, CHN.day.10cm.bayenv.candidates.names)))
d15 <- length(Reduce(intersect, list(CHN.shadow.days.bayenv.candidates.names, CHN.temp.bayenv.candidates.names)))
d13 <- length(Reduce(intersect, list(CHN.shadow.days.bayenv.candidates.names, CHN.pcpt.bayenv.candidates.names)))
d14 <- length(Reduce(intersect, list(CHN.shadow.days.bayenv.candidates.names, CHN.day.10cm.bayenv.candidates.names)))
d35 <- length(Reduce(intersect, list(CHN.temp.bayenv.candidates.names, CHN.pcpt.bayenv.candidates.names)))
d45 <- length(Reduce(intersect, list(CHN.temp.bayenv.candidates.names, CHN.day.10cm.bayenv.candidates.names)))
d34 <- length(Reduce(intersect, list(CHN.pcpt.bayenv.candidates.names, CHN.day.10cm.bayenv.candidates.names)))

d125 <- length(Reduce(intersect, list(CHN.rad.bayenv.candidates.names, CHN.shadow.days.bayenv.candidates.names,CHN.temp.bayenv.candidates.names)))
d123 <- length(Reduce(intersect, list(CHN.rad.bayenv.candidates.names, CHN.shadow.days.bayenv.candidates.names,CHN.pcpt.bayenv.candidates.names)))
d124 <- length(Reduce(intersect, list(CHN.rad.bayenv.candidates.names, CHN.shadow.days.bayenv.candidates.names,CHN.day.10cm.bayenv.candidates.names)))
d135 <- length(Reduce(intersect, list(CHN.shadow.days.bayenv.candidates.names, CHN.temp.bayenv.candidates.names,CHN.pcpt.bayenv.candidates.names)))
d235 <- length(Reduce(intersect, list(CHN.rad.bayenv.candidates.names, CHN.temp.bayenv.candidates.names,CHN.pcpt.bayenv.candidates.names)))
d245 <- length(Reduce(intersect, list(CHN.rad.bayenv.candidates.names, CHN.temp.bayenv.candidates.names,CHN.day.10cm.bayenv.candidates.names)))
d234 <- length(Reduce(intersect, list(CHN.rad.bayenv.candidates.names, CHN.pcpt.bayenv.candidates.names,CHN.day.10cm.bayenv.candidates.names)))
d145 <- length(Reduce(intersect, list(CHN.shadow.days.bayenv.candidates.names, CHN.temp.bayenv.candidates.names,CHN.day.10cm.bayenv.candidates.names)))
d134 <- length(Reduce(intersect, list(CHN.shadow.days.bayenv.candidates.names, CHN.pcpt.bayenv.candidates.names,CHN.day.10cm.bayenv.candidates.names)))
d345 <- length(Reduce(intersect, list(CHN.temp.bayenv.candidates.names, CHN.pcpt.bayenv.candidates.names,CHN.day.10cm.bayenv.candidates.names)))


d1235 <- length(Reduce(intersect, list(CHN.shadow.days.bayenv.candidates.names, CHN.temp.bayenv.candidates.names,
CHN.pcpt.bayenv.candidates.names, CHN.rad.bayenv.candidates.names)))
d1245 <- length(Reduce(intersect, list(CHN.shadow.days.bayenv.candidates.names, CHN.temp.bayenv.candidates.names,
CHN.day.10cm.bayenv.candidates.names, CHN.rad.bayenv.candidates.names)))
d1345 <- length(Reduce(intersect, list(CHN.shadow.days.bayenv.candidates.names, CHN.temp.bayenv.candidates.names,
CHN.pcpt.bayenv.candidates.names, CHN.day.10cm.bayenv.candidates.names)))
d1234 <- length(Reduce(intersect, list(CHN.shadow.days.bayenv.candidates.names, CHN.rad.bayenv.candidates.names,
CHN.pcpt.bayenv.candidates.names, CHN.day.10cm.bayenv.candidates.names)))
d2345 <- length(Reduce(intersect, list(CHN.temp.bayenv.candidates.names, CHN.rad.bayenv.candidates.names,
CHN.pcpt.bayenv.candidates.names, CHN.day.10cm.bayenv.candidates.names)))

d12345 <- length(Reduce(intersect, list(CHN.rad.bayenv.candidates.names, CHN.shadow.days.bayenv.candidates.names, CHN.temp.bayenv.candidates.names, 
CHN.pcpt.bayenv.candidates.names, CHN.day.10cm.bayenv.candidates.names)))

pdf("CHN.bayenv2.20171007.VENN.pdf")
draw.quintuple.venn(area1=d1, area2=d2, area3=d3, area4=d4, area5=d5,
n12=d12, n13=d13, n14=d14, n15=d15, n23=d23, n24=d24, n25=d25, n34=d34, n35=d35, n45=d45,
n123=d123, n124=d124, n125=d125, n134=d134, n135=d135, n145=d145, n234=d234, n235=d235, n245=d245, n345=d345,
n1234=d1234, n1235=d1235, n1245=d1245, n1345=d1345, n2345=d2345, n12345=d12345, 
category=c("CHN.shadow.days", "CHN.rad", "CHN.pcpt", "CHN.day.10cm", "CHN.temp"),
lty="blank", 
fill=c("yellow", "orange", "skyblue1", "skyblue3", "blue")
)
dev.off()



```



##### CHS

```
library(VennDiagram)

d1 <- length(CHS.shadow.days.bayenv.candidates.names)
d2 <- length(CHS.rad.bayenv.candidates.names)
d3 <- length(CHS.pcpt.bayenv.candidates.names)
d4 <- length(CHS.day.10cm.bayenv.candidates.names)
d5 <- length(CHS.temp.bayenv.candidates.names)

d12 <- length(Reduce(intersect, list(CHS.rad.bayenv.candidates.names, CHS.shadow.days.bayenv.candidates.names)))
d25 <- length(Reduce(intersect, list(CHS.rad.bayenv.candidates.names, CHS.temp.bayenv.candidates.names)))
d23 <- length(Reduce(intersect, list(CHS.rad.bayenv.candidates.names, CHS.pcpt.bayenv.candidates.names)))
d24 <- length(Reduce(intersect, list(CHS.rad.bayenv.candidates.names, CHS.day.10cm.bayenv.candidates.names)))
d15 <- length(Reduce(intersect, list(CHS.shadow.days.bayenv.candidates.names, CHS.temp.bayenv.candidates.names)))
d13 <- length(Reduce(intersect, list(CHS.shadow.days.bayenv.candidates.names, CHS.pcpt.bayenv.candidates.names)))
d14 <- length(Reduce(intersect, list(CHS.shadow.days.bayenv.candidates.names, CHS.day.10cm.bayenv.candidates.names)))
d35 <- length(Reduce(intersect, list(CHS.temp.bayenv.candidates.names, CHS.pcpt.bayenv.candidates.names)))
d45 <- length(Reduce(intersect, list(CHS.temp.bayenv.candidates.names, CHS.day.10cm.bayenv.candidates.names)))
d34 <- length(Reduce(intersect, list(CHS.pcpt.bayenv.candidates.names, CHS.day.10cm.bayenv.candidates.names)))

d125 <- length(Reduce(intersect, list(CHS.rad.bayenv.candidates.names, CHS.shadow.days.bayenv.candidates.names,CHS.temp.bayenv.candidates.names)))
d123 <- length(Reduce(intersect, list(CHS.rad.bayenv.candidates.names, CHS.shadow.days.bayenv.candidates.names,CHS.pcpt.bayenv.candidates.names)))
d124 <- length(Reduce(intersect, list(CHS.rad.bayenv.candidates.names, CHS.shadow.days.bayenv.candidates.names,CHS.day.10cm.bayenv.candidates.names)))
d135 <- length(Reduce(intersect, list(CHS.shadow.days.bayenv.candidates.names, CHS.temp.bayenv.candidates.names,CHS.pcpt.bayenv.candidates.names)))
d235 <- length(Reduce(intersect, list(CHS.rad.bayenv.candidates.names, CHS.temp.bayenv.candidates.names,CHS.pcpt.bayenv.candidates.names)))
d245 <- length(Reduce(intersect, list(CHS.rad.bayenv.candidates.names, CHS.temp.bayenv.candidates.names,CHS.day.10cm.bayenv.candidates.names)))
d234 <- length(Reduce(intersect, list(CHS.rad.bayenv.candidates.names, CHS.pcpt.bayenv.candidates.names,CHS.day.10cm.bayenv.candidates.names)))
d145 <- length(Reduce(intersect, list(CHS.shadow.days.bayenv.candidates.names, CHS.temp.bayenv.candidates.names,CHS.day.10cm.bayenv.candidates.names)))
d134 <- length(Reduce(intersect, list(CHS.shadow.days.bayenv.candidates.names, CHS.pcpt.bayenv.candidates.names,CHS.day.10cm.bayenv.candidates.names)))
d345 <- length(Reduce(intersect, list(CHS.temp.bayenv.candidates.names, CHS.pcpt.bayenv.candidates.names,CHS.day.10cm.bayenv.candidates.names)))


d1235 <- length(Reduce(intersect, list(CHS.shadow.days.bayenv.candidates.names, CHS.temp.bayenv.candidates.names,
CHS.pcpt.bayenv.candidates.names, CHS.rad.bayenv.candidates.names)))
d1245 <- length(Reduce(intersect, list(CHS.shadow.days.bayenv.candidates.names, CHS.temp.bayenv.candidates.names,
CHS.day.10cm.bayenv.candidates.names, CHS.rad.bayenv.candidates.names)))
d1345 <- length(Reduce(intersect, list(CHS.shadow.days.bayenv.candidates.names, CHS.temp.bayenv.candidates.names,
CHS.pcpt.bayenv.candidates.names, CHS.day.10cm.bayenv.candidates.names)))
d1234 <- length(Reduce(intersect, list(CHS.shadow.days.bayenv.candidates.names, CHS.rad.bayenv.candidates.names,
CHS.pcpt.bayenv.candidates.names, CHS.day.10cm.bayenv.candidates.names)))
d2345 <- length(Reduce(intersect, list(CHS.temp.bayenv.candidates.names, CHS.rad.bayenv.candidates.names,
CHS.pcpt.bayenv.candidates.names, CHS.day.10cm.bayenv.candidates.names)))

d12345 <- length(Reduce(intersect, list(CHS.rad.bayenv.candidates.names, CHS.shadow.days.bayenv.candidates.names, CHS.temp.bayenv.candidates.names, 
CHS.pcpt.bayenv.candidates.names, CHS.day.10cm.bayenv.candidates.names)))

pdf("CHS.bayenv2.VENN_20171020.pdf")
draw.quintuple.venn(area1=d1, area2=d2, area3=d3, area4=d4, area5=d5,
n12=d12, n13=d13, n14=d14, n15=d15, n23=d23, n24=d24, n25=d25, n34=d34, n35=d35, n45=d45,
n123=d123, n124=d124, n125=d125, n134=d134, n135=d135, n145=d145, n234=d234, n235=d235, n245=d245, n345=d345,
n1234=d1234, n1235=d1235, n1245=d1245, n1345=d1345, n2345=d2345, n12345=d12345, 
category=c("CHS.shadow.days", "CHS.rad", "CHS.pcpt", "CHS.day.10cm", "CHS.temp"),
lty="blank", 
fill=c("yellow", "orange", "skyblue1", "skyblue3", "blue")
)
dev.off()



```



##### CZ
```
library(VennDiagram)

d1 <- length(CZ.shadow.days.bayenv.candidates.names)
d2 <- length(CZ.rad.bayenv.candidates.names)
d3 <- length(CZ.pcpt.bayenv.candidates.names)
d4 <- length(CZ.day.10cm.bayenv.candidates.names)
d5 <- length(CZ.temp.bayenv.candidates.names)

d12 <- length(Reduce(intersect, list(CZ.rad.bayenv.candidates.names, CZ.shadow.days.bayenv.candidates.names)))
d25 <- length(Reduce(intersect, list(CZ.rad.bayenv.candidates.names, CZ.temp.bayenv.candidates.names)))
d23 <- length(Reduce(intersect, list(CZ.rad.bayenv.candidates.names, CZ.pcpt.bayenv.candidates.names)))
d24 <- length(Reduce(intersect, list(CZ.rad.bayenv.candidates.names, CZ.day.10cm.bayenv.candidates.names)))
d15 <- length(Reduce(intersect, list(CZ.shadow.days.bayenv.candidates.names, CZ.temp.bayenv.candidates.names)))
d13 <- length(Reduce(intersect, list(CZ.shadow.days.bayenv.candidates.names, CZ.pcpt.bayenv.candidates.names)))
d14 <- length(Reduce(intersect, list(CZ.shadow.days.bayenv.candidates.names, CZ.day.10cm.bayenv.candidates.names)))
d35 <- length(Reduce(intersect, list(CZ.temp.bayenv.candidates.names, CZ.pcpt.bayenv.candidates.names)))
d45 <- length(Reduce(intersect, list(CZ.temp.bayenv.candidates.names, CZ.day.10cm.bayenv.candidates.names)))
d34 <- length(Reduce(intersect, list(CZ.pcpt.bayenv.candidates.names, CZ.day.10cm.bayenv.candidates.names)))

d125 <- length(Reduce(intersect, list(CZ.rad.bayenv.candidates.names, CZ.shadow.days.bayenv.candidates.names,CZ.temp.bayenv.candidates.names)))
d123 <- length(Reduce(intersect, list(CZ.rad.bayenv.candidates.names, CZ.shadow.days.bayenv.candidates.names,CZ.pcpt.bayenv.candidates.names)))
d124 <- length(Reduce(intersect, list(CZ.rad.bayenv.candidates.names, CZ.shadow.days.bayenv.candidates.names,CZ.day.10cm.bayenv.candidates.names)))
d135 <- length(Reduce(intersect, list(CZ.shadow.days.bayenv.candidates.names, CZ.temp.bayenv.candidates.names,CZ.pcpt.bayenv.candidates.names)))
d235 <- length(Reduce(intersect, list(CZ.rad.bayenv.candidates.names, CZ.temp.bayenv.candidates.names,CZ.pcpt.bayenv.candidates.names)))
d245 <- length(Reduce(intersect, list(CZ.rad.bayenv.candidates.names, CZ.temp.bayenv.candidates.names,CZ.day.10cm.bayenv.candidates.names)))
d234 <- length(Reduce(intersect, list(CZ.rad.bayenv.candidates.names, CZ.pcpt.bayenv.candidates.names,CZ.day.10cm.bayenv.candidates.names)))
d145 <- length(Reduce(intersect, list(CZ.shadow.days.bayenv.candidates.names, CZ.temp.bayenv.candidates.names,CZ.day.10cm.bayenv.candidates.names)))
d134 <- length(Reduce(intersect, list(CZ.shadow.days.bayenv.candidates.names, CZ.pcpt.bayenv.candidates.names,CZ.day.10cm.bayenv.candidates.names)))
d345 <- length(Reduce(intersect, list(CZ.temp.bayenv.candidates.names, CZ.pcpt.bayenv.candidates.names,CZ.day.10cm.bayenv.candidates.names)))


d1235 <- length(Reduce(intersect, list(CZ.shadow.days.bayenv.candidates.names, CZ.temp.bayenv.candidates.names,
CZ.pcpt.bayenv.candidates.names, CZ.rad.bayenv.candidates.names)))
d1245 <- length(Reduce(intersect, list(CZ.shadow.days.bayenv.candidates.names, CZ.temp.bayenv.candidates.names,
CZ.day.10cm.bayenv.candidates.names, CZ.rad.bayenv.candidates.names)))
d1345 <- length(Reduce(intersect, list(CZ.shadow.days.bayenv.candidates.names, CZ.temp.bayenv.candidates.names,
CZ.pcpt.bayenv.candidates.names, CZ.day.10cm.bayenv.candidates.names)))
d1234 <- length(Reduce(intersect, list(CZ.shadow.days.bayenv.candidates.names, CZ.rad.bayenv.candidates.names,
CZ.pcpt.bayenv.candidates.names, CZ.day.10cm.bayenv.candidates.names)))
d2345 <- length(Reduce(intersect, list(CZ.temp.bayenv.candidates.names, CZ.rad.bayenv.candidates.names,
CZ.pcpt.bayenv.candidates.names, CZ.day.10cm.bayenv.candidates.names)))

d12345 <- length(Reduce(intersect, list(CZ.rad.bayenv.candidates.names, CZ.shadow.days.bayenv.candidates.names, CZ.temp.bayenv.candidates.names, 
CZ.pcpt.bayenv.candidates.names, CZ.day.10cm.bayenv.candidates.names)))

pdf("CZ.bayenv2.VENN_20171020.pdf")
draw.quintuple.venn(area1=d1, area2=d2, area3=d3, area4=d4, area5=d5,
n12=d12, n13=d13, n14=d14, n15=d15, n23=d23, n24=d24, n25=d25, n34=d34, n35=d35, n45=d45,
n123=d123, n124=d124, n125=d125, n134=d134, n135=d135, n145=d145, n234=d234, n235=d235, n245=d245, n345=d345,
n1234=d1234, n1235=d1235, n1245=d1245, n1345=d1345, n2345=d2345, n12345=d12345, 
category=c("CZ.shadow.days", "CZ.rad", "CZ.pcpt", "CZ.day.10cm", "CZ.temp"),
lty="blank", 
fill=c("yellow", "orange", "skyblue1", "skyblue3", "blue")
)
dev.off()


```



##### CHS.VS
```
library(VennDiagram)

d1 <- length(CHS.VS.shadow.days.bayenv.candidates.names)
d2 <- length(CHS.VS.rad.bayenv.candidates.names)
d3 <- length(CHS.VS.pcpt.bayenv.candidates.names)
d4 <- length(CHS.VS.day.10cm.bayenv.candidates.names)
d5 <- length(CHS.VS.temp.bayenv.candidates.names)

d12 <- length(Reduce(intersect, list(CHS.VS.rad.bayenv.candidates.names, CHS.VS.shadow.days.bayenv.candidates.names)))
d25 <- length(Reduce(intersect, list(CHS.VS.rad.bayenv.candidates.names, CHS.VS.temp.bayenv.candidates.names)))
d23 <- length(Reduce(intersect, list(CHS.VS.rad.bayenv.candidates.names, CHS.VS.pcpt.bayenv.candidates.names)))
d24 <- length(Reduce(intersect, list(CHS.VS.rad.bayenv.candidates.names, CHS.VS.day.10cm.bayenv.candidates.names)))
d15 <- length(Reduce(intersect, list(CHS.VS.shadow.days.bayenv.candidates.names, CHS.VS.temp.bayenv.candidates.names)))
d13 <- length(Reduce(intersect, list(CHS.VS.shadow.days.bayenv.candidates.names, CHS.VS.pcpt.bayenv.candidates.names)))
d14 <- length(Reduce(intersect, list(CHS.VS.shadow.days.bayenv.candidates.names, CHS.VS.day.10cm.bayenv.candidates.names)))
d35 <- length(Reduce(intersect, list(CHS.VS.temp.bayenv.candidates.names, CHS.VS.pcpt.bayenv.candidates.names)))
d45 <- length(Reduce(intersect, list(CHS.VS.temp.bayenv.candidates.names, CHS.VS.day.10cm.bayenv.candidates.names)))
d34 <- length(Reduce(intersect, list(CHS.VS.pcpt.bayenv.candidates.names, CHS.VS.day.10cm.bayenv.candidates.names)))

d125 <- length(Reduce(intersect, list(CHS.VS.rad.bayenv.candidates.names, CHS.VS.shadow.days.bayenv.candidates.names,CHS.VS.temp.bayenv.candidates.names)))
d123 <- length(Reduce(intersect, list(CHS.VS.rad.bayenv.candidates.names, CHS.VS.shadow.days.bayenv.candidates.names,CHS.VS.pcpt.bayenv.candidates.names)))
d124 <- length(Reduce(intersect, list(CHS.VS.rad.bayenv.candidates.names, CHS.VS.shadow.days.bayenv.candidates.names,CHS.VS.day.10cm.bayenv.candidates.names)))
d135 <- length(Reduce(intersect, list(CHS.VS.shadow.days.bayenv.candidates.names, CHS.VS.temp.bayenv.candidates.names,CHS.VS.pcpt.bayenv.candidates.names)))
d235 <- length(Reduce(intersect, list(CHS.VS.rad.bayenv.candidates.names, CHS.VS.temp.bayenv.candidates.names,CHS.VS.pcpt.bayenv.candidates.names)))
d245 <- length(Reduce(intersect, list(CHS.VS.rad.bayenv.candidates.names, CHS.VS.temp.bayenv.candidates.names,CHS.VS.day.10cm.bayenv.candidates.names)))
d234 <- length(Reduce(intersect, list(CHS.VS.rad.bayenv.candidates.names, CHS.VS.pcpt.bayenv.candidates.names,CHS.VS.day.10cm.bayenv.candidates.names)))
d145 <- length(Reduce(intersect, list(CHS.VS.shadow.days.bayenv.candidates.names, CHS.VS.temp.bayenv.candidates.names,CHS.VS.day.10cm.bayenv.candidates.names)))
d134 <- length(Reduce(intersect, list(CHS.VS.shadow.days.bayenv.candidates.names, CHS.VS.pcpt.bayenv.candidates.names,CHS.VS.day.10cm.bayenv.candidates.names)))
d345 <- length(Reduce(intersect, list(CHS.VS.temp.bayenv.candidates.names, CHS.VS.pcpt.bayenv.candidates.names,CHS.VS.day.10cm.bayenv.candidates.names)))


d1235 <- length(Reduce(intersect, list(CHS.VS.shadow.days.bayenv.candidates.names, CHS.VS.temp.bayenv.candidates.names,
CHS.VS.pcpt.bayenv.candidates.names, CHS.VS.rad.bayenv.candidates.names)))
d1245 <- length(Reduce(intersect, list(CHS.VS.shadow.days.bayenv.candidates.names, CHS.VS.temp.bayenv.candidates.names,
CHS.VS.day.10cm.bayenv.candidates.names, CHS.VS.rad.bayenv.candidates.names)))
d1345 <- length(Reduce(intersect, list(CHS.VS.shadow.days.bayenv.candidates.names, CHS.VS.temp.bayenv.candidates.names,
CHS.VS.pcpt.bayenv.candidates.names, CHS.VS.day.10cm.bayenv.candidates.names)))
d1234 <- length(Reduce(intersect, list(CHS.VS.shadow.days.bayenv.candidates.names, CHS.VS.rad.bayenv.candidates.names,
CHS.VS.pcpt.bayenv.candidates.names, CHS.VS.day.10cm.bayenv.candidates.names)))
d2345 <- length(Reduce(intersect, list(CHS.VS.temp.bayenv.candidates.names, CHS.VS.rad.bayenv.candidates.names,
CHS.VS.pcpt.bayenv.candidates.names, CHS.VS.day.10cm.bayenv.candidates.names)))

d12345 <- length(Reduce(intersect, list(CHS.VS.rad.bayenv.candidates.names, CHS.VS.shadow.days.bayenv.candidates.names, CHS.VS.temp.bayenv.candidates.names, 
CHS.VS.pcpt.bayenv.candidates.names, CHS.VS.day.10cm.bayenv.candidates.names)))

pdf("CHS.VS.bayenv2.VENN_20171020.pdf")
draw.quintuple.venn(area1=d1, area2=d2, area3=d3, area4=d4, area5=d5,
n12=d12, n13=d13, n14=d14, n15=d15, n23=d23, n24=d24, n25=d25, n34=d34, n35=d35, n45=d45,
n123=d123, n124=d124, n125=d125, n134=d134, n135=d135, n145=d145, n234=d234, n235=d235, n245=d245, n345=d345,
n1234=d1234, n1235=d1235, n1245=d1245, n1345=d1345, n2345=d2345, n12345=d12345, 
category=c("CHS.VS.shadow.days", "CHS.VS.rad", "CHS.VS.pcpt", "CHS.VS.day.10cm", "CHS.VS.temp"),
lty="blank", 
fill=c("yellow", "orange", "skyblue1", "skyblue3", "blue")
)
dev.off()


```


##### CHS.TI

```
library(VennDiagram)

d1 <- length(CHS.TI.shadow.days.bayenv.candidates.names)
d2 <- length(CHS.TI.rad.bayenv.candidates.names)
d3 <- length(CHS.TI.pcpt.bayenv.candidates.names)
d4 <- length(CHS.TI.day.10cm.bayenv.candidates.names)
d5 <- length(CHS.TI.temp.bayenv.candidates.names)

d12 <- length(Reduce(intersect, list(CHS.TI.rad.bayenv.candidates.names, CHS.TI.shadow.days.bayenv.candidates.names)))
d25 <- length(Reduce(intersect, list(CHS.TI.rad.bayenv.candidates.names, CHS.TI.temp.bayenv.candidates.names)))
d23 <- length(Reduce(intersect, list(CHS.TI.rad.bayenv.candidates.names, CHS.TI.pcpt.bayenv.candidates.names)))
d24 <- length(Reduce(intersect, list(CHS.TI.rad.bayenv.candidates.names, CHS.TI.day.10cm.bayenv.candidates.names)))
d15 <- length(Reduce(intersect, list(CHS.TI.shadow.days.bayenv.candidates.names, CHS.TI.temp.bayenv.candidates.names)))
d13 <- length(Reduce(intersect, list(CHS.TI.shadow.days.bayenv.candidates.names, CHS.TI.pcpt.bayenv.candidates.names)))
d14 <- length(Reduce(intersect, list(CHS.TI.shadow.days.bayenv.candidates.names, CHS.TI.day.10cm.bayenv.candidates.names)))
d35 <- length(Reduce(intersect, list(CHS.TI.temp.bayenv.candidates.names, CHS.TI.pcpt.bayenv.candidates.names)))
d45 <- length(Reduce(intersect, list(CHS.TI.temp.bayenv.candidates.names, CHS.TI.day.10cm.bayenv.candidates.names)))
d34 <- length(Reduce(intersect, list(CHS.TI.pcpt.bayenv.candidates.names, CHS.TI.day.10cm.bayenv.candidates.names)))

d125 <- length(Reduce(intersect, list(CHS.TI.rad.bayenv.candidates.names, CHS.TI.shadow.days.bayenv.candidates.names,CHS.TI.temp.bayenv.candidates.names)))
d123 <- length(Reduce(intersect, list(CHS.TI.rad.bayenv.candidates.names, CHS.TI.shadow.days.bayenv.candidates.names,CHS.TI.pcpt.bayenv.candidates.names)))
d124 <- length(Reduce(intersect, list(CHS.TI.rad.bayenv.candidates.names, CHS.TI.shadow.days.bayenv.candidates.names,CHS.TI.day.10cm.bayenv.candidates.names)))
d135 <- length(Reduce(intersect, list(CHS.TI.shadow.days.bayenv.candidates.names, CHS.TI.temp.bayenv.candidates.names,CHS.TI.pcpt.bayenv.candidates.names)))
d235 <- length(Reduce(intersect, list(CHS.TI.rad.bayenv.candidates.names, CHS.TI.temp.bayenv.candidates.names,CHS.TI.pcpt.bayenv.candidates.names)))
d245 <- length(Reduce(intersect, list(CHS.TI.rad.bayenv.candidates.names, CHS.TI.temp.bayenv.candidates.names,CHS.TI.day.10cm.bayenv.candidates.names)))
d234 <- length(Reduce(intersect, list(CHS.TI.rad.bayenv.candidates.names, CHS.TI.pcpt.bayenv.candidates.names,CHS.TI.day.10cm.bayenv.candidates.names)))
d145 <- length(Reduce(intersect, list(CHS.TI.shadow.days.bayenv.candidates.names, CHS.TI.temp.bayenv.candidates.names,CHS.TI.day.10cm.bayenv.candidates.names)))
d134 <- length(Reduce(intersect, list(CHS.TI.shadow.days.bayenv.candidates.names, CHS.TI.pcpt.bayenv.candidates.names,CHS.TI.day.10cm.bayenv.candidates.names)))
d345 <- length(Reduce(intersect, list(CHS.TI.temp.bayenv.candidates.names, CHS.TI.pcpt.bayenv.candidates.names,CHS.TI.day.10cm.bayenv.candidates.names)))


d1235 <- length(Reduce(intersect, list(CHS.TI.shadow.days.bayenv.candidates.names, CHS.TI.temp.bayenv.candidates.names,
CHS.TI.pcpt.bayenv.candidates.names, CHS.TI.rad.bayenv.candidates.names)))
d1245 <- length(Reduce(intersect, list(CHS.TI.shadow.days.bayenv.candidates.names, CHS.TI.temp.bayenv.candidates.names,
CHS.TI.day.10cm.bayenv.candidates.names, CHS.TI.rad.bayenv.candidates.names)))
d1345 <- length(Reduce(intersect, list(CHS.TI.shadow.days.bayenv.candidates.names, CHS.TI.temp.bayenv.candidates.names,
CHS.TI.pcpt.bayenv.candidates.names, CHS.TI.day.10cm.bayenv.candidates.names)))
d1234 <- length(Reduce(intersect, list(CHS.TI.shadow.days.bayenv.candidates.names, CHS.TI.rad.bayenv.candidates.names,
CHS.TI.pcpt.bayenv.candidates.names, CHS.TI.day.10cm.bayenv.candidates.names)))
d2345 <- length(Reduce(intersect, list(CHS.TI.temp.bayenv.candidates.names, CHS.TI.rad.bayenv.candidates.names,
CHS.TI.pcpt.bayenv.candidates.names, CHS.TI.day.10cm.bayenv.candidates.names)))

d12345 <- length(Reduce(intersect, list(CHS.TI.rad.bayenv.candidates.names, CHS.TI.shadow.days.bayenv.candidates.names, CHS.TI.temp.bayenv.candidates.names, 
CHS.TI.pcpt.bayenv.candidates.names, CHS.TI.day.10cm.bayenv.candidates.names)))

pdf("CHS.TI.bayenv2.VENN_20171020.pdf")
draw.quintuple.venn(area1=d1, area2=d2, area3=d3, area4=d4, area5=d5,
n12=d12, n13=d13, n14=d14, n15=d15, n23=d23, n24=d24, n25=d25, n34=d34, n35=d35, n45=d45,
n123=d123, n124=d124, n125=d125, n134=d134, n135=d135, n145=d145, n234=d234, n235=d235, n245=d245, n345=d345,
n1234=d1234, n1235=d1235, n1245=d1245, n1345=d1345, n2345=d2345, n12345=d12345, 
category=c("CHS.TI.shadow.days", "CHS.TI.rad", "CHS.TI.pcpt", "CHS.TI.day.10cm", "CHS.TI.temp"),
lty="blank", 
fill=c("yellow", "orange", "skyblue1", "skyblue3", "blue")
)
dev.off()



```


### 2. overlap between LFMM, Bayenv2, PCadapt, XtX, and bayescan within each region

/Users/alexjvr/2016RADAnalysis/3_CH.landscapeGenomics/subsets/Venn/CHP2.MACfilter/


##### CHN

prep data
```
lfmm.outliers <- read.table("CHN.LFMM.alloutliers")
pcadapt.outliers <- read.table("CHN.pcadapt.outliers")
bayenv.outliers <- read.table("CHN.BayEnv.alloutliers")
XtX.outliers <- read.table("CHN.XtX.100outliers")
bayescan.outliers <- read.table("CHN.bayescan.pos.outliers.FDR0.01")
#bayescan.outliers <- read.table("CHN.bayescan.outliers.FDR0.01")

##check that the files are all in the same format

head(lfmm.outliers) 
head(XtX.outliers) 
head(pcadapt.outliers)
head(bayenv.outliers) 
head(bayescan.outliers)

lfmm.outliers <- as.data.frame(lfmm.outliers)
pcadapt.outliers <- as.data.frame(pcadapt.outliers)
XtX.outliers <- as.data.frame(XtX.outliers)
bayenv.outliers <- as.data.frame(bayenv.outliers)
bayescan.outliers <- as.data.frame(bayescan.outliers)


##and correct those that need changing

pcadapt.outliers$V1 <- gsub(":", "\\.", pcadapt.outliers$V1)
bayescan.outliers$V1 <- paste("X.", bayescan.outliers$V1, sep="")
bayescan.outliers$V1 <- gsub(":", "\\.", bayescan.outliers$V1)


colnames(lfmm.outliers) <- "loci"
colnames(XtX.outliers) <- "loci"
colnames(pcadapt.outliers) <- "loci"
colnames(bayenv.outliers) <- "loci"
colnames(bayescan.outliers) <- "loci"


###old code to remove the X. <- I'm now keeping the X. before the locus name to make sure that the locus names don't turn to digits. It removed 0s after the "." before, and I ended up with an incorrect set of loci 
#######################
lfmm.outliers.new <- gsub("X\\.", "", lfmm.outliers$V1)
lfmm.outliers <- NULL
lfmm.outliers <- as.data.frame(lfmm.outliers.new)

bayenv.outliers.new <- gsub("X\\.", "", bayenv.outliers$V1)
bayenv.outliers <- NULL
bayenv.outliers <- as.data.frame(bayenv.outliers.new)

XtX.outliers.new <- gsub("X\\.", "", XtX.outliers$V1)
XtX.outliers <- NULL
XtX.outliers <- as.data.frame(XtX.outliers.new)

pcadapt.new <- gsub("X\\.", "", pcadapt.outliers$V1)
pcadapt.new <- as.data.frame(pcadapt.new)
pcadapt.new <- gsub(":", "\\.", pcadapt.new$pcadapt.new)
pcadapt.outliers <- as.data.frame(pcadapt.new)

```


and draw Venn
```
library(VennDiagram)

bayenv.outliers.names <- bayenv.outliers$loci
XtX.outliers.names <- XtX.outliers$loci
lfmm.outliers.names <- lfmm.outliers$loci
bayescan.outliers.names <- bayescan.outliers$loci
pcadapt.outliers.names <- pcadapt.outliers$loci

d1 <- length(bayenv.outliers.names)
d2 <- length(XtX.outliers.names)
d3 <- length(lfmm.outliers.names)
d4 <- length(bayescan.outliers.names)
d5 <- length(pcadapt.outliers.names)


d12 <- length(Reduce(intersect, list(bayenv.outliers.names, XtX.outliers.names)))
d13 <- length(Reduce(intersect, list(bayenv.outliers.names, lfmm.outliers.names)))
d14 <- length(Reduce(intersect, list(bayenv.outliers.names, bayescan.outliers.names)))
d15 <- length(Reduce(intersect, list(bayenv.outliers.names, pcadapt.outliers.names)))
d23 <- length(Reduce(intersect, list(XtX.outliers.names, lfmm.outliers.names)))
d24 <- length(Reduce(intersect, list(XtX.outliers.names, bayescan.outliers.names)))
d25 <- length(Reduce(intersect, list(XtX.outliers.names, pcadapt.outliers.names)))
d34 <- length(Reduce(intersect, list(lfmm.outliers.names, bayescan.outliers.names)))
d35 <- length(Reduce(intersect, list(lfmm.outliers.names, pcadapt.outliers.names)))
d45 <- length(Reduce(intersect, list(bayescan.outliers.names, pcadapt.outliers.names)))

d123 <- length(Reduce(intersect, list(bayenv.outliers.names, XtX.outliers.names,lfmm.outliers.names)))
d124 <- length(Reduce(intersect, list(bayenv.outliers.names, XtX.outliers.names,bayescan.outliers.names)))
d125 <- length(Reduce(intersect, list(bayenv.outliers.names, XtX.outliers.names,pcadapt.outliers.names)))
d234 <- length(Reduce(intersect, list(XtX.outliers.names, lfmm.outliers.names,bayescan.outliers.names)))
d134 <- length(Reduce(intersect, list(bayenv.outliers.names, lfmm.outliers.names,bayescan.outliers.names)))
d135 <- length(Reduce(intersect, list(bayenv.outliers.names, lfmm.outliers.names,pcadapt.outliers.names)))
d145 <- length(Reduce(intersect, list(bayenv.outliers.names, bayescan.outliers.names,pcadapt.outliers.names)))
d235 <- length(Reduce(intersect, list(XtX.outliers.names, lfmm.outliers.names,pcadapt.outliers.names)))
d245 <- length(Reduce(intersect, list(XtX.outliers.names, bayescan.outliers.names,pcadapt.outliers.names)))
d345 <- length(Reduce(intersect, list(lfmm.outliers.names, bayescan.outliers.names,pcadapt.outliers.names)))


d1234 <- length(Reduce(intersect, list(XtX.outliers.names, lfmm.outliers.names,
bayescan.outliers.names, bayenv.outliers.names)))
d1235 <- length(Reduce(intersect, list(XtX.outliers.names, lfmm.outliers.names,
pcadapt.outliers.names, bayenv.outliers.names)))

d2345 <- length(Reduce(intersect, list(XtX.outliers.names, lfmm.outliers.names,
bayescan.outliers.names, pcadapt.outliers.names)))
d1245 <- length(Reduce(intersect, list(XtX.outliers.names, bayenv.outliers.names,
bayescan.outliers.names, pcadapt.outliers.names)))
d1345 <- length(Reduce(intersect, list(lfmm.outliers.names, bayenv.outliers.names,
bayescan.outliers.names, pcadapt.outliers.names)))
d12345 <- length(Reduce(intersect, list(bayenv.outliers.names, XtX.outliers.names, lfmm.outliers.names, 
bayescan.outliers.names, pcadapt.outliers.names)))


##Venn with new bayescan loci
pdf("CHN.Venn.alloutliers_20171020.pdf")
draw.quintuple.venn(area1=d1, area2=d2, area3=d3, area4=d4, area5=d5,
n12=d12, n13=d13, n14=d14, n15=d15, n23=d23, n24=d24, n25=d25, n34=d34, n35=d35, n45=d45,
n123=d123, n124=d124, n125=d125, n134=d134, n135=d135, n145=d145, n234=d234, n235=d235, n245=d245, n345=d345,
n1234=d1234, n1235=d1235, n1245=d1245, n1345=d1345, n2345=d2345, n12345=d12345, 
category=c("bayenv", "XtX", "lfmm", "bayescan", "pcadapt"),
lty="blank", 
fill=c("yellow", "orange", "skyblue1", "skyblue3", "blue")
)
dev.off()



##previous Venn
pdf("CHN.Venn.alloutliers_20171007.pdf")
draw.quintuple.venn(area1=d1, area2=d2, area3=d3, area4=d4, area5=d5,
n12=d12, n13=d13, n14=d14, n15=d15, n23=d23, n24=d24, n25=d25, n34=d34, n35=d35, n45=d45,
n123=d123, n124=d124, n125=d125, n134=d134, n135=d135, n145=d145, n234=d234, n235=d235, n245=d245, n345=d345,
n1234=d1234, n1235=d1235, n1245=d1245, n1345=d1345, n2345=d2345, n12345=d12345, 
category=c("bayenv", "XtX", "lfmm", "bayescan", "pcadapt"),
lty="blank", 
fill=c("yellow", "orange", "skyblue1", "skyblue3", "blue")
)
dev.off()
```

![alt_txt][CHN.Venn.allmethods]

[CHN.Venn.allmethods]:


##### CHS

prep data
```
lfmm.outliers <- read.table("CHS.LFMM.alloutliers")
pcadapt.outliers <- read.table("CHS.pcadapt.outliers")
bayenv.outliers <- read.table("CHS.BayEnv.alloutliers")
XtX.outliers <- read.table("CHS.XtX.100outliers")
bayescan.outliers <- read.table("CHS.bayescan.pos.outliers.FDR0.01")
#bayescan.outliers <- read.table("CHS.bayescan.outliers.FDR0.01")

##check that the files are all in the same format

head(lfmm.outliers) 
head(XtX.outliers) 
head(pcadapt.outliers)
head(bayenv.outliers) 
head(bayescan.outliers)

lfmm.outliers <- as.data.frame(lfmm.outliers)
pcadapt.outliers <- as.data.frame(pcadapt.outliers)
XtX.outliers <- as.data.frame(XtX.outliers)
bayenv.outliers <- as.data.frame(bayenv.outliers)
bayescan.outliers <- as.data.frame(bayescan.outliers)


##and correct those that need changing

pcadapt.outliers$V1 <- gsub(":", "\\.", pcadapt.outliers$V1)
bayescan.outliers$V1 <- paste("X.", bayescan.outliers$V1, sep="")
bayescan.outliers$V1 <- gsub(":", "\\.", bayescan.outliers$V1)


colnames(lfmm.outliers) <- "loci"
colnames(XtX.outliers) <- "loci"
colnames(pcadapt.outliers) <- "loci"
colnames(bayenv.outliers) <- "loci"
colnames(bayescan.outliers) <- "loci"


###old code to remove the X. <- I'm now keeping the X. before the locus name to make sure that the locus names don't turn to digits. It removed 0s after the "." before, and I ended up with an incorrect set of loci 
#######################
lfmm.outliers.new <- gsub("X\\.", "", lfmm.outliers$V1)
lfmm.outliers <- NULL
lfmm.outliers <- as.data.frame(lfmm.outliers.new)

bayenv.outliers.new <- gsub("X\\.", "", bayenv.outliers$V1)
bayenv.outliers <- NULL
bayenv.outliers <- as.data.frame(bayenv.outliers.new)

XtX.outliers.new <- gsub("X\\.", "", XtX.outliers$V1)
XtX.outliers <- NULL
XtX.outliers <- as.data.frame(XtX.outliers.new)

pcadapt.new <- gsub("X\\.", "", pcadapt.outliers$V1)
pcadapt.new <- as.data.frame(pcadapt.new)
pcadapt.new <- gsub(":", "\\.", pcadapt.new$pcadapt.new)
pcadapt.outliers <- as.data.frame(pcadapt.new)

```


and draw Venn
```
library(VennDiagram)

bayenv.outliers.names <- bayenv.outliers$loci
XtX.outliers.names <- XtX.outliers$loci
lfmm.outliers.names <- lfmm.outliers$loci
bayescan.outliers.names <- bayescan.outliers$loci
pcadapt.outliers.names <- pcadapt.outliers$loci

d1 <- length(bayenv.outliers.names)
d2 <- length(XtX.outliers.names)
d3 <- length(lfmm.outliers.names)
d4 <- length(bayescan.outliers.names)
d5 <- length(pcadapt.outliers.names)


d12 <- length(Reduce(intersect, list(bayenv.outliers.names, XtX.outliers.names)))
d13 <- length(Reduce(intersect, list(bayenv.outliers.names, lfmm.outliers.names)))
d14 <- length(Reduce(intersect, list(bayenv.outliers.names, bayescan.outliers.names)))
d15 <- length(Reduce(intersect, list(bayenv.outliers.names, pcadapt.outliers.names)))
d23 <- length(Reduce(intersect, list(XtX.outliers.names, lfmm.outliers.names)))
d24 <- length(Reduce(intersect, list(XtX.outliers.names, bayescan.outliers.names)))
d25 <- length(Reduce(intersect, list(XtX.outliers.names, pcadapt.outliers.names)))
d34 <- length(Reduce(intersect, list(lfmm.outliers.names, bayescan.outliers.names)))
d35 <- length(Reduce(intersect, list(lfmm.outliers.names, pcadapt.outliers.names)))
d45 <- length(Reduce(intersect, list(bayescan.outliers.names, pcadapt.outliers.names)))

d123 <- length(Reduce(intersect, list(bayenv.outliers.names, XtX.outliers.names,lfmm.outliers.names)))
d124 <- length(Reduce(intersect, list(bayenv.outliers.names, XtX.outliers.names,bayescan.outliers.names)))
d125 <- length(Reduce(intersect, list(bayenv.outliers.names, XtX.outliers.names,pcadapt.outliers.names)))
d234 <- length(Reduce(intersect, list(XtX.outliers.names, lfmm.outliers.names,bayescan.outliers.names)))
d134 <- length(Reduce(intersect, list(bayenv.outliers.names, lfmm.outliers.names,bayescan.outliers.names)))
d135 <- length(Reduce(intersect, list(bayenv.outliers.names, lfmm.outliers.names,pcadapt.outliers.names)))
d145 <- length(Reduce(intersect, list(bayenv.outliers.names, bayescan.outliers.names,pcadapt.outliers.names)))
d235 <- length(Reduce(intersect, list(XtX.outliers.names, lfmm.outliers.names,pcadapt.outliers.names)))
d245 <- length(Reduce(intersect, list(XtX.outliers.names, bayescan.outliers.names,pcadapt.outliers.names)))
d345 <- length(Reduce(intersect, list(lfmm.outliers.names, bayescan.outliers.names,pcadapt.outliers.names)))


d1234 <- length(Reduce(intersect, list(XtX.outliers.names, lfmm.outliers.names,
bayescan.outliers.names, bayenv.outliers.names)))
d1235 <- length(Reduce(intersect, list(XtX.outliers.names, lfmm.outliers.names,
pcadapt.outliers.names, bayenv.outliers.names)))

d2345 <- length(Reduce(intersect, list(XtX.outliers.names, lfmm.outliers.names,
bayescan.outliers.names, pcadapt.outliers.names)))
d1245 <- length(Reduce(intersect, list(XtX.outliers.names, bayenv.outliers.names,
bayescan.outliers.names, pcadapt.outliers.names)))
d1345 <- length(Reduce(intersect, list(lfmm.outliers.names, bayenv.outliers.names,
bayescan.outliers.names, pcadapt.outliers.names)))
d12345 <- length(Reduce(intersect, list(bayenv.outliers.names, XtX.outliers.names, lfmm.outliers.names, 
bayescan.outliers.names, pcadapt.outliers.names)))

###Venn with new outliers
pdf("CHS.Venn.alloutliers_20171020.pdf")
draw.quintuple.venn(area1=d1, area2=d2, area3=d3, area4=d4, area5=d5,
n12=d12, n13=d13, n14=d14, n15=d15, n23=d23, n24=d24, n25=d25, n34=d34, n35=d35, n45=d45,
n123=d123, n124=d124, n125=d125, n134=d134, n135=d135, n145=d145, n234=d234, n235=d235, n245=d245, n345=d345,
n1234=d1234, n1235=d1235, n1245=d1245, n1345=d1345, n2345=d2345, n12345=d12345, 
category=c("bayenv", "XtX", "lfmm", "bayescan", "pcadapt"),
lty="blank", 
fill=c("yellow", "orange", "skyblue1", "skyblue3", "blue")
)
dev.off()



####old Venn diagram
pdf("CHS.Venn.alloutliers_20171007.pdf")
draw.quintuple.venn(area1=d1, area2=d2, area3=d3, area4=d4, area5=d5,
n12=d12, n13=d13, n14=d14, n15=d15, n23=d23, n24=d24, n25=d25, n34=d34, n35=d35, n45=d45,
n123=d123, n124=d124, n125=d125, n134=d134, n135=d135, n145=d145, n234=d234, n235=d235, n245=d245, n345=d345,
n1234=d1234, n1235=d1235, n1245=d1245, n1345=d1345, n2345=d2345, n12345=d12345, 
category=c("bayenv", "XtX", "lfmm", "bayescan", "pcadapt"),
lty="blank", 
fill=c("yellow", "orange", "skyblue1", "skyblue3", "blue")
)
dev.off()
```



##### CZ

prep data
```
lfmm.outliers <- read.table("CZ.LFMM.alloutliers")
pcadapt.outliers <- read.table("CZ.pcadapt.outliers")
bayenv.outliers <- read.table("CZ.BayEnv.alloutliers")
XtX.outliers <- read.table("CZ.XtX.100outliers")
bayescan.outliers <- read.table("CZ.bayescan.pos.outliers.FDR0.01")
#bayescan.outliers <- read.table("CZ.bayescan.outliers.FDR0.01")

##check that the files are all in the same format

head(lfmm.outliers) 
head(XtX.outliers) 
head(pcadapt.outliers)
head(bayenv.outliers) 
head(bayescan.outliers)

lfmm.outliers <- as.data.frame(lfmm.outliers)
pcadapt.outliers <- as.data.frame(pcadapt.outliers)
XtX.outliers <- as.data.frame(XtX.outliers)
bayenv.outliers <- as.data.frame(bayenv.outliers)
bayescan.outliers <- as.data.frame(bayescan.outliers)


##and correct those that need changing

pcadapt.outliers$V1 <- gsub(":", "\\.", pcadapt.outliers$V1)
bayescan.outliers$V1 <- paste("X.", bayescan.outliers$V1, sep="")
bayescan.outliers$V1 <- gsub(":", "\\.", bayescan.outliers$V1)


colnames(lfmm.outliers) <- "loci"
colnames(XtX.outliers) <- "loci"
colnames(pcadapt.outliers) <- "loci"
colnames(bayenv.outliers) <- "loci"
colnames(bayescan.outliers) <- "loci"


###old code to remove the X. <- I'm now keeping the X. before the locus name to make sure that the locus names don't turn to digits. It removed 0s after the "." before, and I ended up with an incorrect set of loci 
#######################
lfmm.outliers.new <- gsub("X\\.", "", lfmm.outliers$V1)
lfmm.outliers <- NULL
lfmm.outliers <- as.data.frame(lfmm.outliers.new)

bayenv.outliers.new <- gsub("X\\.", "", bayenv.outliers$V1)
bayenv.outliers <- NULL
bayenv.outliers <- as.data.frame(bayenv.outliers.new)

XtX.outliers.new <- gsub("X\\.", "", XtX.outliers$V1)
XtX.outliers <- NULL
XtX.outliers <- as.data.frame(XtX.outliers.new)

pcadapt.new <- gsub("X\\.", "", pcadapt.outliers$V1)
pcadapt.new <- as.data.frame(pcadapt.new)
pcadapt.new <- gsub(":", "\\.", pcadapt.new$pcadapt.new)
pcadapt.outliers <- as.data.frame(pcadapt.new)

```


and draw Venn
```
library(VennDiagram)

bayenv.outliers.names <- bayenv.outliers$loci
XtX.outliers.names <- XtX.outliers$loci
lfmm.outliers.names <- lfmm.outliers$loci
bayescan.outliers.names <- bayescan.outliers$loci
pcadapt.outliers.names <- pcadapt.outliers$loci

d1 <- length(bayenv.outliers.names)
d2 <- length(XtX.outliers.names)
d3 <- length(lfmm.outliers.names)
d4 <- length(bayescan.outliers.names)
d5 <- length(pcadapt.outliers.names)


d12 <- length(Reduce(intersect, list(bayenv.outliers.names, XtX.outliers.names)))
d13 <- length(Reduce(intersect, list(bayenv.outliers.names, lfmm.outliers.names)))
d14 <- length(Reduce(intersect, list(bayenv.outliers.names, bayescan.outliers.names)))
d15 <- length(Reduce(intersect, list(bayenv.outliers.names, pcadapt.outliers.names)))
d23 <- length(Reduce(intersect, list(XtX.outliers.names, lfmm.outliers.names)))
d24 <- length(Reduce(intersect, list(XtX.outliers.names, bayescan.outliers.names)))
d25 <- length(Reduce(intersect, list(XtX.outliers.names, pcadapt.outliers.names)))
d34 <- length(Reduce(intersect, list(lfmm.outliers.names, bayescan.outliers.names)))
d35 <- length(Reduce(intersect, list(lfmm.outliers.names, pcadapt.outliers.names)))
d45 <- length(Reduce(intersect, list(bayescan.outliers.names, pcadapt.outliers.names)))

d123 <- length(Reduce(intersect, list(bayenv.outliers.names, XtX.outliers.names,lfmm.outliers.names)))
d124 <- length(Reduce(intersect, list(bayenv.outliers.names, XtX.outliers.names,bayescan.outliers.names)))
d125 <- length(Reduce(intersect, list(bayenv.outliers.names, XtX.outliers.names,pcadapt.outliers.names)))
d234 <- length(Reduce(intersect, list(XtX.outliers.names, lfmm.outliers.names,bayescan.outliers.names)))
d134 <- length(Reduce(intersect, list(bayenv.outliers.names, lfmm.outliers.names,bayescan.outliers.names)))
d135 <- length(Reduce(intersect, list(bayenv.outliers.names, lfmm.outliers.names,pcadapt.outliers.names)))
d145 <- length(Reduce(intersect, list(bayenv.outliers.names, bayescan.outliers.names,pcadapt.outliers.names)))
d235 <- length(Reduce(intersect, list(XtX.outliers.names, lfmm.outliers.names,pcadapt.outliers.names)))
d245 <- length(Reduce(intersect, list(XtX.outliers.names, bayescan.outliers.names,pcadapt.outliers.names)))
d345 <- length(Reduce(intersect, list(lfmm.outliers.names, bayescan.outliers.names,pcadapt.outliers.names)))


d1234 <- length(Reduce(intersect, list(XtX.outliers.names, lfmm.outliers.names,
bayescan.outliers.names, bayenv.outliers.names)))
d1235 <- length(Reduce(intersect, list(XtX.outliers.names, lfmm.outliers.names,
pcadapt.outliers.names, bayenv.outliers.names)))

d2345 <- length(Reduce(intersect, list(XtX.outliers.names, lfmm.outliers.names,
bayescan.outliers.names, pcadapt.outliers.names)))
d1245 <- length(Reduce(intersect, list(XtX.outliers.names, bayenv.outliers.names,
bayescan.outliers.names, pcadapt.outliers.names)))
d1345 <- length(Reduce(intersect, list(lfmm.outliers.names, bayenv.outliers.names,
bayescan.outliers.names, pcadapt.outliers.names)))
d12345 <- length(Reduce(intersect, list(bayenv.outliers.names, XtX.outliers.names, lfmm.outliers.names, 
bayescan.outliers.names, pcadapt.outliers.names)))

pdf("CZ.Venn.alloutliers_20171020.pdf")
draw.quintuple.venn(area1=d1, area2=d2, area3=d3, area4=d4, area5=d5,
n12=d12, n13=d13, n14=d14, n15=d15, n23=d23, n24=d24, n25=d25, n34=d34, n35=d35, n45=d45,
n123=d123, n124=d124, n125=d125, n134=d134, n135=d135, n145=d145, n234=d234, n235=d235, n245=d245, n345=d345,
n1234=d1234, n1235=d1235, n1245=d1245, n1345=d1345, n2345=d2345, n12345=d12345, 
category=c("bayenv", "XtX", "lfmm", "bayescan", "pcadapt"),
lty="blank", 
fill=c("yellow", "orange", "skyblue1", "skyblue3", "blue")
)
dev.off()


###old figure
pdf("CZ.Venn.alloutliers_20171007.pdf")
draw.quintuple.venn(area1=d1, area2=d2, area3=d3, area4=d4, area5=d5,
n12=d12, n13=d13, n14=d14, n15=d15, n23=d23, n24=d24, n25=d25, n34=d34, n35=d35, n45=d45,
n123=d123, n124=d124, n125=d125, n134=d134, n135=d135, n145=d145, n234=d234, n235=d235, n245=d245, n345=d345,
n1234=d1234, n1235=d1235, n1245=d1245, n1345=d1345, n2345=d2345, n12345=d12345, 
category=c("bayenv", "XtX", "lfmm", "bayescan", "pcadapt"),
lty="blank", 
fill=c("yellow", "orange", "skyblue1", "skyblue3", "blue")
)
dev.off()
```

![alt_txt][CZ.Venn.allmethods]

[CZ.Venn.allmethods]:https://user-images.githubusercontent.com/12142475/31231271-4a451eea-a9de-11e7-8a4a-7c17db951078.png



##### CHS.VS

prep data
```
lfmm.outliers <- read.table("CHS.VS.LFMM.alloutliers")
pcadapt.outliers <- read.table("CHS.VS.pcadapt.outliers")
bayenv.outliers <- read.table("CHS.VS.BayEnv.alloutliers")
XtX.outliers <- read.table("CHS.VS.XtX.100outliers")
bayescan.outliers <- read.table("CHS.VS.bayescan.pos.outliers.FDR0.01")
#bayescan.outliers <- read.table("CHS.VS.bayescan.outliers.FDR0.01")

##check that the files are all in the same format

head(lfmm.outliers) 
head(XtX.outliers) 
head(pcadapt.outliers)
head(bayenv.outliers) 
head(bayescan.outliers)

lfmm.outliers <- as.data.frame(lfmm.outliers)
pcadapt.outliers <- as.data.frame(pcadapt.outliers)
XtX.outliers <- as.data.frame(XtX.outliers)
bayenv.outliers <- as.data.frame(bayenv.outliers)
bayescan.outliers <- as.data.frame(bayescan.outliers)


##and correct those that need changing

pcadapt.outliers$V1 <- gsub(":", "\\.", pcadapt.outliers$V1)
bayescan.outliers$V1 <- paste("X.", bayescan.outliers$V1, sep="")
bayescan.outliers$V1 <- gsub(":", "\\.", bayescan.outliers$V1)


colnames(lfmm.outliers) <- "loci"
colnames(XtX.outliers) <- "loci"
colnames(pcadapt.outliers) <- "loci"
colnames(bayenv.outliers) <- "loci"
colnames(bayescan.outliers) <- "loci"


###old code to remove the X. <- I'm now keeping the X. before the locus name to make sure that the locus names don't turn to digits. It removed 0s after the "." before, and I ended up with an incorrect set of loci 
#######################
lfmm.outliers.new <- gsub("X\\.", "", lfmm.outliers$V1)
lfmm.outliers <- NULL
lfmm.outliers <- as.data.frame(lfmm.outliers.new)

bayenv.outliers.new <- gsub("X\\.", "", bayenv.outliers$V1)
bayenv.outliers <- NULL
bayenv.outliers <- as.data.frame(bayenv.outliers.new)

XtX.outliers.new <- gsub("X\\.", "", XtX.outliers$V1)
XtX.outliers <- NULL
XtX.outliers <- as.data.frame(XtX.outliers.new)

pcadapt.new <- gsub("X\\.", "", pcadapt.outliers$V1)
pcadapt.new <- as.data.frame(pcadapt.new)
pcadapt.new <- gsub(":", "\\.", pcadapt.new$pcadapt.new)
pcadapt.outliers <- as.data.frame(pcadapt.new)

```


and draw Venn
```
library(VennDiagram)

bayenv.outliers.names <- bayenv.outliers$loci
XtX.outliers.names <- XtX.outliers$loci
lfmm.outliers.names <- lfmm.outliers$loci
bayescan.outliers.names <- bayescan.outliers$loci
pcadapt.outliers.names <- pcadapt.outliers$loci

d1 <- length(bayenv.outliers.names)
d2 <- length(XtX.outliers.names)
d3 <- length(lfmm.outliers.names)
d4 <- length(bayescan.outliers.names)
d5 <- length(pcadapt.outliers.names)


d12 <- length(Reduce(intersect, list(bayenv.outliers.names, XtX.outliers.names)))
d13 <- length(Reduce(intersect, list(bayenv.outliers.names, lfmm.outliers.names)))
d14 <- length(Reduce(intersect, list(bayenv.outliers.names, bayescan.outliers.names)))
d15 <- length(Reduce(intersect, list(bayenv.outliers.names, pcadapt.outliers.names)))
d23 <- length(Reduce(intersect, list(XtX.outliers.names, lfmm.outliers.names)))
d24 <- length(Reduce(intersect, list(XtX.outliers.names, bayescan.outliers.names)))
d25 <- length(Reduce(intersect, list(XtX.outliers.names, pcadapt.outliers.names)))
d34 <- length(Reduce(intersect, list(lfmm.outliers.names, bayescan.outliers.names)))
d35 <- length(Reduce(intersect, list(lfmm.outliers.names, pcadapt.outliers.names)))
d45 <- length(Reduce(intersect, list(bayescan.outliers.names, pcadapt.outliers.names)))

d123 <- length(Reduce(intersect, list(bayenv.outliers.names, XtX.outliers.names,lfmm.outliers.names)))
d124 <- length(Reduce(intersect, list(bayenv.outliers.names, XtX.outliers.names,bayescan.outliers.names)))
d125 <- length(Reduce(intersect, list(bayenv.outliers.names, XtX.outliers.names,pcadapt.outliers.names)))
d234 <- length(Reduce(intersect, list(XtX.outliers.names, lfmm.outliers.names,bayescan.outliers.names)))
d134 <- length(Reduce(intersect, list(bayenv.outliers.names, lfmm.outliers.names,bayescan.outliers.names)))
d135 <- length(Reduce(intersect, list(bayenv.outliers.names, lfmm.outliers.names,pcadapt.outliers.names)))
d145 <- length(Reduce(intersect, list(bayenv.outliers.names, bayescan.outliers.names,pcadapt.outliers.names)))
d235 <- length(Reduce(intersect, list(XtX.outliers.names, lfmm.outliers.names,pcadapt.outliers.names)))
d245 <- length(Reduce(intersect, list(XtX.outliers.names, bayescan.outliers.names,pcadapt.outliers.names)))
d345 <- length(Reduce(intersect, list(lfmm.outliers.names, bayescan.outliers.names,pcadapt.outliers.names)))


d1234 <- length(Reduce(intersect, list(XtX.outliers.names, lfmm.outliers.names,
bayescan.outliers.names, bayenv.outliers.names)))
d1235 <- length(Reduce(intersect, list(XtX.outliers.names, lfmm.outliers.names,
pcadapt.outliers.names, bayenv.outliers.names)))

d2345 <- length(Reduce(intersect, list(XtX.outliers.names, lfmm.outliers.names,
bayescan.outliers.names, pcadapt.outliers.names)))
d1245 <- length(Reduce(intersect, list(XtX.outliers.names, bayenv.outliers.names,
bayescan.outliers.names, pcadapt.outliers.names)))
d1345 <- length(Reduce(intersect, list(lfmm.outliers.names, bayenv.outliers.names,
bayescan.outliers.names, pcadapt.outliers.names)))
d12345 <- length(Reduce(intersect, list(bayenv.outliers.names, XtX.outliers.names, lfmm.outliers.names, 
bayescan.outliers.names, pcadapt.outliers.names)))

pdf("CHS.VS.Venn.alloutliers.20171020.pdf")
draw.quintuple.venn(area1=d1, area2=d2, area3=d3, area4=d4, area5=d5,
n12=d12, n13=d13, n14=d14, n15=d15, n23=d23, n24=d24, n25=d25, n34=d34, n35=d35, n45=d45,
n123=d123, n124=d124, n125=d125, n134=d134, n135=d135, n145=d145, n234=d234, n235=d235, n245=d245, n345=d345,
n1234=d1234, n1235=d1235, n1245=d1245, n1345=d1345, n2345=d2345, n12345=d12345, 
category=c("bayenv", "XtX", "lfmm", "bayescan", "pcadapt"),
lty="blank", 
fill=c("yellow", "orange", "skyblue1", "skyblue3", "blue")
)
dev.off()




##old figure
pdf("CHS.VS.Venn.alloutliers.20171007.pdf")
draw.quintuple.venn(area1=d1, area2=d2, area3=d3, area4=d4, area5=d5,
n12=d12, n13=d13, n14=d14, n15=d15, n23=d23, n24=d24, n25=d25, n34=d34, n35=d35, n45=d45,
n123=d123, n124=d124, n125=d125, n134=d134, n135=d135, n145=d145, n234=d234, n235=d235, n245=d245, n345=d345,
n1234=d1234, n1235=d1235, n1245=d1245, n1345=d1345, n2345=d2345, n12345=d12345, 
category=c("bayenv", "XtX", "lfmm", "bayescan", "pcadapt"),
lty="blank", 
fill=c("yellow", "orange", "skyblue1", "skyblue3", "blue")
)
dev.off()
```

![alt_txt][CHS.VS.Venn.allmethods]

[CHS.VS.Venn.allmethods]:https://user-images.githubusercontent.com/12142475/31231537-0d92898c-a9df-11e7-8890-bec1fef7e6fd.png






##### CHS.TI

prep data
```
lfmm.outliers <- read.table("CHS.TI.LFMM.alloutliers")
pcadapt.outliers <- read.table("CHS.TI.pcadapt.outliers")
bayenv.outliers <- read.table("CHS.TI.BayEnv.alloutliers")
XtX.outliers <- read.table("CHS.TI.XtX.100outliers")
bayescan.outliers <- read.table("CHS.TI.bayescan.pos.outliers.FDR0.01")
#bayescan.outliers <- read.table("CHS.TI.bayescan.outliers.FDR0.01")

##check that the files are all in the same format

head(lfmm.outliers) 
head(XtX.outliers) 
head(pcadapt.outliers)
head(bayenv.outliers) 
head(bayescan.outliers)

lfmm.outliers <- as.data.frame(lfmm.outliers)
pcadapt.outliers <- as.data.frame(pcadapt.outliers)
XtX.outliers <- as.data.frame(XtX.outliers)
bayenv.outliers <- as.data.frame(bayenv.outliers)
bayescan.outliers <- as.data.frame(bayescan.outliers)


##and correct those that need changing

pcadapt.outliers$V1 <- gsub(":", "\\.", pcadapt.outliers$V1)
bayescan.outliers$V1 <- paste("X.", bayescan.outliers$V1, sep="")
bayescan.outliers$V1 <- gsub(":", "\\.", bayescan.outliers$V1)


colnames(lfmm.outliers) <- "loci"
colnames(XtX.outliers) <- "loci"
colnames(pcadapt.outliers) <- "loci"
colnames(bayenv.outliers) <- "loci"
colnames(bayescan.outliers) <- "loci"


###old code to remove the X. <- I'm now keeping the X. before the locus name to make sure that the locus names don't turn to digits. It removed 0s after the "." before, and I ended up with an incorrect set of loci 
#######################
lfmm.outliers.new <- gsub("X\\.", "", lfmm.outliers$V1)
lfmm.outliers <- NULL
lfmm.outliers <- as.data.frame(lfmm.outliers.new)

bayenv.outliers.new <- gsub("X\\.", "", bayenv.outliers$V1)
bayenv.outliers <- NULL
bayenv.outliers <- as.data.frame(bayenv.outliers.new)

XtX.outliers.new <- gsub("X\\.", "", XtX.outliers$V1)
XtX.outliers <- NULL
XtX.outliers <- as.data.frame(XtX.outliers.new)

pcadapt.new <- gsub("X\\.", "", pcadapt.outliers$V1)
pcadapt.new <- as.data.frame(pcadapt.new)
pcadapt.new <- gsub(":", "\\.", pcadapt.new$pcadapt.new)
pcadapt.outliers <- as.data.frame(pcadapt.new)

```


and draw Venn
```
library(VennDiagram)

bayenv.outliers.names <- bayenv.outliers$loci
XtX.outliers.names <- XtX.outliers$loci
lfmm.outliers.names <- lfmm.outliers$loci
bayescan.outliers.names <- bayescan.outliers$loci
pcadapt.outliers.names <- pcadapt.outliers$loci

d1 <- length(bayenv.outliers.names)
d2 <- length(XtX.outliers.names)
d3 <- length(lfmm.outliers.names)
d4 <- length(bayescan.outliers.names)
d5 <- length(pcadapt.outliers.names)


d12 <- length(Reduce(intersect, list(bayenv.outliers.names, XtX.outliers.names)))
d13 <- length(Reduce(intersect, list(bayenv.outliers.names, lfmm.outliers.names)))
d14 <- length(Reduce(intersect, list(bayenv.outliers.names, bayescan.outliers.names)))
d15 <- length(Reduce(intersect, list(bayenv.outliers.names, pcadapt.outliers.names)))
d23 <- length(Reduce(intersect, list(XtX.outliers.names, lfmm.outliers.names)))
d24 <- length(Reduce(intersect, list(XtX.outliers.names, bayescan.outliers.names)))
d25 <- length(Reduce(intersect, list(XtX.outliers.names, pcadapt.outliers.names)))
d34 <- length(Reduce(intersect, list(lfmm.outliers.names, bayescan.outliers.names)))
d35 <- length(Reduce(intersect, list(lfmm.outliers.names, pcadapt.outliers.names)))
d45 <- length(Reduce(intersect, list(bayescan.outliers.names, pcadapt.outliers.names)))

d123 <- length(Reduce(intersect, list(bayenv.outliers.names, XtX.outliers.names,lfmm.outliers.names)))
d124 <- length(Reduce(intersect, list(bayenv.outliers.names, XtX.outliers.names,bayescan.outliers.names)))
d125 <- length(Reduce(intersect, list(bayenv.outliers.names, XtX.outliers.names,pcadapt.outliers.names)))
d234 <- length(Reduce(intersect, list(XtX.outliers.names, lfmm.outliers.names,bayescan.outliers.names)))
d134 <- length(Reduce(intersect, list(bayenv.outliers.names, lfmm.outliers.names,bayescan.outliers.names)))
d135 <- length(Reduce(intersect, list(bayenv.outliers.names, lfmm.outliers.names,pcadapt.outliers.names)))
d145 <- length(Reduce(intersect, list(bayenv.outliers.names, bayescan.outliers.names,pcadapt.outliers.names)))
d235 <- length(Reduce(intersect, list(XtX.outliers.names, lfmm.outliers.names,pcadapt.outliers.names)))
d245 <- length(Reduce(intersect, list(XtX.outliers.names, bayescan.outliers.names,pcadapt.outliers.names)))
d345 <- length(Reduce(intersect, list(lfmm.outliers.names, bayescan.outliers.names,pcadapt.outliers.names)))


d1234 <- length(Reduce(intersect, list(XtX.outliers.names, lfmm.outliers.names,
bayescan.outliers.names, bayenv.outliers.names)))
d1235 <- length(Reduce(intersect, list(XtX.outliers.names, lfmm.outliers.names,
pcadapt.outliers.names, bayenv.outliers.names)))

d2345 <- length(Reduce(intersect, list(XtX.outliers.names, lfmm.outliers.names,
bayescan.outliers.names, pcadapt.outliers.names)))
d1245 <- length(Reduce(intersect, list(XtX.outliers.names, bayenv.outliers.names,
bayescan.outliers.names, pcadapt.outliers.names)))
d1345 <- length(Reduce(intersect, list(lfmm.outliers.names, bayenv.outliers.names,
bayescan.outliers.names, pcadapt.outliers.names)))
d12345 <- length(Reduce(intersect, list(bayenv.outliers.names, XtX.outliers.names, lfmm.outliers.names, 
bayescan.outliers.names, pcadapt.outliers.names)))


pdf("CHS.TI.Venn.alloutliers.20171020.pdf")
draw.quintuple.venn(area1=d1, area2=d2, area3=d3, area4=d4, area5=d5,
n12=d12, n13=d13, n14=d14, n15=d15, n23=d23, n24=d24, n25=d25, n34=d34, n35=d35, n45=d45,
n123=d123, n124=d124, n125=d125, n134=d134, n135=d135, n145=d145, n234=d234, n235=d235, n245=d245, n345=d345,
n1234=d1234, n1235=d1235, n1245=d1245, n1345=d1345, n2345=d2345, n12345=d12345, 
category=c("bayenv", "XtX", "lfmm", "bayescan", "pcadapt"),
lty="blank", 
fill=c("yellow", "orange", "skyblue1", "skyblue3", "blue")
)
dev.off()



###old figure
pdf("CHS.TI.Venn.alloutliers.20171007.pdf")
draw.quintuple.venn(area1=d1, area2=d2, area3=d3, area4=d4, area5=d5,
n12=d12, n13=d13, n14=d14, n15=d15, n23=d23, n24=d24, n25=d25, n34=d34, n35=d35, n45=d45,
n123=d123, n124=d124, n125=d125, n134=d134, n135=d135, n145=d145, n234=d234, n235=d235, n245=d245, n345=d345,
n1234=d1234, n1235=d1235, n1245=d1245, n1345=d1345, n2345=d2345, n12345=d12345, 
category=c("bayenv", "XtX", "lfmm", "bayescan", "pcadapt"),
lty="blank", 
fill=c("yellow", "orange", "skyblue1", "skyblue3", "blue")
)
dev.off()
```
![alt_txt][CHS.TI.allmethods]

[CHS.TI.allmethods]:https://user-images.githubusercontent.com/12142475/31176809-0bdc9db8-a90c-11e7-8779-9d784057db2a.png



### 3. Overlap between all candidate loci identified for CHall, CHN, CHS, CZ

/Users/alexjvr/2016RADAnalysis/3_CH.landscapeGenomics/subsets/Venn/CHP2.MACfilter

First I need to find the non-redundant set of candidate outliers for each of the datasets


##### CHN

```
CHN.alloutliers <- rbind(bayescan.outliers, lfmm.outliers, bayenv.outliers, pcadapt.outliers, XtX.outliers)  ##Join all data.frames by "loci" column. This only works of colnames are the same (at least one column name)

CHN.alloutliers <- lapply(CHN.alloutliers, unique)  ##select only the unique loci (reduces the dataset from 2160 to 1838)
write.table(CHN.alloutliers, "CHN.alloutliers.20171020", col.names=F, row.names=F, quote=F)
```

#### CHS
```
CHS.alloutliers <- rbind(bayescan.outliers, lfmm.outliers, bayenv.outliers, pcadapt.outliers, XtX.outliers)  ##Join all data.frames by "loci" column. This only works of colnames are the same (at least one column name)

CHS.alloutliers <- lapply(CHS.alloutliers, unique)  ##select only the unique loci (reduces the dataset from 2812 to 2392)
write.table(CHS.alloutliers, "CHS.alloutliers.20171020", col.names=F, row.names=F, quote=F)
```

##### CZ

```
CZ.alloutliers <- rbind(lfmm.outliers, bayenv.outliers, pcadapt.outliers, XtX.outliers)  ##Join all data.frames by "name" column. This only works of colnames are the same (at least one column name)

CZ.alloutliers <- lapply(CZ.alloutliers, unique)  ##select only the unique loci (reduces the dataset from 2069 to 1994)
write.table(CZ.alloutliers, "CZ.alloutliers.20171020", col.names=F, row.names=F, quote=F)
```


Then I can read them into R and draw the VennDiagrams

/Users/alexjvr/2016RADAnalysis/3_CH.landscapeGenomics/subsets/Venn/CHP2/MACfilter

First without CHall

```

CHN.outliers <- read.table("CHN/CHN.alloutliers.20171020")
CHN.outliers <- as.data.frame(CHN.outliers)
colnames(CHN.outliers) <- "loci"
CHN.outliers <- as.character(CHN.outliers$loci)

CZ.outliers <- read.table("CZ/CZ.alloutliers.20171020")
CZ.outliers <- as.data.frame(CZ.outliers)
colnames(CZ.outliers) <- "loci"
CZ.outliers <- as.character(CZ.outliers$loci)

CHS.outliers <- read.table("CHS/CHS.alloutliers.20171020")
CHS.outliers <- as.data.frame(CHS.outliers)
colnames(CHS.outliers) <- "loci"
CHS.outliers <- as.character(CHS.outliers$loci)


d1 <- length(CHN.outliers)
d2 <- length(CHS.outliers)
d3 <- length(CZ.outliers)

d12 <- length(Reduce(intersect, list(CHN.outliers, CHS.outliers)))
d13 <- length(Reduce(intersect, list(CHN.outliers, CZ.outliers)))
d23 <- length(Reduce(intersect, list(CHS.outliers, CZ.outliers)))

d123 <- length(Reduce(intersect, list(CHN.outliers, CHS.outliers,CZ.outliers)))

library(VennDiagram)
pdf("Venn.CHN.CHS.CZ.alloutliers.20171020.pdf")
draw.triple.venn(area1=d1, area2=d2, area3=d3, n12=d12, n13=d13, n23=d23, n123=d123, category=c("CHN", "CHS", "CZ"), lty="blank", fill=c("yellow", "orange", "skyblue1"))
dev.off()

```

I was concerned that the large overlap might be only due to lfmm results, so I drew a venn diagram with only the LFMM outliers.

The above graph has been redrawn with the new data. This test was with the old data without MAC filter

```
CHS.lfmm.outliers <- read.table("CHS/CHS.LFMM.alloutliers", header=F)
colnames(CHS.lfmm.outliers) <- "loci"
CHS.lfmm.outliers <- as.character(CHS.lfmm.outliers$loci)
CHN.lfmm.outliers <- read.table("CHN/CHN.LFMM.alloutliers", header=F)
colnames(CHN.lfmm.outliers) <- "loci"
CHN.lfmm.outliers <- as.character(CHN.lfmm.outliers$loci)
CZ.lfmm.outliers <- read.table("CZ/CZ.LFMM.alloutliers", header=F)
colnames(CZ.lfmm.outliers) <- "loci"
CZ.lfmm.outliers <- as.character(CZ.lfmm.outliers$loci)

d1 <- length(CZ.lfmm.outliers)
d2 <- length(CHS.lfmm.outliers)
d3 <- length(CHN.lfmm.outliers)

d12 <- length(Reduce(intersect, list(CZ.lfmm.outliers, CHS.lfmm.outliers)))
d13 <- length(Reduce(intersect, list(CZ.lfmm.outliers, CHN.lfmm.outliers)))
d23 <- length(Reduce(intersect, list(CHS.lfmm.outliers, CHN.lfmm.outliers)))

d123 <- length(Reduce(intersect, list(CZ.lfmm.outliers, CHS.lfmm.outliers,CHN.lfmm.outliers)))


pdf("Venn.CHN.CHS.CZ.onlylfmm.pdf")
draw.triple.venn(area1=d1, area2=d2, area3=d3, n12=d12, n13=d13, n23=d23, n123=d123, category=c("CZ", "CHS", "CHN"), lty="blank", fill=c("yellow", "orange", "skyblue1"))
dev.off()

```

So 244 of 313 identified loci are from lfmm







### 4. Overlap between all candidate loci identified for CHS, CHS.TI, CHS.VS

First I need to find the unique loci for each dataset. CHS was already done in the previous batch

###### CHS.VS
```
CHS.VS.alloutliers <- rbind(bayescan.outliers, lfmm.outliers, bayenv.outliers, pcadapt.outliers, XtX.outliers)  ##Join all data.frames by "name" column. This only works of colnames are the same (at least one column name)

CHS.VS.alloutliers <- lapply(CHS.VS.alloutliers, unique)  ##select only the unique loci (reduces the dataset from 2961 to 2474)
write.table(CHS.VS.alloutliers, "CHS.VS.alloutliers.20171020", col.names=F, row.names=F, quote=F)

```

###### CHS.TI
```
CHS.TI.alloutliers <- rbind(bayescan.outliers, lfmm.outliers, bayenv.outliers, pcadapt.outliers, XtX.outliers)  ##Join all data.frames by "name" column. This only works of colnames are the same (at least one column name)

CHS.TI.alloutliers <- lapply(CHS.TI.alloutliers, unique)  ##select only the unique loci (reduces the dataset from 2471 to 2135)
write.table(CHS.TI.alloutliers, "CHS.TI.alloutliers.20171020", col.names=F, row.names=F, quote=F)

```

And then draw the Venn diagram

```
library(VennDiagram)


CHS.VS.outliers <- read.table("CHS.VS/CHS.VS.alloutliers.20171020", header=F)
colnames(CHS.VS.outliers) <- "loci"
CHS.VS.outliers <- as.character(CHS.VS.outliers$loci)

CHS.outliers <- read.table("CHS/CHS.alloutliers.20171020", header=F)
colnames(CHS.outliers) <- "loci"
CHS.outliers <- as.character(CHS.outliers$loci)

CHS.TI.outliers <- read.table("CHS.TI/CHS.TI.alloutliers.20171020", header=F)
colnames(CHS.TI.outliers) <- "loci"
CHS.TI.outliers <- as.character(CHS.TI.outliers$loci)


d1 <- length(CHS.VS.outliers)
d2 <- length(CHS.outliers)
d3 <- length(CHS.TI.outliers)

d12 <- length(Reduce(intersect, list(CHS.VS.outliers, CHS.outliers)))
d13 <- length(Reduce(intersect, list(CHS.VS.outliers, CHS.TI.outliers)))
d23 <- length(Reduce(intersect, list(CHS.outliers, CHS.TI.outliers)))

d123 <- length(Reduce(intersect, list(CHS.VS.outliers, CHS.outliers,CHS.TI.outliers)))

library(VennDiagram)
pdf("Venn.CHSandVS.TI.alloutliers.20171020.pdf")
draw.triple.venn(area1=d1, area2=d2, area3=d3, n12=d12, n13=d13, n23=d23, n123=d123, category=c("CHS.VS", "CHS", "CHS.TI"), lty="blank", fill=c("yellow", "orange", "skyblue1"))
dev.off()

```


I was worried that the overlap might be only due to the LFMM loci, so I compared this in a Venn diagram: 
```
CHS.lfmm.outliers <- read.table("CHS/CHS.LFMM.alloutliers", header=F)
colnames(CHS.lfmm.outliers) <- "loci"
CHS.lfmm.outliers <- as.character(CHS.lfmm.outliers$loci)
CHS.VS.lfmm.outliers <- read.table("CHS.VS/CHS.VS.LFMM.alloutliers", header=F)
colnames(CHS.VS.lfmm.outliers) <- "loci"
CHS.VS.lfmm.outliers <- as.character(CHS.VS.lfmm.outliers$loci)
CHS.TI.lfmm.outliers <- read.table("CHS.TI/CHS.TI.LFMM.alloutliers", header=F)
colnames(CHS.TI.lfmm.outliers) <- "loci"
CHS.TI.lfmm.outliers <- as.character(CHS.TI.lfmm.outliers$loci)

d1 <- length(CHS.TI.lfmm.outliers)
d2 <- length(CHS.lfmm.outliers)
d3 <- length(CHS.VS.lfmm.outliers)

d12 <- length(Reduce(intersect, list(CHS.TI.lfmm.outliers, CHS.lfmm.outliers)))
d13 <- length(Reduce(intersect, list(CHS.TI.lfmm.outliers, CHS.VS.lfmm.outliers)))
d23 <- length(Reduce(intersect, list(CHS.lfmm.outliers, CHS.VS.lfmm.outliers)))

d123 <- length(Reduce(intersect, list(CHS.TI.lfmm.outliers, CHS.lfmm.outliers,CHS.VS.lfmm.outliers)))


pdf("Venn.CHS.andVS.TI.onlylfmm.pdf")
draw.triple.venn(area1=d1, area2=d2, area3=d3, n12=d12, n13=d13, n23=d23, n123=d123, category=c("CHS.TI", "CHS", "CHS.VS"), lty="blank", fill=c("yellow", "orange", "skyblue1"))
dev.off()


```



### 5. Overlap between duplicated candidate loci identified for CHall, CHN, CHS, CZ

/Users/alexjvr/2016RADAnalysis/3_CH.landscapeGenomics/subsets/Venn/CHP2

First I need to find only the loci that occur more than once in each dataset. 


##### CHN
```
CHN.alloutliers <- rbind(bayescan.outliers, lfmm.outliers, bayenv.outliers, pcadapt.outliers, XtX.outliers)  ##Join all data.frames by "name" column. This only works of colnames are the same (at least one column name)



CHN.duplicated.outliers <- CHN.alloutliers[duplicated(CHN.alloutliers),]  ##select only loci occurring more than once (here 163)
CHN.duplicated.outliers <- unique(CHN.duplicated.outliers)  ##158 loci

write.table(CHN.duplicated.outliers, "CHN.duplicated.outliers.20171020", col.names=F, row.names=F, quote=F)
```

#### CHS
```
CHS.alloutliers <- rbind(bayescan.outliers, lfmm.outliers, bayenv.outliers, pcadapt.outliers, XtX.outliers)  ##Join all data.frames by "name" column. This only works of colnames are the same (at least one column name)

CHS.duplicated.outliers <- CHS.alloutliers[duplicated(CHS.alloutliers),]  ##select only loci occurring more than once (here 420)
CHS.duplicated.outliers <- unique(CHS.duplicated.outliers)  ###355 loci

write.table(CHS.duplicated.outliers, "CHS.duplicated.outliers.20171020", col.names=F, row.names=F, quote=F)
```

##### CZ

```
CZ.alloutliers <- rbind(bayescan.outliers, lfmm.outliers, bayenv.outliers, pcadapt.outliers, XtX.outliers)  ##Join all data.frames by "name" column. This only works of colnames are the same (at least one column name)

CZ.duplicated.outliers <- CZ.alloutliers[duplicated(CZ.alloutliers),]  ##select only loci occurring more than once (here 226 from 2462)
CZ.duplicated.outliers <- unique(CZ.duplicated.outliers)  ###198 loci

write.table(CZ.duplicated.outliers, "CZ.duplicated.outliers.20171020", col.names=F, row.names=F, quote=F)
```


Then I can read them into R and draw the VennDiagrams

/Users/alexjvr/2016RADAnalysis/3_CH.landscapeGenomics/subsets/Venn/CHP2/MAC.filtered

First without CHall
```
library(VennDiagram)


CHN.duplicated.outliers <- read.table("CHN/CHN.duplicated.outliers.20171020", header=F)
colnames(CHN.duplicated.outliers) <- "loci"
CHN.duplicated.outliers <- as.character(CHN.duplicated.outliers$loci)

CZ.duplicated.outliers <- read.table("CZ/CZ.duplicated.outliers.20171020", header=F)
colnames(CZ.duplicated.outliers) <- "loci"
CZ.duplicated.outliers <- as.character(CZ.duplicated.outliers$loci)

CHS.duplicated.outliers <- read.table("CHS/CHS.duplicated.outliers.20171020", header=F)
colnames(CHS.duplicated.outliers) <- "loci"
CHS.duplicated.outliers <- as.character(CHS.duplicated.outliers$loci)


d1 <- length(CHN.duplicated.outliers)
d2 <- length(CHS.duplicated.outliers)
d3 <- length(CZ.duplicated.outliers)

d12 <- length(Reduce(intersect, list(CHN.duplicated.outliers, CHS.duplicated.outliers)))
d13 <- length(Reduce(intersect, list(CHN.duplicated.outliers, CZ.duplicated.outliers)))
d23 <- length(Reduce(intersect, list(CHS.duplicated.outliers, CZ.duplicated.outliers)))

d123 <- length(Reduce(intersect, list(CHN.duplicated.outliers, CHS.duplicated.outliers,CZ.duplicated.outliers)))


pdf("Venn.CHN.CHS.CZ.duplicated.outliers.20171020.pdf")
draw.triple.venn(area1=d1, area2=d2, area3=d3, n12=d12, n13=d13, n23=d23, n123=d123, category=c("CHN", "CHS", "CZ"), lty="blank", fill=c("yellow", "orange", "skyblue1"))
dev.off()

```





### 6. Overlap between all candidate loci identified for CHS, CHS.TI, CHS.VS

First I need to find the loci that occur more than once. CHS was already done in the previous batch. 

###### CHS.VS
```

CHS.VS.alloutliers <- rbind(bayescan.outliers, lfmm.outliers, bayenv.outliers, pcadapt.outliers, XtX.outliers)  ##Join all data.frames by "name" column. This only works of colnames are the same (at least one column name)

CHS.VS.duplicated.outliers <- CHS.VS.alloutliers[duplicated(CHS.VS.alloutliers),]  ##select only loci occurring more than once (here 487 from 2961)
CHS.VS.duplicated.outliers <- unique(CHS.VS.duplicated.outliers)  ##408 loci


write.table(CHS.VS.duplicated.outliers, "CHS.VS.duplicated.outliers.20171020", col.names=F, row.names=F, quote=F)
```

###### CHS.TI
```

CHS.TI.alloutliers <- rbind(bayescan.outliers, lfmm.outliers, bayenv.outliers, pcadapt.outliers, XtX.outliers)  ##Join all data.frames by "name" column. This only works of colnames are the same (at least one column name)

CHS.TI.duplicated.outliers <- CHS.TI.alloutliers[duplicated(CHS.TI.alloutliers),]  ##select only loci occurring more than once (here 336 from 2471)
CHS.TI.duplicated.outliers <- unique(CHS.TI.duplicated.outliers) ##260

write.table(CHS.TI.duplicated.outliers, "CHS.TI.duplicated.outliers.20171020", col.names=F, row.names=F, quote=F)
```

And then draw the Venn diagram

```
library(VennDiagram)


CHS.VS.duplicated.outliers <- read.table("CHS.VS/CHS.VS.duplicated.outliers.20171020", header=F)
colnames(CHS.VS.duplicated.outliers) <- "loci"
CHS.VS.duplicated.outliers <- as.character(CHS.VS.duplicated.outliers$loci)

CHS.TI.duplicated.outliers <- read.table("CHS.TI/CHS.TI.duplicated.outliers.20171020", header=F)
colnames(CHS.TI.duplicated.outliers) <- "loci"
CHS.TI.duplicated.outliers <- as.character(CHS.TI.duplicated.outliers$loci)

CHS.duplicated.outliers <- read.table("CHS/CHS.duplicated.outliers.20171020", header=F)
colnames(CHS.duplicated.outliers) <- "loci"
CHS.duplicated.outliers <- as.character(CHS.duplicated.outliers$loci)


d1 <- length(CHS.VS.duplicated.outliers)
d2 <- length(CHS.duplicated.outliers)
d3 <- length(CHS.TI.duplicated.outliers)

d12 <- length(Reduce(intersect, list(CHS.VS.duplicated.outliers, CHS.duplicated.outliers)))
d13 <- length(Reduce(intersect, list(CHS.VS.duplicated.outliers, CHS.TI.duplicated.outliers)))
d23 <- length(Reduce(intersect, list(CHS.duplicated.outliers, CHS.TI.duplicated.outliers)))

d123 <- length(Reduce(intersect, list(CHS.VS.duplicated.outliers, CHS.duplicated.outliers,CHS.TI.duplicated.outliers)))


pdf("Venn.CHS.withVS.TI.duplicated.outliers.20171020.pdf")
draw.triple.venn(area1=d1, area2=d2, area3=d3, n12=d12, n13=d13, n23=d23, n123=d123, category=c("CHS.VS", "CHS", "CHS.TI"), lty="blank", fill=c("yellow", "orange", "skyblue1"))
dev.off()

```





# Old Data (no MAC filter)
## Venn Diagrams 

Calculating the overlap in loci identified for all the different datasets. 

getwd()
"/Users/alexjvr/2016RADAnalysis/3_CH.landscapeGenomics/subsets/BayENV2_results/CHP2.results"

I've saved the R project from fgcz47 where I was working: 

fgcz47:/srv/kenlab/alexjvr_p1795/CHcomplete/BayENV2/CHP2


I'm showing: 

1. Venn Diagram within analysis for 
  
  1. LFMM
  
  2. bayEnv2

2. overlap between LFMM, Bayenv2, PCadapt, XtX within each region (i.e. 6 plots)

3. Overlap between all candidate loci identified for CHall, CHN, CHS, CZ

4. Overlap between all candidate loci identified for CHS, CHS.TI, CHS.VS

5. Overlap between all candidate loci identified by 2+ methods fo CHall, CHN, CHS, CZ

6. Overlap between all candidate loci identified by 2+ methods for CHS, CHS.TI, CHS.VS



### 1.1 Venn Diagram for loci within LFMM

These have already been drawn. 

See: https://github.com/alexjvr1/Manuscripts/blob/master/Chp2_CHdata_LFMM.md



Venn.CHN.n5.LFMMonly_20170310.pdf

Venn.CHS.n5.LFMMonly_20170310.pdf

Venn.CZ.n5.LFMMonly_20170310.pdf

Venn.CHS.VS.n5.LFMMonly_20170310.pdf

Venn.CHS.TI.n5.LFMMonly_20170310.pdf




### 1.2 Venn Diagram for loci within BayEnv2


##### CHall

```
load("CHP2.BayEnv2.fgcz.RData")

library(VennDiagram)

d1 <- length(CHall.rad.bayenv.candidates.names)
d2 <- length(CHall.shadow.days.bayenv.candidates.names)
d3 <- length(CHall.temp.bayenv.candidates.names)
d4 <- length(CHall.pcpt.bayenv.candidates.names)
d5 <- length(CHall.day.10cm.bayenv.candidates.names)


d12 <- length(Reduce(intersect, list(CHall.rad.bayenv.candidates.names, CHall.shadow.days.bayenv.candidates.names)))
d13 <- length(Reduce(intersect, list(CHall.rad.bayenv.candidates.names, CHall.temp.bayenv.candidates.names)))
d14 <- length(Reduce(intersect, list(CHall.rad.bayenv.candidates.names, CHall.pcpt.bayenv.candidates.names)))
d15 <- length(Reduce(intersect, list(CHall.rad.bayenv.candidates.names, CHall.day.10cm.bayenv.candidates.names)))
d23 <- length(Reduce(intersect, list(CHall.shadow.days.bayenv.candidates.names, CHall.temp.bayenv.candidates.names)))
d24 <- length(Reduce(intersect, list(CHall.shadow.days.bayenv.candidates.names, CHall.pcpt.bayenv.candidates.names)))
d25 <- length(Reduce(intersect, list(CHall.shadow.days.bayenv.candidates.names, CHall.day.10cm.bayenv.candidates.names)))
d34 <- length(Reduce(intersect, list(CHall.temp.bayenv.candidates.names, CHall.pcpt.bayenv.candidates.names)))
d35 <- length(Reduce(intersect, list(CHall.temp.bayenv.candidates.names, CHall.day.10cm.bayenv.candidates.names)))
d45 <- length(Reduce(intersect, list(CHall.pcpt.bayenv.candidates.names, CHall.day.10cm.bayenv.candidates.names)))

d123 <- length(Reduce(intersect, list(CHall.rad.bayenv.candidates.names, CHall.shadow.days.bayenv.candidates.names,CHall.temp.bayenv.candidates.names)))
d124 <- length(Reduce(intersect, list(CHall.rad.bayenv.candidates.names, CHall.shadow.days.bayenv.candidates.names,CHall.pcpt.bayenv.candidates.names)))
d125 <- length(Reduce(intersect, list(CHall.rad.bayenv.candidates.names, CHall.shadow.days.bayenv.candidates.names,CHall.day.10cm.bayenv.candidates.names)))
d234 <- length(Reduce(intersect, list(CHall.shadow.days.bayenv.candidates.names, CHall.temp.bayenv.candidates.names,CHall.pcpt.bayenv.candidates.names)))
d134 <- length(Reduce(intersect, list(CHall.rad.bayenv.candidates.names, CHall.temp.bayenv.candidates.names,CHall.pcpt.bayenv.candidates.names)))
d135 <- length(Reduce(intersect, list(CHall.rad.bayenv.candidates.names, CHall.temp.bayenv.candidates.names,CHall.day.10cm.bayenv.candidates.names)))
d145 <- length(Reduce(intersect, list(CHall.rad.bayenv.candidates.names, CHall.pcpt.bayenv.candidates.names,CHall.day.10cm.bayenv.candidates.names)))
d235 <- length(Reduce(intersect, list(CHall.shadow.days.bayenv.candidates.names, CHall.temp.bayenv.candidates.names,CHall.day.10cm.bayenv.candidates.names)))
d245 <- length(Reduce(intersect, list(CHall.shadow.days.bayenv.candidates.names, CHall.pcpt.bayenv.candidates.names,CHall.day.10cm.bayenv.candidates.names)))
d345 <- length(Reduce(intersect, list(CHall.temp.bayenv.candidates.names, CHall.pcpt.bayenv.candidates.names,CHall.day.10cm.bayenv.candidates.names)))


d1234 <- length(Reduce(intersect, list(CHall.shadow.days.bayenv.candidates.names, CHall.temp.bayenv.candidates.names,
CHall.pcpt.bayenv.candidates.names, CHall.rad.bayenv.candidates.names)))
d1235 <- length(Reduce(intersect, list(CHall.shadow.days.bayenv.candidates.names, CHall.temp.bayenv.candidates.names,
CHall.day.10cm.bayenv.candidates.names, CHall.rad.bayenv.candidates.names)))

d2345 <- length(Reduce(intersect, list(CHall.shadow.days.bayenv.candidates.names, CHall.temp.bayenv.candidates.names,
CHall.pcpt.bayenv.candidates.names, CHall.day.10cm.bayenv.candidates.names)))
d1245 <- length(Reduce(intersect, list(CHall.shadow.days.bayenv.candidates.names, CHall.rad.bayenv.candidates.names,
CHall.pcpt.bayenv.candidates.names, CHall.day.10cm.bayenv.candidates.names)))
d1345 <- length(Reduce(intersect, list(CHall.temp.bayenv.candidates.names, CHall.rad.bayenv.candidates.names,
CHall.pcpt.bayenv.candidates.names, CHall.day.10cm.bayenv.candidates.names)))
d12345 <- length(Reduce(intersect, list(CHall.rad.bayenv.candidates.names, CHall.shadow.days.bayenv.candidates.names, CHall.temp.bayenv.candidates.names, 
CHall.pcpt.bayenv.candidates.names, CHall.day.10cm.bayenv.candidates.names)))

pdf("CHall.bayenv2.VENN.pdf")
draw.quintuple.venn(area1=d1, area2=d2, area3=d3, area4=d4, area5=d5,
n12=d12, n13=d13, n14=d14, n15=d15, n23=d23, n24=d24, n25=d25, n34=d34, n35=d35, n45=d45,
n123=d123, n124=d124, n125=d125, n134=d134, n135=d135, n145=d145, n234=d234, n235=d235, n245=d245, n345=d345,
n1234=d1234, n1235=d1235, n1245=d1245, n1345=d1345, n2345=d2345, n12345=d12345, 
category=c("CHall.rad", "CHall.shadow.days", "CHall.pcpt", "CHall.temp", "CHall.day.10cm"),
lty="blank", 
fill=c("yellow", "orange", "skyblue1", "skyblue3", "blue")
)
dev.off()
```


##### CHN

```
library(VennDiagram)


#Check that all the lists have names in them. Where no candidates were found, there’ll only be an “X.”
#These can be made to <- NULL so that they aren’t reflected in the Venn

CHN.rad.bayenv.candidates.names
CHN.shadow.days.bayenv.candidates.names
CHN.temp.bayenv.candidates.names
CHN.pcpt.bayenv.candidates.names
CHN.day.10cm.bayenv.candidates.names


CHN.shadow.days.bayenv.candidates.names <- NULL
CHN.temp.bayenv.candidates.names <- NULL
CHN.pcpt.bayenv.candidates.names <- NULL
CHN.day.10cm.bayenv.candidates.names <- NULL


d1 <- length(CHN.rad.bayenv.candidates.names)
d2 <- length(CHN.shadow.days.bayenv.candidates.names)
d3 <- length(CHN.temp.bayenv.candidates.names)
d4 <- length(CHN.pcpt.bayenv.candidates.names)
d5 <- length(CHN.day.10cm.bayenv.candidates.names)


d12 <- length(Reduce(intersect, list(CHN.rad.bayenv.candidates.names, CHN.shadow.days.bayenv.candidates.names)))
d13 <- length(Reduce(intersect, list(CHN.rad.bayenv.candidates.names, CHN.temp.bayenv.candidates.names)))
d14 <- length(Reduce(intersect, list(CHN.rad.bayenv.candidates.names, CHN.pcpt.bayenv.candidates.names)))
d15 <- length(Reduce(intersect, list(CHN.rad.bayenv.candidates.names, CHN.day.10cm.bayenv.candidates.names)))
d23 <- length(Reduce(intersect, list(CHN.shadow.days.bayenv.candidates.names, CHN.temp.bayenv.candidates.names)))
d24 <- length(Reduce(intersect, list(CHN.shadow.days.bayenv.candidates.names, CHN.pcpt.bayenv.candidates.names)))
d25 <- length(Reduce(intersect, list(CHN.shadow.days.bayenv.candidates.names, CHN.day.10cm.bayenv.candidates.names)))
d34 <- length(Reduce(intersect, list(CHN.temp.bayenv.candidates.names, CHN.pcpt.bayenv.candidates.names)))
d35 <- length(Reduce(intersect, list(CHN.temp.bayenv.candidates.names, CHN.day.10cm.bayenv.candidates.names)))
d45 <- length(Reduce(intersect, list(CHN.pcpt.bayenv.candidates.names, CHN.day.10cm.bayenv.candidates.names)))

d123 <- length(Reduce(intersect, list(CHN.rad.bayenv.candidates.names, CHN.shadow.days.bayenv.candidates.names,CHN.temp.bayenv.candidates.names)))
d124 <- length(Reduce(intersect, list(CHN.rad.bayenv.candidates.names, CHN.shadow.days.bayenv.candidates.names,CHN.pcpt.bayenv.candidates.names)))
d125 <- length(Reduce(intersect, list(CHN.rad.bayenv.candidates.names, CHN.shadow.days.bayenv.candidates.names,CHN.day.10cm.bayenv.candidates.names)))
d234 <- length(Reduce(intersect, list(CHN.shadow.days.bayenv.candidates.names, CHN.temp.bayenv.candidates.names,CHN.pcpt.bayenv.candidates.names)))
d134 <- length(Reduce(intersect, list(CHN.rad.bayenv.candidates.names, CHN.temp.bayenv.candidates.names,CHN.pcpt.bayenv.candidates.names)))
d135 <- length(Reduce(intersect, list(CHN.rad.bayenv.candidates.names, CHN.temp.bayenv.candidates.names,CHN.day.10cm.bayenv.candidates.names)))
d145 <- length(Reduce(intersect, list(CHN.rad.bayenv.candidates.names, CHN.pcpt.bayenv.candidates.names,CHN.day.10cm.bayenv.candidates.names)))
d235 <- length(Reduce(intersect, list(CHN.shadow.days.bayenv.candidates.names, CHN.temp.bayenv.candidates.names,CHN.day.10cm.bayenv.candidates.names)))
d245 <- length(Reduce(intersect, list(CHN.shadow.days.bayenv.candidates.names, CHN.pcpt.bayenv.candidates.names,CHN.day.10cm.bayenv.candidates.names)))
d345 <- length(Reduce(intersect, list(CHN.temp.bayenv.candidates.names, CHN.pcpt.bayenv.candidates.names,CHN.day.10cm.bayenv.candidates.names)))


d1234 <- length(Reduce(intersect, list(CHN.shadow.days.bayenv.candidates.names, CHN.temp.bayenv.candidates.names,
CHN.pcpt.bayenv.candidates.names, CHN.rad.bayenv.candidates.names)))
d1235 <- length(Reduce(intersect, list(CHN.shadow.days.bayenv.candidates.names, CHN.temp.bayenv.candidates.names,
CHN.day.10cm.bayenv.candidates.names, CHN.rad.bayenv.candidates.names)))

d2345 <- length(Reduce(intersect, list(CHN.shadow.days.bayenv.candidates.names, CHN.temp.bayenv.candidates.names,
CHN.pcpt.bayenv.candidates.names, CHN.day.10cm.bayenv.candidates.names)))
d1245 <- length(Reduce(intersect, list(CHN.shadow.days.bayenv.candidates.names, CHN.rad.bayenv.candidates.names,
CHN.pcpt.bayenv.candidates.names, CHN.day.10cm.bayenv.candidates.names)))
d1345 <- length(Reduce(intersect, list(CHN.temp.bayenv.candidates.names, CHN.rad.bayenv.candidates.names,
CHN.pcpt.bayenv.candidates.names, CHN.day.10cm.bayenv.candidates.names)))
d12345 <- length(Reduce(intersect, list(CHN.rad.bayenv.candidates.names, CHN.shadow.days.bayenv.candidates.names, CHN.temp.bayenv.candidates.names, 
CHN.pcpt.bayenv.candidates.names, CHN.day.10cm.bayenv.candidates.names)))

pdf("CHN.bayenv2.VENN.pdf")
draw.quintuple.venn(area1=d1, area2=d2, area3=d3, area4=d4, area5=d5,
n12=d12, n13=d13, n14=d14, n15=d15, n23=d23, n24=d24, n25=d25, n34=d34, n35=d35, n45=d45,
n123=d123, n124=d124, n125=d125, n134=d134, n135=d135, n145=d145, n234=d234, n235=d235, n245=d245, n345=d345,
n1234=d1234, n1235=d1235, n1245=d1245, n1345=d1345, n2345=d2345, n12345=d12345, 
category=c("CHN.rad", "CHN.shadow.days", "CHN.pcpt", "CHN.temp", "CHN.day.10cm"),
lty="blank", 
fill=c("yellow", "orange", "skyblue1", "skyblue3", "blue")
)
dev.off()


```



##### CHS

```
library(VennDiagram)


#Check that all the lists have names in them. Where no candidates were found, there’ll only be an “X.”
#These can be made to <- NULL so that they aren’t reflected in the Venn

CHS.rad.bayenv.candidates.names
CHS.shadow.days.bayenv.candidates.names
CHS.temp.bayenv.candidates.names
CHS.pcpt.bayenv.candidates.names
CHS.day.10cm.bayenv.candidates.names



d1 <- length(CHS.rad.bayenv.candidates.names)
d2 <- length(CHS.shadow.days.bayenv.candidates.names)
d3 <- length(CHS.temp.bayenv.candidates.names)
d4 <- length(CHS.pcpt.bayenv.candidates.names)
d5 <- length(CHS.day.10cm.bayenv.candidates.names)


d12 <- length(Reduce(intersect, list(CHS.rad.bayenv.candidates.names, CHS.shadow.days.bayenv.candidates.names)))
d13 <- length(Reduce(intersect, list(CHS.rad.bayenv.candidates.names, CHS.temp.bayenv.candidates.names)))
d14 <- length(Reduce(intersect, list(CHS.rad.bayenv.candidates.names, CHS.pcpt.bayenv.candidates.names)))
d15 <- length(Reduce(intersect, list(CHS.rad.bayenv.candidates.names, CHS.day.10cm.bayenv.candidates.names)))
d23 <- length(Reduce(intersect, list(CHS.shadow.days.bayenv.candidates.names, CHS.temp.bayenv.candidates.names)))
d24 <- length(Reduce(intersect, list(CHS.shadow.days.bayenv.candidates.names, CHS.pcpt.bayenv.candidates.names)))
d25 <- length(Reduce(intersect, list(CHS.shadow.days.bayenv.candidates.names, CHS.day.10cm.bayenv.candidates.names)))
d34 <- length(Reduce(intersect, list(CHS.temp.bayenv.candidates.names, CHS.pcpt.bayenv.candidates.names)))
d35 <- length(Reduce(intersect, list(CHS.temp.bayenv.candidates.names, CHS.day.10cm.bayenv.candidates.names)))
d45 <- length(Reduce(intersect, list(CHS.pcpt.bayenv.candidates.names, CHS.day.10cm.bayenv.candidates.names)))

d123 <- length(Reduce(intersect, list(CHS.rad.bayenv.candidates.names, CHS.shadow.days.bayenv.candidates.names,CHS.temp.bayenv.candidates.names)))
d124 <- length(Reduce(intersect, list(CHS.rad.bayenv.candidates.names, CHS.shadow.days.bayenv.candidates.names,CHS.pcpt.bayenv.candidates.names)))
d125 <- length(Reduce(intersect, list(CHS.rad.bayenv.candidates.names, CHS.shadow.days.bayenv.candidates.names,CHS.day.10cm.bayenv.candidates.names)))
d234 <- length(Reduce(intersect, list(CHS.shadow.days.bayenv.candidates.names, CHS.temp.bayenv.candidates.names,CHS.pcpt.bayenv.candidates.names)))
d134 <- length(Reduce(intersect, list(CHS.rad.bayenv.candidates.names, CHS.temp.bayenv.candidates.names,CHS.pcpt.bayenv.candidates.names)))
d135 <- length(Reduce(intersect, list(CHS.rad.bayenv.candidates.names, CHS.temp.bayenv.candidates.names,CHS.day.10cm.bayenv.candidates.names)))
d145 <- length(Reduce(intersect, list(CHS.rad.bayenv.candidates.names, CHS.pcpt.bayenv.candidates.names,CHS.day.10cm.bayenv.candidates.names)))
d235 <- length(Reduce(intersect, list(CHS.shadow.days.bayenv.candidates.names, CHS.temp.bayenv.candidates.names,CHS.day.10cm.bayenv.candidates.names)))
d245 <- length(Reduce(intersect, list(CHS.shadow.days.bayenv.candidates.names, CHS.pcpt.bayenv.candidates.names,CHS.day.10cm.bayenv.candidates.names)))
d345 <- length(Reduce(intersect, list(CHS.temp.bayenv.candidates.names, CHS.pcpt.bayenv.candidates.names,CHS.day.10cm.bayenv.candidates.names)))


d1234 <- length(Reduce(intersect, list(CHS.shadow.days.bayenv.candidates.names, CHS.temp.bayenv.candidates.names,
CHS.pcpt.bayenv.candidates.names, CHS.rad.bayenv.candidates.names)))
d1235 <- length(Reduce(intersect, list(CHS.shadow.days.bayenv.candidates.names, CHS.temp.bayenv.candidates.names,
CHS.day.10cm.bayenv.candidates.names, CHS.rad.bayenv.candidates.names)))

d2345 <- length(Reduce(intersect, list(CHS.shadow.days.bayenv.candidates.names, CHS.temp.bayenv.candidates.names,
CHS.pcpt.bayenv.candidates.names, CHS.day.10cm.bayenv.candidates.names)))
d1245 <- length(Reduce(intersect, list(CHS.shadow.days.bayenv.candidates.names, CHS.rad.bayenv.candidates.names,
CHS.pcpt.bayenv.candidates.names, CHS.day.10cm.bayenv.candidates.names)))
d1345 <- length(Reduce(intersect, list(CHS.temp.bayenv.candidates.names, CHS.rad.bayenv.candidates.names,
CHS.pcpt.bayenv.candidates.names, CHS.day.10cm.bayenv.candidates.names)))
d12345 <- length(Reduce(intersect, list(CHS.rad.bayenv.candidates.names, CHS.shadow.days.bayenv.candidates.names, CHS.temp.bayenv.candidates.names, 
CHS.pcpt.bayenv.candidates.names, CHS.day.10cm.bayenv.candidates.names)))

pdf("CHS.bayenv2.VENN.pdf")
draw.quintuple.venn(area1=d1, area2=d2, area3=d3, area4=d4, area5=d5,
n12=d12, n13=d13, n14=d14, n15=d15, n23=d23, n24=d24, n25=d25, n34=d34, n35=d35, n45=d45,
n123=d123, n124=d124, n125=d125, n134=d134, n135=d135, n145=d145, n234=d234, n235=d235, n245=d245, n345=d345,
n1234=d1234, n1235=d1235, n1245=d1245, n1345=d1345, n2345=d2345, n12345=d12345, 
category=c("CHS.rad", "CHS.shadow.days", "CHS.pcpt", "CHS.temp", "CHS.day.10cm"),
lty="blank", 
fill=c("yellow", "orange", "skyblue1", "skyblue3", "blue")
)
dev.off()


```



##### CZ
```
library(VennDiagram)


#Check that all the lists have names in them. Where no candidates were found, there’ll only be an “X.”
#These can be made to <- NULL so that they aren’t reflected in the Venn

CZ.rad.bayenv.candidates.names
CZ.shadow.days.bayenv.candidates.names
CZ.temp.bayenv.candidates.names
CZ.pcpt.bayenv.candidates.names
CZ.day.10cm.bayenv.candidates.names



d1 <- length(CZ.rad.bayenv.candidates.names)
d2 <- length(CZ.shadow.days.bayenv.candidates.names)
d3 <- length(CZ.temp.bayenv.candidates.names)
d4 <- length(CZ.pcpt.bayenv.candidates.names)
d5 <- length(CZ.day.10cm.bayenv.candidates.names)


d12 <- length(Reduce(intersect, list(CZ.rad.bayenv.candidates.names, CZ.shadow.days.bayenv.candidates.names)))
d13 <- length(Reduce(intersect, list(CZ.rad.bayenv.candidates.names, CZ.temp.bayenv.candidates.names)))
d14 <- length(Reduce(intersect, list(CZ.rad.bayenv.candidates.names, CZ.pcpt.bayenv.candidates.names)))
d15 <- length(Reduce(intersect, list(CZ.rad.bayenv.candidates.names, CZ.day.10cm.bayenv.candidates.names)))
d23 <- length(Reduce(intersect, list(CZ.shadow.days.bayenv.candidates.names, CZ.temp.bayenv.candidates.names)))
d24 <- length(Reduce(intersect, list(CZ.shadow.days.bayenv.candidates.names, CZ.pcpt.bayenv.candidates.names)))
d25 <- length(Reduce(intersect, list(CZ.shadow.days.bayenv.candidates.names, CZ.day.10cm.bayenv.candidates.names)))
d34 <- length(Reduce(intersect, list(CZ.temp.bayenv.candidates.names, CZ.pcpt.bayenv.candidates.names)))
d35 <- length(Reduce(intersect, list(CZ.temp.bayenv.candidates.names, CZ.day.10cm.bayenv.candidates.names)))
d45 <- length(Reduce(intersect, list(CZ.pcpt.bayenv.candidates.names, CZ.day.10cm.bayenv.candidates.names)))

d123 <- length(Reduce(intersect, list(CZ.rad.bayenv.candidates.names, CZ.shadow.days.bayenv.candidates.names,CZ.temp.bayenv.candidates.names)))
d124 <- length(Reduce(intersect, list(CZ.rad.bayenv.candidates.names, CZ.shadow.days.bayenv.candidates.names,CZ.pcpt.bayenv.candidates.names)))
d125 <- length(Reduce(intersect, list(CZ.rad.bayenv.candidates.names, CZ.shadow.days.bayenv.candidates.names,CZ.day.10cm.bayenv.candidates.names)))
d234 <- length(Reduce(intersect, list(CZ.shadow.days.bayenv.candidates.names, CZ.temp.bayenv.candidates.names,CZ.pcpt.bayenv.candidates.names)))
d134 <- length(Reduce(intersect, list(CZ.rad.bayenv.candidates.names, CZ.temp.bayenv.candidates.names,CZ.pcpt.bayenv.candidates.names)))
d135 <- length(Reduce(intersect, list(CZ.rad.bayenv.candidates.names, CZ.temp.bayenv.candidates.names,CZ.day.10cm.bayenv.candidates.names)))
d145 <- length(Reduce(intersect, list(CZ.rad.bayenv.candidates.names, CZ.pcpt.bayenv.candidates.names,CZ.day.10cm.bayenv.candidates.names)))
d235 <- length(Reduce(intersect, list(CZ.shadow.days.bayenv.candidates.names, CZ.temp.bayenv.candidates.names,CZ.day.10cm.bayenv.candidates.names)))
d245 <- length(Reduce(intersect, list(CZ.shadow.days.bayenv.candidates.names, CZ.pcpt.bayenv.candidates.names,CZ.day.10cm.bayenv.candidates.names)))
d345 <- length(Reduce(intersect, list(CZ.temp.bayenv.candidates.names, CZ.pcpt.bayenv.candidates.names,CZ.day.10cm.bayenv.candidates.names)))


d1234 <- length(Reduce(intersect, list(CZ.shadow.days.bayenv.candidates.names, CZ.temp.bayenv.candidates.names,
CZ.pcpt.bayenv.candidates.names, CZ.rad.bayenv.candidates.names)))
d1235 <- length(Reduce(intersect, list(CZ.shadow.days.bayenv.candidates.names, CZ.temp.bayenv.candidates.names,
CZ.day.10cm.bayenv.candidates.names, CZ.rad.bayenv.candidates.names)))

d2345 <- length(Reduce(intersect, list(CZ.shadow.days.bayenv.candidates.names, CZ.temp.bayenv.candidates.names,
CZ.pcpt.bayenv.candidates.names, CZ.day.10cm.bayenv.candidates.names)))
d1245 <- length(Reduce(intersect, list(CZ.shadow.days.bayenv.candidates.names, CZ.rad.bayenv.candidates.names,
CZ.pcpt.bayenv.candidates.names, CZ.day.10cm.bayenv.candidates.names)))
d1345 <- length(Reduce(intersect, list(CZ.temp.bayenv.candidates.names, CZ.rad.bayenv.candidates.names,
CZ.pcpt.bayenv.candidates.names, CZ.day.10cm.bayenv.candidates.names)))
d12345 <- length(Reduce(intersect, list(CZ.rad.bayenv.candidates.names, CZ.shadow.days.bayenv.candidates.names, CZ.temp.bayenv.candidates.names, 
CZ.pcpt.bayenv.candidates.names, CZ.day.10cm.bayenv.candidates.names)))

pdf("CZ.bayenv2.VENN.pdf")
draw.quintuple.venn(area1=d1, area2=d2, area3=d3, area4=d4, area5=d5,
n12=d12, n13=d13, n14=d14, n15=d15, n23=d23, n24=d24, n25=d25, n34=d34, n35=d35, n45=d45,
n123=d123, n124=d124, n125=d125, n134=d134, n135=d135, n145=d145, n234=d234, n235=d235, n245=d245, n345=d345,
n1234=d1234, n1235=d1235, n1245=d1245, n1345=d1345, n2345=d2345, n12345=d12345, 
category=c("CZ.rad", "CZ.shadow.days", "CZ.pcpt", "CZ.temp", "CZ.day.10cm"),
lty="blank", 
fill=c("yellow", "orange", "skyblue1", "skyblue3", "blue")
)
dev.off()

```



##### CHS.VS
```
library(VennDiagram)


#Check that all the lists have names in them. Where no candidates were found, there’ll only be an “X.”
#These can be made to <- NULL so that they aren’t reflected in the Venn

CHS.VS.rad.bayenv.candidates.names
CHS.VS.shadow.days.bayenv.candidates.names
CHS.VS.temp.bayenv.candidates.names
CHS.VS.pcpt.bayenv.candidates.names
CHS.VS.day.10cm.bayenv.candidates.names



d1 <- length(CHS.VS.rad.bayenv.candidates.names)
d2 <- length(CHS.VS.shadow.days.bayenv.candidates.names)
d3 <- length(CHS.VS.temp.bayenv.candidates.names)
d4 <- length(CHS.VS.pcpt.bayenv.candidates.names)
d5 <- length(CHS.VS.day.10cm.bayenv.candidates.names)


d12 <- length(Reduce(intersect, list(CHS.VS.rad.bayenv.candidates.names, CHS.VS.shadow.days.bayenv.candidates.names)))
d13 <- length(Reduce(intersect, list(CHS.VS.rad.bayenv.candidates.names, CHS.VS.temp.bayenv.candidates.names)))
d14 <- length(Reduce(intersect, list(CHS.VS.rad.bayenv.candidates.names, CHS.VS.pcpt.bayenv.candidates.names)))
d15 <- length(Reduce(intersect, list(CHS.VS.rad.bayenv.candidates.names, CHS.VS.day.10cm.bayenv.candidates.names)))
d23 <- length(Reduce(intersect, list(CHS.VS.shadow.days.bayenv.candidates.names, CHS.VS.temp.bayenv.candidates.names)))
d24 <- length(Reduce(intersect, list(CHS.VS.shadow.days.bayenv.candidates.names, CHS.VS.pcpt.bayenv.candidates.names)))
d25 <- length(Reduce(intersect, list(CHS.VS.shadow.days.bayenv.candidates.names, CHS.VS.day.10cm.bayenv.candidates.names)))
d34 <- length(Reduce(intersect, list(CHS.VS.temp.bayenv.candidates.names, CHS.VS.pcpt.bayenv.candidates.names)))
d35 <- length(Reduce(intersect, list(CHS.VS.temp.bayenv.candidates.names, CHS.VS.day.10cm.bayenv.candidates.names)))
d45 <- length(Reduce(intersect, list(CHS.VS.pcpt.bayenv.candidates.names, CHS.VS.day.10cm.bayenv.candidates.names)))

d123 <- length(Reduce(intersect, list(CHS.VS.rad.bayenv.candidates.names, CHS.VS.shadow.days.bayenv.candidates.names,CHS.VS.temp.bayenv.candidates.names)))
d124 <- length(Reduce(intersect, list(CHS.VS.rad.bayenv.candidates.names, CHS.VS.shadow.days.bayenv.candidates.names,CHS.VS.pcpt.bayenv.candidates.names)))
d125 <- length(Reduce(intersect, list(CHS.VS.rad.bayenv.candidates.names, CHS.VS.shadow.days.bayenv.candidates.names,CHS.VS.day.10cm.bayenv.candidates.names)))
d234 <- length(Reduce(intersect, list(CHS.VS.shadow.days.bayenv.candidates.names, CHS.VS.temp.bayenv.candidates.names,CHS.VS.pcpt.bayenv.candidates.names)))
d134 <- length(Reduce(intersect, list(CHS.VS.rad.bayenv.candidates.names, CHS.VS.temp.bayenv.candidates.names,CHS.VS.pcpt.bayenv.candidates.names)))
d135 <- length(Reduce(intersect, list(CHS.VS.rad.bayenv.candidates.names, CHS.VS.temp.bayenv.candidates.names,CHS.VS.day.10cm.bayenv.candidates.names)))
d145 <- length(Reduce(intersect, list(CHS.VS.rad.bayenv.candidates.names, CHS.VS.pcpt.bayenv.candidates.names,CHS.VS.day.10cm.bayenv.candidates.names)))
d235 <- length(Reduce(intersect, list(CHS.VS.shadow.days.bayenv.candidates.names, CHS.VS.temp.bayenv.candidates.names,CHS.VS.day.10cm.bayenv.candidates.names)))
d245 <- length(Reduce(intersect, list(CHS.VS.shadow.days.bayenv.candidates.names, CHS.VS.pcpt.bayenv.candidates.names,CHS.VS.day.10cm.bayenv.candidates.names)))
d345 <- length(Reduce(intersect, list(CHS.VS.temp.bayenv.candidates.names, CHS.VS.pcpt.bayenv.candidates.names,CHS.VS.day.10cm.bayenv.candidates.names)))


d1234 <- length(Reduce(intersect, list(CHS.VS.shadow.days.bayenv.candidates.names, CHS.VS.temp.bayenv.candidates.names,
CHS.VS.pcpt.bayenv.candidates.names, CHS.VS.rad.bayenv.candidates.names)))
d1235 <- length(Reduce(intersect, list(CHS.VS.shadow.days.bayenv.candidates.names, CHS.VS.temp.bayenv.candidates.names,
CHS.VS.day.10cm.bayenv.candidates.names, CHS.VS.rad.bayenv.candidates.names)))

d2345 <- length(Reduce(intersect, list(CHS.VS.shadow.days.bayenv.candidates.names, CHS.VS.temp.bayenv.candidates.names,
CHS.VS.pcpt.bayenv.candidates.names, CHS.VS.day.10cm.bayenv.candidates.names)))
d1245 <- length(Reduce(intersect, list(CHS.VS.shadow.days.bayenv.candidates.names, CHS.VS.rad.bayenv.candidates.names,
CHS.VS.pcpt.bayenv.candidates.names, CHS.VS.day.10cm.bayenv.candidates.names)))
d1345 <- length(Reduce(intersect, list(CHS.VS.temp.bayenv.candidates.names, CHS.VS.rad.bayenv.candidates.names,
CHS.VS.pcpt.bayenv.candidates.names, CHS.VS.day.10cm.bayenv.candidates.names)))
d12345 <- length(Reduce(intersect, list(CHS.VS.rad.bayenv.candidates.names, CHS.VS.shadow.days.bayenv.candidates.names, CHS.VS.temp.bayenv.candidates.names, 
CHS.VS.pcpt.bayenv.candidates.names, CHS.VS.day.10cm.bayenv.candidates.names)))

pdf("CHS.VS.bayenv2.VENN.pdf")
draw.quintuple.venn(area1=d1, area2=d2, area3=d3, area4=d4, area5=d5,
n12=d12, n13=d13, n14=d14, n15=d15, n23=d23, n24=d24, n25=d25, n34=d34, n35=d35, n45=d45,
n123=d123, n124=d124, n125=d125, n134=d134, n135=d135, n145=d145, n234=d234, n235=d235, n245=d245, n345=d345,
n1234=d1234, n1235=d1235, n1245=d1245, n1345=d1345, n2345=d2345, n12345=d12345, 
category=c("CHS.VS.rad", "CHS.VS.shadow.days", "CHS.VS.pcpt", "CHS.VS.temp", "CHS.VS.day.10cm"),
lty="blank", 
fill=c("yellow", "orange", "skyblue1", "skyblue3", "blue")
)
dev.off()

```


##### CHS.TI

```
library(VennDiagram)


#Check that all the lists have names in them. Where no candidates were found, there’ll only be an “X.”
#These can be made to <- NULL so that they aren’t reflected in the Venn

CHS.TI.rad.bayenv.candidates.names
CHS.TI.shadow.days.bayenv.candidates.names
CHS.TI.temp.bayenv.candidates.names
CHS.TI.pcpt.bayenv.candidates.names
CHS.TI.day.10cm.bayenv.candidates.names



d1 <- length(CHS.TI.rad.bayenv.candidates.names)
d2 <- length(CHS.TI.shadow.days.bayenv.candidates.names)
d3 <- length(CHS.TI.temp.bayenv.candidates.names)
d4 <- length(CHS.TI.pcpt.bayenv.candidates.names)
d5 <- length(CHS.TI.day.10cm.bayenv.candidates.names)


d12 <- length(Reduce(intersect, list(CHS.TI.rad.bayenv.candidates.names, CHS.TI.shadow.days.bayenv.candidates.names)))
d13 <- length(Reduce(intersect, list(CHS.TI.rad.bayenv.candidates.names, CHS.TI.temp.bayenv.candidates.names)))
d14 <- length(Reduce(intersect, list(CHS.TI.rad.bayenv.candidates.names, CHS.TI.pcpt.bayenv.candidates.names)))
d15 <- length(Reduce(intersect, list(CHS.TI.rad.bayenv.candidates.names, CHS.TI.day.10cm.bayenv.candidates.names)))
d23 <- length(Reduce(intersect, list(CHS.TI.shadow.days.bayenv.candidates.names, CHS.TI.temp.bayenv.candidates.names)))
d24 <- length(Reduce(intersect, list(CHS.TI.shadow.days.bayenv.candidates.names, CHS.TI.pcpt.bayenv.candidates.names)))
d25 <- length(Reduce(intersect, list(CHS.TI.shadow.days.bayenv.candidates.names, CHS.TI.day.10cm.bayenv.candidates.names)))
d34 <- length(Reduce(intersect, list(CHS.TI.temp.bayenv.candidates.names, CHS.TI.pcpt.bayenv.candidates.names)))
d35 <- length(Reduce(intersect, list(CHS.TI.temp.bayenv.candidates.names, CHS.TI.day.10cm.bayenv.candidates.names)))
d45 <- length(Reduce(intersect, list(CHS.TI.pcpt.bayenv.candidates.names, CHS.TI.day.10cm.bayenv.candidates.names)))

d123 <- length(Reduce(intersect, list(CHS.TI.rad.bayenv.candidates.names, CHS.TI.shadow.days.bayenv.candidates.names,CHS.TI.temp.bayenv.candidates.names)))
d124 <- length(Reduce(intersect, list(CHS.TI.rad.bayenv.candidates.names, CHS.TI.shadow.days.bayenv.candidates.names,CHS.TI.pcpt.bayenv.candidates.names)))
d125 <- length(Reduce(intersect, list(CHS.TI.rad.bayenv.candidates.names, CHS.TI.shadow.days.bayenv.candidates.names,CHS.TI.day.10cm.bayenv.candidates.names)))
d234 <- length(Reduce(intersect, list(CHS.TI.shadow.days.bayenv.candidates.names, CHS.TI.temp.bayenv.candidates.names,CHS.TI.pcpt.bayenv.candidates.names)))
d134 <- length(Reduce(intersect, list(CHS.TI.rad.bayenv.candidates.names, CHS.TI.temp.bayenv.candidates.names,CHS.TI.pcpt.bayenv.candidates.names)))
d135 <- length(Reduce(intersect, list(CHS.TI.rad.bayenv.candidates.names, CHS.TI.temp.bayenv.candidates.names,CHS.TI.day.10cm.bayenv.candidates.names)))
d145 <- length(Reduce(intersect, list(CHS.TI.rad.bayenv.candidates.names, CHS.TI.pcpt.bayenv.candidates.names,CHS.TI.day.10cm.bayenv.candidates.names)))
d235 <- length(Reduce(intersect, list(CHS.TI.shadow.days.bayenv.candidates.names, CHS.TI.temp.bayenv.candidates.names,CHS.TI.day.10cm.bayenv.candidates.names)))
d245 <- length(Reduce(intersect, list(CHS.TI.shadow.days.bayenv.candidates.names, CHS.TI.pcpt.bayenv.candidates.names,CHS.TI.day.10cm.bayenv.candidates.names)))
d345 <- length(Reduce(intersect, list(CHS.TI.temp.bayenv.candidates.names, CHS.TI.pcpt.bayenv.candidates.names,CHS.TI.day.10cm.bayenv.candidates.names)))


d1234 <- length(Reduce(intersect, list(CHS.TI.shadow.days.bayenv.candidates.names, CHS.TI.temp.bayenv.candidates.names,
CHS.TI.pcpt.bayenv.candidates.names, CHS.TI.rad.bayenv.candidates.names)))
d1235 <- length(Reduce(intersect, list(CHS.TI.shadow.days.bayenv.candidates.names, CHS.TI.temp.bayenv.candidates.names,
CHS.TI.day.10cm.bayenv.candidates.names, CHS.TI.rad.bayenv.candidates.names)))

d2345 <- length(Reduce(intersect, list(CHS.TI.shadow.days.bayenv.candidates.names, CHS.TI.temp.bayenv.candidates.names,
CHS.TI.pcpt.bayenv.candidates.names, CHS.TI.day.10cm.bayenv.candidates.names)))
d1245 <- length(Reduce(intersect, list(CHS.TI.shadow.days.bayenv.candidates.names, CHS.TI.rad.bayenv.candidates.names,
CHS.TI.pcpt.bayenv.candidates.names, CHS.TI.day.10cm.bayenv.candidates.names)))
d1345 <- length(Reduce(intersect, list(CHS.TI.temp.bayenv.candidates.names, CHS.TI.rad.bayenv.candidates.names,
CHS.TI.pcpt.bayenv.candidates.names, CHS.TI.day.10cm.bayenv.candidates.names)))
d12345 <- length(Reduce(intersect, list(CHS.TI.rad.bayenv.candidates.names, CHS.TI.shadow.days.bayenv.candidates.names, CHS.TI.temp.bayenv.candidates.names, 
CHS.TI.pcpt.bayenv.candidates.names, CHS.TI.day.10cm.bayenv.candidates.names)))

pdf("CHS.TI.bayenv2.VENN.pdf")
draw.quintuple.venn(area1=d1, area2=d2, area3=d3, area4=d4, area5=d5,
n12=d12, n13=d13, n14=d14, n15=d15, n23=d23, n24=d24, n25=d25, n34=d34, n35=d35, n45=d45,
n123=d123, n124=d124, n125=d125, n134=d134, n135=d135, n145=d145, n234=d234, n235=d235, n245=d245, n345=d345,
n1234=d1234, n1235=d1235, n1245=d1245, n1345=d1345, n2345=d2345, n12345=d12345, 
category=c("CHS.TI.rad", "CHS.TI.shadow.days", "CHS.TI.pcpt", "CHS.TI.temp", "CHS.TI.day.10cm"),
lty="blank", 
fill=c("yellow", "orange", "skyblue1", "skyblue3", "blue")
)
dev.off()


```


### 2. overlap between LFMM, Bayenv2, PCadapt, XtX within each region

/Users/alexjvr/2016RADAnalysis/3_CH.landscapeGenomics/subsets/Venn/CHP2

##### CHall

NEED LFMM data


##### CHN

```
library(VennDiagram)

lfmm.outliers <- read.table("CHN.LFMM.alloutliers")
colnames(lfmm.outliers) <- "loci"
lfmm.outliers <- as.character(lfmm.outliers$loci)

bayenv.outliers <- read.table("CHN.BayEnv.alloutliers", header=F)
bayenv.outliers <- bayenv.outliers[-c(3),]  ##remove the X. this is just an empty row but is counted as an outlier in the Venn Diagram
bayenv.outliers <- as.data.frame(bayenv.outliers)
bayenv.outliers <- as.character(bayenv.outliers)


XtX.outliers <- read.table("CHN.XtX.100outliers")
colnames(XtX.outliers) <- "loci"
XtX.outliers <- as.character(XtX.outliers$loci)

pcadapt.outliers <- read.table("CHN.pcadapt.outliers")
colnames(pcadapt.outliers) <- "loci"
pcadapt.outliers <- as.character(pcadapt.outliers$loci)

d1 <- length(lfmm.outliers)
d2 <- length(bayenv.outliers)
d3 <- length(XtX.outliers)
d4 <- length(pcadapt.outliers)

d12 <- length(Reduce(intersect, list(lfmm.outliers, bayenv.outliers)))
d13 <- length(Reduce(intersect, list(lfmm.outliers, XtX.outliers)))
d14 <- length(Reduce(intersect, list(lfmm.outliers, pcadapt.outliers)))
d23 <- length(Reduce(intersect, list(bayenv.outliers, XtX.outliers)))
d24 <- length(Reduce(intersect, list(bayenv.outliers, pcadapt.outliers)))
d34 <- length(Reduce(intersect, list(XtX.outliers, pcadapt.outliers)))

d123 <- length(Reduce(intersect, list(lfmm.outliers, bayenv.outliers,XtX.outliers)))
d124 <- length(Reduce(intersect, list(lfmm.outliers, bayenv.outliers,pcadapt.outliers)))
d234 <- length(Reduce(intersect, list(bayenv.outliers, XtX.outliers,pcadapt.outliers)))
d134 <- length(Reduce(intersect, list(lfmm.outliers, XtX.outliers,pcadapt.outliers)))

d1234 <- length(Reduce(intersect, list(lfmm.outliers, bayenv.outliers, XtX.outliers, pcadapt.outliers)))

pdf(file="Venn.CHN.alloutliers.pdf")
draw.quad.venn(area1=d1, area2=d2, area3=d3, area4=d4, n12=d12, n13=d13, n14=d14, n23=d23, n24=d24, n34=d34, n123=d123, n124=d124, n134=d134, n234=d234, n1234=d1234, category=c("lfmm", "bayenv", "XtX", "pcadapt"), lty="blank", fill=c("yellow", "orange", "skyblue1", "blue"))
dev.off()
```

##### CHS

```
library(VennDiagram)

lfmm.outliers <- read.table("CHS.LFMM.alloutliers")
colnames(lfmm.outliers) <- "loci"
lfmm.outliers <- as.character(lfmm.outliers$loci)

bayenv.outliers <- read.table("CHS.BayEnv.alloutliers", header=F)
colnames(bayenv.outliers) <- "loci"
bayenv.outliers <- as.character(bayenv.outliers$loci)

XtX.outliers <- read.table("CHS.XtX.100outliers")
colnames(XtX.outliers) <- "loci"
XtX.outliers <- as.character(XtX.outliers$loci)

pcadapt.outliers <- read.table("CHS.pcadapt.outliers")
colnames(pcadapt.outliers) <- "loci"
pcadapt.outliers <- as.character(pcadapt.outliers$loci)

d1 <- length(lfmm.outliers)
d2 <- length(bayenv.outliers)
d3 <- length(XtX.outliers)
d4 <- length(pcadapt.outliers)

d12 <- length(Reduce(intersect, list(lfmm.outliers, bayenv.outliers)))
d13 <- length(Reduce(intersect, list(lfmm.outliers, XtX.outliers)))
d14 <- length(Reduce(intersect, list(lfmm.outliers, pcadapt.outliers)))
d23 <- length(Reduce(intersect, list(bayenv.outliers, XtX.outliers)))
d24 <- length(Reduce(intersect, list(bayenv.outliers, pcadapt.outliers)))
d34 <- length(Reduce(intersect, list(XtX.outliers, pcadapt.outliers)))

d123 <- length(Reduce(intersect, list(lfmm.outliers, bayenv.outliers,XtX.outliers)))
d124 <- length(Reduce(intersect, list(lfmm.outliers, bayenv.outliers,pcadapt.outliers)))
d234 <- length(Reduce(intersect, list(bayenv.outliers, XtX.outliers,pcadapt.outliers)))
d134 <- length(Reduce(intersect, list(lfmm.outliers, XtX.outliers,pcadapt.outliers)))

d1234 <- length(Reduce(intersect, list(lfmm.outliers, bayenv.outliers, XtX.outliers, pcadapt.outliers)))

pdf(file="Venn.CHS.alloutliers.pdf")
draw.quad.venn(area1=d1, area2=d2, area3=d3, area4=d4, n12=d12, n13=d13, n14=d14, n23=d23, n24=d24, n34=d34, n123=d123, n124=d124, n134=d134, n234=d234, n1234=d1234, category=c("lfmm", "bayenv", "XtX", "pcadapt"), lty="blank", fill=c("yellow", "orange", "skyblue1", "blue"))
dev.off()



```




##### CZ

```
library(VennDiagram)

lfmm.outliers <- read.table("CZ.LFMM.alloutliers")
colnames(lfmm.outliers) <- "loci"
lfmm.outliers <- as.character(lfmm.outliers$loci)

bayenv.outliers <- read.table("CZ.BayEnv.alloutliers", header=F)
colnames(bayenv.outliers) <- "loci"
bayenv.outliers <- as.character(bayenv.outliers$loci)

XtX.outliers <- read.table("CZ.XtX.100outliers")
colnames(XtX.outliers) <- "loci"
XtX.outliers <- as.character(XtX.outliers$loci)

pcadapt.outliers <- read.table("CZ.pcadapt.outliers")
colnames(pcadapt.outliers) <- "loci"
pcadapt.outliers <- as.character(pcadapt.outliers$loci)

d1 <- length(lfmm.outliers)
d2 <- length(bayenv.outliers)
d3 <- length(XtX.outliers)
d4 <- length(pcadapt.outliers)

d12 <- length(Reduce(intersect, list(lfmm.outliers, bayenv.outliers)))
d13 <- length(Reduce(intersect, list(lfmm.outliers, XtX.outliers)))
d14 <- length(Reduce(intersect, list(lfmm.outliers, pcadapt.outliers)))
d23 <- length(Reduce(intersect, list(bayenv.outliers, XtX.outliers)))
d24 <- length(Reduce(intersect, list(bayenv.outliers, pcadapt.outliers)))
d34 <- length(Reduce(intersect, list(XtX.outliers, pcadapt.outliers)))

d123 <- length(Reduce(intersect, list(lfmm.outliers, bayenv.outliers,XtX.outliers)))
d124 <- length(Reduce(intersect, list(lfmm.outliers, bayenv.outliers,pcadapt.outliers)))
d234 <- length(Reduce(intersect, list(bayenv.outliers, XtX.outliers,pcadapt.outliers)))
d134 <- length(Reduce(intersect, list(lfmm.outliers, XtX.outliers,pcadapt.outliers)))

d1234 <- length(Reduce(intersect, list(lfmm.outliers, bayenv.outliers, XtX.outliers, pcadapt.outliers)))

pdf(file="Venn.CZ.alloutliers.pdf")
draw.quad.venn(area1=d1, area2=d2, area3=d3, area4=d4, n12=d12, n13=d13, n14=d14, n23=d23, n24=d24, n34=d34, n123=d123, n124=d124, n134=d134, n234=d234, n1234=d1234, category=c("lfmm", "bayenv", "XtX", "pcadapt"), lty="blank", fill=c("yellow", "orange", "skyblue1", "blue"))
dev.off()



```

##### CHS.VS

```
library(VennDiagram)

lfmm.outliers <- read.table("CHS.VS.LFMM.alloutliers")
colnames(lfmm.outliers) <- "loci"
lfmm.outliers <- as.character(lfmm.outliers$loci)

bayenv.outliers <- read.table("CHS.VS.BayEnv.alloutliers", header=F)
colnames(bayenv.outliers) <- "loci"
bayenv.outliers <- as.character(bayenv.outliers$loci)

XtX.outliers <- read.table("CHS.VS.XtX.100outliers")
colnames(XtX.outliers) <- "loci"
XtX.outliers <- as.character(XtX.outliers$loci)

pcadapt.outliers <- read.table("CHS.VS.pcadapt.outliers")
colnames(pcadapt.outliers) <- "loci"
pcadapt.outliers <- as.character(pcadapt.outliers$loci)

d1 <- length(lfmm.outliers)
d2 <- length(bayenv.outliers)
d3 <- length(XtX.outliers)
d4 <- length(pcadapt.outliers)

d12 <- length(Reduce(intersect, list(lfmm.outliers, bayenv.outliers)))
d13 <- length(Reduce(intersect, list(lfmm.outliers, XtX.outliers)))
d14 <- length(Reduce(intersect, list(lfmm.outliers, pcadapt.outliers)))
d23 <- length(Reduce(intersect, list(bayenv.outliers, XtX.outliers)))
d24 <- length(Reduce(intersect, list(bayenv.outliers, pcadapt.outliers)))
d34 <- length(Reduce(intersect, list(XtX.outliers, pcadapt.outliers)))

d123 <- length(Reduce(intersect, list(lfmm.outliers, bayenv.outliers,XtX.outliers)))
d124 <- length(Reduce(intersect, list(lfmm.outliers, bayenv.outliers,pcadapt.outliers)))
d234 <- length(Reduce(intersect, list(bayenv.outliers, XtX.outliers,pcadapt.outliers)))
d134 <- length(Reduce(intersect, list(lfmm.outliers, XtX.outliers,pcadapt.outliers)))

d1234 <- length(Reduce(intersect, list(lfmm.outliers, bayenv.outliers, XtX.outliers, pcadapt.outliers)))

pdf(file="Venn.CHS.VS.alloutliers.pdf")
draw.quad.venn(area1=d1, area2=d2, area3=d3, area4=d4, n12=d12, n13=d13, n14=d14, n23=d23, n24=d24, n34=d34, n123=d123, n124=d124, n134=d134, n234=d234, n1234=d1234, category=c("lfmm", "bayenv", "XtX", "pcadapt"), lty="blank", fill=c("yellow", "orange", "skyblue1", "blue"))
dev.off()


```

##### CHS.TI

```
library(VennDiagram)

lfmm.outliers <- read.table("CHS.TI.LFMM.alloutliers")
colnames(lfmm.outliers) <- "loci"
lfmm.outliers <- as.character(lfmm.outliers$loci)

bayenv.outliers <- read.table("CHS.TI.BayEnv.alloutliers", header=F)
colnames(bayenv.outliers) <- "loci"
bayenv.outliers <- as.character(bayenv.outliers$loci)

XtX.outliers <- read.table("CHS.TI.XtX.100outliers")
colnames(XtX.outliers) <- "loci"
XtX.outliers <- as.character(XtX.outliers$loci)

pcadapt.outliers <- read.table("CHS.TI.pcadapt.outliers")
colnames(pcadapt.outliers) <- "loci"
pcadapt.outliers <- as.character(pcadapt.outliers$loci)

d1 <- length(lfmm.outliers)
d2 <- length(bayenv.outliers)
d3 <- length(XtX.outliers)
d4 <- length(pcadapt.outliers)

d12 <- length(Reduce(intersect, list(lfmm.outliers, bayenv.outliers)))
d13 <- length(Reduce(intersect, list(lfmm.outliers, XtX.outliers)))
d14 <- length(Reduce(intersect, list(lfmm.outliers, pcadapt.outliers)))
d23 <- length(Reduce(intersect, list(bayenv.outliers, XtX.outliers)))
d24 <- length(Reduce(intersect, list(bayenv.outliers, pcadapt.outliers)))
d34 <- length(Reduce(intersect, list(XtX.outliers, pcadapt.outliers)))

d123 <- length(Reduce(intersect, list(lfmm.outliers, bayenv.outliers,XtX.outliers)))
d124 <- length(Reduce(intersect, list(lfmm.outliers, bayenv.outliers,pcadapt.outliers)))
d234 <- length(Reduce(intersect, list(bayenv.outliers, XtX.outliers,pcadapt.outliers)))
d134 <- length(Reduce(intersect, list(lfmm.outliers, XtX.outliers,pcadapt.outliers)))

d1234 <- length(Reduce(intersect, list(lfmm.outliers, bayenv.outliers, XtX.outliers, pcadapt.outliers)))

pdf(file="Venn.CHS.TI.alloutliers.pdf")
draw.quad.venn(area1=d1, area2=d2, area3=d3, area4=d4, n12=d12, n13=d13, n14=d14, n23=d23, n24=d24, n34=d34, n123=d123, n124=d124, n134=d134, n234=d234, n1234=d1234, category=c("lfmm", "bayenv", "XtX", "pcadapt"), lty="blank", fill=c("yellow", "orange", "skyblue1", "blue"))
dev.off()

```

### 3. Overlap between all candidate loci identified for CHall, CHN, CHS, CZ

/Users/alexjvr/2016RADAnalysis/3_CH.landscapeGenomics/subsets/Venn/CHP2

First I need to find the non-redundant set of candidate outliers for each of the datasets

##### CHall
```
###I still need the LFMM results for this
```

##### CHN
```
lfmm.outliers <- as.data.frame(lfmm.outliers)
pcadapt.outliers <- as.data.frame(pcadapt.outliers)
XtX.outliers <- as.data.frame(XtX.outliers)
bayenv.outliers <- as.data.frame(bayenv.outliers)

colnames(lfmm.outliers) <- "loci"
colnames(XtX.outliers) <- "loci"
colnames(pcadapt.outliers) <- "loci"
colnames(bayenv.outliers) <- "loci"

CHN.alloutliers <- rbind(lfmm.outliers, bayenv.outliers, pcadapt.outliers, XtX.outliers)  ##Join all data.frames by "name" column. This only works of colnames are the same (at least one column name)

CHN.alloutliers <- lapply(CHN.alloutliers, unique)  ##select only the unique loci (reduces the dataset from 2976 to 2950)
write.table(CHN.alloutliers, "CHN.alloutliers", col.names=F, row.names=F, quote=F)
```

#### CHS
```

lfmm.outliers <- as.data.frame(lfmm.outliers)
pcadapt.outliers <- as.data.frame(pcadapt.outliers)
XtX.outliers <- as.data.frame(XtX.outliers)
bayenv.outliers <- as.data.frame(bayenv.outliers)

colnames(lfmm.outliers) <- "loci"
colnames(XtX.outliers) <- "loci"
colnames(pcadapt.outliers) <- "loci"
colnames(bayenv.outliers) <- "loci"

CHS.alloutliers <- rbind(lfmm.outliers, bayenv.outliers, pcadapt.outliers, XtX.outliers)  ##Join all data.frames by "name" column. This only works of colnames are the same (at least one column name)

CHS.alloutliers <- lapply(CHS.alloutliers, unique)  ##select only the unique loci (reduces the dataset from 4608 to 4376)
write.table(CHS.alloutliers, "CHS.alloutliers", col.names=F, row.names=F, quote=F)
```

##### CZ

```
lfmm.outliers <- as.data.frame(lfmm.outliers)
pcadapt.outliers <- as.data.frame(pcadapt.outliers)
XtX.outliers <- as.data.frame(XtX.outliers)
bayenv.outliers <- as.data.frame(bayenv.outliers)

colnames(lfmm.outliers) <- "loci"
colnames(XtX.outliers) <- "loci"
colnames(pcadapt.outliers) <- "loci"
colnames(bayenv.outliers) <- "loci"

CZ.alloutliers <- rbind(lfmm.outliers, bayenv.outliers, pcadapt.outliers, XtX.outliers)  ##Join all data.frames by "name" column. This only works of colnames are the same (at least one column name)

CZ.alloutliers <- lapply(CZ.alloutliers, unique)  ##select only the unique loci (reduces the dataset from 3090 to 3044)
write.table(CZ.alloutliers, "CZ.alloutliers", col.names=F, row.names=F, quote=F)
```


Then I can read them into R and draw the VennDiagrams

/Users/alexjvr/2016RADAnalysis/3_CH.landscapeGenomics/subsets/Venn/CHP2

First without CHall

```

CHN.outliers <- as.data.frame(CHN.outliers)
colnames(CHN.outliers) <- "loci"
CHN.outliers <- as.character(CHN.outliers$loci)

CZ.outliers <- as.data.frame(CZ.outliers)
colnames(CZ.outliers) <- "loci"
CZ.outliers <- as.character(CZ.outliers$loci)

CHS.outliers <- as.data.frame(CHS.outliers)
colnames(CHS.outliers) <- "loci"
CHS.outliers <- as.character(CHS.outliers$loci)


d1 <- length(CHN.outliers)
d2 <- length(CHS.outliers)
d3 <- length(CZ.outliers)

d12 <- length(Reduce(intersect, list(CHN.outliers, CHS.outliers)))
d13 <- length(Reduce(intersect, list(CHN.outliers, CZ.outliers)))
d23 <- length(Reduce(intersect, list(CHS.outliers, CZ.outliers)))

d123 <- length(Reduce(intersect, list(CHN.outliers, CHS.outliers,CZ.outliers)))


#pdf("Venn.CHSandVS.TI.alloutliers.pdf")
draw.triple.venn(area1=d1, area2=d2, area3=d3, n12=d12, n13=d13, n23=d23, n123=d123, category=c("CHN", "CHS", "CZ"), lty="blank", fill=c("yellow", "orange", "skyblue1"))
#dev.off()

```


I was concerned that the large overlap might be only due to lfmm results, so I drew a venn diagram with only the LFMM outliers.
```
CHS.lfmm.outliers <- read.table("CHS/CHS.LFMM.alloutliers", header=F)
colnames(CHS.lfmm.outliers) <- "loci"
CHS.lfmm.outliers <- as.character(CHS.lfmm.outliers$loci)
CHN.lfmm.outliers <- read.table("CHN/CHN.LFMM.alloutliers", header=F)
colnames(CHN.lfmm.outliers) <- "loci"
CHN.lfmm.outliers <- as.character(CHN.lfmm.outliers$loci)
CZ.lfmm.outliers <- read.table("CZ/CZ.LFMM.alloutliers", header=F)
colnames(CZ.lfmm.outliers) <- "loci"
CZ.lfmm.outliers <- as.character(CZ.lfmm.outliers$loci)

d1 <- length(CZ.lfmm.outliers)
d2 <- length(CHS.lfmm.outliers)
d3 <- length(CHN.lfmm.outliers)

d12 <- length(Reduce(intersect, list(CZ.lfmm.outliers, CHS.lfmm.outliers)))
d13 <- length(Reduce(intersect, list(CZ.lfmm.outliers, CHN.lfmm.outliers)))
d23 <- length(Reduce(intersect, list(CHS.lfmm.outliers, CHN.lfmm.outliers)))

d123 <- length(Reduce(intersect, list(CZ.lfmm.outliers, CHS.lfmm.outliers,CHN.lfmm.outliers)))


pdf("Venn.CHN.CHS.CZ.onlylfmm.pdf")
draw.triple.venn(area1=d1, area2=d2, area3=d3, n12=d12, n13=d13, n23=d23, n123=d123, category=c("CZ", "CHS", "CHN"), lty="blank", fill=c("yellow", "orange", "skyblue1"))
dev.off()

```

So 244 of 313 identified loci are from lfmm



######Still have to rerun the CHall LFMM analysis
And with
```
library(VennDiagram)

CHall.outliers <- read.table("CHall/CHall.alloutliers", header=F)
colnames(CHall.outliers) <- "loci"
CHall.outliers <- as.character(CHall.outliers$loci)

CHN.outliers <- read.table("CHN/CHN.alloutliers", header=F)
colnames(CHN.outliers) <- "loci"
CHN.outliers <- as.character(CHN.outliers$loci)

CHS.outliers <- read.table("CHS/CHS.alloutliers", header=F)
colnames(CHS.outliers) <- "loci"
CHS.outliers <- as.character(CHS.outliers$loci)

CZ.outliers <- read.table("CZ/CZ.alloutliers", header=F)
colnames(CZ.outliers) <- "loci"
CZ.outliers <- as.character(CZ.outliers$loci)


d1 <- length(CHall.outliers)
d2 <- length(CHN.outliers)
d3 <- length(CHS.outliers)
d4 <- length(CZ.outliers)

d12 <- length(Reduce(intersect, list(CHall.outliers, CHN.outliers)))
d13 <- length(Reduce(intersect, list(CHall.outliers, CHS.outliers)))
d14 <- length(Reduce(intersect, list(CHall.outliers, CZ.outliers)))
d23 <- length(Reduce(intersect, list(CHN.outliers, CHS.outliers)))
d24 <- length(Reduce(intersect, list(CHN.outliers, CZ.outliers)))
d34 <- length(Reduce(intersect, list(CHS.outliers, CZ.outliers)))

d123 <- length(Reduce(intersect, list(CHall.outliers, CHN.outliers,CHS.outliers)))
d124 <- length(Reduce(intersect, list(CHall.outliers, CHN.outliers,CZ.outliers)))
d234 <- length(Reduce(intersect, list(CHN.outliers, CHS.outliers,CZ.outliers)))
d134 <- length(Reduce(intersect, list(CHall.outliers, CHS.outliers,CZ.outliers)))

d1234 <- length(Reduce(intersect, list(CHall.outliers, CHN.outliers, CHS.outliers, CZ.outliers)))

pdf(file="Venn.CHall.CHS.CHN.CZ.alloutliers.pdf")
draw.quad.venn(area1=d1, area2=d2, area3=d3, area4=d4, n12=d12, n13=d13, n14=d14, n23=d23, n24=d24, n34=d34, n123=d123, n124=d124, n134=d134, n234=d234, n1234=d1234, category=c("lfmm", "bayenv", "XtX", "pcadapt"), lty="blank", fill=c("yellow", "orange", "skyblue1", "blue"))
dev.off()

```



### 4. Overlap between all candidate loci identified for CHS, CHS.TI, CHS.VS

First I need to find the unique loci for each dataset. CHS was already done in the previous batch

###### CHS.VS
```
lfmm.outliers <- as.data.frame(lfmm.outliers)
pcadapt.outliers <- as.data.frame(pcadapt.outliers)
XtX.outliers <- as.data.frame(XtX.outliers)
bayenv.outliers <- as.data.frame(bayenv.outliers)

colnames(lfmm.outliers) <- "loci"
colnames(XtX.outliers) <- "loci"
colnames(pcadapt.outliers) <- "loci"
colnames(bayenv.outliers) <- "loci"

CHS.VS.alloutliers <- rbind(lfmm.outliers, bayenv.outliers, pcadapt.outliers, XtX.outliers)  ##Join all data.frames by "name" column. This only works of colnames are the same (at least one column name)

CHS.VS.alloutliers <- lapply(CHS.VS.alloutliers, unique)  ##select only the unique loci (reduces the dataset from 3090 to 3044)
write.table(CHS.VS.alloutliers, "CHS.VS.alloutliers", col.names=F, row.names=F, quote=F)
```

###### CHS.TI
```
lfmm.outliers <- as.data.frame(lfmm.outliers)
pcadapt.outliers <- as.data.frame(pcadapt.outliers)
XtX.outliers <- as.data.frame(XtX.outliers)
bayenv.outliers <- as.data.frame(bayenv.outliers)

colnames(lfmm.outliers) <- "loci"
colnames(XtX.outliers) <- "loci"
colnames(pcadapt.outliers) <- "loci"
colnames(bayenv.outliers) <- "loci"

CHS.TI.alloutliers <- rbind(lfmm.outliers, bayenv.outliers, pcadapt.outliers, XtX.outliers)  ##Join all data.frames by "name" column. This only works of colnames are the same (at least one column name)

CHS.TI.alloutliers <- lapply(CHS.TI.alloutliers, unique)  ##select only the unique loci (reduces the dataset from 3090 to 3044)
write.table(CHS.TI.alloutliers, "CHS.TI.alloutliers", col.names=F, row.names=F, quote=F)

```

And then draw the Venn diagram

```
library(VennDiagram)


CHS.VS.outliers <- read.table("CHS.VS/CHS.VS.alloutliers", header=F)
colnames(CHS.VS.outliers) <- "loci"
CHS.VS.outliers <- as.character(CHS.VS.outliers$loci)

CHS.outliers <- read.table("CHS/CHS.alloutliers", header=F)
colnames(CHS.outliers) <- "loci"
CHS.outliers <- as.character(CHS.outliers$loci)

CHS.TI.outliers <- read.table("CHS.TI/CHS.TI.alloutliers", header=F)
colnames(CHS.TI.outliers) <- "loci"
CHS.TI.outliers <- as.character(CHS.TI.outliers$loci)


d1 <- length(CHS.VS.outliers)
d2 <- length(CHS.outliers)
d3 <- length(CHS.TI.outliers)

d12 <- length(Reduce(intersect, list(CHS.VS.outliers, CHS.outliers)))
d13 <- length(Reduce(intersect, list(CHS.VS.outliers, CHS.TI.outliers)))
d23 <- length(Reduce(intersect, list(CHS.outliers, CHS.TI.outliers)))

d123 <- length(Reduce(intersect, list(CHS.VS.outliers, CHS.outliers,CHS.TI.outliers)))


pdf("Venn.CHSandVS.TI.alloutliers.pdf")
draw.triple.venn(area1=d1, area2=d2, area3=d3, n12=d12, n13=d13, n23=d23, n123=d123, category=c("CHS.VS", "CHS", "CHS.TI"), lty="blank", fill=c("yellow", "orange", "skyblue1"))
dev.off()

```


I was worried that the overlap might be only due to the LFMM loci, so I compared this in a Venn diagram: 
```
CHS.lfmm.outliers <- read.table("CHS/CHS.LFMM.alloutliers", header=F)
colnames(CHS.lfmm.outliers) <- "loci"
CHS.lfmm.outliers <- as.character(CHS.lfmm.outliers$loci)
CHS.VS.lfmm.outliers <- read.table("CHS.VS/CHS.VS.LFMM.alloutliers", header=F)
colnames(CHS.VS.lfmm.outliers) <- "loci"
CHS.VS.lfmm.outliers <- as.character(CHS.VS.lfmm.outliers$loci)
CHS.TI.lfmm.outliers <- read.table("CHS.TI/CHS.TI.LFMM.alloutliers", header=F)
colnames(CHS.TI.lfmm.outliers) <- "loci"
CHS.TI.lfmm.outliers <- as.character(CHS.TI.lfmm.outliers$loci)

d1 <- length(CHS.TI.lfmm.outliers)
d2 <- length(CHS.lfmm.outliers)
d3 <- length(CHS.VS.lfmm.outliers)

d12 <- length(Reduce(intersect, list(CHS.TI.lfmm.outliers, CHS.lfmm.outliers)))
d13 <- length(Reduce(intersect, list(CHS.TI.lfmm.outliers, CHS.VS.lfmm.outliers)))
d23 <- length(Reduce(intersect, list(CHS.lfmm.outliers, CHS.VS.lfmm.outliers)))

d123 <- length(Reduce(intersect, list(CHS.TI.lfmm.outliers, CHS.lfmm.outliers,CHS.VS.lfmm.outliers)))


pdf("Venn.CHS.andVS.TI.onlylfmm.pdf")
draw.triple.venn(area1=d1, area2=d2, area3=d3, n12=d12, n13=d13, n23=d23, n123=d123, category=c("CHS.TI", "CHS", "CHS.VS"), lty="blank", fill=c("yellow", "orange", "skyblue1"))
dev.off()


```



### 5. Overlap between duplicated candidate loci identified for CHall, CHN, CHS, CZ

/Users/alexjvr/2016RADAnalysis/3_CH.landscapeGenomics/subsets/Venn/CHP2

First I need to find only the loci that occur more than once in each dataset. 

##### CHall
```
###I still need the LFMM results for this
```

##### CHN
```
CHN.bayenv.outliers <- read.table("CHN/CHN.bayenv.alloutliers", header=F)
colnames(CHN.bayenv.outliers) <- "loci"
CHN.bayenv.outliers <- as.character(CHN.bayenv.outliers$loci)
CHN.bayenv.outliers <- CHN.bayenv.outliers[-c(3)]
CHN.bayenv.outliers <- as.data.frame(CHN.bayenv.outliers)
colnames(CHN.bayenv.outliers) <- "loci"


CHN.lfmm.outliers <- read.table("CHN/CHN.LFMM.alloutliers", header=F)
colnames(CHN.lfmm.outliers) <- "loci"
CHN.lfmm.outliers <- as.character(CHN.lfmm.outliers$loci)
CHN.lfmm.outliers <- as.data.frame(CHN.lfmm.outliers)
colnames(CHN.lfmm.outliers)  <- "loci"


CHN.pcadapt.outliers <- read.table("CHN/CHN.pcadapt.outliers", header=F)
colnames(CHN.pcadapt.outliers) <- "loci"
CHN.pcadapt.outliers <- as.character(CHN.pcadapt.outliers$loci)
CHN.pcadapt.outliers <- as.data.frame(CHN.pcadapt.outliers)
colnames(CHN.pcadapt.outliers)  <- "loci"


CHN.XtX.outliers <- read.table("CHN/CHN.XtX.100outliers", header=F)
colnames(CHN.XtX.outliers) <- "loci"
CHN.XtX.outliers <- as.character(CHN.XtX.outliers$loci)
CHN.XtX.outliers <- as.data.frame(CHN.XtX.outliers)
colnames(CHN.XtX.outliers)  <- "loci"


CHN.alloutliers <- rbind(CHN.lfmm.outliers, CHN.bayenv.outliers, CHN.pcadapt.outliers, CHN.XtX.outliers)  ##Join all data.frames by "name" column. This only works of colnames are the same (at least one column name)

CHN.duplicated.outliers <- CHN.alloutliers[duplicated(CHN.alloutliers),]  ##select only loci occurring more than once (here 26)

write.table(CHN.duplicated.outliers, "CHN.duplicated.outliers", col.names=F, row.names=F, quote=F)
```

#### CHS
```

CHS.bayenv.outliers <- read.table("CHS/CHS.bayenv.alloutliers", header=F)
colnames(CHS.bayenv.outliers) <- "loci"
CHS.bayenv.outliers <- as.character(CHS.bayenv.outliers$loci)
CHS.bayenv.outliers <- as.data.frame(CHS.bayenv.outliers)
colnames(CHS.bayenv.outliers) <- "loci"


CHS.lfmm.outliers <- read.table("CHS/CHS.LFMM.alloutliers", header=F)
colnames(CHS.lfmm.outliers) <- "loci"
CHS.lfmm.outliers <- as.character(CHS.lfmm.outliers$loci)
CHS.lfmm.outliers <- as.data.frame(CHS.lfmm.outliers)
colnames(CHS.lfmm.outliers)  <- "loci"


CHS.pcadapt.outliers <- read.table("CHS/CHS.pcadapt.outliers", header=F)
colnames(CHS.pcadapt.outliers) <- "loci"
CHS.pcadapt.outliers <- as.character(CHS.pcadapt.outliers$loci)
CHS.pcadapt.outliers <- as.data.frame(CHS.pcadapt.outliers)
colnames(CHS.pcadapt.outliers)  <- "loci"


CHS.XtX.outliers <- read.table("CHS/CHS.XtX.100outliers", header=F)
colnames(CHS.XtX.outliers) <- "loci"
CHS.XtX.outliers <- as.character(CHS.XtX.outliers$loci)
CHS.XtX.outliers <- as.data.frame(CHS.XtX.outliers)
colnames(CHS.XtX.outliers)  <- "loci"


CHS.alloutliers <- rbind(CHS.lfmm.outliers, CHS.bayenv.outliers, CHS.pcadapt.outliers, CHS.XtX.outliers)  ##Join all data.frames by "name" column. This only works of colnames are the same (at least one column name)

CHS.duplicated.outliers <- CHS.alloutliers[duplicated(CHS.alloutliers),]  ##select only loci occurring more than once (here 26)

write.table(CHS.duplicated.outliers, "CHS.duplicated.outliers", col.names=F, row.names=F, quote=F)
```

##### CZ

```
CZ.bayenv.outliers <- read.table("CZ/CZ.bayenv.alloutliers", header=F)
colnames(CZ.bayenv.outliers) <- "loci"
CZ.bayenv.outliers <- as.character(CZ.bayenv.outliers$loci)
CZ.bayenv.outliers <- as.data.frame(CZ.bayenv.outliers)
colnames(CZ.bayenv.outliers) <- "loci"


CZ.lfmm.outliers <- read.table("CZ/CZ.LFMM.alloutliers", header=F)
colnames(CZ.lfmm.outliers) <- "loci"
CZ.lfmm.outliers <- as.character(CZ.lfmm.outliers$loci)
CZ.lfmm.outliers <- as.data.frame(CZ.lfmm.outliers)
colnames(CZ.lfmm.outliers)  <- "loci"


CZ.pcadapt.outliers <- read.table("CZ/CZ.pcadapt.outliers", header=F)
colnames(CZ.pcadapt.outliers) <- "loci"
CZ.pcadapt.outliers <- as.character(CZ.pcadapt.outliers$loci)
CZ.pcadapt.outliers <- as.data.frame(CZ.pcadapt.outliers)
colnames(CZ.pcadapt.outliers)  <- "loci"


CZ.XtX.outliers <- read.table("CZ/CZ.XtX.100outliers", header=F)
colnames(CZ.XtX.outliers) <- "loci"
CZ.XtX.outliers <- as.character(CZ.XtX.outliers$loci)
CZ.XtX.outliers <- as.data.frame(CZ.XtX.outliers)
colnames(CZ.XtX.outliers)  <- "loci"


CZ.alloutliers <- rbind(CZ.lfmm.outliers, CZ.bayenv.outliers, CZ.pcadapt.outliers, CZ.XtX.outliers)  ##Join all data.frames by "name" column. This only works of colnames are the same (at least one column name)

CZ.duplicated.outliers <- CZ.alloutliers[duplicated(CZ.alloutliers),]  ##select only loci occurring more than once (here 26)

write.table(CZ.duplicated.outliers, "CZ.duplicated.outliers", col.names=F, row.names=F, quote=F)
```


Then I can read them into R and draw the VennDiagrams

/Users/alexjvr/2016RADAnalysis/3_CH.landscapeGenomics/subsets/Venn/CHP2

First without CHall
```
library(VennDiagram)


CHN.duplicated.outliers <- read.table("CHN.duplicated.outliers", header=F)
colnames(CHN.duplicated.outliers) <- "loci"
CHN.duplicated.outliers <- as.character(CHN.duplicated.outliers$loci)

CZ.duplicated.outliers <- read.table("CZ.duplicated.outliers", header=F)
colnames(CZ.duplicated.outliers) <- "loci"
CZ.duplicated.outliers <- as.character(CZ.duplicated.outliers$loci)

CHS.duplicated.outliers <- read.table("CHS.duplicated.outliers", header=F)
colnames(CHS.duplicated.outliers) <- "loci"
CHS.duplicated.outliers <- as.character(CHS.duplicated.outliers$loci)


d1 <- length(CHN.duplicated.outliers)
d2 <- length(CHS.duplicated.outliers)
d3 <- length(CZ.duplicated.outliers)

d12 <- length(Reduce(intersect, list(CHN.duplicated.outliers, CHS.duplicated.outliers)))
d13 <- length(Reduce(intersect, list(CHN.duplicated.outliers, CZ.duplicated.outliers)))
d23 <- length(Reduce(intersect, list(CHS.duplicated.outliers, CZ.duplicated.outliers)))

d123 <- length(Reduce(intersect, list(CHN.duplicated.outliers, CHS.duplicated.outliers,CZ.duplicated.outliers)))


pdf("Venn.CHN.CHS.CZ.duplicated.outliers.pdf")
draw.triple.venn(area1=d1, area2=d2, area3=d3, n12=d12, n13=d13, n23=d23, n123=d123, category=c("CHN", "CHS", "CZ"), lty="blank", fill=c("yellow", "orange", "skyblue1"))
dev.off()

```








And with CHall
```
library(VennDiagram)

CHall.outliers <- read.table("CHall/CHall.alloutliers", header=F)
colnames(CHall.outliers) <- "loci"
CHall.outliers <- as.character(CHall.outliers$loci)

CHN.outliers <- read.table("CHN/CHN.alloutliers", header=F)
colnames(CHN.outliers) <- "loci"
CHN.outliers <- as.character(CHN.outliers$loci)

CHS.outliers <- read.table("CHS/CHS.alloutliers", header=F)
colnames(CHS.outliers) <- "loci"
CHS.outliers <- as.character(CHS.outliers$loci)

CZ.outliers <- read.table("CZ/CZ.alloutliers", header=F)
colnames(CZ.outliers) <- "loci"
CZ.outliers <- as.character(CZ.outliers$loci)


d1 <- length(CHall.outliers)
d2 <- length(CHN.outliers)
d3 <- length(CHS.outliers)
d4 <- length(CZ.outliers)

d12 <- length(Reduce(intersect, list(CHall.outliers, CHN.outliers)))
d13 <- length(Reduce(intersect, list(CHall.outliers, CHS.outliers)))
d14 <- length(Reduce(intersect, list(CHall.outliers, CZ.outliers)))
d23 <- length(Reduce(intersect, list(CHN.outliers, CHS.outliers)))
d24 <- length(Reduce(intersect, list(CHN.outliers, CZ.outliers)))
d34 <- length(Reduce(intersect, list(CHS.outliers, CZ.outliers)))

d123 <- length(Reduce(intersect, list(CHall.outliers, CHN.outliers,CHS.outliers)))
d124 <- length(Reduce(intersect, list(CHall.outliers, CHN.outliers,CZ.outliers)))
d234 <- length(Reduce(intersect, list(CHN.outliers, CHS.outliers,CZ.outliers)))
d134 <- length(Reduce(intersect, list(CHall.outliers, CHS.outliers,CZ.outliers)))

d1234 <- length(Reduce(intersect, list(CHall.outliers, CHN.outliers, CHS.outliers, CZ.outliers)))

#pdf(file="Venn.CHall.CHS.CHN.CZ.duplicated.outliers.pdf")
draw.quad.venn(area1=d1, area2=d2, area3=d3, area4=d4, n12=d12, n13=d13, n14=d14, n23=d23, n24=d24, n34=d34, n123=d123, n124=d124, n134=d134, n234=d234, n1234=d1234, category=c("lfmm", "bayenv", "XtX", "pcadapt"), lty="blank", fill=c("yellow", "orange", "skyblue1", "blue"))
#dev.off()

```



### 4. Overlap between all candidate loci identified for CHS, CHS.TI, CHS.VS

First I need to find the loci that occur more than once. CHS was already done in the previous batch. 

###### CHS.VS
```
CHS.VS.bayenv.outliers <- read.table("CHS.VS/CHS.VS.bayenv.alloutliers", header=F)
colnames(CHS.VS.bayenv.outliers) <- "loci"
CHS.VS.bayenv.outliers <- as.character(CHS.VS.bayenv.outliers$loci)
CHS.VS.bayenv.outliers <- as.data.frame(CHS.VS.bayenv.outliers)
colnames(CHS.VS.bayenv.outliers) <- "loci"


CHS.VS.lfmm.outliers <- read.table("CHS.VS/CHS.VS.LFMM.alloutliers", header=F)
colnames(CHS.VS.lfmm.outliers) <- "loci"
CHS.VS.lfmm.outliers <- as.character(CHS.VS.lfmm.outliers$loci)
CHS.VS.lfmm.outliers <- as.data.frame(CHS.VS.lfmm.outliers)
colnames(CHS.VS.lfmm.outliers)  <- "loci"


CHS.VS.pcadapt.outliers <- read.table("CHS.VS/CHS.VS.pcadapt.outliers", header=F)
colnames(CHS.VS.pcadapt.outliers) <- "loci"
CHS.VS.pcadapt.outliers <- as.character(CHS.VS.pcadapt.outliers$loci)
CHS.VS.pcadapt.outliers <- as.data.frame(CHS.VS.pcadapt.outliers)
colnames(CHS.VS.pcadapt.outliers)  <- "loci"


CHS.VS.XtX.outliers <- read.table("CHS.VS/CHS.VS.XtX.100outliers", header=F)
colnames(CHS.VS.XtX.outliers) <- "loci"
CHS.VS.XtX.outliers <- as.character(CHS.VS.XtX.outliers$loci)
CHS.VS.XtX.outliers <- as.data.frame(CHS.VS.XtX.outliers)
colnames(CHS.VS.XtX.outliers)  <- "loci"


CHS.VS.alloutliers <- rbind(CHS.VS.lfmm.outliers, CHS.VS.bayenv.outliers, CHS.VS.pcadapt.outliers, CHS.VS.XtX.outliers)  ##Join all data.frames by "name" column. This only works of colnames are the same (at least one column name)

CHS.VS.duplicated.outliers <- CHS.VS.alloutliers[duplicated(CHS.VS.alloutliers),]  ##select only loci occurring more than once (here 26)

write.table(CHS.VS.duplicated.outliers, "CHS.VS.duplicated.outliers", col.names=F, row.names=F, quote=F)
```

###### CHS.TI
```
CHS.TI.bayenv.outliers <- read.table("CHS.TI/CHS.TI.bayenv.alloutliers", header=F)
colnames(CHS.TI.bayenv.outliers) <- "loci"
CHS.TI.bayenv.outliers <- as.character(CHS.TI.bayenv.outliers$loci)
CHS.TI.bayenv.outliers <- as.data.frame(CHS.TI.bayenv.outliers)
colnames(CHS.TI.bayenv.outliers) <- "loci"


CHS.TI.lfmm.outliers <- read.table("CHS.TI/CHS.TI.LFMM.alloutliers", header=F)
colnames(CHS.TI.lfmm.outliers) <- "loci"
CHS.TI.lfmm.outliers <- as.character(CHS.TI.lfmm.outliers$loci)
CHS.TI.lfmm.outliers <- as.data.frame(CHS.TI.lfmm.outliers)
colnames(CHS.TI.lfmm.outliers)  <- "loci"


CHS.TI.pcadapt.outliers <- read.table("CHS.TI/CHS.TI.pcadapt.outliers", header=F)
colnames(CHS.TI.pcadapt.outliers) <- "loci"
CHS.TI.pcadapt.outliers <- as.character(CHS.TI.pcadapt.outliers$loci)
CHS.TI.pcadapt.outliers <- as.data.frame(CHS.TI.pcadapt.outliers)
colnames(CHS.TI.pcadapt.outliers)  <- "loci"


CHS.TI.XtX.outliers <- read.table("CHS.TI/CHS.TI.XtX.100outliers", header=F)
colnames(CHS.TI.XtX.outliers) <- "loci"
CHS.TI.XtX.outliers <- as.character(CHS.TI.XtX.outliers$loci)
CHS.TI.XtX.outliers <- as.data.frame(CHS.TI.XtX.outliers)
colnames(CHS.TI.XtX.outliers)  <- "loci"


CHS.TI.alloutliers <- rbind(CHS.TI.lfmm.outliers, CHS.TI.bayenv.outliers, CHS.TI.pcadapt.outliers, CHS.TI.XtX.outliers)  ##Join all data.frames by "name" column. This only works of colnames are the same (at least one column name)

CHS.TI.duplicated.outliers <- CHS.TI.alloutliers[duplicated(CHS.TI.alloutliers),]  ##select only loci occurring more than once (here 26)

write.table(CHS.TI.duplicated.outliers, "CHS.TI.duplicated.outliers", col.names=F, row.names=F, quote=F)
```

And then draw the Venn diagram

```
library(VennDiagram)


CHS.VS.duplicated.outliers <- read.table("CHS.VS.duplicated.outliers", header=F)
colnames(CHS.VS.duplicated.outliers) <- "loci"
CHS.VS.duplicated.outliers <- as.character(CHS.VS.duplicated.outliers$loci)

CHS.TI.duplicated.outliers <- read.table("CHS.TI.duplicated.outliers", header=F)
colnames(CHS.TI.duplicated.outliers) <- "loci"
CHS.TI.duplicated.outliers <- as.character(CHS.TI.duplicated.outliers$loci)

CHS.duplicated.outliers <- read.table("CHS.duplicated.outliers", header=F)
colnames(CHS.duplicated.outliers) <- "loci"
CHS.duplicated.outliers <- as.character(CHS.duplicated.outliers$loci)


d1 <- length(CHS.VS.duplicated.outliers)
d2 <- length(CHS.duplicated.outliers)
d3 <- length(CHS.TI.duplicated.outliers)

d12 <- length(Reduce(intersect, list(CHS.VS.duplicated.outliers, CHS.duplicated.outliers)))
d13 <- length(Reduce(intersect, list(CHS.VS.duplicated.outliers, CHS.TI.duplicated.outliers)))
d23 <- length(Reduce(intersect, list(CHS.duplicated.outliers, CHS.TI.duplicated.outliers)))

d123 <- length(Reduce(intersect, list(CHS.VS.duplicated.outliers, CHS.duplicated.outliers,CHS.TI.duplicated.outliers)))


pdf("Venn.CHS.withVS.TI.duplicated.outliers.pdf")
draw.triple.venn(area1=d1, area2=d2, area3=d3, n12=d12, n13=d13, n23=d23, n123=d123, category=c("CHS.VS", "CHS", "CHS.TI"), lty="blank", fill=c("yellow", "orange", "skyblue1"))
dev.off()

```


# 7: Overlap of BestLoci (GF) per variable

Shows the shared adaptive variation from the top loci identified using GF (i.e. BestLoci = contributes to 80% of R2 for that variable in that transect)

/Users/alexjvr/2016RADAnalysis/3_CH.landscapeGenomics/subsets/GradientForest/Oct2017


### sol.rad.60d
```
CZ.sol.rad.60d <- best.Adapt.CZ.sol.rad.60d$loci
CHS.sol.rad.60d <- best.Adapt.CHS.sol.rad.60d$loci
CHN.sol.rad.60d <- best.Adapt.CHN.sol.rad.60d$loci
CHS.TI.sol.rad.60d <- best.Adapt.CHS.TI.sol.rad.60d$loci
CHS.VS.sol.rad.60d <- best.Adapt.CHS.VS.sol.rad.60d$loci

d1 <- length(CZ.sol.rad.60d)
d2 <- length(CHS.sol.rad.60d)
d3 <- length(CHN.sol.rad.60d)
d4 <- length(CHS.TI.sol.rad.60d)
d5 <- length(CHS.VS.sol.rad.60d)


d12 <- length(Reduce(intersect, list(CZ.sol.rad.60d, CHS.sol.rad.60d)))
d13 <- length(Reduce(intersect, list(CZ.sol.rad.60d, CHN.sol.rad.60d)))
d14 <- length(Reduce(intersect, list(CZ.sol.rad.60d, CHS.TI.sol.rad.60d)))
d15 <- length(Reduce(intersect, list(CZ.sol.rad.60d, CHS.VS.sol.rad.60d)))
d23 <- length(Reduce(intersect, list(CHS.sol.rad.60d, CHN.sol.rad.60d)))
d24 <- length(Reduce(intersect, list(CHS.sol.rad.60d, CHS.TI.sol.rad.60d)))
d25 <- length(Reduce(intersect, list(CHS.sol.rad.60d, CHS.VS.sol.rad.60d)))
d34 <- length(Reduce(intersect, list(CHN.sol.rad.60d, CHS.TI.sol.rad.60d)))
d35 <- length(Reduce(intersect, list(CHN.sol.rad.60d, CHS.VS.sol.rad.60d)))
d45 <- length(Reduce(intersect, list(CHS.TI.sol.rad.60d, CHS.VS.sol.rad.60d)))

d123 <- length(Reduce(intersect, list(CZ.sol.rad.60d, CHS.sol.rad.60d,CHN.sol.rad.60d)))
d124 <- length(Reduce(intersect, list(CZ.sol.rad.60d, CHS.sol.rad.60d,CHS.TI.sol.rad.60d)))
d125 <- length(Reduce(intersect, list(CZ.sol.rad.60d, CHS.sol.rad.60d,CHS.VS.sol.rad.60d)))
d234 <- length(Reduce(intersect, list(CHS.sol.rad.60d, CHN.sol.rad.60d,CHS.TI.sol.rad.60d)))
d134 <- length(Reduce(intersect, list(CZ.sol.rad.60d, CHN.sol.rad.60d,CHS.TI.sol.rad.60d)))
d135 <- length(Reduce(intersect, list(CZ.sol.rad.60d, CHN.sol.rad.60d,CHS.VS.sol.rad.60d)))
d145 <- length(Reduce(intersect, list(CZ.sol.rad.60d, CHS.TI.sol.rad.60d,CHS.VS.sol.rad.60d)))
d235 <- length(Reduce(intersect, list(CHS.sol.rad.60d, CHN.sol.rad.60d,CHS.VS.sol.rad.60d)))
d245 <- length(Reduce(intersect, list(CHS.sol.rad.60d, CHS.TI.sol.rad.60d,CHS.VS.sol.rad.60d)))
d345 <- length(Reduce(intersect, list(CHN.sol.rad.60d, CHS.TI.sol.rad.60d,CHS.VS.sol.rad.60d)))


d1234 <- length(Reduce(intersect, list(CHS.sol.rad.60d, CHN.sol.rad.60d,
CHS.TI.sol.rad.60d, CZ.sol.rad.60d)))
d1235 <- length(Reduce(intersect, list(CHS.sol.rad.60d, CHN.sol.rad.60d,
CHS.VS.sol.rad.60d, CZ.sol.rad.60d)))

d2345 <- length(Reduce(intersect, list(CHS.sol.rad.60d, CHN.sol.rad.60d,
CHS.TI.sol.rad.60d, CHS.VS.sol.rad.60d)))
d1245 <- length(Reduce(intersect, list(CHS.sol.rad.60d, CZ.sol.rad.60d,
CHS.TI.sol.rad.60d, CHS.VS.sol.rad.60d)))
d1345 <- length(Reduce(intersect, list(CHN.sol.rad.60d, CZ.sol.rad.60d,
CHS.TI.sol.rad.60d, CHS.VS.sol.rad.60d)))
d12345 <- length(Reduce(intersect, list(CZ.sol.rad.60d, CHS.sol.rad.60d, CHN.sol.rad.60d, 
CHS.TI.sol.rad.60d, CHS.VS.sol.rad.60d)))

#library(VennDiagram)

pdf("Venn.bestLoci.sol.rad.60d.pdf")
draw.quintuple.venn(area1=d1, area2=d2, area3=d3, area4=d4, area5=d5,
n12=d12, n13=d13, n14=d14, n15=d15, n23=d23, n24=d24, n25=d25, n34=d34, n35=d35, n45=d45,
n123=d123, n124=d124, n125=d125, n134=d134, n135=d135, n145=d145, n234=d234, n235=d235, n245=d245, n345=d345,
n1234=d1234, n1235=d1235, n1245=d1245, n1345=d1345, n2345=d2345, n12345=d12345, 
category=c("CZ", "CHS", "CHN", "CHS.TI", "CHS.VS"),
lty="blank", 
fill=c("yellow", "orange", "skyblue1", "skyblue3", "blue")
)
dev.off()



```


### pcpt.60d
```
CZ.pcpt.60d <- best.Adapt.CZ.pcpt.60d$loci
CHS.pcpt.60d <- best.Adapt.CHS.pcpt.60d$loci
CHN.pcpt.60d <- best.Adapt.CHN.pcpt.60d$loci
CHS.TI.pcpt.60d <- best.Adapt.CHS.TI.pcpt.60d$loci
CHS.VS.pcpt.60d <- best.Adapt.CHS.VS.pcpt.60d$loci

d1 <- length(CZ.pcpt.60d)
d2 <- length(CHS.pcpt.60d)
d3 <- length(CHN.pcpt.60d)
d4 <- length(CHS.TI.pcpt.60d)
d5 <- length(CHS.VS.pcpt.60d)


d12 <- length(Reduce(intersect, list(CZ.pcpt.60d, CHS.pcpt.60d)))
d13 <- length(Reduce(intersect, list(CZ.pcpt.60d, CHN.pcpt.60d)))
d14 <- length(Reduce(intersect, list(CZ.pcpt.60d, CHS.TI.pcpt.60d)))
d15 <- length(Reduce(intersect, list(CZ.pcpt.60d, CHS.VS.pcpt.60d)))
d23 <- length(Reduce(intersect, list(CHS.pcpt.60d, CHN.pcpt.60d)))
d24 <- length(Reduce(intersect, list(CHS.pcpt.60d, CHS.TI.pcpt.60d)))
d25 <- length(Reduce(intersect, list(CHS.pcpt.60d, CHS.VS.pcpt.60d)))
d34 <- length(Reduce(intersect, list(CHN.pcpt.60d, CHS.TI.pcpt.60d)))
d35 <- length(Reduce(intersect, list(CHN.pcpt.60d, CHS.VS.pcpt.60d)))
d45 <- length(Reduce(intersect, list(CHS.TI.pcpt.60d, CHS.VS.pcpt.60d)))

d123 <- length(Reduce(intersect, list(CZ.pcpt.60d, CHS.pcpt.60d,CHN.pcpt.60d)))
d124 <- length(Reduce(intersect, list(CZ.pcpt.60d, CHS.pcpt.60d,CHS.TI.pcpt.60d)))
d125 <- length(Reduce(intersect, list(CZ.pcpt.60d, CHS.pcpt.60d,CHS.VS.pcpt.60d)))
d234 <- length(Reduce(intersect, list(CHS.pcpt.60d, CHN.pcpt.60d,CHS.TI.pcpt.60d)))
d134 <- length(Reduce(intersect, list(CZ.pcpt.60d, CHN.pcpt.60d,CHS.TI.pcpt.60d)))
d135 <- length(Reduce(intersect, list(CZ.pcpt.60d, CHN.pcpt.60d,CHS.VS.pcpt.60d)))
d145 <- length(Reduce(intersect, list(CZ.pcpt.60d, CHS.TI.pcpt.60d,CHS.VS.pcpt.60d)))
d235 <- length(Reduce(intersect, list(CHS.pcpt.60d, CHN.pcpt.60d,CHS.VS.pcpt.60d)))
d245 <- length(Reduce(intersect, list(CHS.pcpt.60d, CHS.TI.pcpt.60d,CHS.VS.pcpt.60d)))
d345 <- length(Reduce(intersect, list(CHN.pcpt.60d, CHS.TI.pcpt.60d,CHS.VS.pcpt.60d)))


d1234 <- length(Reduce(intersect, list(CHS.pcpt.60d, CHN.pcpt.60d,
CHS.TI.pcpt.60d, CZ.pcpt.60d)))
d1235 <- length(Reduce(intersect, list(CHS.pcpt.60d, CHN.pcpt.60d,
CHS.VS.pcpt.60d, CZ.pcpt.60d)))

d2345 <- length(Reduce(intersect, list(CHS.pcpt.60d, CHN.pcpt.60d,
CHS.TI.pcpt.60d, CHS.VS.pcpt.60d)))
d1245 <- length(Reduce(intersect, list(CHS.pcpt.60d, CZ.pcpt.60d,
CHS.TI.pcpt.60d, CHS.VS.pcpt.60d)))
d1345 <- length(Reduce(intersect, list(CHN.pcpt.60d, CZ.pcpt.60d,
CHS.TI.pcpt.60d, CHS.VS.pcpt.60d)))
d12345 <- length(Reduce(intersect, list(CZ.pcpt.60d, CHS.pcpt.60d, CHN.pcpt.60d, 
CHS.TI.pcpt.60d, CHS.VS.pcpt.60d)))

#library(VennDiagram)

pdf("Venn.bestLoci.pcpt.60d.pdf")
draw.quintuple.venn(area1=d1, area2=d2, area3=d3, area4=d4, area5=d5,
n12=d12, n13=d13, n14=d14, n15=d15, n23=d23, n24=d24, n25=d25, n34=d34, n35=d35, n45=d45,
n123=d123, n124=d124, n125=d125, n134=d134, n135=d135, n145=d145, n234=d234, n235=d235, n245=d245, n345=d345,
n1234=d1234, n1235=d1235, n1245=d1245, n1345=d1345, n2345=d2345, n12345=d12345, 
category=c("CZ", "CHS", "CHN", "CHS.TI", "CHS.VS"),
lty="blank", 
fill=c("yellow", "orange", "skyblue1", "skyblue3", "blue")
)
dev.off()



```


### shadow.days
```
CZ.shadow.days <- best.Adapt.CZ.shadow.days$loci
CHS.shadow.days <- best.Adapt.CHS.shadow.days$loci
CHN.shadow.days <- best.Adapt.CHN.shadow.days$loci
CHS.TI.shadow.days <- best.Adapt.CHS.TI.shadow.days$loci
CHS.VS.shadow.days <- NULL

d1 <- length(CZ.shadow.days)
d2 <- length(CHS.shadow.days)
d3 <- length(CHN.shadow.days)
d4 <- length(CHS.TI.shadow.days)
d5 <- length(CHS.VS.shadow.days)


d12 <- length(Reduce(intersect, list(CZ.shadow.days, CHS.shadow.days)))
d13 <- length(Reduce(intersect, list(CZ.shadow.days, CHN.shadow.days)))
d14 <- length(Reduce(intersect, list(CZ.shadow.days, CHS.TI.shadow.days)))
d15 <- length(Reduce(intersect, list(CZ.shadow.days, CHS.VS.shadow.days)))
d23 <- length(Reduce(intersect, list(CHS.shadow.days, CHN.shadow.days)))
d24 <- length(Reduce(intersect, list(CHS.shadow.days, CHS.TI.shadow.days)))
d25 <- length(Reduce(intersect, list(CHS.shadow.days, CHS.VS.shadow.days)))
d34 <- length(Reduce(intersect, list(CHN.shadow.days, CHS.TI.shadow.days)))
d35 <- length(Reduce(intersect, list(CHN.shadow.days, CHS.VS.shadow.days)))
d45 <- length(Reduce(intersect, list(CHS.TI.shadow.days, CHS.VS.shadow.days)))

d123 <- length(Reduce(intersect, list(CZ.shadow.days, CHS.shadow.days,CHN.shadow.days)))
d124 <- length(Reduce(intersect, list(CZ.shadow.days, CHS.shadow.days,CHS.TI.shadow.days)))
d125 <- length(Reduce(intersect, list(CZ.shadow.days, CHS.shadow.days,CHS.VS.shadow.days)))
d234 <- length(Reduce(intersect, list(CHS.shadow.days, CHN.shadow.days,CHS.TI.shadow.days)))
d134 <- length(Reduce(intersect, list(CZ.shadow.days, CHN.shadow.days,CHS.TI.shadow.days)))
d135 <- length(Reduce(intersect, list(CZ.shadow.days, CHN.shadow.days,CHS.VS.shadow.days)))
d145 <- length(Reduce(intersect, list(CZ.shadow.days, CHS.TI.shadow.days,CHS.VS.shadow.days)))
d235 <- length(Reduce(intersect, list(CHS.shadow.days, CHN.shadow.days,CHS.VS.shadow.days)))
d245 <- length(Reduce(intersect, list(CHS.shadow.days, CHS.TI.shadow.days,CHS.VS.shadow.days)))
d345 <- length(Reduce(intersect, list(CHN.shadow.days, CHS.TI.shadow.days,CHS.VS.shadow.days)))


d1234 <- length(Reduce(intersect, list(CHS.shadow.days, CHN.shadow.days,
CHS.TI.shadow.days, CZ.shadow.days)))
d1235 <- length(Reduce(intersect, list(CHS.shadow.days, CHN.shadow.days,
CHS.VS.shadow.days, CZ.shadow.days)))

d2345 <- length(Reduce(intersect, list(CHS.shadow.days, CHN.shadow.days,
CHS.TI.shadow.days, CHS.VS.shadow.days)))
d1245 <- length(Reduce(intersect, list(CHS.shadow.days, CZ.shadow.days,
CHS.TI.shadow.days, CHS.VS.shadow.days)))
d1345 <- length(Reduce(intersect, list(CHN.shadow.days, CZ.shadow.days,
CHS.TI.shadow.days, CHS.VS.shadow.days)))
d12345 <- length(Reduce(intersect, list(CZ.shadow.days, CHS.shadow.days, CHN.shadow.days, 
CHS.TI.shadow.days, CHS.VS.shadow.days)))

#library(VennDiagram)

pdf("Venn.bestLoci.shadow.days.pdf")
draw.quintuple.venn(area1=d1, area2=d2, area3=d3, area4=d4, area5=d5,
n12=d12, n13=d13, n14=d14, n15=d15, n23=d23, n24=d24, n25=d25, n34=d34, n35=d35, n45=d45,
n123=d123, n124=d124, n125=d125, n134=d134, n135=d135, n145=d145, n234=d234, n235=d235, n245=d245, n345=d345,
n1234=d1234, n1235=d1235, n1245=d1245, n1345=d1345, n2345=d2345, n12345=d12345, 
category=c("CZ", "CHS", "CHN", "CHS.TI", "CHS.VS"),
lty="blank", 
fill=c("yellow", "orange", "skyblue1", "skyblue3", "blue")
)
dev.off()



```


### day10cm
```
CZ.day10cm <- best.Adapt.CZ.day10cm$loci
CHS.day10cm <- best.Adapt.CHS.day10cm$loci
CHN.day10cm <- best.Adapt.CHN.day10cm$loci
CHS.TI.day10cm <- best.Adapt.CHS.TI.day10cm$loci
CHS.VS.day10cm <- best.Adapt.CHS.VS.day10cm$loci

d1 <- length(CZ.day10cm)
d2 <- length(CHS.day10cm)
d3 <- length(CHN.day10cm)
d4 <- length(CHS.TI.day10cm)
d5 <- length(CHS.VS.day10cm)


d12 <- length(Reduce(intersect, list(CZ.day10cm, CHS.day10cm)))
d13 <- length(Reduce(intersect, list(CZ.day10cm, CHN.day10cm)))
d14 <- length(Reduce(intersect, list(CZ.day10cm, CHS.TI.day10cm)))
d15 <- length(Reduce(intersect, list(CZ.day10cm, CHS.VS.day10cm)))
d23 <- length(Reduce(intersect, list(CHS.day10cm, CHN.day10cm)))
d24 <- length(Reduce(intersect, list(CHS.day10cm, CHS.TI.day10cm)))
d25 <- length(Reduce(intersect, list(CHS.day10cm, CHS.VS.day10cm)))
d34 <- length(Reduce(intersect, list(CHN.day10cm, CHS.TI.day10cm)))
d35 <- length(Reduce(intersect, list(CHN.day10cm, CHS.VS.day10cm)))
d45 <- length(Reduce(intersect, list(CHS.TI.day10cm, CHS.VS.day10cm)))

d123 <- length(Reduce(intersect, list(CZ.day10cm, CHS.day10cm,CHN.day10cm)))
d124 <- length(Reduce(intersect, list(CZ.day10cm, CHS.day10cm,CHS.TI.day10cm)))
d125 <- length(Reduce(intersect, list(CZ.day10cm, CHS.day10cm,CHS.VS.day10cm)))
d234 <- length(Reduce(intersect, list(CHS.day10cm, CHN.day10cm,CHS.TI.day10cm)))
d134 <- length(Reduce(intersect, list(CZ.day10cm, CHN.day10cm,CHS.TI.day10cm)))
d135 <- length(Reduce(intersect, list(CZ.day10cm, CHN.day10cm,CHS.VS.day10cm)))
d145 <- length(Reduce(intersect, list(CZ.day10cm, CHS.TI.day10cm,CHS.VS.day10cm)))
d235 <- length(Reduce(intersect, list(CHS.day10cm, CHN.day10cm,CHS.VS.day10cm)))
d245 <- length(Reduce(intersect, list(CHS.day10cm, CHS.TI.day10cm,CHS.VS.day10cm)))
d345 <- length(Reduce(intersect, list(CHN.day10cm, CHS.TI.day10cm,CHS.VS.day10cm)))


d1234 <- length(Reduce(intersect, list(CHS.day10cm, CHN.day10cm,
CHS.TI.day10cm, CZ.day10cm)))
d1235 <- length(Reduce(intersect, list(CHS.day10cm, CHN.day10cm,
CHS.VS.day10cm, CZ.day10cm)))

d2345 <- length(Reduce(intersect, list(CHS.day10cm, CHN.day10cm,
CHS.TI.day10cm, CHS.VS.day10cm)))
d1245 <- length(Reduce(intersect, list(CHS.day10cm, CZ.day10cm,
CHS.TI.day10cm, CHS.VS.day10cm)))
d1345 <- length(Reduce(intersect, list(CHN.day10cm, CZ.day10cm,
CHS.TI.day10cm, CHS.VS.day10cm)))
d12345 <- length(Reduce(intersect, list(CZ.day10cm, CHS.day10cm, CHN.day10cm, 
CHS.TI.day10cm, CHS.VS.day10cm)))

#library(VennDiagram)

pdf("Venn.bestLoci.day10cm.pdf")
draw.quintuple.venn(area1=d1, area2=d2, area3=d3, area4=d4, area5=d5,
n12=d12, n13=d13, n14=d14, n15=d15, n23=d23, n24=d24, n25=d25, n34=d34, n35=d35, n45=d45,
n123=d123, n124=d124, n125=d125, n134=d134, n135=d135, n145=d145, n234=d234, n235=d235, n245=d245, n345=d345,
n1234=d1234, n1235=d1235, n1245=d1245, n1345=d1345, n2345=d2345, n12345=d12345, 
category=c("CZ", "CHS", "CHN", "CHS.TI", "CHS.VS"),
lty="blank", 
fill=c("yellow", "orange", "skyblue1", "skyblue3", "blue")
)
dev.off()



```

# 8: Pleitropy in bestLoci per transect

BestLoci that were found to be associated with multiple environmental variables. 

### CHN.BestLoci

Count the number of loci used more than once (total-unique)
```
CHN.sol.rad.60d.BestLoci <- best.Adapt.CHN.sol.rad.60d$loci
CHN.temp.laying.date.BestLoci <- best.Adapt.CHN.temp.laying.date$loci
CHN.pcpt.60d.BestLoci <- best.Adapt.CHN.pcpt.60d$loci
CHN.shadow.days.BestLoci <- best.Adapt.CHN.shadow.days$loci
CHN.day10cm.BestLoci <- best.Adapt.CHN.day10cm$loci

length(c(CHN.sol.rad.60d.BestLoci, CHN.temp.laying.date.BestLoci, CHN.pcpt.60d.BestLoci, CHN.shadow.days.BestLoci, CHN.day10cm.BestLoci))

length(unique(c(CHN.sol.rad.60d.BestLoci, CHN.temp.laying.date.BestLoci, CHN.pcpt.60d.BestLoci, CHN.shadow.days.BestLoci, CHN.day10cm.BestLoci)))
```


then plot
```
d1 <- length(CHN.sol.rad.60d.BestLoci)
d2 <- length(CHN.temp.laying.date.BestLoci)
d3 <- length(CHN.pcpt.60d.BestLoci)
d4 <- length(CHN.shadow.days.BestLoci)
d5 <- length(CHN.day10cm.BestLoci)


d12 <- length(Reduce(intersect, list(CHN.sol.rad.60d.BestLoci, CHN.temp.laying.date.BestLoci)))
d13 <- length(Reduce(intersect, list(CHN.sol.rad.60d.BestLoci, CHN.pcpt.60d.BestLoci)))
d14 <- length(Reduce(intersect, list(CHN.sol.rad.60d.BestLoci, CHN.shadow.days.BestLoci)))
d15 <- length(Reduce(intersect, list(CHN.sol.rad.60d.BestLoci, CHN.day10cm.BestLoci)))
d23 <- length(Reduce(intersect, list(CHN.temp.laying.date.BestLoci, CHN.pcpt.60d.BestLoci)))
d24 <- length(Reduce(intersect, list(CHN.temp.laying.date.BestLoci, CHN.shadow.days.BestLoci)))
d25 <- length(Reduce(intersect, list(CHN.temp.laying.date.BestLoci, CHN.day10cm.BestLoci)))
d34 <- length(Reduce(intersect, list(CHN.pcpt.60d.BestLoci, CHN.shadow.days.BestLoci)))
d35 <- length(Reduce(intersect, list(CHN.pcpt.60d.BestLoci, CHN.day10cm.BestLoci)))
d45 <- length(Reduce(intersect, list(CHN.shadow.days.BestLoci, CHN.day10cm.BestLoci)))

d123 <- length(Reduce(intersect, list(CHN.sol.rad.60d.BestLoci, CHN.temp.laying.date.BestLoci,CHN.pcpt.60d.BestLoci)))
d124 <- length(Reduce(intersect, list(CHN.sol.rad.60d.BestLoci, CHN.temp.laying.date.BestLoci,CHN.shadow.days.BestLoci)))
d125 <- length(Reduce(intersect, list(CHN.sol.rad.60d.BestLoci, CHN.temp.laying.date.BestLoci,CHN.day10cm.BestLoci)))
d234 <- length(Reduce(intersect, list(CHN.temp.laying.date.BestLoci, CHN.pcpt.60d.BestLoci,CHN.shadow.days.BestLoci)))
d134 <- length(Reduce(intersect, list(CHN.sol.rad.60d.BestLoci, CHN.pcpt.60d.BestLoci,CHN.shadow.days.BestLoci)))
d135 <- length(Reduce(intersect, list(CHN.sol.rad.60d.BestLoci, CHN.pcpt.60d.BestLoci,CHN.day10cm.BestLoci)))
d145 <- length(Reduce(intersect, list(CHN.sol.rad.60d.BestLoci, CHN.shadow.days.BestLoci,CHN.day10cm.BestLoci)))
d235 <- length(Reduce(intersect, list(CHN.temp.laying.date.BestLoci, CHN.pcpt.60d.BestLoci,CHN.day10cm.BestLoci)))
d245 <- length(Reduce(intersect, list(CHN.temp.laying.date.BestLoci, CHN.shadow.days.BestLoci,CHN.day10cm.BestLoci)))
d345 <- length(Reduce(intersect, list(CHN.pcpt.60d.BestLoci, CHN.shadow.days.BestLoci,CHN.day10cm.BestLoci)))


d1234 <- length(Reduce(intersect, list(CHN.temp.laying.date.BestLoci, CHN.pcpt.60d.BestLoci,
CHN.shadow.days.BestLoci, CHN.sol.rad.60d.BestLoci)))
d1235 <- length(Reduce(intersect, list(CHN.temp.laying.date.BestLoci, CHN.pcpt.60d.BestLoci,
CHN.day10cm.BestLoci, CHN.sol.rad.60d.BestLoci)))

d2345 <- length(Reduce(intersect, list(CHN.temp.laying.date.BestLoci, CHN.pcpt.60d.BestLoci,
CHN.shadow.days.BestLoci, CHN.day10cm.BestLoci)))
d1245 <- length(Reduce(intersect, list(CHN.temp.laying.date.BestLoci, CHN.sol.rad.60d.BestLoci,
CHN.shadow.days.BestLoci, CHN.day10cm.BestLoci)))
d1345 <- length(Reduce(intersect, list(CHN.pcpt.60d.BestLoci, CHN.sol.rad.60d.BestLoci,
CHN.shadow.days.BestLoci, CHN.day10cm.BestLoci)))
d12345 <- length(Reduce(intersect, list(CHN.sol.rad.60d.BestLoci, CHN.temp.laying.date.BestLoci, CHN.pcpt.60d.BestLoci, 
CHN.shadow.days.BestLoci, CHN.day10cm.BestLoci)))

#library(VennDiagram)

pdf("Venn.bestLoci.CHN.pdf")
draw.quintuple.venn(area1=d1, area2=d2, area3=d3, area4=d4, area5=d5,
n12=d12, n13=d13, n14=d14, n15=d15, n23=d23, n24=d24, n25=d25, n34=d34, n35=d35, n45=d45,
n123=d123, n124=d124, n125=d125, n134=d134, n135=d135, n145=d145, n234=d234, n235=d235, n245=d245, n345=d345,
n1234=d1234, n1235=d1235, n1245=d1245, n1345=d1345, n2345=d2345, n12345=d12345, 
category=c("sol.rad.60d", "temp.laying.date", "pcpt.60d", "shadow.days", "day10cm"),
lty="blank", 
fill=c("yellow", "orange", "skyblue1", "skyblue3", "blue")
)
dev.off()
```


### CHS.BestLoci

Count the number of loci used more than once (total-unique)
```
CHS.sol.rad.60d.BestLoci <- best.Adapt.CHS.sol.rad.60d$loci
CHS.temp.laying.date.BestLoci <- best.Adapt.CHS.temp.laying.date$loci
CHS.pcpt.60d.BestLoci <- best.Adapt.CHS.pcpt.60d$loci
CHS.shadow.days.BestLoci <- best.Adapt.CHS.shadow.days$loci
CHS.day10cm.BestLoci <- best.Adapt.CHS.day10cm$loci


length(c(CHS.sol.rad.60d.BestLoci, CHS.temp.laying.date.BestLoci, CHS.pcpt.60d.BestLoci, CHS.shadow.days.BestLoci, CHS.day10cm.BestLoci))

length(unique(c(CHS.sol.rad.60d.BestLoci, CHS.temp.laying.date.BestLoci, CHS.pcpt.60d.BestLoci, CHS.shadow.days.BestLoci, CHS.day10cm.BestLoci)))
```


then plot
```
d1 <- length(CHS.sol.rad.60d.BestLoci)
d2 <- length(CHS.temp.laying.date.BestLoci)
d3 <- length(CHS.pcpt.60d.BestLoci)
d4 <- length(CHS.shadow.days.BestLoci)
d5 <- length(CHS.day10cm.BestLoci)


d12 <- length(Reduce(intersect, list(CHS.sol.rad.60d.BestLoci, CHS.temp.laying.date.BestLoci)))
d13 <- length(Reduce(intersect, list(CHS.sol.rad.60d.BestLoci, CHS.pcpt.60d.BestLoci)))
d14 <- length(Reduce(intersect, list(CHS.sol.rad.60d.BestLoci, CHS.shadow.days.BestLoci)))
d15 <- length(Reduce(intersect, list(CHS.sol.rad.60d.BestLoci, CHS.day10cm.BestLoci)))
d23 <- length(Reduce(intersect, list(CHS.temp.laying.date.BestLoci, CHS.pcpt.60d.BestLoci)))
d24 <- length(Reduce(intersect, list(CHS.temp.laying.date.BestLoci, CHS.shadow.days.BestLoci)))
d25 <- length(Reduce(intersect, list(CHS.temp.laying.date.BestLoci, CHS.day10cm.BestLoci)))
d34 <- length(Reduce(intersect, list(CHS.pcpt.60d.BestLoci, CHS.shadow.days.BestLoci)))
d35 <- length(Reduce(intersect, list(CHS.pcpt.60d.BestLoci, CHS.day10cm.BestLoci)))
d45 <- length(Reduce(intersect, list(CHS.shadow.days.BestLoci, CHS.day10cm.BestLoci)))

d123 <- length(Reduce(intersect, list(CHS.sol.rad.60d.BestLoci, CHS.temp.laying.date.BestLoci,CHS.pcpt.60d.BestLoci)))
d124 <- length(Reduce(intersect, list(CHS.sol.rad.60d.BestLoci, CHS.temp.laying.date.BestLoci,CHS.shadow.days.BestLoci)))
d125 <- length(Reduce(intersect, list(CHS.sol.rad.60d.BestLoci, CHS.temp.laying.date.BestLoci,CHS.day10cm.BestLoci)))
d234 <- length(Reduce(intersect, list(CHS.temp.laying.date.BestLoci, CHS.pcpt.60d.BestLoci,CHS.shadow.days.BestLoci)))
d134 <- length(Reduce(intersect, list(CHS.sol.rad.60d.BestLoci, CHS.pcpt.60d.BestLoci,CHS.shadow.days.BestLoci)))
d135 <- length(Reduce(intersect, list(CHS.sol.rad.60d.BestLoci, CHS.pcpt.60d.BestLoci,CHS.day10cm.BestLoci)))
d145 <- length(Reduce(intersect, list(CHS.sol.rad.60d.BestLoci, CHS.shadow.days.BestLoci,CHS.day10cm.BestLoci)))
d235 <- length(Reduce(intersect, list(CHS.temp.laying.date.BestLoci, CHS.pcpt.60d.BestLoci,CHS.day10cm.BestLoci)))
d245 <- length(Reduce(intersect, list(CHS.temp.laying.date.BestLoci, CHS.shadow.days.BestLoci,CHS.day10cm.BestLoci)))
d345 <- length(Reduce(intersect, list(CHS.pcpt.60d.BestLoci, CHS.shadow.days.BestLoci,CHS.day10cm.BestLoci)))


d1234 <- length(Reduce(intersect, list(CHS.temp.laying.date.BestLoci, CHS.pcpt.60d.BestLoci,
CHS.shadow.days.BestLoci, CHS.sol.rad.60d.BestLoci)))
d1235 <- length(Reduce(intersect, list(CHS.temp.laying.date.BestLoci, CHS.pcpt.60d.BestLoci,
CHS.day10cm.BestLoci, CHS.sol.rad.60d.BestLoci)))

d2345 <- length(Reduce(intersect, list(CHS.temp.laying.date.BestLoci, CHS.pcpt.60d.BestLoci,
CHS.shadow.days.BestLoci, CHS.day10cm.BestLoci)))
d1245 <- length(Reduce(intersect, list(CHS.temp.laying.date.BestLoci, CHS.sol.rad.60d.BestLoci,
CHS.shadow.days.BestLoci, CHS.day10cm.BestLoci)))
d1345 <- length(Reduce(intersect, list(CHS.pcpt.60d.BestLoci, CHS.sol.rad.60d.BestLoci,
CHS.shadow.days.BestLoci, CHS.day10cm.BestLoci)))
d12345 <- length(Reduce(intersect, list(CHS.sol.rad.60d.BestLoci, CHS.temp.laying.date.BestLoci, CHS.pcpt.60d.BestLoci, 
CHS.shadow.days.BestLoci, CHS.day10cm.BestLoci)))

#library(VennDiagram)

pdf("Venn.bestLoci.CHS.pdf")
draw.quintuple.venn(area1=d1, area2=d2, area3=d3, area4=d4, area5=d5,
n12=d12, n13=d13, n14=d14, n15=d15, n23=d23, n24=d24, n25=d25, n34=d34, n35=d35, n45=d45,
n123=d123, n124=d124, n125=d125, n134=d134, n135=d135, n145=d145, n234=d234, n235=d235, n245=d245, n345=d345,
n1234=d1234, n1235=d1235, n1245=d1245, n1345=d1345, n2345=d2345, n12345=d12345, 
category=c("sol.rad.60d", "temp.laying.date", "pcpt.60d", "shadow.days", "day10cm"),
lty="blank", 
fill=c("yellow", "orange", "skyblue1", "skyblue3", "blue")
)
dev.off()



```



### CZ.BestLoci

Count the number of loci used more than once (total-unique)
```
CZ.sol.rad.60d.BestLoci <- best.Adapt.CZ.sol.rad.60d$loci
CZ.temp.laying.date.BestLoci <- best.Adapt.CZ.temp.laying.date$loci
CZ.pcpt.60d.BestLoci <- best.Adapt.CZ.pcpt.60d$loci
CZ.shadow.days.BestLoci <- best.Adapt.CZ.shadow.days$loci
CZ.day10cm.BestLoci <- best.Adapt.CZ.day10cm$loci


length(c(CZ.sol.rad.60d.BestLoci, CZ.temp.laying.date.BestLoci, CZ.pcpt.60d.BestLoci, CZ.shadow.days.BestLoci, CZ.day10cm.BestLoci))

length(unique(c(CZ.sol.rad.60d.BestLoci, CZ.temp.laying.date.BestLoci, CZ.pcpt.60d.BestLoci, CZ.shadow.days.BestLoci, CZ.day10cm.BestLoci)))
```


then plot
```
d1 <- length(CZ.sol.rad.60d.BestLoci)
d2 <- length(CZ.temp.laying.date.BestLoci)
d3 <- length(CZ.pcpt.60d.BestLoci)
d4 <- length(CZ.shadow.days.BestLoci)
d5 <- length(CZ.day10cm.BestLoci)


d12 <- length(Reduce(intersect, list(CZ.sol.rad.60d.BestLoci, CZ.temp.laying.date.BestLoci)))
d13 <- length(Reduce(intersect, list(CZ.sol.rad.60d.BestLoci, CZ.pcpt.60d.BestLoci)))
d14 <- length(Reduce(intersect, list(CZ.sol.rad.60d.BestLoci, CZ.shadow.days.BestLoci)))
d15 <- length(Reduce(intersect, list(CZ.sol.rad.60d.BestLoci, CZ.day10cm.BestLoci)))
d23 <- length(Reduce(intersect, list(CZ.temp.laying.date.BestLoci, CZ.pcpt.60d.BestLoci)))
d24 <- length(Reduce(intersect, list(CZ.temp.laying.date.BestLoci, CZ.shadow.days.BestLoci)))
d25 <- length(Reduce(intersect, list(CZ.temp.laying.date.BestLoci, CZ.day10cm.BestLoci)))
d34 <- length(Reduce(intersect, list(CZ.pcpt.60d.BestLoci, CZ.shadow.days.BestLoci)))
d35 <- length(Reduce(intersect, list(CZ.pcpt.60d.BestLoci, CZ.day10cm.BestLoci)))
d45 <- length(Reduce(intersect, list(CZ.shadow.days.BestLoci, CZ.day10cm.BestLoci)))

d123 <- length(Reduce(intersect, list(CZ.sol.rad.60d.BestLoci, CZ.temp.laying.date.BestLoci,CZ.pcpt.60d.BestLoci)))
d124 <- length(Reduce(intersect, list(CZ.sol.rad.60d.BestLoci, CZ.temp.laying.date.BestLoci,CZ.shadow.days.BestLoci)))
d125 <- length(Reduce(intersect, list(CZ.sol.rad.60d.BestLoci, CZ.temp.laying.date.BestLoci,CZ.day10cm.BestLoci)))
d234 <- length(Reduce(intersect, list(CZ.temp.laying.date.BestLoci, CZ.pcpt.60d.BestLoci,CZ.shadow.days.BestLoci)))
d134 <- length(Reduce(intersect, list(CZ.sol.rad.60d.BestLoci, CZ.pcpt.60d.BestLoci,CZ.shadow.days.BestLoci)))
d135 <- length(Reduce(intersect, list(CZ.sol.rad.60d.BestLoci, CZ.pcpt.60d.BestLoci,CZ.day10cm.BestLoci)))
d145 <- length(Reduce(intersect, list(CZ.sol.rad.60d.BestLoci, CZ.shadow.days.BestLoci,CZ.day10cm.BestLoci)))
d235 <- length(Reduce(intersect, list(CZ.temp.laying.date.BestLoci, CZ.pcpt.60d.BestLoci,CZ.day10cm.BestLoci)))
d245 <- length(Reduce(intersect, list(CZ.temp.laying.date.BestLoci, CZ.shadow.days.BestLoci,CZ.day10cm.BestLoci)))
d345 <- length(Reduce(intersect, list(CZ.pcpt.60d.BestLoci, CZ.shadow.days.BestLoci,CZ.day10cm.BestLoci)))


d1234 <- length(Reduce(intersect, list(CZ.temp.laying.date.BestLoci, CZ.pcpt.60d.BestLoci,
CZ.shadow.days.BestLoci, CZ.sol.rad.60d.BestLoci)))
d1235 <- length(Reduce(intersect, list(CZ.temp.laying.date.BestLoci, CZ.pcpt.60d.BestLoci,
CZ.day10cm.BestLoci, CZ.sol.rad.60d.BestLoci)))

d2345 <- length(Reduce(intersect, list(CZ.temp.laying.date.BestLoci, CZ.pcpt.60d.BestLoci,
CZ.shadow.days.BestLoci, CZ.day10cm.BestLoci)))
d1245 <- length(Reduce(intersect, list(CZ.temp.laying.date.BestLoci, CZ.sol.rad.60d.BestLoci,
CZ.shadow.days.BestLoci, CZ.day10cm.BestLoci)))
d1345 <- length(Reduce(intersect, list(CZ.pcpt.60d.BestLoci, CZ.sol.rad.60d.BestLoci,
CZ.shadow.days.BestLoci, CZ.day10cm.BestLoci)))
d12345 <- length(Reduce(intersect, list(CZ.sol.rad.60d.BestLoci, CZ.temp.laying.date.BestLoci, CZ.pcpt.60d.BestLoci, 
CZ.shadow.days.BestLoci, CZ.day10cm.BestLoci)))

#library(VennDiagram)

pdf("Venn.bestLoci.CZ.pdf")
draw.quintuple.venn(area1=d1, area2=d2, area3=d3, area4=d4, area5=d5,
n12=d12, n13=d13, n14=d14, n15=d15, n23=d23, n24=d24, n25=d25, n34=d34, n35=d35, n45=d45,
n123=d123, n124=d124, n125=d125, n134=d134, n135=d135, n145=d145, n234=d234, n235=d235, n245=d245, n345=d345,
n1234=d1234, n1235=d1235, n1245=d1245, n1345=d1345, n2345=d2345, n12345=d12345, 
category=c("sol.rad.60d", "temp.laying.date", "pcpt.60d", "shadow.days", "day10cm"),
lty="blank", 
fill=c("yellow", "orange", "skyblue1", "skyblue3", "blue")
)
dev.off()



```

### CHS.TI.BestLoci

Count the number of loci used more than once (total-unique)
```
CHS.TI.sol.rad.60d.BestLoci <- best.Adapt.CHS.TI.sol.rad.60d$loci
CHS.TI.temp.laying.date.BestLoci <- best.Adapt.CHS.TI.temp.laying.date$loci
CHS.TI.pcpt.60d.BestLoci <- best.Adapt.CHS.TI.pcpt.60d$loci
CHS.TI.shadow.days.BestLoci <- best.Adapt.CHS.TI.shadow.days$loci
CHS.TI.day10cm.BestLoci <- best.Adapt.CHS.TI.day10cm$loci


length(c(CHS.TI.sol.rad.60d.BestLoci, CHS.TI.temp.laying.date.BestLoci, CHS.TI.pcpt.60d.BestLoci, CHS.TI.shadow.days.BestLoci, CHS.TI.day10cm.BestLoci))

length(unique(c(CHS.TI.sol.rad.60d.BestLoci, CHS.TI.temp.laying.date.BestLoci, CHS.TI.pcpt.60d.BestLoci, CHS.TI.shadow.days.BestLoci, CHS.TI.day10cm.BestLoci)))
```


then plot
```
d1 <- length(CHS.TI.sol.rad.60d.BestLoci)
d2 <- length(CHS.TI.temp.laying.date.BestLoci)
d3 <- length(CHS.TI.pcpt.60d.BestLoci)
d4 <- length(CHS.TI.shadow.days.BestLoci)
d5 <- length(CHS.TI.day10cm.BestLoci)


d12 <- length(Reduce(intersect, list(CHS.TI.sol.rad.60d.BestLoci, CHS.TI.temp.laying.date.BestLoci)))
d13 <- length(Reduce(intersect, list(CHS.TI.sol.rad.60d.BestLoci, CHS.TI.pcpt.60d.BestLoci)))
d14 <- length(Reduce(intersect, list(CHS.TI.sol.rad.60d.BestLoci, CHS.TI.shadow.days.BestLoci)))
d15 <- length(Reduce(intersect, list(CHS.TI.sol.rad.60d.BestLoci, CHS.TI.day10cm.BestLoci)))
d23 <- length(Reduce(intersect, list(CHS.TI.temp.laying.date.BestLoci, CHS.TI.pcpt.60d.BestLoci)))
d24 <- length(Reduce(intersect, list(CHS.TI.temp.laying.date.BestLoci, CHS.TI.shadow.days.BestLoci)))
d25 <- length(Reduce(intersect, list(CHS.TI.temp.laying.date.BestLoci, CHS.TI.day10cm.BestLoci)))
d34 <- length(Reduce(intersect, list(CHS.TI.pcpt.60d.BestLoci, CHS.TI.shadow.days.BestLoci)))
d35 <- length(Reduce(intersect, list(CHS.TI.pcpt.60d.BestLoci, CHS.TI.day10cm.BestLoci)))
d45 <- length(Reduce(intersect, list(CHS.TI.shadow.days.BestLoci, CHS.TI.day10cm.BestLoci)))

d123 <- length(Reduce(intersect, list(CHS.TI.sol.rad.60d.BestLoci, CHS.TI.temp.laying.date.BestLoci,CHS.TI.pcpt.60d.BestLoci)))
d124 <- length(Reduce(intersect, list(CHS.TI.sol.rad.60d.BestLoci, CHS.TI.temp.laying.date.BestLoci,CHS.TI.shadow.days.BestLoci)))
d125 <- length(Reduce(intersect, list(CHS.TI.sol.rad.60d.BestLoci, CHS.TI.temp.laying.date.BestLoci,CHS.TI.day10cm.BestLoci)))
d234 <- length(Reduce(intersect, list(CHS.TI.temp.laying.date.BestLoci, CHS.TI.pcpt.60d.BestLoci,CHS.TI.shadow.days.BestLoci)))
d134 <- length(Reduce(intersect, list(CHS.TI.sol.rad.60d.BestLoci, CHS.TI.pcpt.60d.BestLoci,CHS.TI.shadow.days.BestLoci)))
d135 <- length(Reduce(intersect, list(CHS.TI.sol.rad.60d.BestLoci, CHS.TI.pcpt.60d.BestLoci,CHS.TI.day10cm.BestLoci)))
d145 <- length(Reduce(intersect, list(CHS.TI.sol.rad.60d.BestLoci, CHS.TI.shadow.days.BestLoci,CHS.TI.day10cm.BestLoci)))
d235 <- length(Reduce(intersect, list(CHS.TI.temp.laying.date.BestLoci, CHS.TI.pcpt.60d.BestLoci,CHS.TI.day10cm.BestLoci)))
d245 <- length(Reduce(intersect, list(CHS.TI.temp.laying.date.BestLoci, CHS.TI.shadow.days.BestLoci,CHS.TI.day10cm.BestLoci)))
d345 <- length(Reduce(intersect, list(CHS.TI.pcpt.60d.BestLoci, CHS.TI.shadow.days.BestLoci,CHS.TI.day10cm.BestLoci)))


d1234 <- length(Reduce(intersect, list(CHS.TI.temp.laying.date.BestLoci, CHS.TI.pcpt.60d.BestLoci,
CHS.TI.shadow.days.BestLoci, CHS.TI.sol.rad.60d.BestLoci)))
d1235 <- length(Reduce(intersect, list(CHS.TI.temp.laying.date.BestLoci, CHS.TI.pcpt.60d.BestLoci,
CHS.TI.day10cm.BestLoci, CHS.TI.sol.rad.60d.BestLoci)))

d2345 <- length(Reduce(intersect, list(CHS.TI.temp.laying.date.BestLoci, CHS.TI.pcpt.60d.BestLoci,
CHS.TI.shadow.days.BestLoci, CHS.TI.day10cm.BestLoci)))
d1245 <- length(Reduce(intersect, list(CHS.TI.temp.laying.date.BestLoci, CHS.TI.sol.rad.60d.BestLoci,
CHS.TI.shadow.days.BestLoci, CHS.TI.day10cm.BestLoci)))
d1345 <- length(Reduce(intersect, list(CHS.TI.pcpt.60d.BestLoci, CHS.TI.sol.rad.60d.BestLoci,
CHS.TI.shadow.days.BestLoci, CHS.TI.day10cm.BestLoci)))
d12345 <- length(Reduce(intersect, list(CHS.TI.sol.rad.60d.BestLoci, CHS.TI.temp.laying.date.BestLoci, CHS.TI.pcpt.60d.BestLoci, 
CHS.TI.shadow.days.BestLoci, CHS.TI.day10cm.BestLoci)))

#library(VennDiagram)

pdf("Venn.bestLoci.CHS.TI.pdf")
draw.quintuple.venn(area1=d1, area2=d2, area3=d3, area4=d4, area5=d5,
n12=d12, n13=d13, n14=d14, n15=d15, n23=d23, n24=d24, n25=d25, n34=d34, n35=d35, n45=d45,
n123=d123, n124=d124, n125=d125, n134=d134, n135=d135, n145=d145, n234=d234, n235=d235, n245=d245, n345=d345,
n1234=d1234, n1235=d1235, n1245=d1245, n1345=d1345, n2345=d2345, n12345=d12345, 
category=c("sol.rad.60d", "temp.laying.date", "pcpt.60d", "shadow.days", "day10cm"),
lty="blank", 
fill=c("yellow", "orange", "skyblue1", "skyblue3", "blue")
)
dev.off()



```

### CHS.VS.BestLoci

Count the number of loci used more than once (total-unique)
```
CHS.VS.sol.rad.60d.BestLoci <- best.Adapt.CHS.VS.sol.rad.60d$loci
CHS.VS.temp.laying.date.BestLoci <- best.Adapt.CHS.VS.temp.laying.date$loci
CHS.VS.pcpt.60d.BestLoci <- best.Adapt.CHS.VS.pcpt.60d$loci
CHS.VS.shadow.days.BestLoci <- NULL
CHS.VS.day10cm.BestLoci <- best.Adapt.CHS.VS.day10cm$loci


length(c(CHS.VS.sol.rad.60d.BestLoci, CHS.VS.temp.laying.date.BestLoci, CHS.VS.pcpt.60d.BestLoci, CHS.VS.shadow.days.BestLoci, CHS.VS.day10cm.BestLoci))

length(unique(c(CHS.VS.sol.rad.60d.BestLoci, CHS.VS.temp.laying.date.BestLoci, CHS.VS.pcpt.60d.BestLoci, CHS.VS.shadow.days.BestLoci, CHS.VS.day10cm.BestLoci)))
```


then plot
```
d1 <- length(CHS.VS.sol.rad.60d.BestLoci)
d2 <- length(CHS.VS.temp.laying.date.BestLoci)
d3 <- length(CHS.VS.pcpt.60d.BestLoci)
d4 <- length(CHS.VS.shadow.days.BestLoci)
d5 <- length(CHS.VS.day10cm.BestLoci)


d12 <- length(Reduce(intersect, list(CHS.VS.sol.rad.60d.BestLoci, CHS.VS.temp.laying.date.BestLoci)))
d13 <- length(Reduce(intersect, list(CHS.VS.sol.rad.60d.BestLoci, CHS.VS.pcpt.60d.BestLoci)))
d14 <- length(Reduce(intersect, list(CHS.VS.sol.rad.60d.BestLoci, CHS.VS.shadow.days.BestLoci)))
d15 <- length(Reduce(intersect, list(CHS.VS.sol.rad.60d.BestLoci, CHS.VS.day10cm.BestLoci)))
d23 <- length(Reduce(intersect, list(CHS.VS.temp.laying.date.BestLoci, CHS.VS.pcpt.60d.BestLoci)))
d24 <- length(Reduce(intersect, list(CHS.VS.temp.laying.date.BestLoci, CHS.VS.shadow.days.BestLoci)))
d25 <- length(Reduce(intersect, list(CHS.VS.temp.laying.date.BestLoci, CHS.VS.day10cm.BestLoci)))
d34 <- length(Reduce(intersect, list(CHS.VS.pcpt.60d.BestLoci, CHS.VS.shadow.days.BestLoci)))
d35 <- length(Reduce(intersect, list(CHS.VS.pcpt.60d.BestLoci, CHS.VS.day10cm.BestLoci)))
d45 <- length(Reduce(intersect, list(CHS.VS.shadow.days.BestLoci, CHS.VS.day10cm.BestLoci)))

d123 <- length(Reduce(intersect, list(CHS.VS.sol.rad.60d.BestLoci, CHS.VS.temp.laying.date.BestLoci,CHS.VS.pcpt.60d.BestLoci)))
d124 <- length(Reduce(intersect, list(CHS.VS.sol.rad.60d.BestLoci, CHS.VS.temp.laying.date.BestLoci,CHS.VS.shadow.days.BestLoci)))
d125 <- length(Reduce(intersect, list(CHS.VS.sol.rad.60d.BestLoci, CHS.VS.temp.laying.date.BestLoci,CHS.VS.day10cm.BestLoci)))
d234 <- length(Reduce(intersect, list(CHS.VS.temp.laying.date.BestLoci, CHS.VS.pcpt.60d.BestLoci,CHS.VS.shadow.days.BestLoci)))
d134 <- length(Reduce(intersect, list(CHS.VS.sol.rad.60d.BestLoci, CHS.VS.pcpt.60d.BestLoci,CHS.VS.shadow.days.BestLoci)))
d135 <- length(Reduce(intersect, list(CHS.VS.sol.rad.60d.BestLoci, CHS.VS.pcpt.60d.BestLoci,CHS.VS.day10cm.BestLoci)))
d145 <- length(Reduce(intersect, list(CHS.VS.sol.rad.60d.BestLoci, CHS.VS.shadow.days.BestLoci,CHS.VS.day10cm.BestLoci)))
d235 <- length(Reduce(intersect, list(CHS.VS.temp.laying.date.BestLoci, CHS.VS.pcpt.60d.BestLoci,CHS.VS.day10cm.BestLoci)))
d245 <- length(Reduce(intersect, list(CHS.VS.temp.laying.date.BestLoci, CHS.VS.shadow.days.BestLoci,CHS.VS.day10cm.BestLoci)))
d345 <- length(Reduce(intersect, list(CHS.VS.pcpt.60d.BestLoci, CHS.VS.shadow.days.BestLoci,CHS.VS.day10cm.BestLoci)))


d1234 <- length(Reduce(intersect, list(CHS.VS.temp.laying.date.BestLoci, CHS.VS.pcpt.60d.BestLoci,
CHS.VS.shadow.days.BestLoci, CHS.VS.sol.rad.60d.BestLoci)))
d1235 <- length(Reduce(intersect, list(CHS.VS.temp.laying.date.BestLoci, CHS.VS.pcpt.60d.BestLoci,
CHS.VS.day10cm.BestLoci, CHS.VS.sol.rad.60d.BestLoci)))

d2345 <- length(Reduce(intersect, list(CHS.VS.temp.laying.date.BestLoci, CHS.VS.pcpt.60d.BestLoci,
CHS.VS.shadow.days.BestLoci, CHS.VS.day10cm.BestLoci)))
d1245 <- length(Reduce(intersect, list(CHS.VS.temp.laying.date.BestLoci, CHS.VS.sol.rad.60d.BestLoci,
CHS.VS.shadow.days.BestLoci, CHS.VS.day10cm.BestLoci)))
d1345 <- length(Reduce(intersect, list(CHS.VS.pcpt.60d.BestLoci, CHS.VS.sol.rad.60d.BestLoci,
CHS.VS.shadow.days.BestLoci, CHS.VS.day10cm.BestLoci)))
d12345 <- length(Reduce(intersect, list(CHS.VS.sol.rad.60d.BestLoci, CHS.VS.temp.laying.date.BestLoci, CHS.VS.pcpt.60d.BestLoci, 
CHS.VS.shadow.days.BestLoci, CHS.VS.day10cm.BestLoci)))

#library(VennDiagram)

pdf("Venn.bestLoci.CHS.VS.pdf")
draw.quintuple.venn(area1=d1, area2=d2, area3=d3, area4=d4, area5=d5,
n12=d12, n13=d13, n14=d14, n15=d15, n23=d23, n24=d24, n25=d25, n34=d34, n35=d35, n45=d45,
n123=d123, n124=d124, n125=d125, n134=d134, n135=d135, n145=d145, n234=d234, n235=d235, n245=d245, n345=d345,
n1234=d1234, n1235=d1235, n1245=d1245, n1345=d1345, n2345=d2345, n12345=d12345, 
category=c("sol.rad.60d", "temp.laying.date", "pcpt.60d", "shadow.days", "day10cm"),
lty="blank", 
fill=c("yellow", "orange", "skyblue1", "skyblue3", "blue")
)
dev.off()



```




