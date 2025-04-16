# 🪖 rallypoint.py

**Because even your files need a rendezvous point.**

This script is a utility tool that moves all files found within subdirectories of a specified directory **back** to that main directory. Born from chaos, this tool fixes the aftermath of accidentally recursive scripts that put every damn file into its own folder. Whoops. 😅

---

## 📦 What It Does
- Recursively traverses all folders within your target directory
- Moves all discovered files back to the root directory
- Ignores already-rooted files and tries not to yeet your system into the void

---

## 📂 Example Use Case
You accidentally ran a script that moved each file into its own folder... now you've got a thousand folders with one file each. This script will rally your files back to base like a digital evac team.

---

## ⚙️ How To Use
```python
main_directory = r"C:\Users\Whiskey\Downloads\FilesInFolders"
```
Set `main_directory` to the directory where all your nested files are.

Then run the script:
```bash
python rallypoint.py
```

---

## 📋 Output
Each file moved is printed to the console:
```
Moved report_23.pdf to C:\Users\Whiskey\Downloads\FilesInFolders
Moved meme_001.jpg to C:\Users\Whiskey\Downloads\FilesInFolders
```

---

## 🚨 Warnings
- Overwrites can happen if files with the same name exist in different subfolders. (Script does **not** currently handle filename collisions.)
- Does not delete empty folders after moving files (so your clutter is at least hollow now).

---

## 💡 Pro Tips
- Run this after a folder explosion disaster.
- Combine with `os.rmdir()` if you want it to delete the empty folders after.

---

## ✨ Inspiration
This exists purely because Whiskey ran a chaos script that recursively exploded a file archive into a thousand micro-folders.

Like a rally point in a military op, this script calls all your files home.

---

## 🧠 Author
**Whiskey** — Creator of chaos, savior of digital sanity.

> "Not all who wander are lost. Unless they were files. Then they probably are."

---

## 💻 Code
```python
import os
import shutil

# Specify the main directory where you want to move the files
main_directory = r"C:\Users\User\Downloads\FilesInFolders"

# Loop through all subdirectories in the main directory
for root, _, files in os.walk(main_directory):
    for file in files:
        # Get the full path of the file
        file_path = os.path.join(root, file)

        # Check if it's not the main directory itself
        if file_path != main_directory:
            try:
                # Move the file to the main directory
                shutil.move(file_path, main_directory)
                print(f"Moved {file} to {main_directory}")
            except Exception as e:
                print(f"Error moving {file}: {str(e)}")
```

