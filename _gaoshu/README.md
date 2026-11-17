# 高等数学复习笔记的 Hugo 源码

GitHub Pages 从 `main` 分支根目录发布静态文件。`_gaoshu/content/` 是笔记源码，构建后的网页位于 `gaoshu/`。旧站首页和「学习」页各有一个入口。

使用 Hugo **0.139.3 Extended** 和固定版本的 **Hugo Book**。在仓库根目录运行以下命令，把输出放到临时目录检查。

```sh
build_dir=$(mktemp -d)
git clone https://github.com/alex-shpak/hugo-book.git "$build_dir/themes/hugo-book"
git -C "$build_dir/themes/hugo-book" checkout --detach 645c868cec1396548456eac68205eabbd8ca9564
hugo --source _gaoshu --themesDir "$build_dir/themes" --destination "$build_dir/gaoshu" --panicOnWarning
```

更新笔记时，编辑 `content/`，用相同命令构建。检查输出后，将 `gaoshu/` 更新为新版本，连同源码提交到 `main`。GitHub Pages 会在推送后部署。行内公式使用 `$…$`。独立公式使用 `$$…$$`，前后各留一个空行。Hugo 在构建时渲染公式。
