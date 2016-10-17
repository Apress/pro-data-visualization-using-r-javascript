Defects Over Time
========================================================




```r
bugExport <- "/Applications/MAMP/htdocs/allbugs.csv"
bugs <- read.table(bugExport, header = TRUE, sep = ",")
bugs <- bugs[order(as.Date(bugs$Date, "%m-%d-%Y")), ]

sprintDates <- "/Applications/MAMP/htdocs/iterationdates.csv"
sprintInfo <- read.table(sprintDates, header = TRUE, sep = ",")


# output ordered list to new flat file
write.table(bugs, col.names = TRUE, row.names = FALSE, file = "/Applications/MAMP/htdocs/allbugsOrdered.csv", 
    quote = FALSE, sep = ",")

totalbugsByDate <- table(factor(bugs$Date))

plot(totalbugsByDate, type = "l", main = "New Bugs by Date", col = "red")
```

![plot of chunk unnamed-chunk-1](figure/unnamed-chunk-11.png) 

```r
xblocks(totalbugsByDate >= sprintInfo[1, ]$WeekStart & totalbugsByDate <= 
    sprintInfo[1, ]$WeekEnd, col = rgb[2])  ## the rest gray
```



```
## Error: could not find function "xblocks"
```



```r



runningTotalBugs <- cumsum(totalbugsByDate)

plot(runningTotalBugs, type = "l", xlab = "", ylab = "", pch = 15, 
    lty = 1, col = "red", main = "Cumulative Defects Over Time", axes = FALSE)
axis(1, at = 1:length(runningTotalBugs), lab = row.names(totalbugsByDate))
axis(2, las = 1, at = 10 * 0:max(runningTotalBugs))
```

![plot of chunk unnamed-chunk-1](figure/unnamed-chunk-12.png) 

```r

write.table(totalbugsByDate, col.names = TRUE, row.names = FALSE, 
    file = "/Applications/MAMP/htdocs/runningTotalBugs.csv", quote = FALSE, 
    sep = ",")
```






```r
bugsbySeverity <- table(factor(format(as.Date(bugs$Date), "%m-%d-%Y")), 
    bugs$Severity)

plot(bugsbySeverity[, 3], type = "l", xlab = "", ylab = "", pch = 15, 
    lty = 1, col = "orange", main = "New Bugs by Severity", axes = FALSE)
lines(bugsbySeverity[, 1], type = "l", col = "red", lty = 1)
lines(bugsbySeverity[, 2], type = "l", col = "yellow", lty = 1)
axis(1, at = 1:length(runningTotalBugs), lab = row.names(totalbugsByDate))
axis(2, las = 1, at = 0:max(bugsbySeverity[, 3]))
legend("topleft", inset = 0.01, title = "Legend", colnames(bugsbySeverity), 
    lty = c(1, 1, 1), col = c("red", "yellow", "orange"))
```

![plot of chunk unnamed-chunk-2](figure/unnamed-chunk-2.png) 





```r

plot(cumsum(bugsbySeverity[, 3]), type = "l", xlab = "", ylab = "", 
    pch = 15, lty = 1, col = "orange", main = "Running Total of Bugs by Severity", 
    axes = FALSE)
lines(cumsum(bugsbySeverity[, 1]), type = "l", col = "red", lty = 1)
lines(cumsum(bugsbySeverity[, 2]), type = "l", col = "yellow", lty = 1)
axis(1, at = 1:length(runningTotalBugs), lab = row.names(totalbugsByDate))
axis(2, las = 1, at = 0:max(cumsum(bugsbySeverity[, 3])))
legend("topleft", inset = 0.01, title = "Legend", colnames(bugsbySeverity), 
    lty = c(1, 1, 1), col = c("red", "yellow", "orange"))
```

![plot of chunk unnamed-chunk-3](figure/unnamed-chunk-3.png) 

