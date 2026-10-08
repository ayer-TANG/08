# comic 分支 · 过程记录（可检查的版本记录）

- 记录时间：2026-10-08 21:01:00
- 仓库：https://github.com/ayer-TANG/08
- 分支：`comic`（上游 `origin/comic`）
- 版本标记：`q08-comic-v1`（annotated tag）→ bae7985
- 涉及文件：`skills/ppt-make.md`

## 一、这次做了什么

给 PPT 生成技能加了一条硬性要求：**生成 PPT 时必须加入热门卡通角色形象**，并把它接进流水线的执行与交付环节。

改动前该技能只要求"每一页都要有一个视觉元素"，对角色形象没有任何要求；改动后封面与结尾页必须有角色形象，正文页至少一半要有，且全套不少于 4 个不同角色。

## 二、分支与提交（均为实测命令输出）

### 2.1 提交图（`git log --graph --oneline --decorate --all`）

```
* 0065efa (HEAD -> comic, tag: q08-comic-v1, origin/comic) feat(skill): ppt-make 加入热门卡通角色硬性要求（3.3 节）
*   fd4bf57 (origin/main, origin/HEAD, main) merge: 将 feature/extract-skills-zip 合并回 main
|\  
| * dda7d09 (origin/feature/extract-skills-zip, feature/extract-skills-zip) feat: 解压 skills.zip，将 skills 内容作为源码纳入版本管理
|/  
* ab10cf9 Add files via upload
* 183f5be Initial commit
```

### 2.2 comic 相对 main 的提交（`git log main..q08-comic-v1`）

```
0065efa  2026-10-08 20:52  ayer-TANG  feat(skill): ppt-make 加入热门卡通角色硬性要求（3.3 节）
```

> 本文档自身是标签之后的又一次提交，所以不在上面的列表里；`git log --oneline main..comic` 会把它一并列出。

### 2.3 提交详情（`git show --stat q08-comic-v1`）

```
tag q08-comic-v1
Tagger: ayer-TANG <336701071+ayer-TANG@users.noreply.github.com>

Q08 comic 分支：ppt-make 技能加入热门卡通角色硬性要求（3.3 节）

覆盖规则：封面与结尾页必须有角色形象，正文页至少一半有，不允许连续两页空缺；全套至少 4 个不同角色。改动落在 skills/ppt-make.md，共 5 处。
commit 0065efaa7697ae5c8dd19a344de72f992514bfc2
Author: ayer-TANG <336701071+ayer-TANG@users.noreply.github.com>
Date:   2026-10-08 20:52:29 +0800

    feat(skill): ppt-make 加入热门卡通角色硬性要求（3.3 节）

 skills/ppt-make.md | 27 ++++++++++++++++++++++++++-
 1 file changed, 26 insertions(+), 1 deletion(-)
```

## 三、改动范围（`git diff --stat main..q08-comic-v1`）

```
 skills/ppt-make.md | 27 ++++++++++++++++++++++++++-
 1 file changed, 26 insertions(+), 1 deletion(-)
```

共 5 处改动，全部在 `skills/ppt-make.md`：

1. 新增 `### 3.3 卡通角色（硬性要求）`：覆盖规则（封面与结尾页必须有、正文页至少一半、不允许连续两页空缺）、至少 4 个不同角色、12 个角色的推荐池、取图与存放路径（`build\assets\<角色名>.png`，单张 ≤ 300 KB）、位置与尺寸（右下或左上，宽 3~4 cm，不压正文）、风格统一、情绪匹配、来源 URL 留痕、emoji 兜底
2. frontmatter `description`：补上"成稿还需按 3.3 节加入热门卡通角色形象"
3. 第 4 节（调用 pptx 技能）：要求交出角色素材清单并逐页放置
4. 5.4 交付：新增第 6 项，交付时列出角色清单与兜底页
5. 7 边界情况：新增"角色图片下载失败 / 找不到合适素材"的处理

同时写入两条纪律：角色只做装饰与情绪引导，不得为放角色删减或歪曲内容；结尾页加版权说明。

## 四、文件指纹（改动后）

| 文件 | SHA256 |
| --- | --- |
| `skills/ppt-make.md`（仓库副本，LF 归一化） | `B1A70E9115483DABA8FE7ADC8729BBB19CFB3F6E9E3D365F9633EB9B084F615D` |
| `D:\xuexi\.dsh\skills\ppt-make.md`（活动技能） | `B1A70E9115483DABA8FE7ADC8729BBB19CFB3F6E9E3D365F9633EB9B084F615D` |

两者一致 —— 活动技能已同步，新要求即时生效。

## 五、怎么自己检查

本地（在 `D:\xuexi\Q08_分支与安全提交\08仓库` 下）：

```bash
git log --oneline --graph --decorate --all
git show --stat q08-comic-v1
git diff main..comic -- skills/ppt-make.md
git ls-remote origin
```

GitHub 页面：

- 分支：https://github.com/ayer-TANG/08/tree/comic
- 与 main 对比：https://github.com/ayer-TANG/08/compare/main...comic
- 标签列表：https://github.com/ayer-TANG/08/tags

## 六、远端 ref 快照（`git ls-remote origin`）

```
fd4bf57e2977e76283713aad23b44eb4981a0301	HEAD
0065efaa7697ae5c8dd19a344de72f992514bfc2	refs/heads/comic
dda7d091258491ac57a597721c154f13697a6ae8	refs/heads/feature/extract-skills-zip
fd4bf57e2977e76283713aad23b44eb4981a0301	refs/heads/main
```

## 七、当前状态与未完成的部分

- `main` 仍停在 `fd4bf57`，**comic 尚未合并回 main**（Q08 第 5 步未执行）。要合并：
  ```bash
  git checkout main
  git merge --no-ff comic -m "merge: 将 comic 合并回 main"
  git push origin main
  ```
- `feature/extract-skills-zip` 仍保留在远端，作为上一阶段（把 `skills.zip` 解压成源码纳入版本管理）的记录。
- 生成本文档前的工作区状态：（干净，无未提交改动）