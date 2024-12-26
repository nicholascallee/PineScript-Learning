// This Pine Script™ code is subject to the terms of the Mozilla Public License 2.0 at https://mozilla.org/MPL/2.0/
// © nickallee8529

//@version=6
indicator("Alerts Learning")
plot(close)

// higher close (1 indexed)
hc = close > high[1]
lc = close < low[1]

if hc
    alert(message = "This bar closed higher than previous bar:" + str.tostring(close), freq = alert.freq_once_per_bar_close)
if lc
    alert(message = "This bar closed lower than previous bar:" + str.tostring(close), freq = alert.freq_once_per_bar_close)


// cant be in if statement
// cant add str.tostring() in string params. Instead, must use placeholders. Example : {{close}}
alertcondition(hc, title = "Higher Close Alert", message = "This bar closed lower than previous bar: {{close}}")
