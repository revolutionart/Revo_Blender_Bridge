# REVO Bridge Docs

User documentation for REVO Bridge, built with MkDocs (Read the Docs theme).

## Preview locally

```powershell
python -m pip install -r requirements.txt
python -m mkdocs serve --dev-addr 127.0.0.1:8000
```

The site live-reloads when you save a markdown file under `docs/`.

Open `http://127.0.0.1:8000` in a browser. Edit pages under `docs/` and save;
the preview refreshes automatically.

## Publish

```powershell
python -m mkdocs build
```

To publish with GitHub Pages after Pages is configured for the repository:

```powershell
python -m mkdocs gh-deploy
```

The addon source lives next to this folder in `REVO_Bridge`. Drop screenshots into `docs/assets/img/` and reference them from the matching page.
