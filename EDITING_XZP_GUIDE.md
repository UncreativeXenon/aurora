# Modifying `.xzp` Theme Files for Aurora

## 📘 Overview

This guide provides step-by-step instructions for extracting, editing, and rebuilding `.xzp` files used by the **Aurora dashboard** on Xbox 360.

## 🔧 Requirements

- **Windows 7 or newer**  
  *(Running under Wine on Linux/macOS is untested and not officially supported.)*

- **Required Tools**:
  - **Xbox 360 SDK** — Cannot be directly linked, but can be found by searching:  
    `xbox 360 sdk 21256.3 site:archive.org`
  - **[XZP TOOL v2.0](https://digiex.net/threads/xzp-tool-v2-0-browse-edit-xbox-360-zxp-files.15990/)** — For extracting and rebuilding `.xzp` files
  - **[AuroraElements (XUI Extensions)](http://phoenix.xboxunity.net/downloads/AuroraElements%20(XUI%20Extensions).rar)** — Required to work with Aurora's extended XUI elements

## 📂 Extracting a `.xzp` File

1. Launch `XzpTool 2.exe`.
2. Click **Open**, then select your `.xzp` theme file.
3. Click **Extract** to unpack its contents.

### Common extracted file types:

- `.xur` — Aurora's UI layout and theme files
- `.png`, `.jpg`, `.dds` — Image assets used in the theme

## 🔍 Extracting `.xur` Files

1. Open **Xbox UI Authoring Tool** (`XuiTool.exe`), typically found at:  
   `C:\Program Files (x86)\Microsoft Xbox 360 SDK\bin\win32`
2. Go to **Tools > Options... > General**, then under **XML Extensions**, click **Change...**, followed by **Add...**.  
   Locate your `AuroraElements` folder, select `AuroraElements.xml`, and click **OK**. Restart the UI Tool afterward.
3. Open a `.xur` file via **File > Open**.  
   Most skin content resides in `Aurora_Skin.xur`, but elements like game titles and counts are stored in files such as `Aurora_Main.xur`.
4. With the `.xur` file open, go to **File > Save As**, and save it using the **same name but with a `.xui` extension**.  
   *(Note: `.xui` files are XML-based and easy to edit manually.)*

## 🛠 Editing `.xui` Files

1. Open the `.xui` file in any text editor or IDE (e.g., VSCode, Notepad++).
2. Look for ARGB color values — these begin with `0xff` followed by six hexadecimal digits (e.g., `0xffcad3f5`).  
   > ⚠️ These values are stored as **ARGB**, meaning the Alpha channel comes first, followed by Red, Green, and Blue.
3. Edit colors or other attributes as needed. Since `.xui` files lack visual references, try:
   - Searching for known hex color codes
   - Replacing multiple color values with a unique marker (e.g., `0xff123456`) for easier identification
   - Rebuilding and testing until you find the relevant element

## 📦 Rebuilding `.xur` Files from `.xui`

1. Open the modified `.xui` file in the **Xbox UI Authoring Tool**.
2. Go to **File > Export Binary**, and save the file with the same name, but with a `.xur` extension.

## 📁 Rebuilding the `.xzp` File

1. Launch `XzpTool 2.exe`.
2. Click **Open**, then select your original `.xzp` theme file.

### There are two methods for updating the archive:

#### ✅ Option 1: Drag & Drop

- Drag the modified files or folders into the Xzp Tool window.
- When prompted to overwrite existing files, click **Yes**.

#### ✅ Option 2: Manual Add

- Click **Add**:
  - **File to add** — Adds a file to the archive root
  - **Folder to add** — Adds an entire folder (e.g., `Images/`)
- Confirm replacements when prompted

## 🧪 Tips

- Always keep a **backup** of the original `.xzp` file.
- If the dashboard crashes or shows a black screen, use safe mode (if available) and restore the original file via FTP or USB.
- Use consistent file naming, and double-check for typos in `.xui` or `.xur` files.

## 📎 Credits & Resources

- [Phoenix for Aurora](http://phoenix.xboxunity.net/)
- [How to use XuiTool to mod/make Aurora themes. by S0DA – RealModScene.com (via archive.org)](https://web.archive.org/web/20250523185254/https://www.realmodscene.com/index.php?/topic/22763-how-to-use-xuitool-to-modmake-aurora-themes/)
- [XZP Tool v2.0 – Digiex](https://digiex.net/threads/xzp-tool-v2-0-browse-edit-xbox-360-zxp-files.15990/)
