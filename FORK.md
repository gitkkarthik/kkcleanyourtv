# Tamil calendar fork

This fork of [cleanyourtv](https://github.com/Gathin23/cleanyourtv) adds a Tamil daily calendar to the reference
launcher, worked out offline for Chennai. It needs no network and no new permission.

<img src="docs/switches/tamil_panchangam.jpg" width="640" alt="The Tamil calendar sheet under the clock on a Hisense TV">

- **`tamil_panchangam`:** a daily calendar sheet under the clock showing:
  - the Tamil date, with the 60-year cycle name and the weekday
  - the Hijri date and sunrise
  - thithi and nakshatram, with their end times in nazhigai and by the clock (thirukanitham)
  - Rahu, Kuligai and Emagandam
  - soolam with its remedy
  - the good horas
- **`tamil_date`:** the Tamil date in Tamil script under the date, e.g. `ஐப்பசி 10 · பராபவ`.

How it's worked out:
- **Tamil month:** it starts when the sun enters the next sign (sidereal, Lahiri ayanamsa). If that happens before
  Chennai's sunset, that day is the 1st; otherwise the next day is.
- **Moon:** Jean Meeus' chapter 47 series, with the larger terms only, so end times are good to a few minutes.
- **Checking:** I checked 27-10-2026 against a printed daily sheet and Prokerala. Printed sheets that use vakya give
  different end times, so the sheet says it uses thirukanitham.
- **Left out:** nalla neram, gowri, rasi palan and festival notes. They differ between publishers and follow no
  rule that can be computed.

Tested on a Hisense HiSmartTV A4, Android TV 9.

## Use it

Clean up the TV and install the launcher as the upstream [README](README.md) and [PROMPT.md](PROMPT.md) describe,
using this branch. Both switches are off by default. Turn them on in
`launcher/app/src/main/res/values/config.xml` before building:

```xml
<bool name="tamil_panchangam">true</bool>
<bool name="tamil_date">false</bool>   <!-- the sheet already shows the date -->
```

Or set `"tamil_panchangam": true` in a theme's `config.json`. The code is in `Tamil.java` and `Panchangam.java`,
with tests in `TamilTest` and `PanchangamTest`.
