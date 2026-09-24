# CN_Complete_Patch — PZ B42 模组物品名汉化补全补丁

[Project Zomboid](https://store.steampowered.com/app/108600/Project_Zomboid/) **Build 42.20** 模组简体中文补全补丁。补齐社区三大汉化包（统一·中文汉化、统一·模组汉化、栀子的模组补充汉化）**未收录**的模组物品名。

## 覆盖范围（388 条，15 个模组 100%）

| 模组 | 条目数 | 说明 |
|---|---|---|
| ModernFirearmsSystem（现代火器系统） | 221 | 枪械/弹匣/弹药盒/装弹台 |
| FantasyWorkshopVS42_4.0（幻想工坊） | 96 | 服装/背包/胸挂 |
| VanillaFoodsExpanded（原版食物扩展） | 24 | 食物/容器/茶包 |
| 42_VSGirlBodySFW | 15 | 发型/化妆 |
| damnlib（DAMN 车辆库） | 23 | 车门/挡风装甲/轮胎/座椅/图纸 |
| 其余 10 个模组 | 各 1-2 | ToadTraits、LB/LD/LS 背包、SRJ、VRO/VSO、OpenAllContainers、KI5campers、RaccoonCity、GydeTraitMags |

## 安装

1. 下载本仓库，把 `CN_Complete_Patch/` 文件夹放进：
   - 服务端：`Zomboid/mods/`
   - 客户端：`C:\Users\<你>\Zomboid\Workshop\` 或同样放 `Zomboid\mods\`
2. 在模组列表里启用 `CN_Complete_Patch`
3. **加载顺序：放在所有汉化包之后**（推荐排在 Mods= 列表最尾部）：

```
...;Spawn Location_CN;GardeniaTranslate_CN;B42ModTrans_CN;B42Trans_CN;CN_Complete_Patch
```

## 与其他汉化包的关系

- **不冲突、不替代**：本补丁只补三大包没覆盖的物品名；词条格式为 B42 标准 JSON（`media/lua/shared/Translate/CN/ItemName.json`，键 = `Module.Item`）。
- **加载顺序靠后**保证我们的词条覆盖同名冲突（仅针对三大包没翻的键，正常不会撞）。
- 已确认兼容：统一·中文汉化（B42Trans_CN 3556544454）、统一·模组汉化（B42ModTrans_CN 3556540080）、栀子补充（GardeniaTranslate_CN 3488835702）、Spawn Location_CN（3448235767）。

## 维护方式（自己加词条）

1. 找到目标模组的物品脚本：`mods/<模组>/media/scripts/*.txt`
2. 确认物品所在的 `module`（键 = `模块名.物品脚本名`，**不是** mod id）
3. 往对应版本目录（`42.20/` 或 `common/`）的 `ItemName.json` 里加一行：

```json
"Base.你的物品键": "中文名"
```

4. 重启服务器即可生效（客户端也需要装本补丁才能显示）。

## 覆盖率核对方法

`coverage.json` 记录每个模组的补丁条目数。核对脚本逻辑：

1. 收集所有汉化包 JSON 的完整键（`Module.Item`）
2. 解析模组 `media/scripts/*.txt`，按 `module` 声明对每个 `item` 生成完整键
3. 差集即缺口

## 已验证环境

- Project Zomboid B42.20 专用服务器（Ubuntu 24.04 LXC，无头）
- 与 51→49 模组共存的多人服务器配置实机验证，`SERVER STARTED`，无 mod 加载错误

## License

MIT（翻译文本随意取用，注明来源即可）
