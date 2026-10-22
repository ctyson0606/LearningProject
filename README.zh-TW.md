<!-- Hero -->
<div align="center">
  <h1>學習專案模板</h1>
  <p><b>放在你自己電腦上的 Claude Project</b>：每個科目一個資料夾，裡面放你的教材、筆記和 AI 的記憶，所以你在那裡打開的任何 agent 都能從上一個停下的地方接著教。</p>
  <p>
    <img alt="agents: Claude Code | OpenCode | DeepSeek Harness" src="https://img.shields.io/badge/agents-Claude%20Code%20%7C%20OpenCode%20%7C%20DeepSeek%20Harness-4d6bfe">
    <img alt="content: Markdown only" src="https://img.shields.io/badge/content-Markdown%20only-brightgreen">
  </p>
  <p>🌏 <a href="./README.zh-CN.md">简体中文</a> · 繁體中文 · <a href="./README.md">English</a></p>
</div>

<!-- Screenshot placeholder: commit the image at docs/screenshot.png, then remove this comment pair.
<p align="center"><img src="docs/screenshot.png" alt="VS Code 裡黑板上的一堂課" width="720"></p>
-->

假設上課上到一半 Claude 的額度用完，你換了另一個 agent。平常新的 agent 什麼都不知道，你得從頭解釋一遍。在這裡，記憶是資料夾裡的普通檔案，每個 agent 讀寫的都是同一批檔案，而且邊做邊存：一個 agent 突然停掉，最多只會損失最後幾分鐘。

## ✨ 功能

- **記憶就是普通檔案**：你學到哪、懂了什麼、做過什麼決定、接下來做什麼，都在 `memory/` 裡。
- **隨時換 agent**：關掉一個，在同一個資料夾打開另一個，它會告訴你學到哪裡。
- **邊做邊存**：不用特別叫它存；只有想一次全部存好時才說「handoff」。
- **黑板**：教學內容寫在 `materials/generated/blackboard.md`，VS Code 會直接顯示排版好的樣子，數學式也是；聊天只留簡短訊息。
- **用你的語言**：寫給你看的都用你選的語言；寫給 AI 的保持英文。
- **模式**：說「我三天後考試」或「今天只想練習」，教法就會跟著變。
- **搬移 Claude Project**：你的指示、教材和進度都能一起帶過來。

## 🚀 安裝

前提：git、VS Code，以及至少一個 agent：Claude Code、OpenCode 或 DeepSeek Harness。

**方式一 · Windows（PowerShell）**

```powershell
git clone https://github.com/ctyson0606/LearningProject.git
mkdir D:\learning\my-topic
Copy-Item -Recurse LearningProject\template\* D:\learning\my-topic\
```

**方式二 · macOS 或 Linux**

<details>
<summary>同樣的步驟，用 POSIX shell</summary>

```bash
git clone https://github.com/ctyson0606/LearningProject.git
mkdir -p ~/learning/my-topic
cp -r LearningProject/template/. ~/learning/my-topic/
```

</details>

新資料夾要建在這個 repository **外面**，然後把你的書、投影片和考古題放進它的 `materials/sources/`。

**驗證**

用 VS Code 打開新資料夾，在裡面啟動一個 agent，隨便說句話，例如「hi」。它會先問你想用哪種語言。

## 🕹️ 使用

### 第一次對話

1. agent 會問你的語言，再問這是新科目，還是從 Claude Project 搬過來的。
2. 如果是新科目，它會問幾個關於你的目標和學習習慣的問題。
3. 它會給你看一份簡短的教學方式摘要。你說沒問題之後，就開始上課。

### 搬移現有的 Claude Project

照上面安裝，然後選「從 Claude Project 搬過來」。agent 會請你：

- 把舊的專案指示給它，貼上或提供檔案都可以；
- 把原始教材放進 `materials/sources/`，之前 AI 幫你做的東西放進 `materials/generated/`；
- 問舊的 Claude Project「我們學到哪裡了，接下來做什麼？」，再把回答貼過來。

它會把你的指示翻成英文，改掉只在 claude.ai 上才有用的部分，存檔前把每一處改動都給你看。

### 換到另一個 agent

關掉舊的 agent，在同一個資料夾打開新的。如果舊的還能用，先說「handoff」。同一時間一個資料夾只開一個 agent：如果看起來還有別的 session 開著，新的會先問你再繼續。

