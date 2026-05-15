# Better Cleaned URL Bar

Elegant and minimalistic glassmorphic URL bar for [Zen Browser](https://zen-browser.app/) with a frosted glass effect, rounded results, and extensive color customization.

<img width="1743" height="1184" alt="Image" src="https://github.com/user-attachments/assets/8b71dd02-7ef4-45d7-8238-50c0bc034385" />

## About

This is a maintained fork of [dinnoyow/zen-cleaned-url-bar](https://github.com/dinnoyow/zen-cleaned-url-bar) with bugfixes and new features.

### What's fixed

- **Transparent/broken URL bar on Zen 1.19.9b+** ([#27](https://github.com/dinnoyow/zen-cleaned-url-bar/issues/27), [#37](https://github.com/dinnoyow/zen-cleaned-url-bar/issues/37), [#23](https://github.com/dinnoyow/zen-cleaned-url-bar/issues/23)) — Firefox 150 removed the stacking context from `#browser`, breaking `backdrop-filter` on child elements. Fixed by re-establishing a no-op `backdrop-filter` on the parent.
- **Custom colors not working** ([#19](https://github.com/dinnoyow/zen-cleaned-url-bar/issues/19), [#29](https://github.com/dinnoyow/zen-cleaned-url-bar/issues/29), [#31](https://github.com/dinnoyow/zen-cleaned-url-bar/issues/31), [#35](https://github.com/dinnoyow/zen-cleaned-url-bar/issues/35)) — Zen renamed `#urlbar-background` (ID) to `.urlbar-background` (class), so the old selector stopped matching. Updated all selectors accordingly.
- **Black text on dark mode** ([#21](https://github.com/dinnoyow/zen-cleaned-url-bar/issues/21)) — Selected result font color now targets child elements directly to override Zen's built-in styles.

### What's new

- **Accent color mode** for both the URL bar and selected result — uses Zen's accent color instead of custom colors
- **Configurable blur amount** — set any value or `0px` to disable
- **Selected result opacity** — control transparency of the selection highlight
- **Dim URLs in results** — reduces URL opacity to make titles more prominent
- **Configurable favicon background** on selected results (white, subtle, or transparent)
- **Smooth transition** on result row selection

## Installation

### Zen Theme Store

This mod has been submitted to the [Zen Theme Store](https://zen-browser.app/themes) and is waiting for approval (see [PR](https://github.com/zen-browser/theme-store/pull/1990)). Once approved, you'll be able to install it directly from the store.

### Local Installation

Unfortunately, Zen doesn't currently support installing mods from a zip or local folder. The built-in "Import" feature only works for mods already in the theme store (it uses the mod ID to fetch from the remote API).

As a workaround, you can manually place the files in the right location. This is a one-time setup and will persist across restarts (unlike editing `zen-themes.css` directly).

1. Open Zen Browser
2. Type `about:support` in the address bar and press Enter
3. Look for the **Application Basics** section
4. Find **Profile Directory** and click on **Open Directory**
   > On the Flatpak version of Zen, the profile folder is at `~/.var/app/app.zen_browser.zen/.zen`
5. Inside the profile folder, navigate to `chrome/zen-themes/`  
   (create the folders if they don't exist)
6. Create a new folder named `zen-better-cleaned-url-bar`
7. Copy `chrome.css`, `preferences.json`, and `readme.md` from this repo into that folder
8. Open `zen-themes.json` in the profile folder root and add an entry:
   ```json
   {
     "zen-better-cleaned-url-bar": {
       "id": "zen-better-cleaned-url-bar",
       "name": "Better Cleaned URL Bar",
       "description": "Elegant and minimalistic glassmorphic URL bar with customizable blur, transparency and colors.",
       "author": "matteo-tafuro",
       "version": "1.0.0",
       "homepage": "https://github.com/matteo-tafuro/zen-better-cleaned-url-bar",
       "style": "https://raw.githubusercontent.com/matteo-tafuro/zen-better-cleaned-url-bar/main/chrome.css",
       "readme": "https://raw.githubusercontent.com/matteo-tafuro/zen-better-cleaned-url-bar/main/readme.md",
       "preferences": "https://raw.githubusercontent.com/matteo-tafuro/zen-better-cleaned-url-bar/main/preferences.json",
       "enabled": true
     }
   }
   ```
   If the file already has entries, add the new one alongside them (it's a flat object).
9. Restart Zen Browser

You should now be able to see (and customize) the mod from `Settings / Zen Mods`!

## Customization

All preferences are accessible from the mod settings in Zen.

### URL Bar

| Preference | Type | Default |
|---|---|---|
| Color opacity | Text (CSS %) | `90%` |
| Use accent color | Checkbox | On |
| Custom color [Dark Mode] | Text (CSS color) | `hsl(0 0 10)` |
| Custom color [Light Mode] | Text (CSS color) | `hsl(0 0 90)` |
| Background blur amount | Text (CSS length) | `25px` |

- **Color opacity** — Controls how transparent the background color is. `0%` is fully solid, `100%` is fully transparent.
- **Use accent color** — When checked, the URL bar uses Zen's accent color. Uncheck to use the custom dark/light mode colors below.
- **Custom color [Dark/Light Mode]** — The URL bar background color for each theme. Only applies when "Use accent color" is unchecked. Accepts any CSS color format (rgb, hsl, hex).
- **Background blur amount** — The intensity of the frosted glass blur effect behind the URL bar. Set to `0px` to disable.

### Selected Result

| Preference | Type | Default |
|---|---|---|
| Opacity | Text (CSS %) | `70%` |
| Use accent color | Checkbox | On |
| Custom background color | Text (CSS color) | `hsl(0 0 80)` |
| Custom font color | Text (CSS color) | `rgb(255,255,255)` |
| Favicon background | Dropdown | Subtle |

- **Opacity** — Transparency of the color used for the selcted results row. `0%` is fully solid, `100%` is fully transparent.
- **Use accent color** — When checked, the selected result uses Zen's accent color. Uncheck to use custom colors below.
- **Custom background color** — Background color for the selected result row. Only applies when "Use accent color" is unchecked.
- **Custom font color** — Text color for the selected result's title, URL, and action. Only applies when "Use accent color" is unchecked.
- **Favicon background** — Controls the background behind the favicon on selected results. *White* is the Zen default, *Subtle* uses a soft hover-like tint, and *Transparent* removes it entirely.

### Other

| Preference | Type | Default |
|---|---|---|
| Dim URLs in results | Checkbox | On |

- **Dim URLs in results** — Reduces the opacity of URLs in result rows to make page titles more prominent.

