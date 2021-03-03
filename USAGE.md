[bump2version](https://github.com/c4urself/bump2version) 是一个辅助修改版本号的命令行工具：
1. 按自定策略升级版本号，比如 1.8.0 → 1.8.1
2. 将散布在项目各处文件里的老版本号，同步修改为新版本号。比如 Makefile, install.sh, README.md, USAGE.md, config.yaml, setup.py, init.py
3. 可选：使用新版本号打 git tag，提交 git 记录："Bump version: 1.8.0 → 1.8.1"

## 用法演示

```sh
$ bump2version alpha
1.8.0-alpha.39

$ bump2version alpha
1.8.0-alpha.40

$ bump2version alpha
1.8.0-alpha.41

$ bump2version alpha
1.8.0-alpha.42

$ bump2version --new-version 1.8.0 patch
1.8.0

$ bump2version patch
1.8.1

$ bump2version patch
1.8.2

$ bump2version minor
1.9.0

$ bump2version minor
1.10.0

$ bump2version major
2.0.0

$ bump2version patch
2.0.1

$ bump2version --new-version 2.1.0-alpha.1 alpha
2.1.0-alpha.1

$ bump2version alpha
2.1.0-alpha.2

$ bump2version alpha
2.1.0-alpha.3

$ bump2version alpha
2.1.0-alpha.4
```

## 附录
上面演示中使用的 .bumpversion.cfg 配置：

```ini
[bumpversion]
current_version = 2.0.0
parse = (?P<major>\d+)\.(?P<minor>\d+)\.(?P<patch>\d+)(-alpha\.(?P<alpha>\d+))?
serialize = 
	{major}.{minor}.{patch}-alpha.{alpha}
	{major}.{minor}.{patch}
commit = True
tag = True

[bumpversion:file:Makefile]

[bumpversion:file:README.md]
```

