# FridgeRX

FridgeRX helps older adults organize doctor and cancer treatment appointments and share the details with family members who may want to come along.

Upload a photo of an appointment note, review its transcription alongside close-ups of each detected line, and fill the appointment form from the corrected text. Appointment details can then be shared by email or the device sharing menu, or downloaded as a calendar event.

## Public website

Open **https://samlund2011.github.io/FridgeRX/**. No sign-in, installation, or local server is required.

The public version reads photos in the browser. It works best with printed text and neat block letters; handwriting accuracy differs from the macOS reader. Review results before using them. Appointments remain in the current browser.

## Run locally

Requires **macOS**, **Python 3**, and **Apple Command Line Tools** (including `swiftc`). The text reader uses Apple's Vision framework and does not run on Windows or Linux.

If the Command Line Tools are missing, install them with:

```sh
xcode-select --install
```

Start the app:

```sh
python3 FridgeRX.py
```

Open **http://127.0.0.1:8765/** if the browser does not open automatically. Keep the Python process running while using the app. Press Ctrl+C to stop it.

The first launch compiles a small Swift text reader. No third-party Python packages or API keys are required.

If port 8765 is in use, choose another port:

```sh
FRIDGERX_PORT=8766 python3 FridgeRX.py
```

## How to use it

1. Choose **Add appointment** and upload a clear photo of the note.
2. Compare the transcription with the highlighted image and individual line close-ups. Correct any mistakes or select an alternative reading.
3. Choose **Fill empty fields from this text**. The app recognizes labeled appointment information and patterns such as street addresses and visit reasons. Existing entries are preserved.
4. Review all fields and save the appointment.
5. Use **Share** to send the details, or **Calendar** to download an `.ics` file. Confirm company with your loved one, then mark it arranged.

## Technology

- **Python:** local HTTP server and image-upload endpoint.
- **Swift and Apple Vision:** on-device text recognition, with full-page and isolated-line passes.
- **HTML, CSS, and JavaScript:** responsive interface, editable transcription, field extraction, sharing, and calendar export.
- **Canvas:** photo previews, detected-text boxes, and line close-ups.
- **Browser localStorage:** appointments, attached photos, and family contacts on the current device.

## Files

- `FridgeRX.py` is the complete runnable app. It embeds the webpage and Swift reader in a single Python file.
- `FridgeRX.html` is the frontend source snapshot. Opening it directly displays the interface, but text recognition requires the running Python app.
- `TECHNOLOGY.txt` explains how the technologies are used.

## Current limits

Recognition can misread handwriting, dates, or addresses. Always compare the results with the original note. Field extraction uses rules and may miss unfamiliar phrasing. Uploaded photos must be under 4 MB.

Data is saved only in the current browser. There are no shared online accounts, server database, automatic family synchronization, or scheduled notifications. Sharing sends appointment text; attached note photos are not included automatically.

Photos are processed on the Mac. The interface loads fonts from Google Fonts when available. The server listens only on the local loopback address; this repository is source code, not a hosted multi-user service.

## Author

Samuel Lundberg
