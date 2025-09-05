# Deployment

## 1️⃣ **mkdocs gh-deploy**

```bash
mkdocs gh-deploy
```

```bash
mkdocs gh-deploy --force
```


```bash title="Terminal Ouput" linenums="1" hl_lines="3-4 11-12"
(myvenv) Tiffany@MacBookPro PyConTW2025 % mkdocs gh-deploy
INFO    -  Cleaning site directory
INFO    -  Building documentation to directory:
           /Users/Tiffany/Desktop/PyConTW2025/site
INFO    -  The following pages exist in the docs directory, but are not included
           in the "nav" configuration:
             - autodocs.md
             - deploy.md
INFO    -  Documentation built in 0.19 seconds
WARNING -  Version check skipped: No version specified in previous deployment.
INFO    -  Copying '/Users/Tiffany/Desktop/PyConTW2025/site' to 'gh-pages'
           branch and pushing to GitHub.
Enumerating objects: 75, done.
Counting objects: 100% (75/75), done.
Delta compression using up to 8 threads
Compressing objects: 100% (63/63), done.
Writing objects: 100% (75/75), 585.79 KiB | 6.58 MiB/s, done.
Total 75 (delta 12), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (12/12), done.
remote: 
remote: Create a pull request for 'gh-pages' on GitHub by visiting:
remote:      https://github.com/AllergicAlligator/PyConTW2025/pull/new/gh-pages
remote: 
To https://github.com/AllergicAlligator/PyConTW2025.git
 * [new branch]      gh-pages -> gh-pages
INFO    -  Your documentation should shortly be available at:
           https://AllergicAlligator.github.io/PyConTW2025/
(myvenv) Tiffany@MacBookPro PyConTW2025 % 
```

## 2️⃣ **github actions**


`.github/workflows/ci.yaml`

```yaml
name: ci 
on:
  push:
    branches:
      - master 
      - main
permissions:
  contents: write
jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Configure Git Credentials
        run: |
          git config user.name github-actions[bot]
          git config user.email 41898282+github-actions[bot]@users.noreply.github.com
      - uses: actions/setup-python@v5
        with:
          python-version: 3.x
      - run: echo "cache_id=$(date --utc '+%V')" >> $GITHUB_ENV 
      - uses: actions/cache@v4
        with:
          key: mkdocs-material-${{ env.cache_id }}
          path: ~/.cache 
          restore-keys: |
            mkdocs-material-
      - run: pip install mkdocs-material 
      - run: mkdocs gh-deploy --force
```

## References

* [Material for MkDocs Documentation](https://squidfunk.github.io/mkdocs-material/publishing-your-site/)