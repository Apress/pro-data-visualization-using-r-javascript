Balancing Delivery with Quality
========================================================



```r
library(MASS)

cardeaths <- data.frame(Seatbelts[, 1], Seatbelts[, 5], Seatbelts[, 
    6], Seatbelts[, 8])
colnames(cardeaths) <- c("DriversKilled", "DistanceDriven", "PriceofGas", 
    "SeatbeltLaw")
parcoord(cardeaths, col = rainbow(length(cardeaths[, 1])), var.label = TRUE)
```

![plot of chunk unnamed-chunk-1](figure/unnamed-chunk-11.png) 

```r


tvFile <- "/Applications/MAMP/htdocs/teamvelocity.txt"
teamvelocity <- read.table(tvFile, sep = ",", header = TRUE)
t <- data.frame(teamvelocity$Sprint, teamvelocity$TotalPoints, teamvelocity$TotalDevs, 
    teamvelocity$BugBacklog, teamvelocity$BugsOpened, teamvelocity$ProductionIncidents)
colnames(t) <- c("sprint", "points", "devs", "total bugs", "new bugs", 
    "prod incidents")
parcoord(t, col = rainbow(length(t[, 1])), var.label = TRUE)
```

![plot of chunk unnamed-chunk-1](figure/unnamed-chunk-12.png) 




```r
teFile <- "/Applications/MAMP/htdocs/teameffort.txt"
teameffort <- read.table(teFile, sep = ",", header = TRUE)

parcoord(teameffort, col = rainbow(length(teameffort[, 1])), var.label = TRUE, 
    main = "Level of Effort Spent")
```

![plot of chunk unnamed-chunk-2](figure/unnamed-chunk-2.png) 

