# Generalised dissimilarity model

Aim: Compare the most important environmental drivers of adaptive divergence between gradients. 

This model allows ranking of the most important env. variables. 

I'll use only the candidate adaptive loci. 


/Users/alexjvr/2016RADAnalysis/3_CH.landscapeGenomics/subsets/GDM


The vignette and pdf can both be found here: 

https://cran.r-project.org/web/packages/gdm/index.html



Input files: 

1. Response matrix: Fst matrix based on all candidate loci for each transect. The first column should be all the sites names. i.e. not square

I'm using a dissimilarity matrix, which is what is recommended for Fst data. (see gdm.pdf). This needs to be created with adegenet
First convert the vcf file to plink. And then use pgdspider to convert this to normal structure format. This will be read into R. 

2. Predictor matrix: site by predictor table. 

I'm just using the EnvData files that I created for comparing the environmental gradients between regions. 



Response matrix: I'm using a site by variable matrix with the 5 important Env Variables and coordinate information

#### CHN
```
#install.packages("Gdm01", repos="http://R-Forge.R-project.org")
#library(Gdm01)
library(gdm)
library(hierfstat)
library(adegenet)
library(reshape)

CHN.229.25 <- read.structure("CHN.AdaptiveLoci.str")
CHN229.pop <- read.table("CHN229.pop", header=T)
CHN.pop.factor <- as.factor(CHN229.pop$pop)
CHN.229.25@pop <- CHN.pop.factor
CHN.229.25@pop

CHN229.25.fst <- pairwise.fst(CHN.229.25, pop=NULL, res.type=c("dist", "matrix"))  ##this creates the lower half of a pairwise distance matrix
m.CHN229 <- as.matrix(CHN229.25.fst)  ##make this a full matrix
m.CHN229.scaled <- apply(m.CHN229[,1:ncol(m.CHN229)], MARGIN=2, FUN=function(X) (X-min(X))/diff(range(X))) ##scale the data 
CHN.pop.names <- unique(CHN.pop.factor)
rownames(m.CHN229.scaled) <- CHN.pop.names  #select only the unique pop names
write.table(m.CHN229.scaled, "CHN229.25.Fst.table", row.names=T, col.names=F, quote=F)


#####Read in the EnvironData
CHN.EnvData <- read.table("CHN.EnvData", header=T)
CHN.EnvData.importantVariables <- CHN.EnvData[,c("site", "long", "lat", "sol.rad.60d", "temp.laying.date", "pcpt.60d", "shadow.days", "day10cm")]  ##subset the data to use only the important variables


CHN.fst <- read.table("CHN229.25.Fst.table")
names(CHN.fst)[1] <- "site"  ##make sure site column is named the same in both the Env and fst files


##### GDM
###Create pairwise gdm input format

CHN.gdmData <- formatsitepair(CHN.fst, bioFormat=3, dist="bray", siteColumn="site", XColumn="lat", YColumn="long", predData=CHN.EnvData.importantVariables
) ##create the pairwise GDM input format


###Run GDM
CHN.gdm <- gdm(CHN.gdmData, geo=T)

plot(CHN.gdm, plot.layout=c(3,3))

###Plot of Splines across each EnvVar

##For comparison between all env variables, I need to normalise the Splines (0-1) for each Env variable

CHN.gdm.Splines <- isplineExtract(CHN.gdm) ##extract the spline data to make plotting easier
plot(gdm.1.splineDat$x[,"Geographic"], gdm.1.splineDat$y[,"Geographic"], lwd=3, type="l", xlab="Geographic distance", ylab="Partial ecological distance")  #example of a plot

CHN.gdm.Splines.scaled.y <- CHN.gdm.Splines$y  ##CHN.gdm.Splines is a list. I want to scale y (the Spline value), so I'm moving it to a new data frame
CHN.gdm.Splines.scaled.y <- apply(CHN.gdm.Splines.scaled.y[,1:ncol(CHN.gdm.Splines.scaled.y)], MARGIN=2, FUN=function(X) (X-min(X))/diff(range(X))) ##scale
plot(CHN.gdm.Splines$x[,"pcpt.60d"], CHN.gdm.Splines.scaled.y$pcpt.60d, lwd=3,type="l", xlab="Pcpt 60d", ylab="Partial ecological distance") ##and then we can plot them like this
plot(CHN.gdm.Splines$x[,"day10cm"], CHN.gdm.Splines.scaled.y$day10cm, lwd=3,type="l", xlab="Day 10cm", ylab="Partial ecological distance")


###Prepare the Spline data for the comparative plot
###I need the relative importance of each env variable. I'm calculating this by comparing the maximum Spline value for each variable, and normalising across all 5 EnvVariables. The height of each spline gives the importance - i.e. change in height at a particular EnvVariable value = bigger change in Fst than before. 

library(ggplot2) 

CHN.RelativeImportance.Splines <- CHN.gdm.Splines$y[200,]  ##the maximum value is the last row of the splines list
CHN.RelativeImportance.Splines <- as.data.frame(CHN.RelativeImportance.Splines)
CHN.RelativeImportance.Splines <- apply(CHN.RelativeImportance.Splines, MARGIN=2, FUN=function(X) (X-min(X))/diff(range(X))) ##normalise
CHN.RelativeImportance.Splines <- as.data.frame(CHN.RelativeImportance.Splines)

CHN.RelativeImportance.Splines$EnvVar <- c("Geography", "sol.rad.60d", "temp.laying.date", "pcpt.60d", "shadow.days", "day10cm")
CHN.RelativeImportance.Splines$Transect <- c("CHN", "CHN", "CHN", "CHN", "CHN", "CHN")
colnames(CHN.RelativeImportance.Splines) <- c("RelativeImportance.Splines", "EnvVar", "Transect")
ggplot(CHN.RelativeImportance.Splines, aes(x=Transect, y=EnvVar, fill=RelativeImportance.Splines)) + geom_tile() + coord_equal() + scale_fill_gradient(name="R2") +theme(axis.title.x=element_blank(), axis.title.y=element_blank())  ##check that it looks right

```


