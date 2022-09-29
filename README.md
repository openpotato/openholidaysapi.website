# OpenHolidays API Documentation

This is the documentation for the OpenHolidays API project. The documentation is Open Source and we have implemented it using [MkDocs](https://www.mkdocs.org) and [Material for MkDocs](https://squidfunk.github.io/mkdocs-material). 

## Install MkDocs for Windows

1. Install [Python](https://www.python.org). Go to the [Python downloads](https://www.python.org/downloads/) page and download the latest version for Windows. 

2. Launch the installer and follow the on-screen instructions.

3. Run the command prompt as Administrator.

4. Enter the command `python --version` and `pip --version` to check the Python installation. In both cases a version number should appear as an output in the command prompt.

5. Enter the command `pip install mkdocs mkdocs-material mkdocs-minify-plugin` to install the *MkDocs* Python package, the *Material for MkDocs* theme and the MkDocs plugin [Minify](https://github.com/byrnereese/mkdocs-minify-plugin).

6. Final test: Enter the command `mkdocs --version`. A version nummer in the command prompt will let you know if everything has been installed correctly.

## Clone Repository

This repository is a Git repository. To clone the repository to a local commputer you will need a Git client. Either install [Git for Windows](https://gitforwindows.org/) and use the command prompt or install one of the many GUIs. We recommend [GitHub Desktop](https://desktop.github.com) or [SourceTree](https://www.sourcetreeapp.com).

1. Create a local directory for the documentation e.g. `c:\openholidaysapi`.

2. Open the command prompt and change to directory `c:\openholidaysapi`.

3. Enter the command `git clone https://github.com/openpotato/openholidaysapi.website.git` to clone the repository.

## Download Repository as Zip Archive

If you don't want to use Git you can even download the repository as a Zip Archive:

1. Open the URL `https://github.com/openpotato/openholidaysapi.website` in your web browser

2. Click on the `Clone or download` button then select `Download ZIP`.

3. Extract the Zip Archive to a local folder, e.g. `c:\openholidaysapi`.

##  Using MkDocs

You have installed Python and MkDocs, cloned the repository or downloaded it as a Zip Archive. Now you can generate the documentation locally on your computer.

1. Start the command prompt and change to the directory `c:\openholidaysapi\de` for German documentation or `c:\openholidaysapi\en` for the English documentation.

2. Enter the command `mkdocs build`. The documentation will be regenerated.

3. To display the result, enter the command `mkdocs serve` and open the URL `http://127.0.0.1:8000` in your Web browser.

The table of contents can be found in the `mkdocs.yml` file and the individual chapters are in the `docs` subdirectory. 

## Can I help?

Yes, that would be much appreciated. The best way to help is to post a response via the Issue Tracker and/or submit corrections via a Pull Request.