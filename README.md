# 08
第八题

## 仓库内容

`skills.zip` 已解压为 `skills/`，作为源码纳入版本管理：

| 路径 | 说明 |
| --- | --- |
| `skills/ppt-make.md` | PPT 制作 Skill 说明 |
| `skills/pptx/` | pptx Skill：`SKILL.md`、生成脚本、OOXML schema 与校验器 |
| `skills/weekly-learning-summary.md` | 每周学习总结 Skill |

- 压缩包指纹：`git hash-object skills.zip` = `310a0821b6556c41ac3bb57e64eaae2e6f33e7e4`
- `__pycache__/` 与 `*.pyc` 已由 `.gitignore` 排除：本机运行脚本产生的编译缓存，不属于源码

## 分支

- `main`：稳定版本
- `feature/extract-skills-zip`：本次解压压缩包的功能分支，已合并回 `main`