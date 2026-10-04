# HTTPS Interception Guides

Step-by-step guides for intercepting, inspecting and replaying HTTP/HTTPS traffic using **Charles Proxy**, **Burp Suite**, **Caido** and **PowHTTP**.

Built from my day-to-day work in web scraping and automation where understanding what a client really sends to a server is the first step of everything else.

> ⚠️ **Use responsibly.** These guides are for testing your own applications, or sites and apps you have explicit permission to test. Always respect applicable laws and terms of service.

## Contents

| Tool | What's covered | Guide |
|------|----------------|-------|
| Charles Proxy | Setup, SSL proxying, mobile device config, rewrite/map rules | [charles](./charles.md) |
| Burp Suite | Proxy config, certificate install, Repeater, Intruder basics | [burp](./burp.md) |
| Caido | Setup, project workflow, replay, automate | [caido](./caido.md) |
| PowHTTP | Setup, capturing requests, inspecting TLS/HTTP details | [powhttp](./powhttp.md) |

## Common topics

- Installing and trusting the proxy's CA certificate (desktop, Android, iOS)
- Configuring system and per-app proxy settings
- Handling SSL pinning and what to do when traffic won't show up
- Filtering noise and finding the one request that matters
- Replaying and modifying requests
- Exporting requests to code (cURL, Python `requests`, etc.)

## Repository structure

```
.
├── charles/
├── burp/
├── caido/
├── powhttp/
└── README.md
```

## Before you commit

Exported captures (`.har`, `.chls`, `.burp`, …) often contain cookies, API keys, and personal data. **Scrub or avoid committing them.** The `.gitignore` already blocks the common formats.

## Contributing

Spotted an error or want to add another tool (mitmproxy, Fiddler, HTTP Toolkit…)? Open an issue or PR.

## License

[MIT](./LICENSE)

## Author

**Priyanka Rajput**: [GitHub](https://github.com/rajputpriyankaa)
