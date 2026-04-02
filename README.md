# Tanium Exclusion Creator

A single-file web app that generates security exclusion lists for endpoint protection software (AV/EDR) based on your Tanium deployment.

It dynamically scrapes the [Tanium security exclusions documentation](https://help.tanium.com/bundle/ug_client_cloud/page/client/security_exclusions.html) to build module lists, so the tool stays current as Tanium adds or changes modules.

## Usage

1. Open `index.html` in any modern browser (Chrome, Edge, Firefox, Safari)
2. Select your target operating system(s)
3. Choose your Tanium Client directory (Default or Custom path)
4. Select an exclusion mode:
   - **Folder Level Exclusions Only** — returns only the base Tanium Client folder paths
   - **Include Process/File Exclusions** — returns folder, file, and process exclusions for selected modules
5. Check the modules you have deployed
6. Click **Generate Exclusions**
7. Copy to clipboard, download as CSV, or download as TXT

## Features

- **Zero dependencies** — single HTML file, no installs or build steps required
- **Dynamic module list** — scraped from Tanium docs on each load, automatically reflects changes
- **OS-aware path resolution** — replaces `<Tanium Client>` placeholder with the correct default path per OS, or a custom path you specify
- **Multiple export formats** — on-page display, clipboard copy, CSV, and plain text
- **Local caching** — caches exclusion data in localStorage for 24 hours to reduce load times
- **Always-included modules** — Client Management, Direct Connect, End-User Notifications, and Integrations Gallery exclusions are included by default

## Requirements

- A modern web browser with JavaScript enabled
- Internet connection (for initial data fetch from Tanium docs)

## How It Works

The app fetches exclusion data from the Tanium documentation backend API (`help-be.tanium.com`) via a CORS proxy, parses the HTML tables from the response, and builds an interactive UI for selecting OS, modules, and export options. Parsed data is cached in `localStorage` to avoid redundant network requests.
