# NWS Weather Alert Ticker — OBS Browser Source

Live weather alert tickers for OBS Studio, powered by the free NWS API.

## Files

| File                    |       Description              |
|-------------------------|--------------------------------|
| `index.html`            | Original ticker (v4)           |
| `ticker-broadcast.html` | Broadcast-style ticker (v2)    |

## OBS Setup

1. Add a **Browser Source** to your scene
2. Uncheck **Local file** if hosting online. If the file is local, you **MUST** check "Local File" for it to work, and use the local directory where it's sitting.
3. Set the browser source's URL to your public hosted URL:
   - `https://YOURUSERNAME.github.io/REPONAME/` — original ticker
   - `https://YOURUSERNAME.github.io/REPONAME/ticker-broadcast.html` — broadcast style
4. Width: `1920`
5. Height: `72` (or `102` if DEBUG is enabled)
6. ✅ Refresh browser when scene becomes active
7. ❌ Uncheck "Shutdown source when not visible"
8. Page permissions: **Full access to OBS**

## Config

Edit the `CONFIG` block near the top of each HTML file:

```js
const CONFIG = {
  STATES          : ["IN"],       // state codes to monitor. IN for Indiana, IL for Illinois, etc.
  FILTER_COUNTIES : [],           // [] = keep blank for statewide, or enter abbreviations for specific zones. (LPCO for Laporte County, etc.)
  POLL_MS         : 60000,        // poll interval in ms (30000 is the absolute MINIMUM!)
  SPEED_PX        : 80,           // scroll speed (ms)
  DEBUG           : false         // true = show debug bar (Top of browswer source)
};
```

## Finding Your NWS Zone IDs

Navigate to (https://www.weather.gov/pimar/PubZone) and select your state using PDF or JPG on the right side of the page. From there, you will see your state's county codes. You may enter them into the [] area under the Ticker Broadcast file "config" section.

Example(s) for the "NWS Zone IDs"
For instance, IN (state) then (Z), then county code.
INZ001 = Indiana's Lake County
ILZ064 = Illinois Bond County