### 你可以說的話

| 說 | 會發生什麼 |
| --- | --- |
| 「我三天後考試」 | 衝刺：只教考試需要的，大量練習 |
| 「今天只想練習」 | 練習：不教新東西，只做題和訂正 |
| 「回到正常」 | 恢復正常教學 |
| 「Handoff」 | 立刻存好一切，方便你換 agent |
| 「我加了新檔案」 | 它會讀那些檔案，並更新你的教材清單 |

如果你的專案指示定義了自己的模式，就以那些為準。

## 📁 你的資料夾裡有什麼

| 路徑 | 是什麼 | 誰寫 |
| --- | --- | --- |
| `AGENTS.md` | 每個 agent 都要遵守的規則，以及這個專案怎麼教你 | 設定時由 agent 寫；之後只在你要求時才改 |
| `CLAUDE.md` | 讓 Claude Code 去讀 `AGENTS.md` | 沒人寫；保持原樣 |
| `materials/sources/` | 你的原始教材 | 你；agent 只會讀 |
| `materials/generated/` | agent 幫你做的東西：筆記、練習、摘要 | agent |
| `materials/generated/blackboard.md` | 目前的教學內容，數學式正確顯示 | agent |
| `materials/generated/obsidian/` | 可以用 Obsidian vault 打開的筆記 | agent |
| `memory/` | 你學到哪、懂了什麼、決定、待辦、每次 session 的摘要 | agent，自動 |

## 📊 狀態

已經在六個真實科目的資料夾裡天天使用，主要用 Claude Code。2026-10-21 在其中一個的副本上，分別用 Claude Code、OpenCode 和 DeepSeek Harness 跑了同樣的兩輪對話：

- **交接可行**：一個 OpenCode session 沒有 handoff 就關掉，在同一個資料夾打開 Claude Code，它說出了學習進度。
- **模型比 agent 更重要**：用 DeepSeek V4.1 Flash 時，OpenCode 和 DeepSeek Harness 都遵守了每條規則；免費和本地模型只適合短暫接手。
- **還沒試過**：OpenCode 和 DeepSeek Harness 的互動介面，這次都是一次一個指令驅動的。

## 📦 專案結構

```text
template/AGENTS.md
template/CLAUDE.md
template/materials/sources/
template/materials/generated/blackboard.md
template/memory/
template/.vscode/settings.json
```

- `template/AGENTS.md`：每個複製出來的資料夾一開始帶著的規則和教學方法；
- `template/CLAUDE.md`：Claude Code 會讀的指引；
- `template/materials/sources/`：空的，放學習者的教材；
- `template/materials/generated/blackboard.md`：黑板；
- `template/memory/`：記憶檔，維持初始格式；
- `template/.vscode/settings.json`：把黑板以排版預覽打開，並開啟數學式。

只有 `template/` 會被複製。這個 repository 的其他部分（`kit/`、`scripts/`、最上層的 `AGENTS.md`）是用來製作模板的工具。

## ⚠️ 相容性與限制

- Claude Code 能讀 `materials/sources/` 裡的 PDF；OpenCode 和 DeepSeek Harness 能不能讀還不知道。
- DeepSeek Harness 最多只載入 64 KiB 的指示，所以 `AGENTS.md` 超過 60,000 bytes 時，agent 會建議把一部分移到 `memory/`。
- 如果有東西（同步、git 操作）動到了所有檔案的日期，即使沒有別的 session 開著，開 session 檢查也可能會問你。
- 日期一律用英國日期，也不寫時刻，不管 agent 在哪台電腦上跑。

## ❓ 常見問題

| 症狀 | 怎麼做 |
| --- | --- |
| 上課上到一半 Claude 額度用完 | 在同一個資料夾打開另一個 agent；它會從記憶接著教 |
| 新的 agent 問是不是還有別的 session 開著 | 把另一個關掉，或告訴它已經關了 |
| 數學式在聊天裡顯示成原始 LaTeX | 看黑板；VS Code 會排版顯示 |
| 命令列的 DeepSeek Harness 讀不到你的 API key | 在環境變數設定 `DEEPSEEK_API_KEY`；網頁設定裡存的 key 在那裡不會被用到 |