#### CHS

```
CHS.283.228 <- read.structure("CHS.AdaptiveLoci.str")
CHS283.pop <- read.table("CHS283.pop", header=T)
CHS.pop.factor <- as.factor(CHS283.pop$pop)
CHS.283.228@pop <- CHS.pop.factor
CHS.283.228@pop

CHS283.228.fst <- pairwise.fst(CHS.283.228, pop=NULL, res.type=c("dist", "matrix"))  ##this creates the lower half of a pairwise distance matrix
m.CHS283 <- as.matrix(CHS283.228.fst)  ##make this a full matrix
m.CHS283.scaled <- apply(m.CHS283[,1:ncol(m.CHS283)], MARGIN=2, FUN=function(X) (X-min(X))/diff(range(X))) ##scale the data 
CHS.pop.names <- unique(CHS.pop.factor)
rownames(m.CHS283.scaled) <- CHS.pop.names  #select only the unique pop names
m.CHS283.scaled <- m.CHS283.scaled[-23,-23] ##remove stba because this has missing EnvData
write.table(m.CHS283.scaled, "CHS283.228.Fst.table", row.names=T, col.names=F, quote=F)


#####Read in the EnvironData
CHS.EnvData <- read.table("CHS.EnvData", header=T)
CHS.EnvData.importantVariables <- CHS.EnvData[,c("site", "long", "lat", "sol.rad.60d", "temp.laying.date", "pcpt.60d", "shadow.days", "day10cm")]  
##subset the data to use only the important variables

CHS.EnvData.importantVariables <- CHS.EnvData.importantVariables[-23,]##remove stba

CHS.fst <- read.table("CHS283.228.Fst.table")
names(CHS.fst)[1] <- "site"  ##make sure site column is named the same in both the Env and fst files


##### GDM
###Create pairwise gdm input format


CHS.gdmData <- formatsitepair(CHS.fst, bioFormat=3, dist="bray", siteColumn="site", XColumn="lat", YColumn="long", predData=CHS.EnvData.importantVariables
) ##create the pairwise GDM input format

###Run GDM
CHS.gdm <- gdm(CHS.gdmData, geo=T)

plot(CHS.gdm, plot.layout=c(3,3))


###Plot of Splines across each EnvVar

##For comparison between all env variables, I need to normalise the Splines (0-1) for each Env variable

CHS.gdm.Splines <- isplineExtract(CHS.gdm) ##extract the spline data to make plotting easier
plot(gdm.1.splineDat$x[,"Geographic"], gdm.1.splineDat$y[,"Geographic"], lwd=3, type="l", xlab="Geographic distance", ylab="Partial ecological distance")  #example of a plot

CHS.gdm.Splines.scaled.y <- CHS.gdm.Splines$y  ##CHS.gdm.Splines is a list. I want to scale y (the Spline value), so I'm moving it to a new data frame
CHS.gdm.Splines.scaled.y <- apply(CHS.gdm.Splines.scaled.y[,1:ncol(CHS.gdm.Splines.scaled.y)], MARGIN=2, FUN=function(X) (X-min(X))/diff(range(X))) ##scale
plot(CHS.gdm.Splines$x[,"pcpt.60d"], CHS.gdm.Splines.scaled.y$pcpt.60d, lwd=3,type="l", xlab="Pcpt 60d", ylab="Partial ecological distance") ##and then we can plot them like this
plot(CHS.gdm.Splines$x[,"day10cm"], CHS.gdm.Splines.scaled.y$day10cm, lwd=3,type="l", xlab="Day 10cm", ylab="Partial ecological distance")


###Prepare the Spline data for the comparative plot
###I need the relative importance of each env variable. I'm calculating this by comparing the maximum Spline value for each variable, and normalising across all 5 EnvVariables. The height of each spline gives the importance - i.e. change in height at a particular EnvVariable value = bigger change in Fst than before. 

library(ggplot2) 

CHS.RelativeImportance.Splines <- CHS.gdm.Splines$y[200,]  ##the maximum value is the last row of the splines list
CHS.RelativeImportance.Splines <- as.data.frame(CHS.RelativeImportance.Splines)
CHS.RelativeImportance.Splines <- apply(CHS.RelativeImportance.Splines, MARGIN=2, FUN=function(X) (X-min(X))/diff(range(X))) ##normalise
CHS.RelativeImportance.Splines <- as.data.frame(CHS.RelativeImportance.Splines)

CHS.RelativeImportance.Splines$EnvVar <- c("Geography", "sol.rad.60d", "temp.laying.date", "pcpt.60d", "shadow.days", "day10cm")
CHS.RelativeImportance.Splines$Transect <- c("CHS", "CHS", "CHS", "CHS", "CHS", "CHS")
colnames(CHS.RelativeImportance.Splines) <- c("RelativeImportance.Splines", "EnvVar", "Transect")
ggplot(CHS.RelativeImportance.Splines, aes(x=Transect, y=EnvVar, fill=RelativeImportance.Splines)) + geom_tile() + coord_equal() + scale_fill_gradient(name="R2") +theme(axis.title.x=element_blank(), axis.title.y=element_blank())  ##check that it looks right


```




