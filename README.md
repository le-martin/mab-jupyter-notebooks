# jupyterhub-binder-template

**The following information was extracted from ["From Zero to Binder in Python!" by Sarah Gibson (The Alan Turing Institute)](https://github.com/alan-turing-institute/the-turing-way/blob/main/workshops/boost-research-reproducibility-binder/workshop-presentations/zero-to-binder-python.md) (21.01.2022) which belongs to [The Turing Way Community](https://github.com/alan-turing-institute/the-turing-way). This repo uses content of former mentioned repository and should provide a brief summary of required steps to run a Jupyter Notebook in a Git repository using [Binder](https://mybinder.org/).**

## Quick Instructions

Either use this repository as template or create a complete new repository following the rules below.

1. Create/upload your Jupyter Notebooks and a `requirements.txt` file containing the dependencies of your Jupyter Notebooks.
2. Visit [https://mybinder.org/](https://mybinder.org/) and type in your repository information.
3. The Binder URL leading to the Jupyter Notebook in Binder is generated and can then be copied.
4. (Optional) For [embedding a binder badge](#binder-badge) in the `README.md`, [linking a certain Jupyter Notebook](#direct-link-to-jupyter-notebook) or [using custom public data](#add-data-to-your-binder), see below.

## Binder Badge
[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/mle313/jupyterhub-binder-template/main?labpath=test.ipynb) (Binder badge for `test.ipnyb` Jupyter notebook)

### How to add a binder badge to your README.md
1. Type in the URL of your Git repository on the [Binder webpage](https://mybinder.org/).
2. Expend the the last toggle element in the gray box (**Expand to see the text below, paste it into your README to show a binder badge:**).
3. Copy the Markdown or ReStructeured text snippet into your `README.md`.

It should have the following format (Replace `<SOME VARIABLE>` with your data):
- Markdown
```
[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/<GIT USER>/<REPOSITORY>/HEAD)
```
- ReStructured Text
```
.. image:: https://mybinder.org/badge_logo.svg
 :target: https://mybinder.org/v2/gh/<GIT USER>/<REPOSITORY>/HEAD
```

### Direct Link to Jupyter Notebook
In order to link a certain Jupyter Notebook adjust the above link to the following format:
 
`https://mybinder.org/v2/gh/<GIT USER>/<REPOSITORY>/HEAD?labpath=<JUPYTER NOTEBOOK NAME>`
 
Example: [https://mybinder.org/v2/gh/mle313/jupyterhub-binder-template/HEAD?labpath=test.ipynb](https://mybinder.org/v2/gh/mle313/jupyterhub-binder-template/HEAD?labpath=test.ipynb)

## Add data to your Binder

### Small size data (up to 10 MB)
- Add directly to your repository

### Middle size data (between 10 MB and 100 MB)
- Add a `postBuild` script/file  to your repo
- `postBuild` script can include middle size data into your image
- See [Binder's `postBuild` example](https://mybinder.readthedocs.io/en/latest/using/config_files.html#postbuild-run-code-after-installing-the-environment) for more uses of the `postBuild` script.

Example [`postBuild`](https://github.com/mle313/jupyterhub-binder-template/blob/main/postBuild) for downloading data from the internet and add them to your repo image created by Binder:
```bash
wget -q -O gapminder.csv http://bit.ly/2uh4s3g
```

### Large size data
- Use a library specific to the data format to stream the data as you're using it or to download it on demand as part of your code
- For security reasons, the outgoing traffic of your Binder is restricted to HTTP or GitHub connections only. You will not be able to use FTP sites to fetch data on mybinder.org

_Note: Only public data can be shared here. In order to share private data, the local deployment of [BinderHub](https://binderhub.readthedocs.io/en/latest/) is required. This is not part of this manual._

## Example Binder repositories:
To find more examples and other Binder repositories with various cool user interfaces, check this [link](https://mybinder.readthedocs.io/en/latest/examples/sample_repos.html).

---

<a rel="license" href="http://creativecommons.org/licenses/by/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by/4.0/88x31.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by/4.0/">Creative Commons Attribution 4.0 International License</a>.
