# Download Gzip Artifact

This is a simple action to download an artifact and unpacks it with ``tar``.
Use [Upload Gzip Artifact](https://github.com/nmerget/upload-gzip-artifact) to upload an artifact with gzip compression.


## How to use

`````yaml
---
name: Deploy to gh-pages

on:
  push:
    branches:
      - "main"

jobs:
  deploy:
    name: Deploy
    runs-on: ubuntu-latest
    steps:
      - name: ⏬ Checkout repo
        uses: actions/checkout@v3

      - name: ⏬ Download build
        uses: nmerget/download-gzip-artifact@main
        with:
          name: frontend-build
          path: dist

      - name: 🥅 Deploy to GH-Pages
        uses: peaceiris/actions-gh-pages@v3
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./dist

`````

## Configuration

````yaml
...
- name: ⏫ Upload build
  uses: nmerget/download-tar-artifact@main
  with:
    name: frontend-build # use the name of the uploaded artifact
    path: dist # your directory to unpack to
...
````

