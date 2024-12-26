// This Pine Script™ code is subject to the terms of the Mozilla Public License 2.0 at https://mozilla.org/MPL/2.0/
// © nickallee8529

//@version=6
indicator("Plot Learning")

//plot(close, title = "Plot Learning Title", color = color.purple, linewidth = 2)

// plot volume as columns
//plot(volume, title = "Plot Learning Title", color = color.purple, linewidth = 2, style = plot.style_columns)

// trackprice true creates a horizontal line that moves up and down the y axis to follow the price
//plot(close, title = "Plot Learning Title", color = color.purple, linewidth = 2, style = plot.style_line, trackprice = true)


// plots values above the hist base on the positive, the values below are plotted on the negitive. (Like the Macd)
//plot(close, title = "Plot Learning Title", color = color.purple, linewidth = 2, style = plot.style_columns, trackprice = true, histbase = 1.17)

// shifts plots the values 10 bars ahead (-10 shifts the values 10 bars back)
//plot(volume, title = "Plot Learning Title", color = color.purple, linewidth = 2, style = plot.style_line, offset = 10)

// cross points with no connecting line
//plot(volume, title = "Plot Learning Title", color = color.purple, linewidth = 2, style = plot.style_cross, offset = 10)

// cross points with a connecting line
plot(volume, title = "Plot Learning Title", color = color.purple, linewidth = 2, style = plot.style_cross, offset = 10, join = true)

// restrict the user from editing the plot
plot(volume, title = "Plot Learning Title", color = color.purple, linewidth = 2, style = plot.style_cross, offset = 10, editable = false)

// show the last 10 bars
plot(volume, title = "Plot Learning Title", color = color.purple, linewidth = 2, style = plot.style_cross, offset = 10, show_last = 10)

// display the plot as invisible
plot(close, title = "Plot Learning Title", color = color.purple, linewidth = 2, style = plot.style_cross, offset = 10, display = display.none)
