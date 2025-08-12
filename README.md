# Save and Load

![Platform](https://img.shields.io/badge/Platform-Windows-blue)
![License](https://img.shields.io/badge/License-MIT-yellow)
![Status](https://img.shields.io/badge/Status-Portable-brightgreen)
![Version](https://img.shields.io/badge/Version-v1.1.3-brightgreen)

## Download & Install

1. Download Save and Load from
   [releases](https://github.com/cadburry0407/save-and-load-diskless/releases)
2. Run the .exe file
3. Open the application

## Admin Setup

1. Default admin account:

Username: **admin** Password: **p4ssw0rd123**

2. Enter the FTP server's IP address (local ip), username, and password, then
   save.

3. Upon successful FTP account save:

- The application will automatically connect.
- A data.json file will be created on the folder and accounts.json on the ftp server
- Admin password can be updated in data.json.

4. Add game name and save file location.

## User Instructions

1. Create an account.
2. Choose the game to save.
3. Select a save slot and click save.

## Server Configuration

Admins can use FileZilla Server or similar software to set up an FTP account.
Ensure the following settings are applied:

Server > Configure > Server Listener

Set the protocol for 0.0.0.0 to **Explicit FTP over TLS and insecure plain
FTP**.

## Disclaimer

This application is exclusively for saving game save files. For additional
features, please use different software.

## Core Functionality

For Regular Users:

### 1. Account Management

- Register a new user account
- Login with existing credentials
- Change personal password (except for admin users)
- Logout from the system

### 2. Game Save Management

- Save game progress to the ftp server
- Load saved games from the ftp server
- View and manage existing save files across multiple games
- Delete old or unwanted save files
- Support for multiple save slots per game

## For Admin Users:

### 1. Server Configuration

- Configure FTP server connection settings
- Test connectivity to the FTP server

### 2. Game Configuration

- Add, edit, and remove supported games
- Define save locations for different games
- Configure game-specific settings

### 3. User Management

- Reset user passwords
- View user information

## User Experience Flow

1. Users connect to the FTP server (connection status shown on the UI)
2. Users log in with their credentials or register a new account
3. Regular users see their games list and can select games to save/load
4. Admin users see the admin panel with configuration options
5. Users can manage their save files and account settings

## 📜 Licensing

This application is licensed under the [MIT License](./LICENSE.txt).

It is provided **free of charge** and **only in executable form**; the source
code is **not distributed** by the copyright holder.

You are free to use, copy, modify, merge, publish, distribute, sublicense,
and/or sell copies of this software, in accordance with the terms of the MIT
License. If you obtain the source code from any source, you may use it under the
same license terms.