#### CHS.TI

```
CHS.TI.148.285 <- read.structure("CHS.TI.AdaptiveLoci.str")
CHS.TI148.pop <- read.table("CHS.TI148.pop", header=T)
CHS.TI.pop.factor <- as.factor(CHS.TI148.pop$pop)
CHS.TI.148.285@pop <- CHS.TI.pop.factor
CHS.TI.148.285@pop

CHS.TI148.285.fst <- pairwise.fst(CHS.TI.148.285, pop=NULL, res.type=c("dist", "matrix"))  ##this creates the lower half of a pairwise distance matrix
m.CHS.TI148 <- as.matrix(CHS.TI148.285.fst)  ##make this a full matrix
m.CHS.TI148.scaled <- apply(m.CHS.TI148[,1:ncol(m.CHS.TI148)], MARGIN=2, FUN=function(X) (X-min(X))/diff(range(X))) ##scale the data 
CHS.TI.pop.names <- unique(CHS.TI.pop.factor) #select only the unique pop names
rownames(m.CHS.TI148.scaled) <- CHS.TI.pop.names  
m.CHS.TI148.scaled <- m.CHS.TI148.scaled[-14,-14] ##remove stba because this has missing EnvData
write.table(m.CHS.TI148.scaled, "CHS.TI148.285.Fst.table", row.names=T, col.names=F, quote=F)


#####Read in the EnvironData
CHS.TI.EnvData <- read.table("CHS.TI.EnvData", header=T)
CHS.TI.EnvData.importantVariables <- CHS.TI.EnvData[,c("site", "long", "lat", "sol.rad.60d", "temp.laying.date", "pcpt.60d", "shadow.days", "day10cm")]  ##subset the data to use only the important variables


CHS.TI.fst <- read.table("CHS.TI148.285.Fst.table")
names(CHS.TI.fst)[1] <- "site"  ##make sure site column is named the same in both the Env and fst files


##### GDM
###Create pairwise gdm input format


CHS.TI.gdmData <- formatsitepair(CHS.TI.fst, bioFormat=3, dist="bray", siteColumn="site", XColumn="lat", YColumn="long", predData=CHS.TI.EnvData.importantVariables
) ##create the pairwise GDM input format

###Run GDM
CHS.TI.gdm <- gdm(CHS.TI.gdmData, geo=T)

plot(CHS.TI.gdm, plot.layout=c(3,3))


###Plot of Splines across each EnvVar

##For comparison between all env variables, I need to normalise the Splines (0-1) for each Env variable

CHS.TI.gdm.Splines <- isplineExtract(CHS.TI.gdm) ##extract the spline data to make plotting easier
plot(gdm.1.splineDat$x[,"Geographic"], gdm.1.splineDat$y[,"Geographic"], lwd=3, type="l", xlab="Geographic distance", ylab="Partial ecological distance")  #example of a plot

CHS.TI.gdm.Splines.scaled.y <- CHS.TI.gdm.Splines$y  ##CHS.TI.gdm.Splines is a list. I want to scale y (the Spline value), so I'm moving it to a new data frame
CHS.TI.gdm.Splines.scaled.y <- apply(CHS.TI.gdm.Splines.scaled.y[,1:ncol(CHS.TI.gdm.Splines.scaled.y)], MARGIN=2, FUN=function(X) (X-min(X))/diff(range(X))) ##scale
plot(CHS.TI.gdm.Splines$x[,"pcpt.60d"], CHS.TI.gdm.Splines.scaled.y$pcpt.60d, lwd=3,type="l", xlab="Pcpt 60d", ylab="Partial ecological distance") ##and then we can plot them like this
plot(CHS.TI.gdm.Splines$x[,"day10cm"], CHS.TI.gdm.Splines.scaled.y$day10cm, lwd=3,type="l", xlab="Day 10cm", ylab="Partial ecological distance")


###Prepare the Spline data for the comparative plot
###I need the relative importance of each env variable. I'm calculating this by comparing the maximum Spline value for each variable, and normalising across all 5 EnvVariables. The height of each spline gives the importance - i.e. change in height at a particular EnvVariable value = bigger change in Fst than before. 

library(ggplot2) 

CHS.TI.RelativeImportance.Splines <- CHS.TI.gdm.Splines$y[200,]  ##the maximum value is the last row of the splines list
CHS.TI.RelativeImportance.Splines <- as.data.frame(CHS.TI.RelativeImportance.Splines)
CHS.TI.RelativeImportance.Splines <- apply(CHS.TI.RelativeImportance.Splines, MARGIN=2, FUN=function(X) (X-min(X))/diff(range(X))) ##normalise
CHS.TI.RelativeImportance.Splines <- as.data.frame(CHS.TI.RelativeImportance.Splines)

CHS.TI.RelativeImportance.Splines$EnvVar <- c("Geography", "sol.rad.60d", "temp.laying.date", "pcpt.60d", "shadow.days", "day10cm")
CHS.TI.RelativeImportance.Splines$Transect <- c("CHS.TI", "CHS.TI", "CHS.TI", "CHS.TI", "CHS.TI", "CHS.TI")
colnames(CHS.TI.RelativeImportance.Splines) <- c("RelativeImportance.Splines", "EnvVar", "Transect")
ggplot(CHS.TI.RelativeImportance.Splines, aes(x=Transect, y=EnvVar, fill=RelativeImportance.Splines)) + geom_tile() + coord_equal() + scale_fill_gradient(name="R2") +theme(axis.title.x=element_blank(), axis.title.y=element_blank())  ##check that it looks right


```





