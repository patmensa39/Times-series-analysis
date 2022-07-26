# Times-series-analysis
### TIMES SERIES ANALYSIS ###

# Loading pacman and tidyverse 
pacman::p_load(pacman, tidyverse)

## loading the dataset 
library(datasets)

# Single time series 
### Data from the United States population(Getting information about the data)
?uspop

###Viewing or displaying the data set 
uspop

### Getting information about time series objects 
?ts

class(uspop) ## knowing the class of the dataset
is.ts(uspop) #asking if the data is a time series data
str(uspop) #looking for the structure of the dataset


### Plotting the data by default 
plot(uspop, main = "Time series analysis of US population \n from 1790 to 1970")

###Plotting the time series data in details 
uspop %>% plot(main = "Time series analysis of US population \n from 1790 to 1970", # title 
               sub = "(Source: dataset:: uspopulation)", #subtitle 
               xlab = "Year", ylab = "Population (in millions)", #naming the axes 
               )
abline(v = 1930, col = "green")
text(1930, 20, "1930", col = "black")
abline(v = 1940, col = "green")
text(1940, 2, "1940", col = "black")

###Plotting with ts.plot() This deals with plotting multiple times series 
?ts.plot()
### ploting the same data 
ts.plot(uspop, main = "Time series analysis of US population \n from 1790 to 1970", # title 
        sub = "(Source: dataset:: uspopulation)", #subtitle 
        xlab = "Year", ylab = "Population (in millions)")
abline(v = 1930, col = "green")
text(1930, 20, "1930", col = "black")
abline(v = 1940, col = "green")
text(1940, 2, "1940", col = "black")


### plotting the same thing using piping 
uspop %>% ts.plot(main = "Time series analysis of US population \n from 1790 to 1970", # title 
                  sub = "(Source: dataset:: uspopulation)", #subtitle 
                  xlab = "Year", ylab = "Population (in millions)")
abline(v = 1930, col = "green")
abline(v = 1930, col = "green")
text(1930, 20, "1930", col = "black")
abline(v = 1940, col = "green")
text(1940, 2, "1940", col = "black")


### plotting with plot.ts()
# This is more powerful alternative
?plot.ts
plot.ts(uspop, main = "Time series analysis of US population \n from 1790 to 1970", # title 
        sub = "(Source: dataset:: uspopulation)", #subtitle 
        xlab = "Year", ylab = "Population (in millions)")
abline(v = 1930, col = "green")
text(1930, 20, "1930", col = "black")
abline(v = 1940, col = "green")
text(1940, 2, "1940", col = "black")

# MULTIPLE TIME SERIES ###
# Eroupean stock markets
?EuStockMarkets
### Viewing the dataset 
EuStockMarkets

### plotting with the default (Generic plot command)
plot(EuStockMarkets, col = "red")
### This shows in a stacked in windows and they keep tracking each other 

### plotting with plot.ts 
plot.ts(EuStockMarkets, col = "green")
### This look normal like the generic plot command 

### Plotting with ts.plot
ts.plot(EuStockMarkets, col = heat.colors(6))

### Plotting with same ts.plot in details 
ts.plot(EuStockMarkets, col = heat.colors(6), main = "Euro Stock Market")

# Monthtly deaths from Lung Diseases in the UK 
data(UKLungDeaths)
?UKLungDeaths

ts.plot(ldeaths,mdeaths, fdeaths, xlab = "Year", ylab = "Deaths", 
        main  = "Time series monthly deaths from \n Lung Diseases in the UK " , lty = c(1:3), 
        col = rainbow(3))

# Another way 
data(sunspots)
?sunspots
plot(sunspots, main = "Monthly sunspot numbers from 1749 to 1983", col = "red")

#This works because it was inherited from a time series class 



