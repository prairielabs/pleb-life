PRAIRIE LABS GENERAL USE SHELL STANDARD
Version: 1.1.0
Publisher: Prairie Labs, Inc.
Purpose: reusable prompt-operational package shell
Status: app-neutral template

WHAT THIS IS
This is the reusable Prairie Labs shell for app-store packages.
It is stripped of demo-specific material.
It is stripped of application-specific material.
It is not a flat directory.
It contains only the shell and the placeholder payload area.
The app payload must carry its own operating instructions.

STANDARD LOCAL / HARNESS USER FLOW
Download the package.
Ask the harness: Inspect latest download
When prompted, type: install
After installation completes, the declared program entry point appears immediately.

STANDARD BROWSER-DROP USER FLOW
Drop, upload, or paste the package into a browser-only chat environment.
The system detects that it cannot manipulate the user's filesystem.
The shell sheds install behavior.
The program runs directly from the declared payload entry point.
No Desktop/Prairie folder is created.
No Downloads scan is attempted.
No fake file movement is claimed.

STANDARD COMMANDS
Inspection command, local harness: Inspect latest download
Install command, local harness: install
Browser drop mode: no install command required unless the user explicitly asks to simulate installation.

STANDARD INSTALL SUBSTRATE, LOCAL HARNESS ONLY
The installer operates relative to one folder on the user's Desktop:
Desktop/Prairie

If Desktop/Prairie does not exist, create it.
If Desktop/Prairie already exists, use it normally.
Every Prairie Labs application receives its own subfolder inside Desktop/Prairie.

STANDARD PACKAGE SEQUENCE, LOCAL HARNESS
0. Filename
1. Root/Hooks.txt
2. Root/README.txt
3. Root/Browser_Drop_Handler.txt
4. Root/Layer_1_Installer/Installer.txt
5. User types install
6. Desktop/Prairie is created or reused
7. Application folder is created or reused under Desktop/Prairie
8. Root/Layer_1_Installer/Layer_2_Preload/Metadata.txt is read
9. Root/Layer_1_Installer/Layer_2_Preload/Map.txt is read
10. Declared payload is loaded from Root/Layer_1_Installer/Layer_2_Preload/Layer_3_Payload/
11. Declared entry point is rendered immediately

STANDARD PACKAGE SEQUENCE, BROWSER DROP
0. User drops, uploads, or pastes package/file content into browser chat.
1. Read Root/Hooks.txt when present.
2. Read Root/README.txt when present.
3. Read Root/Browser_Drop_Handler.txt when present.
4. Read Metadata.txt and Map.txt when present.
5. Ignore local install behavior.
6. Ignore Desktop/Prairie behavior.
7. Load declared ENTRY_FILE from payload.
8. Render ENTRY_POINT immediately inside chat.
9. If the user chooses Save and no filesystem exists, emit a copyable SAVE BLOCK instead of claiming a real file was written.
10. If the user chooses Load Game and no filesystem exists, ask for a pasted/uploaded SAVE BLOCK or visible save text.

STANDARD FILENAME FORM
PrairieLabs_INSPECT-LATEST-DOWNLOAD_[APP-SLUG]_v[VERSION].zip

The filename is operational. It helps the harness choose the newest downloaded package and avoid scanning the entire Downloads folder.

STANDARD TREE
Root/
  README.txt
  Hooks.txt
  Browser_Drop_Handler.txt
  SHELL_TREE.txt
  Layer_1_Installer/
    Installer.txt
    Layer_2_Preload/
      Metadata.txt
      Map.txt
      Layer_3_Payload/
        README_PAYLOAD.txt
        app payload files begin here
        Layer_4_and_beyond/ optional as needed

BOUNDARY RULE
Root, Hooks, Browser_Drop_Handler, Installer, Desktop/Prairie substrate behavior, and the Download -> Inspect latest download -> install -> entry point flow are standard shell behavior.
Metadata, Map, and Layer_3+ payload files are application-specific.

SHELL BOUNDARY RULE
The shell routes and launches applications.
It is not an app manual.
If an application needs instructions, those instructions belong in the application payload.

FINAL v1.1.0 HARDENING RULES
After local installation, route from Desktop/Prairie/[APP_FOLDER_NAME]/Root/, not from Downloads or a temporary extraction path.
On reinstall or update, preserve saves, projects, exports, and user-created .txt files.
After the declared entry point is rendered, stop narrating shell behavior unless the user explicitly asks.

TRUTH RULE
Do not claim installation, extraction, folder creation, file creation, preload completion, or payload load unless the harness actually performs or confirms it.
In browser-drop mode, explicitly avoid claiming any local filesystem action.

END README
