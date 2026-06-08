# 紫微斗數 Skill for Claude Code

一個給 [Claude Code](https://claude.com/claude-code) 用的紫微斗數 skill。內含命盤計算腳本、十四主星 / 十二宮位 / 四化 / 飛化的完整解盤方法論，以及解盤倫理規範。

**特色**：重解盤實戰，不僅止於排盤。化忌視為動力源頭（非凶星）、對宮為明鏡、空劫為宮位概念。

---

## 安裝

需要 Claude Code v2.0+。

```
/plugin marketplace add t42ji2ji/ziwei-doushu
/plugin install ziwei-doushu
```

或手動安裝：

```bash
git clone https://github.com/t42ji2ji/ziwei-doushu.git /tmp/ziwei-doushu
cp -R /tmp/ziwei-doushu/skills/ziwei-doushu ~/.claude/skills/
```

---

## 使用

直接在 Claude Code 對話中輸入紫微相關問題即可觸發：

```
我想算一下紫微，1990 年 8 月 15 日下午 2 點，女生
```

支援的問題類型：

- **排盤**：給西曆生辰、性別 → 出命盤
- **解盤**：命宮、運勢、性格、感情、事業、財運、健康
- **飛化推演**：A 宮 → B 宮的影響
- **大限 / 流年運勢**
- 14 主星、12 宮位、煞星、四化的任何問題

---

## 結構

```
skills/ziwei-doushu/
├── SKILL.md               # 主指令、解盤姿態、答題原則
├── ETHICS.md              # 倫理規範（不替未授權他人排盤等）
├── LICENSE                # CC BY-NC-SA 4.0
├── scripts/
│   └── ziwei_calc.py     # 排盤腳本（純 Python，無外部依賴）
├── references/
│   ├── 01-paipan.md      # 時辰邊界、早晚子、夏令時、大限起運
│   ├── 02-jiepan.md      # 觀盤順序、三方四正、對宮為明鏡
│   ├── 03-feihua.md      # 四化本質、飛化、自化、化忌入十二宮
│   ├── 04-zhuxing.md     # 14 主星 × 12 宮位
│   ├── 05-shiergong.md   # 12 宮本義、延伸涵義
│   ├── 06-shaxing-konjie.md  # 擎羊陀羅火鈴、空劫、貴人星
│   └── 07-zhexue.md      # 命運觀、改運法、算命倫理
└── assets/
    └── banner.png
```

---

## 排盤腳本

純 Python 3，無需安裝任何套件：

```bash
python skills/ziwei-doushu/scripts/ziwei_calc.py 1990 8 15 14 女
```

支援參數：
- `--zipai early`：採八字早子派（23:00 算當日）。預設為紫微傳統「子正派」（23:00 後算次日）

---

## 倫理立場

這個 skill 內建以下原則（詳見 `ETHICS.md`）：

- 不替未授權的他人排盤
- 不預測具體死期
- 自傷情境提供危機資源
- 不用煞忌嚇使用者（明確反對江相派恐嚇行銷）
- 吉凶並陳，語言用「傾向」「可能」，非「一定」「絕對」
- 命盤是地圖與功課表，不是判決書

---

## 授權

[CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/) — 自由分享與改編，禁商用，衍生作品需同樣授權。

---

## 免責

紫微斗數命盤僅供參考，不構成醫療、法律、投資等專業建議。
