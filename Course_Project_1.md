---
title: "Course Project 1"
author: "Andy Kannurpatti"
date: "Saturday, February 07, 2015"
output: html_document
---
#plot1.R

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
        
#plot2.R

        plot2 <- function (textfilename = character) {
                data1 <- subset(read.table(textfilename, header= TRUE, sep=";",stringsAsFactors = FALSE), {Date == "1/2/2007" | Date == "2/2/2007"})
                x <- as.POSIXct(data1$Date, format = "%d/%m/%Y")
                xx <- paste(x, data1$Time)
                datetime <- strptime (xx, "%Y-%m-%d %H:%M:%S")
                data1 <- cbind(datetime, data1)
                with(data1, plot(datetime, as.numeric(Global_active_power),type = "l", xlab="", ylab = "Global Active Power (kilowatts)", col="black"))
                dev.copy(png, filename = "plot2.png", width = 480, height = 480)
                dev.off()
        }

#plot3.R

        plot3 <- function (textfilename = character) {
                data1 <- subset(read.table(textfilename, header= TRUE, sep=";",stringsAsFactors = FALSE), {Date == "1/2/2007" | Date == "2/2/2007"})
                x <- as.POSIXct(data1$Date, format = "%d/%m/%Y")
                xx <- paste(x, data1$Time)
                datetime <- strptime (xx, "%Y-%m-%d %H:%M:%S")
                data1 <- cbind(datetime, data1)
                plotcol <- c("black", "red","blue")
                par(cex=0.8)
                with(data1, plot(datetime, as.numeric(Sub_metering_1),type = "l", xlab="", ylab = "Energy sub metering", col=plotcol[1]))
                par(new=T)
                plot(data1$datetime, as.numeric(data1$Sub_metering_2), type="l", xlab ="", ylab="", axes= F,col=plotcol[2], ylim = range(as.numeric(data1$Sub_metering_1)))
                par(new=T)
                plot(data1$datetime, as.numeric(data1$Sub_metering_3), type="l", xlab ="", ylab="", axes= F,col=plotcol[3], ylim = range(as.numeric(data1$Sub_metering_1)))
                legend("topright", c("Sub_metering_1","Sub_metering_2","Sub_metering_3"),lty=1, col=plotcol, cex=0.6, inset=0.08, bty="n")
                dev.copy(png, filename = "plot3.png", width = 480, height = 480)
                dev.off()
        
        }

#plot4.R


        plot4 <- function (textfilename = character) {
                data1 <- subset(read.table(textfilename, header= TRUE, sep=";",stringsAsFactors = FALSE), {Date == "1/2/2007" | Date == "2/2/2007"})
                x <- as.POSIXct(data1$Date, format = "%d/%m/%Y")
                xx <- paste(x, data1$Time)
                datetime <- strptime (xx, "%Y-%m-%d %H:%M:%S")
                data1 <<- cbind(datetime, data1)
                par(mfrow=c(2,2),cex=0.8)
                plot2(data1)
                plot11(data1)
                plot3(data1)
                plot12(data1)
                dev.copy(png, filename = "plot4.png", width = 480, height = 480)
                dev.off()       
        
        }

        plot11 <- function (x) {
                with(data1, plot(datetime, as.numeric(Voltage), type="l", xlab = "datetime", ylab = "Voltage", col="black"))
        }

        plot2 <- function (x) {
                with(data1, plot(datetime, as.numeric(Global_active_power),type = "l", xlab="", ylab = "Global Active Power", col="black"))
        }

        plot3 <- function(x) {
                plotcol <- c("black", "red","blue")
                par(cex=0.8)
                with(data1, plot(datetime, as.numeric(Sub_metering_1),type = "l", xlab="", ylab = "Energy sub metering", col=plotcol[1]))
                par(new=T)
                plot(data1$datetime, as.numeric(data1$Sub_metering_2), type="l", xlab ="", ylab="", axes= F,col=plotcol[2], ylim = range(as.numeric(data1$Sub_metering_1)))
                par(new=T)
                plot(data1$datetime, as.numeric(data1$Sub_metering_3), type="l", xlab ="", ylab="", axes= F,col=plotcol[3], ylim = range(as.numeric(data1$Sub_metering_1)))
                legend("topright", c("Sub_metering_1","Sub_metering_2","Sub_metering_3"),lty=1, col=plotcol, cex=0.6, inset=0.1, bty="n")
        }

        plot12 <- function (x) {
                with(data1, plot(datetime, as.numeric(Global_reactive_power), type="l", xlab = "datetime",ylab="Global_reactive_power", col="black"))
        
        }
