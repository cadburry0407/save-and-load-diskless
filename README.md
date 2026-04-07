# Save and Load

![Platform](https://img.shields.io/badge/Platform-Windows-blue)
![License](https://img.shields.io/badge/License-MIT-yellow)
![Status](https://img.shields.io/badge/Status-Portable-brightgreen)
![Version](https://img.shields.io/badge/Version-v1.2.0-brightgreen)

## Download & Install

1. Download Save and Load from [releases](https://github.com/cadburry0407/save-and-load-diskless/releases)
2. Run the .exe file
3. Open the application

## Admin Setup

1. Default admin account:

   Username: **admin**  
   Password: **p4ssw0rd123**

2. Enter the FTP server's IP address (local IP), username, and password, then
   save.

3. Configure the maximum allowed save size in MB if needed.

4. Upon successful FTP account save:
   - The application will automatically connect.
   - A `data.json` file will be created in the application folder (stores admin
     account and game configurations locally)
   - An `accounts.json` file will be created on the FTP server (stores regular
     user accounts)

5. Add game name and save file location.
   - Basic format: `C:\Path\To\SaveFolder`
   - **Folder exclusion format**:
     `C:\Path\To\SaveFolder_[Folder1,Folder2,Folder3]`
     - Use underscore `_` followed by brackets `[]` at the end of the path
     - List folder names inside brackets, separated by commas (no spaces)
     - These folders will be excluded when saving/loading game files

6. Admin password can be reset to default using the "Reset Admin Password"
   button (admin login only).

## User Instructions

1. Create an account.
2. Choose the game to save.
3. Select a save slot and click save.
4. To load a save, select the slot and click load.
5. Overwrite existing saves by saving to an occupied slot.
6. If a save exceeds the configured size limit, the app will show a popup
   warning instead of uploading it.

## Server Configuration

Admins can use FileZilla Server or similar software to set up an FTP account.
Ensure the following settings are applied:

**Server > Configure > Server Listener**

Set the protocol for 0.0.0.0 to **Explicit FTP over TLS and insecure plain
FTP**.

## Auto-Save Feature

The application includes an optional auto-save feature for users:

1. Enable auto-save by checking the "Auto-Save" checkbox in the Games view
2. The app will monitor save file locations for all games that have existing
   saves
3. When files change in a monitored game's save location, the app automatically
   saves to the FTP server after a 5-second delay
4. Auto-save respects folder exclusion patterns (if configured)
5. Only games with at least one existing save will be monitored
6. Toggle off to disable auto-save at any time

**Resource Usage**: Auto-save uses approximately 10-30 MB RAM and <1% CPU when
idle.

## Disclaimer

This application is exclusively for saving game save files. For additional
features, please use different software.

## Core Functionality

### For Regular Users:

#### 1. Account Management

- Register a new user account
- Login with existing credentials
- Change personal password
- Logout from the system

#### 2. Game Save Management

- Save game progress to the FTP server
- Load saved games from the FTP server
- View and manage existing save files across multiple games
- Delete old or unwanted save files
- Support for multiple save slots per game
- Overwrite existing saves with confirmation
- Auto-save feature for active games (optional)

### For Admin Users:

#### 1. Server Configuration

- Configure FTP server connection settings
- Configure the maximum allowed save size in MB
- Test connectivity to the FTP server
- Connection status indicator (connected/disconnected)

#### 2. Game Configuration

- Add, edit, and remove supported games
- Define save locations for different games
- Configure folder exclusions for selective saving/loading
- Support for advanced path patterns

#### 3. User Management

- Reset user passwords
- View user accounts
- Change passwords with improved validation
- Reset admin password to default

## User Experience Flow

1. On first launch, the app creates a `data.json` file with the default admin
   account
2. Users see connection status (green = connected, red = disconnected)
3. Admin configures FTP server settings and adds games
4. Users log in with their credentials or register a new account
5. Regular users see their games list and can select games to save/load
6. Admin users see the admin panel with configuration options
7. Users can enable auto-save to automatically backup changes
8. Users can manage their save files and account settings

## Security Features

- Admin account stored locally in `data.json` (not on FTP server)
- User accounts stored on FTP server in `accounts.json`
- All passwords are hashed using bcrypt before storage
- Password encryption for FTP credentials
- Separate authentication for admin and regular users
- Connection verification before operations

## Technical Features

- **Folder Exclusion**: Exclude specific folders from save/load operations using
  `_[Folder1,Folder2]` syntax
- **Save Size Limit**: Restrict uploads with a configurable maximum save size in
  MB
- **Auto-Save**: Optional file watcher that monitors game save locations and
  automatically uploads changes
- **Connection Management**: Real-time FTP connection status monitoring
- **Debouncing**: Auto-save waits 5 seconds after the last file change before
  uploading
- **Error Handling**: Clear error messages for disconnection, authentication
  failures, and file operations
- **Overwrite Protection**: Confirmation modals before overwriting existing
  saves
- **Popup Warnings**: Oversized saves are shown in a dedicated popup with clear
  guidance

## 📜 Licensing

This application is licensed under the [MIT License](./LICENSE.txt).

It is provided **free of charge** and **only in executable form**; the source
code is **not distributed** by the copyright holder.

You are free to use, copy, modify, merge, publish, distribute, sublicense,
and/or sell copies of this software, in accordance with the terms of the MIT
License. If you obtain the source code from any source, you may use it under the
same license terms.
