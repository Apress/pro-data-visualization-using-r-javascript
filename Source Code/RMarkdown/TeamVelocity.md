Correlation Analysis with Team Dynamics
========================================================




```r

tvFile <- "/Applications/MAMP/htdocs/teamvelocity.txt"
teamvelocity <- read.table(tvFile, sep = ",", header = TRUE)

plot(teamvelocity$TotalPoints, teamvelocity$TotalDevs, type = "p", 
    ylab = "Team Members", xlab = "Velocity", bg = "#CCCCCC", pch = 21)
```

![plot of chunk unnamed-chunk-1](figure/unnamed-chunk-11.png) 

```r

plot(teamvelocity$TotalPoints, teamvelocity$BugsOpened, type = "p", 
    xlab = "Velocity", ylab = "Bugs Opened During Sprint", bg = "#CCCCCC", pch = 21)
```

![plot of chunk unnamed-chunk-1](figure/unnamed-chunk-12.png) 

```r

plot(teamvelocity$TotalPoints, teamvelocity$BugBacklog, type = "p", 
    xlab = "Velocity", ylab = "Total Bug Backlog", bg = "#CCCCCC", pch = 21)
```

![plot of chunk unnamed-chunk-1](figure/unnamed-chunk-13.png) 

```r

plot(teamvelocity$TotalPoints, teamvelocity$ProductionIncidents, 
    type = "p", xlab = "Velocity", ylab = "Production Incidents after Release", 
    bg = "#CCCCCC", pch = 21)
```

![plot of chunk unnamed-chunk-1](figure/unnamed-chunk-14.png) 




```r
symbols(teamvelocity$TotalPoints, teamvelocity$TotalDevs, circles = teamvelocity$Team, 
    inches = 0.35, fg = "#000000", bg = "#CCCCCC", ylab = "Team Members", xlab = "Velocity")
```

![plot of chunk unnamed-chunk-2](figure/unnamed-chunk-21.png) 

```r

symbols(teamvelocity$TotalPoints, teamvelocity$TotalDevs, circles = teamvelocity$BugsOpened, 
    inches = 0.35, fg = "#000000", bg = "#CCCCCC", ylab = "Team Members", xlab = "Velocity", 
    main = "Velocity by Team Size by Bugs Opened")
```

![plot of chunk unnamed-chunk-2](figure/unnamed-chunk-22.png) 

```r

symbols(teamvelocity$TotalPoints, teamvelocity$BugsOpened, circles = teamvelocity$ProductionIncidents, 
    inches = 0.35, fg = "#000000", bg = "#CCCCCC", ylab = "Bugs Opened", xlab = "Velocity", 
    main = "Velocity by Bugs Opened by Production Incidents Opened")
```

![plot of chunk unnamed-chunk-2](figure/unnamed-chunk-23.png) 




```r
plot(teamvelocity)
```

![plot of chunk unnamed-chunk-3](figure/unnamed-chunk-3.png) 

