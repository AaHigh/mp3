# AAHIGH mp3

http://mp3.ahightower.com

Original music from AAHIGH. GitHub Pages repo: `AaHigh/mp3`.

## What plays

`description.json` is the only catalog. The player does not scan the folder.

If a file is sitting in this repo and you do not list it in `description.json`, it will not play. `frodd.mp3` is kept on disk on purpose as the omitted alt of `FrawdNCalifornia.mp3`. If `frodd` ever starts playing, the player is inferring tracks from the directory and that is a bug.

## Add a track

1. Commit the `.mp3` into the right folder (`/` or `johnny/` or `johnny2/`).
2. Add one object under the station `tracks` array in `description.json`.
3. Push. That is the whole add path.

Minimum track object:

```json
{
  "file": "new-song.mp3",
  "bytes": 1234567
}
```

Title defaults from the filename. Spaces become dashes. You can still set `title` yourself if you want a different label.

Useful optional fields:

- `title`, `subtitle`, `description`, `credits`, `notes`, `artwork`
- `startAt` and `endAt` in seconds, only honored when `bytes` matches the live file size
- `karaoke` is not stored here. Put timed lines in `karaoke.json`

After you edit an MP3 in place, the byte size changes and any old `startAt` / `endAt` tags stop applying by themselves. You do not have to clean the JSON first.

## Stations

Stations are the `albums` array. The radio control on the page lists those names. Add a station by adding another album object.

## Karaoke

`karaoke.json` is optional. Key each entry with the same `file` string used in `description.json`. Times are file-absolute seconds.

Lyrics show only when the user turns on EQ + LYRICS.

## iPhone background audio

Playback uses a real HTML audio element. On iPhone the graphical EQ starts off so Safari can keep playing after you leave the tab. Turning EQ on routes audio through Web Audio for the spectrum, which can stop background playback until you reload.

## Drop-in replace

Replace these four files. Leave every `.mp3`, `album_art.png`, `johnny/`, `johnny2/`, and `CNAME` alone.

- `index.html`
- `description.json`
- `karaoke.json`
- `README.md`
