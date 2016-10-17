Production Incidents by Feature
========================================================



```r
prodincidentsFile <- "/Applications/MAMP/htdocs/productionIncidents.txt"
prodData <- read.table(prodincidentsFile, sep = ",", header = TRUE)
prodincidentByFeature <- aggregate(prodData$ID, by = list(Feature = prodData$Feature), 
    FUN = length)
prodincidentByFeature <- prodincidentByFeature[order(prodincidentByFeature$x), 
    ]
write.table(prodincidentByFeature, col.names = TRUE, row.names = FALSE, 
    file = "/Applications/MAMP/htdocs/prodincidentByFeature.csv", quote = FALSE, 
    sep = ",")

opar <- par(no.readonly = TRUE)
par(las = 1, mar = c(10, 10, 10, 10))
barplot(prodincidentByFeature$x, xlab = "Number of Incidents", names.arg = prodincidentByFeature$Feature, 
    horiz = TRUE, space = 1, cex.axis = 0.6, cex.names = 0.8, main = "Production Incidents by Feature", 
    col = "#CCCCCC")
```

![plot of chunk unnamed-chunk-1](figure/unnamed-chunk-1.png) 

```r
par(opar)
```








```r

prodincidentByFeatureBySeverity <- table(factor(prodData$Feature), 
    prodData$Severity)

opar <- par(no.readonly = TRUE)
par(las = 1, mar = c(10, 10, 10, 10))
barplot(t(prodincidentByFeatureBySeverity), xlab = "Number of Incidents", 
    names.arg = rownames(prodincidentByFeatureBySeverity), horiz = TRUE, space = 1, 
    cex.axis = 0.6, cex.names = 0.8, main = "Production Incidents by Feature", 
    col = c("#CCCCCC", "#666666", "#AAAAAA", "#333333"))
legend("bottomright", inset = 0.01, title = "Legend", c("Sev1", "Sev2", 
    "Sev3", "Sev4"), fill = c("#CCCCCC", "#666666", "#AAAAAA", "#333333"))
```

![plot of chunk unnamed-chunk-2](figure/unnamed-chunk-2.png) 

```r
par(opar)
```




