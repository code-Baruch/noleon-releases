# Noleon

**A local-first workspace for developers on Windows.** Search your code by meaning, check whether a project builds, and keep your projects, notes and alarms in one place. It runs on your PC. No account, no cloud AI, free.

> **Status: v0.1.0 beta.** It works, and it has rough edges. Feedback is the point of this release.

**[Download the latest version](https://github.com/code-Baruch/noleon-releases/releases/latest)** (Windows 10 1809+ or Windows 11, 64-bit, about 78 MB)

<img src="https://github.com/user-attachments/assets/048df844-ca37-48ec-b286-90ac94865882" alt="Software Screenshot" width="100%" />
<img src="https://github.com/user-attachments/assets/e678104a-114e-4976-be8d-4cd1cf6f" alt="Demo GIF" width="100%" />
<img src="https://github.com/user-attachments/assets/bbf54c83-4025-4a84-a9ef-ae9c367a69c6" alt="Chat Screenshot" width="100%" />

## Why it exists

Finding the right file in a project you half remember is slow. Plain-text search needs the exact word, and cloud tools want your code on someone else's server. Noleon indexes your folders on your own machine and answers in plain language, so "where do we hash files" finds the function even when no file says "hash files".

## What it does

**Search your projects' code.**
Attach a folder to a project and ask in plain language. Results are ranked two ways at once, by meaning (a small embedding model) and by words (it understands `checkFilePermissions` and `check_file_permissions` as "check file permissions"), then merged. You get the file and the exact line.
- Word search works within seconds of opening a project. Meaning-based ranking fills in behind it, in the background.
- On our own test (30 questions on a 124-file project), the right file was in the top 5 results 97% of the time and first 73% of the time. That is a small test on our own code, so treat it as a rough guide, not a promise.

**Check if it runs.**
One button opens the project in VS Code and checks it for errors: `cargo check` for Rust, your `typecheck` script or `tsc` for Node and TypeScript, a syntax pass for Python. It lists each error with file and line. It checks; it doesn't start your program.

**Find files by meaning.**
Noleon learns your Documents, Downloads, Desktop and project folders in the background and finds files by what they are about, not only by name. Code and text files are read first. PDFs, Word, PowerPoint and e-books are found by name by default; you can turn on reading inside them in Settings (slower).

**Projects, notes, alarms.**
Projects with tasks, notes, attached files and folders, a deadline, and a work timer with target hours. Alarms linked to a project. You can open the project straight from the alarm.

**Open apps by asking.** "open notepad".

**Chat (optional).**
Noleon ships no language model, which keeps the download small. If you want to chat, install [Ollama](https://ollama.com), pull any model, and pick it under Settings → AI model. Chat talks only to Ollama on your own computer. Everything above works without it.

## Privacy, plainly

- Your files, chats, notes and projects stay on your computer.
- The search index is on your computer. The search model is built in, so Noleon works offline.
- Two things use the internet: **feedback you choose to send**, and **a small anonymous usage ping** (a random install ID, the app version, and the date). The ping is always on and can't be switched off inside the app. It never contains file names, folders or chats. You can block Noleon in Windows Firewall and everything else keeps working.
- Noleon doesn't edit, move or delete your existing files.

The full notice is shown during install and in the app under About.

## Install

1. Download `Noleon-setup-v0.1.0.exe` from the [latest release](https://github.com/code-Baruch/noleon-releases/releases/latest).
2. Run it. It installs for your user and doesn't need admin rights.
3. **Windows SmartScreen may warn you.** This beta isn't code-signed yet. Click *More info*, then *Run anyway*.
4. To check the download is genuine, compare its hash with the SHA-256 on the release page:
   ```powershell
   Get-FileHash .\Noleon-setup-v0.1.0.exe
   ```

The first launch starts learning your files about 20 seconds after it opens, quietly in the background, with a progress bar. You can use Noleon right away.

## Known limits (beta)

- Windows only, 10 (version 1809 or newer) and 11, 64-bit. If it won't start, run Windows Update first.
- Not code-signed yet, so SmartScreen warns.
- The first index of a large project can take a while to finish its meaning-based ranking (word search works immediately). It speeds up when you aren't using the PC.
- Chat is whatever model you choose; small models can be wrong, and none of them browse the web.
- Very large PDFs are read by their opening pages only, and only if you turn on document reading.
- Closed beta software: it can have bugs and may change.

## Feedback

Use **Send Feedback** inside the app, the fastest way to tell us what broke. You can also [open an issue](https://github.com/code-Baruch/noleon-releases/issues) or write to **noleon.contact@gmail.com**.

The most useful things to tell us: did it install cleanly, did search find what you looked for (and what it missed), and how slow was the first scan on your project.

## About

Noleon is made by one person and is meant to become a small company. The source code is not public at this time. The installer is free to use under its license, shown during install.
