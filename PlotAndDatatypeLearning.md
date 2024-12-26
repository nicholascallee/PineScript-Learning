// This Pine Script™ code is subject to the terms of the Mozilla Public License 2.0 at https://mozilla.org/MPL/2.0/
// © nickallee8529

//@version=6
indicator(title="generic indicator title")

candleOpen= open
candleHigh = high
candleLow = low
candleClose = close
  
floatType = 33.3
colorType = color.rgb(0,255,0,100)
//Analyze price data

// calc candle size
candleSize = candleHigh - candleLow
candleSize10BarsAgo = high[10] - low[10]
candleSizeRatio = candleSize/ candleSize10BarsAgo

plot(candleSize, color = color.green)
plot(floatType, color = colorType)
plot(candleSizeRatio, color = color.blue)

//plot(candleOpen, color = color.blue)
//plot(candleHigh, color = color.red)
//plot(candleLow, color = color.green)
//plot(candleClose, color = color.purple)


// Get user input
booleanInput = input.bool(title = "give me a true or false", defval=true)
integerInput = input.int(title = "give me an int", defval = 33, minval=0, maxval=40, step=2)
floatInput = input.float(title = "give me a float", defval = 32.22)

//these inputs require you to pick a spot on the chart. price is y axis, time is x axis
priceInput = input.price(title="price input", defval = 0, confirm = true)
timeInput = input.time(title = "time input", defval = 0,confirm = true)
