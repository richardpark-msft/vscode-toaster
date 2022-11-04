# Toaster

I created this extension because I was customizing Codespaces and devcontainers enough that
I really wanted to be able to use the information notification / toast APIs inside of VS Code
to display the output from a shell script or other process.

## Features

Any file placed in `~/.toasts/` or `%HOME%\.toasts` is considered a toast and will be
displayed as long as the extension is running and the file was created or updated in the
last minute.

The file is deleted after being shown and a `*.toasted` file is written with the outcome
in case your scrip is waiting to react to acknowledgement or navigation.

If the file is valid JSON, it can have additional properties:

- type: `information`, `warning`, `error`
- message: text to display
- ok: optional text to show on the no-op button other than 'OK'
- okUrl: optional URL to navigate to, being a mailto link, https link, or vscode link
- url: optional 2nd choice that is a web url to navigate to
- urlDisplayName: optional choice display to use for the 2nd url option, otherwise, includes the URL to navigate to

## Release Notes

### 1.0.1

- Corrects issue where toasted files are not deleted
- Adds support for a new "url" property and optional "urlDisplayName" property that allows for adding a URL for navigation as a second choice
- Adds a "okUrl" property that adds a URL navigation to the "OK" or choice display name
- "Toasts" files by placing the interpreted toast file in a `.toasted` file in `~/.toasts`:
  - Given a file `~/.toasts/hi.txt`, after the user responds to the toast, it will write `~/.toasts/hi.toasted` as a JSON file with details:
    - The toast file as interpreted
    - The iso8601 time the toast file was written
    - The iso8601 time the user made a choice
    - The choice they may
    - Any URL that was navigated to
- There is likely a timeout issue where if a user never acknowledges the toast that the app will hang waiting for the choice

### 1.0.0

First attempt at learning about extensions.

## NOTICE

The icon is "bread" from the Tabler Icons, licensed MIT, from https://tabler-icons.io/i/bread. Thanks Paweł Kuna!

```
MIT License

Copyright (c) 2020-2022 Paweł Kuna

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```