#### CHS.VS

```
CHS.VS.135.356 <- read.structure("CHS.VS.AdaptiveLoci.str")
CHS.VS135.pop <- read.table("CHS.VS135.pop", header=T)
CHS.pop.factor <- as.factor(CHS.VS135.pop$pop)
CHS.VS.135.356@pop <- CHS.pop.factor
CHS.VS.135.356@pop

CHS.VS135.356.fst <- pairwise.fst(CHS.VS.135.356, pop=NULL, res.type=c("dist", "matrix"))  ##this creates the lower half of a pairwise distance matrix
m.CHS.VS135 <- as.matrix(CHS.VS135.356.fst)  ##make this a full matrix
m.CHS.VS135.scaled <- apply(m.CHS.VS135[,1:ncol(m.CHS.VS135)], MARGIN=2, FUN=function(X) (X-min(X))/diff(range(X))) ##scale the data 
CHS.pop.names <- unique(CHS.pop.factor)
rownames(m.CHS.VS135.scaled) <- CHS.pop.names  #select only the unique pop names
write.table(m.CHS.VS135.scaled, "CHS.VS135.356.Fst.table", row.names=T, col.names=F, quote=F)


#####Read in the EnvironData
CHS.VS.EnvData <- read.table("CHS.VS.EnvData", header=T)
CHS.VS.EnvData.importantVariables <- CHS.VS.EnvData[,c("site", "long", "lat", "sol.rad.60d", "temp.laying.date", "pcpt.60d", "shadow.days", "day10cm")]  
##subset the data to use only the important variables


CHS.VS.fst <- read.table("CHS.VS135.356.Fst.table")
names(CHS.VS.fst)[1] <- "site"  ##make sure site column is named the same in both the Env and fst files


##### GDM
###Create pairwise gdm input format


CHS.VS.gdmData <- formatsitepair(CHS.VS.fst, bioFormat=3, dist="bray", siteColumn="site", XColumn="lat", YColumn="long", predData=CHS.VS.EnvData.importantVariables
) ##create the pairwise GDM input format


###Run GDM
CHS.VS.gdm <- gdm(CHS.VS.gdmData, geo=T)

plot(CHS.VS.gdm, plot.layout=c(3,3))

###Plot of Splines across each EnvVar

##For comparison between all env variables, I need to normalise the Splines (0-1) for each Env variable

CHS.VS.gdm.Splines <- isplineExtract(CHS.VS.gdm) ##extract the spline data to make plotting easier
plot(gdm.1.splineDat$x[,"Geographic"], gdm.1.splineDat$y[,"Geographic"], lwd=3, type="l", xlab="Geographic distance", ylab="Partial ecological distance")  #example of a plot

CHS.VS.gdm.Splines.scaled.y <- CHS.VS.gdm.Splines$y  ##CHS.VS.gdm.Splines is a list. I want to scale y (the Spline value), so I'm moving it to a new data frame
CHS.VS.gdm.Splines.scaled.y <- apply(CHS.VS.gdm.Splines.scaled.y[,1:ncol(CHS.VS.gdm.Splines.scaled.y)], MARGIN=2, FUN=function(X) (X-min(X))/diff(range(X))) ##scale
plot(CHS.VS.gdm.Splines$x[,"pcpt.60d"], CHS.VS.gdm.Splines.scaled.y$pcpt.60d, lwd=3,type="l", xlab="Pcpt 60d", ylab="Partial ecological distance") ##and then we can plot them like this
plot(CHS.VS.gdm.Splines$x[,"day10cm"], CHS.VS.gdm.Splines.scaled.y$day10cm, lwd=3,type="l", xlab="Day 10cm", ylab="Partial ecological distance")


###Prepare the Spline data for the comparative plot
###I need the relative importance of each env variable. I'm calculating this by comparing the maximum Spline value for each variable, and normalising across all 5 EnvVariables. The height of each spline gives the importance - i.e. change in height at a particular EnvVariable value = bigger change in Fst than before. 

library(ggplot2) 

CHS.VS.RelativeImportance.Splines <- CHS.VS.gdm.Splines$y[200,]  ##the maximum value is the last row of the splines list
CHS.VS.RelativeImportance.Splines <- as.data.frame(CHS.VS.RelativeImportance.Splines)
CHS.VS.RelativeImportance.Splines <- apply(CHS.VS.RelativeImportance.Splines, MARGIN=2, FUN=function(X) (X-min(X))/diff(range(X))) ##normalise

CHS.VS.RelativeImportance.Splines$EnvVar <- c("Geography", "sol.rad.60d", "temp.laying.date", "pcpt.60d", "shadow.days", "day10cm")
CHS.VS.RelativeImportance.Splines$Transect <- c("CHS.VS", "CHS.VS", "CHS.VS", "CHS.VS", "CHS.VS", "CHS.VS")
colnames(CHS.VS.RelativeImportance.Splines) <- c("RelativeImportance.Splines", "EnvVar", "Transect")
ggplot(CHS.VS.RelativeImportance.Splines, aes(x=Transect, y=EnvVar, fill=RelativeImportance.Splines)) + geom_tile() + coord_equal() + scale_fill_gradient(name="R2") +theme(axis.title.x=element_blank(), axis.title.y=element_blank())  ##check that it looks right

```





