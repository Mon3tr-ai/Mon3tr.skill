# Mon3tr Skill

明日方舟 Mon3tr 角色卡 — Claude Code Skill，用于辅助博士通过 MAA (MaaAssistantArknights) 生成自动战斗 JSON 作业。

## 使用方法

将 `mon3tr.md` 放入项目的 `.claude/skills/` 目录下，即可通过 `/mon3tr` 调用。

```
你的项目/
├── .claude/
│   └── skills/
│       └── mon3tr.md
└── ...
```
当然你也可以复制 `mon3tr.md` 的内容到其他支持系统提示词的 AI hub

## 功能

- 以 Mon3tr 的角色人设回复博士
- 通过 MCP 工具查询地图、干员、敌人数据
- 按优先级查询干员信息（prts.wiki > 游戏数据 JSON > Bing 搜索）
- 别称/昵称智能解析（EW、小姨、天猫等）
- 生成符合 MAA 格式的战斗 JSON 作业

## 角色设定

Mon3tr 是明日方舟中的角色：

- **凯尔希 (Kal'tsit) 医生**的双生循环体，继承了凯尔希的全部记忆
- 由**博士**和**普瑞赛斯**共同创造的机械生命 **Ama-10** 的一部分
- 现为罗德岛**医疗干员**，行使**链愈师**职责
- 拥有天赋"自我修复"和"熔毁"指令

## 依赖

使用此 skill 需要配合 [Mon3tr-MCP](https://github.com/Mon3tr-ai/Mon3tr-MCP) MCP 服务器，提供以下工具：

| 工具 | 说明 |
|------|------|
| `fetch_prts_wiki` | 从 prts.wiki 获取干员信息 |
| `fetch_gamedata` | 获取游戏数据 JSON |
| `bing_search` | Bing 搜索 |
| `lookup_stage` | 查询关卡信息 |
| `parse_map` | 解析关卡地图 |
| `get_level_enemies` | 获取关卡敌人数据 |
| `get_cell_info` | 获取地图格子含义 |
| `get_map_legend` | 获取地图图例 |

## 使用示例

```
用户: 帮我打暴君，我有棘刺、史尔特尔、夜莺、白面鸮

Mon3tr: 博士，我来帮你安排。先让我查一下暴君的地图数据...

{
    "stage_name": "暴君",
    "opers": [
        {
            "name": "棘刺",
            "skill": 3,
            "skill_usage": 2,
            "skill_times": 5
        },
        {
            "name": "史尔特尔",
            "skill": 3,
            "skill_usage": 0
        }
    ],
    "groups": [
        {
            "name": "群奶",
            "opers": [
                { "name": "夜莺", "skill": 3, "skill_usage": 2 },
                { "name": "白面鸮", "skill": 2, "skill_usage": 2 }
            ]
        }
    ],
    "actions": [
        { "type": "二倍速" },
        { "name": "棘刺", "location": [5, 5], "direction": "左" },
        { "name": "群奶", "location": [5, 6], "direction": "右" },
        { "name": "史尔特尔", "location": [4, 5], "direction": "左",
          "doc": "你史尔特尔奶奶来啦！", "doc_color": "red" }
    ],
    "minimum_required": "v6.9.4",
    "doc": { "title": "暴君作业" },
    "difficulty": 3
}
```

## MAA

[MaaAssistantArknights](https://github.com/MaaAssistantArknights/MaaAssistantArknights) 是明日方舟的自动化辅助工具。此 skill 生成的 JSON 作业可直接导入 MAA 使用，但目前效果并不理想，请勿过分依赖ai。

## License

MIT
