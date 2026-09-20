# manuscript-preflight · 社科论文交导师前检查

面向社会科学、心理学、管理学中英文科研论文的 Codex skill。中文默认按《心理学报》，英文默认按 APA 7；可在每次检查时指定其他期刊或导师要求。

默认保留原稿，输出逐处问题、修改建议、判断依据和覆盖范围。适合交导师前校对及修改后复查。

## 检查内容

| 范围 | 主要检查 |
| --- | --- |
| 文字与大小写 | 拼写、重字漏字、语法性 typo、句首/标题大小写、专名与作者姓名、缩写、标点和空格。 |
| 文内引用 | 作者拼写、年份、a/b 后缀、et al./等、作者人数、复合姓、同名消歧和引语定位。 |
| 参考文献 | 全文双向对应、缺项、未引用条目、重复、中文双语配对、题名/刊名大小写、出版信息及 DOI/URL 疑点。 |
| 全文一致性 | 构念和变量名、样本量、统计符号、结果方向、研究/假设编号、图表与附录指向。 |
| 文档与图像 | 可读的表格、脚注、文本框、图中文字、修订批注及可见格式，明确记录无法读取或核实的部分。 |

支持 DOCX、PDF、Markdown、纯文本和 LaTeX（可附 `.bib` 与章节文件）。实际提取、OCR、渲染和联网能力取决于运行 skill 的环境；本仓库不捆绑文档解析器或第三方运行时。

## 安装

在有 `skill-installer` 的 Codex 环境中，发送：

```text
使用 $skill-installer 安装 https://github.com/YangQiu1221/manuscript-preflight 根目录的 skill，名称为 manuscript-preflight。
```

也可以在 GitHub 点击 **Code → Download ZIP**，解压后把包含 `SKILL.md`、`agents/` 和 `references/` 的文件夹命名为 `manuscript-preflight`，放到当前环境使用的个人技能目录。当前官方文档列出的用户目录是 `~/.agents/skills/`，Windows 对应 `%USERPROFILE%\.agents\skills\`；如果环境已经配置其他技能目录，沿用其配置。安装后应存在 `manuscript-preflight/SKILL.md`，不要再额外嵌套一层同名文件夹。

如果新技能没有出现，重启 Codex 后再调用。安装与发现方式参见 [OpenAI 官方技能文档](https://developers.openai.com/zh-Hans/docs/build-skills)。

## 使用

附上论文文件，或提供当前环境可读取的路径，然后发送：

```text
使用 $manuscript-preflight 对这篇论文做交导师前的完整检查。
中文按《心理学报》，英文按 APA 7。
逐处列出错误位置、原文、建议改法和依据，完成文内引用与参考文献双向核对。
保留原稿，区分确定错误与待核实项，并说明实际检查范围。
```

默认完整检查稿内引用关系，对书目信息疑点及拟更正字段进行必要的外部核验。需要逐条联网核验全部参考文献时，加上：

```text
逐条核验所有参考文献的公开书目信息，记录核验来源及无法确认的字段。
```

需要改稿时明确要求：

```text
在副本中修正有充分依据的问题，保留原文件、引文管理器字段、样式与批注。
```

复查修改稿时，附上旧报告：

```text
请复查这份修改稿和上次报告，区分已修复、仍存在、新增和无法复核的问题。
```

## 输出

- 采用规范、稿件版本及实际覆盖范围。
- 全量问题清单：位置、原文、建议、依据、优先级、信心与处理状态。
- 全部引文与参考文献的对应关系，分别记录内部匹配和外部核验状态。
- 未完成范围和需作者确认的具体事项。

短稿可以在对话中给完整报告；长稿使用 Markdown 和必要的 CSV 附表，避免只给前几项问题。

## 文件结构

```text
manuscript-preflight/
├── SKILL.md
├── agents/
│   └── openai.yaml
└── references/
    ├── audit-protocol.md
    ├── profile-acta.md
    ├── profile-apa.md
    └── sources.md
```

[SKILL.md](SKILL.md) 是执行入口；[共同协议](references/audit-protocol.md)说明全文与引用核对方法；[中文规范](references/profile-acta.md)和[英文规范](references/profile-apa.md)按需加载。

## 来源、验证和边界

本 skill 的指令为独立编写，参考了 [K-Dense citation-management](https://github.com/K-Dense-AI/scientific-agent-skills/tree/main/skills/citation-management) 和 [Essarai/english-journal-proofreader](https://github.com/Essarai/english-journal-proofreader) 等项目的工作流思路，未复制或捆绑其代码。调研、规则来源与版本限制见 [sources.md](references/sources.md)。

已进行结构校验和中英文样例试跑，覆盖同类 typo 多处定位、作者消歧、双语配对、引用合法例外及修改后复查。公开仓库不包含私人论文或检查报告；这些试跑也不构成准确率或零漏检保证。

部分 APA 官方细则页面在整理时未能取得正文，规范文件已保留该核验限制。遇到版本冲突或复杂例外，应核对实际期刊与官方资料。确认文献存在不代表其支持正文论断；不凭猜测修改作者、年份、数值或研究结论，也不把格式偏好当成确定错误。
