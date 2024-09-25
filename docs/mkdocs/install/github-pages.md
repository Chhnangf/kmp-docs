# GitHub Pages
----

## [托管](https://chhnangf.github.io/kmp-docs/)

部署项目到[GitHub Pages](https://docs.github.com/en/pages/getting-started-with-github-pages/creating-a-github-pages-site)

在GitHub中创建一个**Public**仓库

将项目推送到仓库中

```
git checkout --orphan gh-pages
git rm -rf .
cp -a ../docs/site/. .
git add .
git commit -m "Update GitHub Pages"
git push origin gh-pages
git checkout -
```

或者使用简化的指令

```
mkdocs gh-deploy --force
```

效果同上

根据实际地址修改path和url

在仓库主干根目录中创建一个`.github/workflows`目录及`github-actions-demo.yml`工作流文件

```
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
          path: .cache
          restore-keys: |
            mkdocs-material-
      - run: pip install mkdocs-material 
      - run: mkdocs gh-deploy --force
```

执行Actions


表示托管成功，通过浏览器访问