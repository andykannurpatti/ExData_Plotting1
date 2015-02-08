---
title: "Course Project 1"
author: "Andy Kannurpatti"
date: "Saturday, February 07, 2015"
output: html_document
---
## Below is the function plot1.R to generate plot
plot1 <- function (textfilename = character) {
        data1 <- subset(read.table(textfilename, header= TRUE, sep=";",stringsAsFactors = FALSE), {Date == "1/2/2007" | Date == "2/2/2007"})
        x <- as.POSIXct(data1$Date, format = "%d/%m/%Y")
        xx <- paste(x, data1$Time)
        datetime <- strptime (xx, "%Y-%m-%d %H:%M:%S")
        data1 <- cbind(datetime, data1)
        par(mfrow=c(1,1))
        with(data1, hist(as.numeric(Global_active_power), xlab = "Global Active Power (kilowatts)", main = "Global Active Power", col="red"))
        dev.copy(png, filename = "plot1.png", width = 480, height = 480)
        dev.off()
        
       
}