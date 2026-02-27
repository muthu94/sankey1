ignoreIntegrity: true is correct for development/re-upload — once you finalize hosting, you should compute the SHA-256 hash of each JS file and fill in the integrity field, then set ignoreIntegrity: false

⚠️ Action needed after upload: If you want integrity checking enabled for production, generate the hash like this:
bashcat main.js | openssl dgst -sha256 -binary | openssl base64 -A
# Then format as: "sha256-<value>"
