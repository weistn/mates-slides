# mates-slides
MaTeS bundle for slide decks

## Compile the example

To use mates slides, you must install [MaTeS](https://github.com/weistn/mates).
Make sure that the `mates` binary is in your path.

Enter the `example` directory.
It containse a `site.yaml` file that references the slides bundle.
MaTeS must know the path where the bundle can be found.
The easiest way is to pass it on the command line.
Alternatively, you can set the `MATESPATH` environment variable.

```bash
cd example
mates -path ../../ .
```

This will build the site in the current directory (e.g. `.`) and search for bundles in `../../`.
The output can be found in the `public` directory.
The resulting files can be copied to any web server.
To test locally, use `python` to serve the static web pages

```bash
python -m SimpleHTTPServer 8000
```

and open `http://localhost:8000` in your browser.

# Reveal.js

This bundle includes the distribution files from [reveal.js](https://revealjs.com/) for convenience.