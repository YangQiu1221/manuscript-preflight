# 来源、取舍与维护

调研日期：2026-09-20。此 skill 的文字为本次独立编写；未复制或安装下列仓库代码，亦未运行其测试。记录是调研时快照，不代表永久维护状态或实测准确率。

## GitHub 调研

| 项目 | 核实的用途与证据 | 本 skill 的取舍 |
| --- | --- | --- |
| [K-Dense citation-management](https://github.com/K-Dense-AI/scientific-agent-skills/tree/main/skills/citation-management) | MIT；BibTeX/DOI/引用键检查脚本，有[专门测试](https://github.com/K-Dense-AI/scientific-agent-skills/blob/main/tests/citation-management/test_scripts.py)及修复提交。 | 借鉴书目身份核对思想。其引用键解析并非 Word 作者年份引文解析，不能直接代替双向核对。没有 DOI/卷页不自动判错。 |
| [Essarai/english-journal-proofreader](https://github.com/Essarai/english-journal-proofreader) | Apache-2.0；逐条书目核验、覆盖/证据状态及文本一致性脚本，有测试文件。2026-09-03 建库，调研时历史短。 | 借鉴覆盖分母和“核验范围”区分；不能因工作流详细便称长期成熟。 |
| [zuhdanadyfataron-oss/academic-proofreader](https://github.com/zuhdanadyfataron-oss/academic-proofreader) | 社科/管理学机械校对清单；调研时未见 LICENSE 或测试。 | 仅比较功能范围，未复制其文本；合法引用例外和不同期刊格式不能一刀切。 |
| [BrettRey/claude-academic-skills](https://github.com/BrettRey/claude-academic-skills/tree/main/academic-latex-proofread) | MIT；LaTeX 只读校对。 | 不采用将破折号、句首 however、固定段长普遍判错的偏好规则。 |
| [MicheleNuijten/statcheck](https://github.com/MicheleNuijten/statcheck) | GPL-3；长期维护的 R 统计报告一致性工具，有测试及变更记录。 | 可在未来用户明确需要统计重算且环境合适时单独采用；不因安装本 skill 引入 R，不用它宣称检查大小写或引用。 |

结论：现成工具各有所长，但未验证存在一个可直接满足本用户全部范围的成熟组合。当前用原创指令、分离规范、覆盖记录与逐项证据组成专用 skill，无强制网络服务、账号、外部脚本或运行时依赖。

## 官方格式来源

- 中文规则以 [《心理学报》中文官网](https://journal.psych.ac.cn/xlxb/CN/column/column6.shtml)及[下载中心](https://journal.psych.ac.cn/xlxb/CN/column/column7.shtml)当前链接为入口；具体采用文档与冲突见 `profile-acta.md`。
- 英文默认与核验限制见 `profile-apa.md`。不要把 APA 官网入口成功打开当作各细则已读。
- [AOM 官方风格指南](https://www.aom.org/publications/journals/publishing-with-aom/author-and-reviewer-resources/author-resources/author-resources-editorial-style-guides/)在调研中说明管理学期刊可能采用与 APA 7 不同的多作者规则，因此本 skill 不把“管理学”视为 AOM 格式开关。用户选具体期刊后再查适用规则。

## 更新和验证

- 官方网页与附件链接可能变化。用户指定新版本、提供新模板、发现冲突或规则影响关键结论时重查；保留已查版本与日期，不静默换用第三方总结。
- 维护时测试真实可观察行为：能否定位所有实际出现处；双语条目是否只算一个来源；缩写/作者消歧是否误改；节选/提取失败是否诚实计入覆盖；数字冲突是否保留两侧证据。
- 用英文与中文的小样本分别检查。包括确定 typo、合法例外、无法确定的书目信息；另查只给节选和修改后复查场景。测试素材放临时工作区，不混入用户论文。
- 以后增加自动化解析时，先证明对目标格式的识别范围与漏检边界，留下可运行回归检查；不要用只处理简单正则样本的脚本替代全文审读。
