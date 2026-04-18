# Save and Load

![Platform](https://img.shields.io/badge/Platform-Windows-blue)
![License](https://img.shields.io/badge/License-MIT-yellow)
![Status](https://img.shields.io/badge/Status-Portable-brightgreen)
![Version](https://img.shields.io/badge/Version-v2.0.0-brightgreen)

Save and Load is a Windows desktop app for backing up and restoring game save
files through an FTP server.

It is built for a simple shared setup: the app keeps the FTP connection details
locally, while the actual shared app data lives on the FTP server so the admin
and all users are working from the same source of truth.

## Download & Install

1. Download Save and Load portable or installer from [releases](https://github.com/cadburry0407/save-and-load-diskless/releases)
2. Run the `save-and-load.exe` file

## What The App Does

- Admins set up the FTP connection, configure the save size limit, and add the
  games that users can back up.
- Users can register, sign in, save to a slot, load a save, and delete old save
  slots.
- If a save is too large, the app stops the upload and shows a warning instead.
- Existing FTP data is reused. If `save-load-data.json` is already on the
  server, the app loads the saved accounts, games, and save size limit instead
  of replacing them.

## Admin Setup

Default admin login:

- Username: **admin**
- Password: **p4ssw0rd123**

On first run, open the app and sign in as admin with the default password.

After signing in as admin:

1. Enter the FTP server IP, username, and password.
2. Save the server settings.
3. If the FTP server already has a `save-load-data.json`, the app loads the
   existing games list and max save size right away.
4. Change the default admin password when prompted.
5. Add or update the games you want the app to manage.
6. Test the FTP connection before regular users start using the app.

When setup is completed:

- `data.json` is stored beside the executable and keeps only local FTP bootstrap
  settings in `ftpConfig`.
- `save-load-data.json` on FTP stores shared app data: accounts, games, and save
  limits.
- The app preserves existing FTP data whenever possible instead of resetting it.

## Adding Game Paths

Use a normal folder path like:

`C:\Path\To\SaveFolder`

To exclude specific folders, use this format:

`C:\Path\To\SaveFolder_[Folder1,Folder2,Folder3]`

Rules:

- Add an underscore `_` before the bracketed folder list.
- Separate folder names with commas.
- Do not add spaces inside the exclusion list.

## How Users Use It

1. Create an account or sign in.
2. Choose a game.
3. Pick a save slot and click Save.
4. To restore a save, choose a slot and click Load.
5. Users can also change their own password without affecting saved data.

Admins can also reset user passwords and reset the admin password when needed.

## FTP Server Notes

If you are using FileZilla Server or a similar FTP server, make sure the server
listener for `0.0.0.0` is set to:

**Explicit FTP over TLS and insecure plain FTP**

## Data & Security Notes

- `data.json` is local-only and stores the FTP bootstrap config.
- Shared app data is stored on the FTP server in `save-load-data.json`.
- Passwords are hashed before storage.
- FTP credentials are stored in encrypted form.
- The app verifies the connection before running FTP operations.
- Before upgrading the app, back up both `data.json` and `save-load-data.json`.

## Disclaimer

This application is intended for backing up and restoring game save files. If
you need broader file management features, use a different tool.

## Licensing

This application is licensed under the [MIT License](./LICENSE.txt).

It is provided **free of charge** and **only in executable form**; the source
code is **not distributed** by the copyright holder.

You are free to use, copy, modify, merge, publish, distribute, sublicense,
and/or sell copies of this software in accordance with the MIT License. If you
obtain the source code from any source, you may use it under the same license
terms.
