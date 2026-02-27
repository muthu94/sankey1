ignoreIntegrity: true is correct for development/re-upload — once you finalize hosting, you should compute the SHA-256 hash of each JS file and fill in the integrity field, then set ignoreIntegrity: false

⚠️ Action needed after upload: If you want integrity checking enabled for production, generate the hash like this:
bashcat main.js | openssl dgst -sha256 -binary | openssl base64 -A
# Then format as: "sha256-<value>"


{
  "kind": "main",
  "tag": "com-sap-sac-sample-echarts-sankeyyg",
  "url": "/main.js",
  "integrity": "sha256-HAHlBWe9J7FN0Zr5lPbBAkNpepQN3v4XXtmHgE2JOdY=",
  "ignoreIntegrity": false   ← now SAC WILL verify the hash
},
{
  "kind": "styling",
  "tag": "com-sap-sac-sample-echarts-sankeyyg-styling",
  "url": "/sankeyChartStyling.js",
  "integrity": "sha256-AR0uDO+9h8nu9EyJotSinZ2APDWD5Ja2JmdFcZCH1Xo=",
  "ignoreIntegrity": false
}
