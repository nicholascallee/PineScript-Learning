// This Pine Script™ code is subject to the terms of the Mozilla Public License 2.0 at https://mozilla.org/MPL/2.0/
// © nickallee8529

//https://www.youtube.com/watch?v=M1RIZxBsXFk

//@version=6
indicator("High and Low of Given Timeframe", overlay = true)


timeSession = input.session(title="Session to Monitor", defval = "0830-0845")
timezone = input.string(title = "Timezone", defval = "GMT")
debugPaint = input.bool(title = "Color the Session?", defval = false)

// if timeframe is within the given period, on any day of the week gmt time
//InSession(sess) => na(time(timeframe.period, sess + ":1234567", "GMT")) == false


// if timeframe is within the given period, Monday through Friday gmt time
InSession(sess) => na(time(timeframe.period, sess + ":23456", "GMT")) == false

// adding var makes the variable immutable
var float todayHigh = high
var float todayLow = low
var float todayClose = close

var float yesterdayHigh = na
var float yesterdayLow = na
var float yesterdayClose = na

// used to reset todays high low close
var bool firstBarOfNewSession = false

// if in the timeframe specified
if InSession(timeSession)
    if firstBarOfNewSession
        todayHigh := high
        todayLow := low
        todayClose := close
        firstBarOfNewSession := false
    if high > todayHigh
        todayHigh := high
    if low < todayLow
        todayLow := low
else
    // save yesterdays high low close for tomorrow
    if not firstBarOfNewSession
        yesterdayHigh := todayHigh
        yesterdayLow := todayLow
        yesterdayClose := todayClose
        firstBarOfNewSession := true

plot(yesterdayHigh != yesterdayHigh[1] ? na : yesterdayHigh, color = color.red, style = plot.style_linebr)

plot(yesterdayLow != yesterdayLow[1] ? na : yesterdayLow, color = color.blue, style = plot.style_linebr)

plot(yesterdayClose != yesterdayClose[1] ? na : yesterdayClose, color = color.green, style = plot.style_linebr)
