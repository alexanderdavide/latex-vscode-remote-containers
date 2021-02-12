# LaTeX VSCode Remote Containers [![build status](https://github.com/alexanderdavide/latex-vscode-remote-containers/workflows/latex-build/badge.svg)](https://github.com/alexanderdavide/latex-vscode-remote-containers/actions)

## Prerequisites

1. Install [VSCode](https://code.visualstudio.com/)
2. Install the VSCode [Remote Development plugin](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.vscode-remote-extensionpack)
3. Install [Docker](https://www.docker.com) and [Docker Compose](https://docs.docker.com/compose/)

## Starting

1. Clone this repository
2. Open the folder in VSCode
3. Execute 'Remote-Containers: Reopen in Container' from the VSCode command palette
4. VSCode automatically downloads the dependencies and starts up the LaTeX container.
5. You will be left with a VSCode window to write your LaTeX project in. Every integrated terminal is running inside the LaTeX container.

## Shutdown

Simply close VSCode.

## Things to know

* This project relies on [tianon/latex](https://hub.docker.com/r/tianon/latex/) and [LaTeX Workshop](https://marketplace.visualstudio.com/items?itemName=James-Yu.latex-workshop).
* Put your LaTeX files in `/workspace` just as the `main.tex`.
* Once you save a `.tex` file, it will automatically be built with [Latexmk](https://mg.readthedocs.io/latexmk.html) which seamlessly integrates BibTeX bibliography in the compilation.
* The GitHub Action `latex-build` runs on each push to build your project with [Latexmk](https://mg.readthedocs.io/latexmk.html) and upload the PDF as an artifact of the run. If you don't want to use the action, it is safe to delete the `.github` folder. You may need to adapt the `latex-build.env` section to fit your requirements.
    * `LATEX_FILE_PATH`: path of the used LaTeX file, relative to `/workspace`
    * `OUTPUT_DIR_PATH`: path of the output directory, relative to `/workspace`
    * `OUTPUT_BASE_FILENAME`: name of the created artifact archive and containing PDF file
