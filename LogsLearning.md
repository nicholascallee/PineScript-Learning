// This Pine Script™ code is subject to the terms of the Mozilla Public License 2.0 at https://mozilla.org/MPL/2.0/
// © nickallee8529
// https://www.youtube.com/watch?v=EeGEdVehWT0&list=PL2vvCj1sdUJd-pI_54OWMfDZR7YZLDHlc&index=3
// https://www.tradingview.com/blog/en/pine-logs-in-pine-script-40490/

//@version=6
indicator("Logs Learning")

// prints bar info

// if bar is from the past
if barstate.ishistory
    if bar_index % 100 == 0
        // log every 100 bars
        log.warning("\nBar index: {0,number,#}", bar_index)
else
    // Realtime bar processing.
    varip lastTime = timenow
    varip updateNo = 0
    if barstate.isnew
        updateNo := 0
        log.error("\nNew bar")
    else
        log.info("\nUpdate no: {0}\nclose: {1}\nSeconds elapsed: {2}", updateNo, close, (timenow - lastTime) / 1000)
        updateNo += 1
    lastTime := timenow
plot(timenow)
