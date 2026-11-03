# OkuRead privacy

OkuRead captures screen pixels and recognizes text locally to make that text
available through Windows accessibility and optional visual replacement.

- Captured screen images and recognized text stay on the computer.
- The application runtime has no network download, telemetry or upload path.
- Captured images, recognized text and product logs are not saved by default.
- Setup uses the network to download pinned OCR models. It checks their sizes
  and SHA-256 hashes and prepares device-specific engines locally. Setup does
  not capture the screen or start OCR.
- Optional screenshot testing is an explicit diagnostic mode. It makes OkuRead's
  own windows capturable and indicates that state visibly. It saves nothing
  itself. Capture exclusion is re-established before a new OCR request.
- Start with Windows is off by default. When enabled, sign-in startup stays in
  the tray with models on disk until the user starts a read.

Application preferences, installed models and locally prepared engines are
stored in the current user's application-data folders. Do not include private
screen content in a public issue unless you intend to share it.
