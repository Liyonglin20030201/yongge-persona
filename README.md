# 勇哥口吻 Codex Skill

这是一个 Codex skill，用于在用户明确要求时，以“勇哥”这一用户定义角色的支支吾吾、谦虚和回避式口吻回答问题。

## 发布到 GitHub

在本目录（包含 `SKILL.md` 的目录）打开 PowerShell，执行：

```powershell
git init
git add .
git commit -m "Add yongge persona skill"
git branch -M main
git remote add origin https://github.com/Liyonglin20030201/yongge-persona.git
git push -u origin main
```

先登录 GitHub 账号 `Liyonglin20030201`，在 GitHub 网页上创建一个空仓库 `yongge-persona`，不要预先添加 README、许可证或 .gitignore，然后执行上面的命令。

如果使用 GitHub CLI，则在完成 `git init`、`git add .`、`git commit` 和 `git branch -M main` 后，用下面的命令创建并推送仓库，替代上面的 `git remote add` 和 `git push`：

```powershell
gh repo create Liyonglin20030201/yongge-persona --public --source . --remote origin --push
```

## 安装

### Windows PowerShell

仓库发布后，运行以下命令安装。命令会优先使用 `CODEX_HOME`，没有设置时使用默认目录：

```powershell
$skillRoot = if ($env:CODEX_HOME) { Join-Path $env:CODEX_HOME 'skills' } else { Join-Path $env:USERPROFILE '.codex\skills' }
New-Item -ItemType Directory -Force -Path $skillRoot | Out-Null
git clone https://github.com/Liyonglin20030201/yongge-persona.git (Join-Path $skillRoot 'yongge-persona')
```

安装后重新打开 Codex 或新建对话，让它重新发现 skill。调用方式：

```text
$yongge-persona 请用勇哥口吻回答：周末一起吃饭吗？
```

也可以直接说“请用勇哥口吻回答下面的问题：……”，让 Codex 自动匹配这个 skill。

### 手动安装 ZIP

在 GitHub 仓库页面选择 **Code → Download ZIP**，解压后把包含 `SKILL.md` 的 `yongge-persona` 文件夹放到：

```text
%USERPROFILE%\.codex\skills\yongge-persona
```

如果设置了 `CODEX_HOME`，则放到 `%CODEX_HOME%\skills\yongge-persona`。不要多套一层目录；最终路径应直接包含 `SKILL.md`。

## 说明

其中关于冯玉洁的回答是角色扮演台词，不是现实关系的事实声明；需要事实核验时，应使用可靠来源而不是这个 skill。
