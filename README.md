# VS Code LaTeX Report Template

Skeleton of a TU Delft-style report with a ready-to-go VS Code workspace, built on the [TU Delft Unofficial Report Template](https://github.com/dzwaneveld/TU-Delft-Unofficial-Report-Template) by Daan Zwaneveld (full template README below the rule).

## VS Code setup

### 1. Install a LaTeX distribution

LaTeX Workshop drives your system's LaTeX tools (`latexmk`, `pdflatex`/`xelatex`/`lualatex`, `biber`) — it does not bundle them, so one of these must be installed first. Full details: [LaTeX Workshop install wiki](https://github.com/James-Yu/LaTeX-Workshop/wiki/Install).

* **macOS** — [MacTeX](https://www.tug.org/mactex/): `brew install --cask mactex-no-gui` (smaller, no GUI apps) or `brew install --cask mactex` (full). Make sure `/Library/TeX/texbin` is on your `PATH` (a new terminal after install usually picks it up automatically).
* **Windows** — [MiKTeX](https://miktex.org/download) (installs packages on demand) or [TeX Live](https://www.tug.org/texlive/windows.html).
* **Linux** — TeX Live via your package manager, e.g. `sudo apt install texlive-full` (Debian/Ubuntu) or `sudo pacman -S texlive-most` (Arch). A minimal install may be missing packages this template needs (`biblatex`, `biber`, `parskip`, `FiraSans`, `pdfpages`, `easylist`, …) — prefer the "full"/"most" variant, or install missing packages as errors point to them.

Verify with `latexmk -v` and `biber --version` in a terminal.

### 2. Open the workspace

Open `report.code-workspace`. It configures:

* **LaTeX Workshop** — builds with `latexmk`, outputs to `build/`, opens the PDF in a tab with SyncTeX.
* **LTeX** — `en-GB` grammar/spell checking on save.
* Prose-friendly editor settings (font, line height, word wrap) scoped to `.tex` files.

`.vscode/extensions.json` recommends the two extensions above (`James-Yu.latex-workshop`, `valentjn.vscode-ltex`), so VS Code will prompt to install them the first time you open the workspace. That prompt only offers to *install* them — installed extensions are global to your VS Code, not scoped to this workspace. Per-workspace enable/disable is possible (right-click an extension → "Enable (Workspace)" / "Disable (Workspace)"), but that's a manual local choice stored in your VS Code state, not something this repo can ship or pre-configure.

`.vscode/keybindings.json` binds `alt+s` to `latex-workshop.synctex` (jump between `.tex` source and the built PDF) as a workspace-scoped keybinding, so it applies automatically when this workspace is open, without touching your global keybindings.

If biber breaks, clear its cache by running `rm -rf $(biber --cache)`.

### 3. Sync `report.bib` from Zotero

1. Install the [Better BibTeX](https://retorque.re/zotero-better-bibtex/) plugin for Zotero.
2. In Zotero, create or choose the collection you want exported (e.g. a "Report" collection, or a whole library).
3. Right-click the collection → **Export Collection** → format **Better BibLaTeX** (not plain BibTeX — this template uses `biblatex`/`biber`).
4. Check **"Keep updated"** in the export dialog. Zotero will then rewrite the file automatically whenever the collection changes.
5. Save it as `report.bib` directly in this repo, overwriting the placeholder.
6. In Better BibTeX preferences, pin a consistent citekey format so keys don't shuffle on every re-export.

---

# LaTeX x TU Delft - Report/Thesis Template

This template aims to simplify and improve the (Xe)LaTeX report/thesis template by Delft University of Technology with the following three main design principles:

* **Simplicity First:** A class file that has been reduced by nearly 70% to simplify customization;
* **Effortless:** A careful selection of common packages to get started immediately;
* **Complete:** Ready-to-go when it comes to the document and file structure.

This template works with _pdfLaTeX_, _XeLaTeX_ and _LuaLaTeX_. In order to adhere to the TU Delft house style, either _XeLaTeX_ or _LuaLaTeX_ is required, as it supports TrueType and OpenType fonts. _BibLaTeX_ is used for the bibliography with as backend _biber_. Please visit https://dzwaneveld.github.io/report/ for the full documentation.

## Documentation (Abridged)

As a report/thesis is generally a substantial document, the chapters and appendices have been separated into different files and folders for convenience. The folders are based on the three parts in the document: the frontmatter, mainmatter and appendix. All files are inserted in the main file, `report.tex`, using the `\input{filename}` command. The document class, which can be found in `tudelft-report.cls`, is based on the `book` class.

The template will automatically generate a cover when the `\makecover` command is used. The title, subtitle and author will also be present on the title page. To give greater flexibility over the title page, the layout is specified in `title-report.tex`.

The bibliography has been set up in `report.tex` to allow for easy customization. It is included in the table of contents and renamed to 'References' using the `heading=bibintoc` and `title=References` options of the `\printbibliography` command respectively. If you would like to use a different `.bib` file, change the command `\addbibresource{report.bib}` accordingly.

*-> Visit https://dzwaneveld.github.io/report/ for the full documentation.*

## License

The underlying [report/thesis template](https://github.com/dzwaneveld/TU-Delft-Unofficial-Report-Template) by Daan Zwaneveld is licensed under [CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/). No attribution is required in PDF outputs created using this template.
