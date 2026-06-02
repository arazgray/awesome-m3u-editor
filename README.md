# Awesome M3U Editor v2

[![GitHub license](https://img.shields.io/github/license/arazgholami/awesome-m3u-editor)](https://github.com/arazgholami/awesome-m3u-editor/blob/main/LICENSE)
[![GitHub stars](https://img.shields.io/github/stars/arazgholami/awesome-m3u-editor)](https://github.com/arazgholami/awesome-m3u-editor/stargazers)

A clean, private, browser-based M3U and M3U8 playlist editor for IPTV playlists.

Awesome M3U Editor lets you open a playlist, edit groups and channels, preserve advanced IPTV metadata, check selected stream URLs, and download the modified playlist directly from your browser.

🔗 **Live Demo**: [https://arazgholami.github.io/awesome-m3u-editor/](https://arazgholami.github.io/awesome-m3u-editor/)

## Features

### Browser-based and private

- No installation required
- No account required
- No backend server required
- Your playlist stays on your computer
- Works directly from a static HTML page

### Complete M3U/M3U8 editing

- Open existing `.m3u` and `.m3u8` files
- Edit the first `#EXTM3U` playlist header line
- Add, edit, rename, move, sort, and delete channels
- Create, rename, sort, reorder, and delete groups
- Download the edited playlist as a new `.m3u` file

### IPTV metadata support

- Preserves playlist header data such as `url-tvg` and `x-tvg-url`
- Preserves channel archive and catchup attributes
- Supports `catchup`, `catchup-type`, `catchup-days`, `catchup-source`, `timeshift`, and custom attributes
- Keeps unknown extra attributes instead of silently deleting provider data
- Includes an Extra Attributes field for custom channel metadata

### Group and channel organization

- Drag and drop groups
- Drag and drop channels
- Sort groups A-Z
- Sort channels A-Z
- Move selected channels between groups
- Filter groups and channels quickly

### Multi-select support

- Use `Shift + Click` to select a range
- Use `Ctrl + Click` or `Cmd + Click` to select multiple separate groups or channels
- Delete, move, check, and reorder selected items

### Selected channel status checker

- Adds a status column beside each channel name
- Default status is `Unknown`
- Checks only selected channels from the channel list
- Adds a Status field in Channel Details
- Adds a Check button in Channel Details for the currently opened channel
- Shows `Checking` while a channel is being tested
- Displays HTTP status codes such as `200`, `403`, `404`, and `5xx`
- Shows readable labels such as `CORS`, `Blocked`, `Bad URL`, `Unsupported`, or `No URL`
- Status values are saved locally but are not exported into the M3U file

### Usability

- Rename buttons for selected groups and channels
- Double-click rename still works
- Live URL preview
- Compact Bootstrap 5 interface
- Local browser storage for continuing later

## Getting Started

### Sample playlists

```txt
# All TV channels grouped by category
https://iptv-org.github.io/iptv/index.category.m3u

# All TV channels grouped by language
https://iptv-org.github.io/iptv/index.language.m3u

# All TV channels grouped by country
https://iptv-org.github.io/iptv/index.country.m3u
```

### Use the web version

1. Open [https://arazgholami.github.io/awesome-m3u-editor/](https://arazgholami.github.io/awesome-m3u-editor/)
2. Click **Choose File**
3. Select your `.m3u` or `.m3u8` playlist
4. Edit groups, channels, URLs, metadata, and playlist header data
5. Select channels and click **Check Selected** when you want to test their URLs
6. Click **Download Modified M3U** when done

### Run locally

```bash
git clone https://github.com/arazgholami/awesome-m3u-editor.git
cd awesome-m3u-editor
```

Then open `index.html` in your browser.

## How to Use

### Edit the playlist header

The first playlist line can contain important IPTV data, for example:

```m3u
#EXTM3U url-tvg="https://example.com/epg.xml" x-tvg-url="https://example.com/epg.xml.gz"
```

Awesome M3U Editor v2 lets you edit and preserve this line, so EPG and global playlist metadata are not lost after saving.

### Edit channel details

Click a channel to edit:

- Name
- URL
- Status
- TVG ID
- TVG Name
- TVG Logo
- Group Title
- Catchup
- Catchup Type
- Catchup Days
- Extra Attributes

Extra Attributes can be used for provider-specific M3U attributes that are not covered by the normal fields.

Example:

```txt
catchup-source="http://example.com/archive/${start}/${duration}" timeshift="3"
```

### Rename groups and channels

You can rename in two ways:

- Select a group or channel and click **Rename**
- Double-click the group or channel name

### Select multiple groups or channels

- `Shift + Click` selects a range
- `Ctrl + Click` selects multiple separate items
- `Cmd + Click` works on macOS

After selecting multiple channels, you can delete, move, reorder, or check them.

### Check selected channel status

Select one or more channels in the channel list, then click **Check Selected**.

The app checks only the selected channels. It does not scan the full playlist automatically.

You can also open a channel and click **Check** in Channel Details to test only that channel.

Common results:

```txt
200        OK. The stream URL is reachable.
301/302    Redirect. The URL redirects somewhere else.
401        Unauthorized. Login, token, or subscription may be required.
403        Forbidden. Access is blocked. It may be geo-limited or provider-limited.
404        Not found. The stream URL may be dead or changed.
5xx        Server error. The provider server may be down or unstable.
CORS       The browser reached the URL but was not allowed to read the real status.
Blocked    The browser blocked the request or could not complete it.
Bad URL    The URL is invalid.
Unsupported Only HTTP and HTTPS URLs can be checked from the browser.
No URL     The channel has no URL.
```

Because this is a fully client-side browser app, some IPTV servers do not allow the browser to read their HTTP status because of CORS. In those cases, the app shows `CORS` instead of guessing.

## Privacy

Awesome M3U Editor works locally in your browser.

Your playlist is not uploaded to any server. File parsing, editing, checking, local saving, and exporting happen on your device.

## Tips

- Use filters to quickly find groups or channels.
- Check only suspicious or newly imported channels instead of the whole playlist.
- Use Extra Attributes when your IPTV provider uses custom archive or catchup parameters.
- Keep the original playlist as a backup before downloading a modified playlist.
- If a stream works in your IPTV player but shows `CORS` here, it does not always mean the stream is dead. It usually means the browser is not allowed to inspect it.

## Contributing

Contributions are welcome.

1. Fork the repository
2. Create your feature branch

```bash
git checkout -b feature/amazing-feature
```

3. Commit your changes

```bash
git commit -m "Add amazing feature"
```

4. Push to the branch

```bash
git push origin feature/amazing-feature
```

5. Open a Pull Request

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Acknowledgments

- Built with [Bootstrap 5](https://getbootstrap.com/)
- Icons by [Bootstrap Icons](https://icons.getbootstrap.com/)
- Drag and drop powered by [SortableJS](https://sortablejs.github.io/Sortable/)

---

Made with ❤️ by [@arazgholami](https://github.com/arazgholami) | [Star on GitHub](https://github.com/arazgholami/awesome-m3u-editor)
