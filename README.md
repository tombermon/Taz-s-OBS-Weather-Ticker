# NWS Weather Alert Ticker — OBS Browser Source

This live weather alert ticker is being built, and maintained for live streaming purposes. You may utilize this file within OBS Studio (or other broadcasting app). The polling is done through the free NWS (National Weather Service) API service.

## Included Files within the repo:

| File                    |       Description              |
|-------------------------|--------------------------------|
| `index.html`            | Original ticker (v4)           |
| `ticker-broadcast.html` | Broadcast-style ticker (v2)    |

## OBS Setup

1. Add a **Browser Source** to your scene
2. If hosting online, please uncheck "Local File" and add the public link as the source url. If you choose to download the Index or Ticker-Broadcast file, check "Local File" and use the "browse" to find the downloaded file.
3. Set the browser source's URL to your public hosted URL:
   - `https://YOURUSERNAME.github.io/REPONAME/` (for example) — original ticker
   - `https://YOURUSERNAME.github.io/REPONAME/ticker-broadcast.html` (for example) — broadcast style
4. Set Width: `1920`
5. Set Height: `72` (or `102` if DEBUG is enabled)
6. Please check ✅ Refresh browser when scene becomes active
7. Please uncheck ❌ "Shutdown source when not visible"
8. Set Page permissions (if applicable): **Full access (In OBS)**

## Set your Config

Edit the `CONFIG` block near the top of each HTML file:

```js
const CONFIG = {
  STATES          : ["IN"],       // Currently set to IN (Indiana) by default. You may set to IL (Illinois), MI (Michigan), etc.
  FILTER_COUNTIES : [],           // [] = keep blank for statewide, or enter FULL names for each county. (Laporte for Laporte County, Lake for Lake County, etc.)
  POLL_MS         : 60000,        // Poll interval in ms. Keep in mind, 30000 is the MINIMUM that you may poll through NWS.
  SPEED_PX        : 80,           // Scroll speed (ms) is set here. Scrolls from right, to left.
  DEBUG           : false         // true = show debug bar (Top of browswer source)
};
```

## Finding Your NWS Zone IDs

Navigate to (https://www.weather.gov/pimar/PubZone) and select your state using PDF or JPG on the right side of the page. From there, you will see your state's county codes. You may enter them into the [] area under the Ticker Broadcast file "config" section.

Example(s) for the "NWS Zone IDs"
For instance, IN (state) then (Z), then county code.
INZ001 = Indiana's Lake County
ILZ064 = Illinois Bond County
