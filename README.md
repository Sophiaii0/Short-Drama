# Short Drama One-Click Storyboard
快速制成可使用的AI短剧分镜的专业skill

当前版本：**0.8.1（执行稿专用）**。本次更新详见 [更新记录](CHANGELOG.md)。

将**已确认的短剧剧本**转为可拍摄、可交给 AI 视频生成或可导出 DOCX 的逐镜头精细分镜执行稿。

## 安装方法

### 方式一：ChatGPT 网页端上传第三方 Skill

**准备完整技能包**

打开 [Short-Drama GitHub 仓库](https://github.com/Sophiaii0/Short-Drama)，点击 `Code → Download ZIP` 下载完整工程。

本技能需要 `SKILL.md`、`agents/openai.yaml` 和 `references/` 中的六份参考文件。请上传包含这些文件的完整 ZIP，避免只上传 `SKILL.md` 导致执行模板和参考资料缺失。若自行打包，保留下方 Codex 安装部分展示的目录层级，不要把多个技能混在同一个包里。

**安装步骤**

1. 登录 ChatGPT 网页端，点击左侧导航栏的 **插件**。
2. 在页面顶部切换到 **技能** 标签。
3. 点击右上角 **添加**，在下拉菜单选择 **从电脑上传**。
4. 在 **上传技能** 弹窗中，将准备好的 ZIP 拖入上传区域，或点击上传区域选择文件。
5. 截图所示入口支持 `.zip`、`.skill` 文件或单独的 `SKILL.md`，每个文件最大 **25 MB**；本项目使用完整 ZIP。阅读页面提示，检查技能来源和内容后，按界面后续提示完成导入。
6. 返回技能页面，在 **已安装** 列表中确认出现 **Short Drama One-Click Storyboard**。若未出现，请检查当前导入结果和页面提示。

**安装后使用**

新建聊天，在输入框输入 `@`，从技能列表中选择 **Short Drama One-Click Storyboard**，再提供已确认剧本并说明场次、交付类型和要求。ChatGPT 的技能选择方式可参考 [OpenAI 官方说明](https://learn.chatgpt.com/docs/build-skills)。

选择技能后，可直接发送：

```text
把我上传的已确认剧本第36集第36-1场拆成脚本展示版详细执行稿。
保留原台词，使用固定8项镜头卡片，卡片内部不留空行。
先输出 Markdown；本次不生成 AI 视频执行版或 DOCX。
```

如果看不到上述网页入口，请以当前账号界面为准，或采用下方的 Codex 安装方式。安装本技能后，DOCX 渲染等交付仍取决于当前会话可用的工具与依赖，见[使用指南](使用指南.md)第 8 节。

### 方式二：Codex 本地安装

把整个 `short-drama-one-click-storyboard` 目录放入目标环境的 `~/.codex/skills/`，并保留以下结构：

```text
~/.codex/skills/short-drama-one-click-storyboard/
├── SKILL.md
├── agents/
│   └── openai.yaml
└── references/
    ├── shotlist-template.md
    ├── shotlist-execution-format-template.md
    ├── shotlist-gold-example-episode36.md
    ├── cinematography-focal-length-manual.md
    ├── lighting-shadow-manual.md
    └── seedance-camera-movement-library.md
```

重新打开 Codex 或新建一个任务后，用 `$short-drama-one-click-storyboard` 显式调用；当用户的需求明显是逐镜头短剧分镜时，Codex 也可以自动选择该技能。

## 适用范围

- 指定场景或集数的逐镜头分镜；
- 秒级镜头时长、对白语速、O.S. 反应切镜、状态锁与镜间衔接；
- 焦段、机位、运镜、光影和空间连续性；
- 按需生成 AI 视频/Seedance 执行版或 DOCX 执行稿。

它不负责故事开发、分场大纲、标准剧本创作、资产清单或导演读本。

## 输入

提供已确认剧本，并尽量说明：剧本版本、场次/集数、起止段落、交付类型、平台/画幅、角色资产与连续性要求。未指定时，技能只确认最小执行范围。

## 输出

默认交付脚本展示版详细执行稿。每镜固定包含 8 项：镜头标题与精确秒数、景别/机位/运镜、主体动作、情绪节拍、连续性继承/允许变化、光影/空间、与上一镜衔接、独立英文负面提示词。

不再输出“镜头目的”字段。镜头卡片内部连续逐行书写，字段、动作节拍和对白定位之间不插入空行；卡片之间和场级信息之间可以保留空行。DOCX 卡片内部同样不插入空段落。

明确提出 AI 视频或 Seedance 需求时，另出 AI 视频执行版；明确提出 DOCX 需求时，先渲染检查版式再交付。

## 使用示例

以下示例用于 Codex；ChatGPT 网页端先输入 `@` 选择 **Short Drama One-Click Storyboard**，再发送任务正文。安装步骤见上方“安装方法”。

```text
使用 $short-drama-one-click-storyboard 把已确认的第36集第36-1场拆成脚本展示版详细执行稿；保留原台词，按短剧快节奏控制时长。
```

## 文档

- [流程图](流程图.md)：从锁定剧本到交付执行稿的最小流程。
- [使用指南](使用指南.md)：Codex 本地安装、ChatGPT 网页端上传第三方 Skill、调用示例、交付格式与常见问题。
- [更新记录](CHANGELOG.md)：版本变化；已安装技能的更新方法与反馈方式见使用指南末尾。

## 参考资料

技能按任务需要加载 `references/` 中的镜头拆解、固定执行稿格式、金标准示例、焦段、光影与 Seedance 运镜资料。详细工作流及不可改写边界见 [SKILL.md](SKILL.md)。
