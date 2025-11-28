# ICS Maker

ICS Maker is a lightweight, self-contained web utility that generates an iCalendar (`.ics`) event from parameters passed in the page URL.
It then triggers an automatic download of the `.ics` file and optionally returns the browser to the previous page.

This tool is designed and authored by **Neil Gordon** (with AI assistance), and is published under the **MIT Licence**.

ICS Maker is hosted via GitHub Pages and requires **no backend** or server-side scripting.
Everything is done client-side using JavaScript.

---

## Purpose

ICS Maker is ideal for:

* Creating calendar events from external systems such as Knack apps
* Providing downloadable `.ics` files for users with a single click
* Automatically returning the user to the source page after download
* Ensuring consistent calendar formatting regardless of the calling system

The tool is used by several workflow systems to generate calendar assignments such as photographic judging schedules.

---

## How It Works

You link to the ICS Maker page like this:

```
https://tehoro.github.io/ics-maker/?title=...&start=...&end=...&uid=...&url=...
```

When opened:

1. ICS Maker parses the query parameters
2. Builds an `.ics` file dynamically in the browser
3. Initiates an automatic download
4. Displays a friendly status box
5. Returns to the previous page after a short delay, **if browsing history exists**
6. If no history exists (e.g., opened in a new tab), the page stays and instructs the user to close it

---

## URL Parameters

### `title` (required)

The event title that appears in the calendar’s *SUMMARY* field.

Example:
`title=Judge%20for%20Whakatane%20Camera%20Club`

### `start` (required)

The event start date. The script accepts:

* `DD/MM/YYYY`
* `YYYY-MM-DD`

Converted internally to the ICS `YYYYMMDD` format.

Example:
`start=05/02/2026`

### `end` (required)

The event end date. Same accepted formats as `start`.

Example:
`end=27/02/2026`

Note: In all-day ICS events, the `DTEND` date is exclusive. If you want a single-day event, use `start` and `end` as the same date.

### `uid` (required)

A unique identifier for the event.
This is used in the ICS `UID:` field.

You can pass any string; a good pattern is something tying the event to its origin, such as:

`uid=psnz-judging-assignment-660`

### `url` (optional)

A URL to embed in the ICS file using the `URL:` property.

This is often used to link back to a Knack record or assignment page.

Example:

```
url=https%3A%2F%2Fpsnz.knack.com%2Fmembership%23judging-assignments%2Fupcoming-assignments%2F
```

If included, the URL appears inside the `.ics` event so the user can return to the source system from their calendar.

---

## Behaviour Summary

### ✔ Automatic ICS File Generation

ICS Maker constructs a valid VCALENDAR/VEVENT structure in memory.

### ✔ Automatic Download

A hidden `<a>` element triggers the download of the `.ics` file.

### ✔ Friendly UI

A modern rounded card is displayed, with clear text indicating what is happening.

### ✔ Auto-Return

After ~5 seconds:

* If `window.history.length > 1`, the browser returns to the preceding page
* Otherwise, the user is shown a message explaining that they may close the tab

### ✔ Fallback Link

If the automatic download does not start, a direct download link appears.

---

## Example Full URL

```
https://tehoro.github.io/ics-maker/
?title=Judge%20for%20Whakatane%20Camera%20Club%20Inc.
&start=05/02/2026
&end=27/02/2026
&uid=psnz-judging-assignment-660
&url=https%3A%2F%2Fpsnz.knack.com%2Fmembership%23judging-assignments%2Fupcoming-assignments%2F
```

---

## File Structure

* **index.html**
  The entire functionality (HTML, CSS, JS) is contained in this file.
  No dependencies, no build process, no external scripts except Google Fonts.

---

## Licence

This project is released under the **MIT Licence**, which permits:

* Free use
* Modification
* Redistribution
* Commercial use

as long as the notice of copyright and the MIT Licence text are included.

---

## Author

**Neil Gordon**
Developer, photographer, and amateur weather system tinkerer.

ICS Maker is maintained in this GitHub repository:

🔗 [https://github.com/tehoro/ics-maker](https://github.com/tehoro/ics-maker)

---

