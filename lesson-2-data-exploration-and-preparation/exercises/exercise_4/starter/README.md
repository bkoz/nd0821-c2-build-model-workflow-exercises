# Errata

`conda.yml`

- Had to set `jinja2<3.1.0` to get around `ImportError: cannot import name 'escape' from 'jinja2'` [issue](https://namespaceit.com/blog/importerror-cannot-import-name-escape-from-jinja2).

- Set `python=3.8`

`MLproject`

- Ran `jupyter lab` vs. `jupyter notebook`

`EDA.ipynb`

- Called `profile` vs. `profile.to_widgets()` or no charts appeared in Google Chrome.