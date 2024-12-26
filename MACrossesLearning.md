// This Pine Script™ code is subject to the terms of the Mozilla Public License 2.0 at https://mozilla.org/MPL/2.0/
// © nickallee8529

//@version=6
indicator("MA Crosses Learning")

//ema 50 and 100
ema1 = ta.ema(close,50)
ema2 = ta.ema(close,100)

maCrossOver = ta.crossover(ema1,ema2)
maCrossUnder = ta.crossunder(ema1,ema2)

plot(ema1, color = color.green)
plot(ema2, color = color.red)

//change background color dependent on crossover or crossunder
bgcolor(maCrossOver ? color.green : na)
bgcolor(maCrossUnder ? color.red : na)
