# Paper to Ledger OCR for Windows

An offline Windows app for importing invoice and receipt photos or PDFs, reading text with local OCR, correcting it, and copying it into SQL Account. This is a separate, fresh PC version. The earlier `gpt.site` app remains unchanged and its documents are not transferred here.

## Install and use

1. Run `Paper-to-Ledger-OCR-Setup-1.0.0-x64.exe` on a Windows 10/11 x64 PC. This first test build is unsigned, so Windows may show a SmartScreen warning. Only run an installer received from a source you trust.
2. Open **Paper to Ledger OCR** from the Start menu. On first launch, choose the suggested `Paper to Ledger Data` folder under your Windows user folder or select another local folder. Avoid a cloud-synced location if the client documents must stay only on the PC.
3. Select **Import files** to add several photos or PDFs, or **Open storage folder** and copy files into it. Files in the chosen folder and its one-level category folders appear automatically. Restarting or refocusing the app rescans the folder as well.
4. Select a document, press **Read text**, compare the result with the large original image, correct errors, and copy the text into SQL Account. PDF OCR supports up to 20 pages. The app works without an AI API or internet connection.
5. Use **Back up** to choose a separate drive or folder. The backup copies originals and a consistent snapshot of the OCR database. Protect that destination too, because the backup is not encrypted by the app.

Original photos and PDFs remain ordinary files. OCR corrections are in `.paper-to-ledger/catalog.sqlite` inside the chosen storage folder. Renaming and moving files within the app changes the real files. Adding, renaming, or deleting files in File Explorer is reflected after a rescan. The app accepts JPEG, PNG, WebP, and PDF files under 100 MB. OCR is not guaranteed correct; check amounts and names against the original.

## Privacy and removal

The desktop app does not open a network port or upload documents to `gpt.site` or an AI provider. It runs under the current Windows user account. Protect that account with a password and enable Windows device encryption or BitLocker when available. Files placed in a OneDrive or other synced folder may be uploaded by that sync service.

The downloaded installer can be deleted after installation. To remove the program, use **Windows Settings → Apps → Installed apps → Paper to Ledger OCR → Uninstall**. The uninstaller removes the program, shortcuts, and app settings but deliberately leaves the chosen storage folder and backups. To remove all client data, confirm backups and then delete that storage folder separately.

## Development

Requirements: Node.js 24 and pnpm 11. Run `pnpm install`, then `pnpm install:electron` if the Electron binary was not downloaded automatically. Run `pnpm check`, `pnpm test`, and `pnpm build`. `pnpm desktop` opens the built app. `pnpm installer` builds the unsigned NSIS installer under `release/`.