#### CZ

```
CZ.404.46 <- read.structure("CZ.AdaptiveLoci.str")
CZ404.pop <- read.table("CZ404.pop", header=T)
CHS.pop.factor <- as.factor(CZ404.pop$pop)
CZ.404.46@pop <- CHS.pop.factor
CZ.404.46@pop

CZ404.46.fst <- pairwise.fst(CZ.404.46, pop=NULL, res.type=c("dist", "matrix"))  ##this creates the lower half of a pairwise distance matrix
m.CZ404 <- as.matrix(CZ404.46.fst)  ##make this a full matrix
m.CZ404.scaled <- apply(m.CZ404[,1:ncol(m.CZ404)], MARGIN=2, FUN=function(X) (X-min(X))/diff(range(X))) ##scale the data 
CHS.pop.names <- unique(CHS.pop.factor)
rownames(m.CZ404.scaled) <- CHS.pop.names  #select only the unique pop names
write.table(m.CZ404.scaled, "CZ404.46.Fst.table", row.names=T, col.names=F, quote=F)


#####Read in the EnvironData
CZ.EnvData <- read.table("CZ.EnvData", header=T)
CZ.EnvData.importantVariables <- CZ.EnvData[,c("site", "long", "lat", "sol.rad.60d", "temp.laying.date", "pcpt.60d", "shadow.days", "day10cm")]  
##subset the data to use only the important variables


CZ.fst <- read.table("CZ404.46.Fst.table")
names(CZ.fst)[1] <- "site"  ##make sure site column is named the same in both the Env and fst files


##### GDM
###Create pairwise gdm input format

CZ.gdmData <- formatsitepair(CZ.fst, bioFormat=3, dist="bray", siteColumn="site", XColumn="lat", YColumn="long", predData=CZ.EnvData.importantVariables
) ##create the pairwise GDM input format

###Run GDM
CZ.gdm <- gdm(CZ.gdmData, geo=T)

plot(CZ.gdm, plot.layout=c(3,3))


###Plot of Splines across each EnvVar

##For comparison between all env variables, I need to normalise the Splines (0-1) for each Env variable

CZ.gdm.Splines <- isplineExtract(CZ.gdm) ##extract the spline data to make plotting easier
plot(gdm.1.splineDat$x[,"Geographic"], gdm.1.splineDat$y[,"Geographic"], lwd=3, type="l", xlab="Geographic distance", ylab="Partial ecological distance")  #example of a plot

CZ.gdm.Splines.scaled.y <- CZ.gdm.Splines$y  ##CZ.gdm.Splines is a list. I want to scale y (the Spline value), so I'm moving it to a new data frame
CZ.gdm.Splines.scaled.y <- apply(CZ.gdm.Splines.scaled.y[,1:ncol(CZ.gdm.Splines.scaled.y)], MARGIN=2, FUN=function(X) (X-min(X))/diff(range(X))) ##scale
plot(CZ.gdm.Splines$x[,"pcpt.60d"], CZ.gdm.Splines.scaled.y$pcpt.60d, lwd=3,type="l", xlab="Pcpt 60d", ylab="Partial ecological distance") ##and then we can plot them like this
plot(CZ.gdm.Splines$x[,"day10cm"], CZ.gdm.Splines.scaled.y$day10cm, lwd=3,type="l", xlab="Day 10cm", ylab="Partial ecological distance")


###Prepare the Spline data for the comparative plot
###I need the relative importance of each env variable. I'm calculating this by comparing the maximum Spline value for each variable, and normalising across all 5 EnvVariables. The height of each spline gives the importance - i.e. change in height at a particular EnvVariable value = bigger change in Fst than before. 

library(ggplot2) 

CZ.RelativeImportance.Splines <- CZ.gdm.Splines$y[200,]  ##the maximum value is the last row of the splines list
CZ.RelativeImportance.Splines <- as.data.frame(CZ.RelativeImportance.Splines)
CZ.RelativeImportance.Splines <- apply(CZ.RelativeImportance.Splines, MARGIN=2, FUN=function(X) (X-min(X))/diff(range(X))) ##normalise
CZ.RelativeImportance.Splines <- as.data.frame(CZ.RelativeImportance.Splines)

CZ.RelativeImportance.Splines$EnvVar <- c("Geography", "sol.rad.60d", "temp.laying.date", "pcpt.60d", "shadow.days", "day10cm")
CZ.RelativeImportance.Splines$Transect <- c("CZ", "CZ", "CZ", "CZ", "CZ", "CZ")
colnames(CZ.RelativeImportance.Splines) <- c("RelativeImportance.Splines", "EnvVar", "Transect")
ggplot(CZ.RelativeImportance.Splines, aes(x=Transect, y=EnvVar, fill=RelativeImportance.Splines)) + geom_tile() + coord_equal() + scale_fill_gradient(name="R2") +theme(axis.title.x=element_blank(), axis.title.y=element_blank())  ##check that it looks right


```


## Figures

### Fig1: Relative Importance of variables in different regions


```
###Combine all the prepared data.frames together and plot


CHall.RelativeImportance.Splines <- rbind(CHN.RelativeImportance.Splines, CHS.RelativeImportance.Splines, CHS.VS.RelativeImportance.Splines, CHS.TI.RelativeImportance.Splines, CZ.RelativeImportance.Splines)

ggplot(CHall.RelativeImportance.Splines, aes(x=Transect, y=EnvVar, fill=RelativeImportance.Splines)) + geom_tile() + coord_equal() + scale_fill_gradient(name="Relative Importance") +theme(axis.title.x=element_blank(), axis.title.y=element_blank())  ##check that it looks right

```


