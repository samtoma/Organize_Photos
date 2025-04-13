# Organize_Photos
# Photo Organizer GUI

A simple graphical application for organizing photos and videos into folders based on their creation date.

## Features

* **Graphical Interface:** Easy-to-use interface for selecting folders and options.
* **Date-Based Organization:** Sorts files into a `YYYY/MM-Mon` folder structure (e.g., `2023/04-Apr`) within your chosen destination folder[cite: 3].
* **Date Extraction:** Attempts to read the creation date from file metadata (EXIF). Uses `exiftool` (if installed) for robust video/HEIC support, falling back to file modification time if no date is found[cite: 4, 5, 7]. Files without a date go into an "Unknown-Date" folder[cite: 8].
* **Duplicate Handling:** Checks for *exact duplicates* (same name, size, and content hash) already present in the destination folder. If found, skips the copy and deletes the redundant source file[cite: 9, 10].
* **Filename Conflict Resolution:** Automatically renames files (e.g., `image_1.jpg`) if a file with the same name but different content exists in the target folder[cite: 11].
* **Configurable Hashing:** Choose the algorithm (MD5, SHA1, SHA256, SHA512) used for file verification after copying[cite: 15].
* **Recursive Processing:** Optionally process subfolders within the source directory[cite: 14].
* **Live Log:** View processing details and potential errors in real-time within the application[cite: 12, 13].

## Requirements

1.  **Operating System:** Windows or macOS.
2.  **Exiftool (CRITICAL for Video/HEIC):**
    * This application relies on the external command-line tool `exiftool` to accurately read creation dates from many video formats and HEIC image files.
    * **You MUST install `exiftool` separately** from [exiftool.org](https://exiftool.org/).
    * After installation, ensure `exiftool` is added to your system's **PATH environment variable** so this application can find it.
    * *Without `exiftool`, video and HEIC files will likely be placed in the "Unknown-Date" folder based on their file modification time.*

## Installation

1.  Download the latest release (`Photo Organizer.exe` for Windows or `Photo Organizer.app` for macOS).
2.  **Install `exiftool`** (see Requirements above). This step is separate but essential for full functionality.
3.  No other installation is needed for the Photo Organizer GUI itself.

## How to Use

1.  **Launch the application:** Double-click `Photo Organizer.exe` (Windows) or `Photo Organizer.app` (macOS).
    * *(macOS Note: You might need to right-click the app and select "Open" the first time due to security settings).*
2.  **Select Source Folder:** Click "Browse..." next to "Source Folder" and choose the directory containing the photos and videos you want to organize.
3.  **Select Destination Folder:** Click "Browse..." next to "Destination Folder" and choose the *existing* directory where the organized `YYYY/MM-Mon` folders should be created. **Do not select the same folder as the source.**
4.  **Choose Options:**
    * Check "Process Subfolders Recursively" if you want to include images/videos inside subdirectories of your source folder.
    * Select the desired "Hash Algorithm" for verifying file copies (MD5 is default).
5.  **Start Organizing:** Click the "Start Organizing" button.
6.  **Monitor Progress:** Observe the progress bar, status messages, and detailed log output at the bottom of the window.
7.  **Cancel (Optional):** Click the "Cancel" button if you need to stop the process prematurely.
8.  **Completion:** A message will pop up when the process is complete or if it was cancelled or encountered critical errors. Review the log for a detailed summary and any error messages.

## License

*Copyright 2025 [Your Name/Organization]. All Rights Reserved.*
*(Consider replacing with an appropriate open-source license like Apache 2.0 or MIT if distributing)*
