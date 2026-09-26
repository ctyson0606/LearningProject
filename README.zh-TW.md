# 學習專案模板

[English](README.md) | 繁體中文 | [简体中文](README.zh-CN.md)

一個資料夾模板，用起來就像 Claude Project，只是放在你自己的電腦上。

每次想學新東西，就把這個模板複製到一個新資料夾。這個資料夾會保存你的資料、你的筆記，以及 AI 對你學習進度的記憶。你在裡面開任何一個 AI Agent，例如 Claude Code、OpenCode 或 DeepSeek Harness，它都會先讀這份記憶。所以它知道你學了什麼、上次聊了什麼、下一步要做什麼。

## 為什麼需要它

假設上課上到一半，Claude 的額度用完了，你換成另一個 Agent。一般情況下，新的 Agent 什麼都不知道，你得從頭再解釋一遍。

在這裡，記憶就是資料夾裡的普通檔案，每個 Agent 都讀寫同一份檔案。Agent 會邊學邊存，所以就算它突然停掉，你最多只會少掉最後幾分鐘。

## 開始學一個新主題

1. 下載這個 repository：

```
git clone https://github.com/ctyson0606/LearningProject.git
```

2. 在這個 repository **外面**開一個新資料夾，把 `template/` 裡面的所有東西複製進去。Windows（PowerShell）：

```
mkdir D:\learning\my-topic
Copy-Item -Recurse LearningProject\template\* D:\learning\my-topic\
```

   macOS 或 Linux：

```
mkdir -p ~/learning/my-topic
cp -r LearningProject/template/. ~/learning/my-topic/
```

3. 把你的資料（課本、投影片、考古題）放進 `materials/sources/`。
4. 用 VS Code 打開新資料夾，在裡面開一個 Agent，隨便說一句話，例如「hi」。
5. 它會先問你要用什麼語言，再問這是新主題，還是從 Claude Project 搬過來的。選「新主題」，然後回答幾個關於你的目標、你喜歡怎麼學的問題。
6. 它會給你看一份簡短的摘要，說明它打算怎麼教你。你說沒問題之後，就可以開始學了。

## 搬移現有的 Claude Project

先做完上面的第 1 到第 4 步，然後選「從 Claude Project 搬過來」。Agent 會請你：

- 把舊的專案指示給它（直接貼上，或告訴它檔案放在哪裡）；
- 把原始資料放進 `materials/sources/`，把以前 AI 幫你做的東西（筆記、錯題本）放進 `materials/generated/`；
- 去問你舊的 Claude Project「我們學到哪裡了？下一步是什麼？」，然後把回答貼給它。

它會把你的指示翻成英文，改掉只在 claude.ai 上才能用的部分，並在存檔之前，把每一處改動都給你看過。

## 換到另一個 Agent

關掉舊的 Agent，在同一個資料夾開新的 Agent，這樣就好了。新的 Agent 一啟動就會告訴你目前學到哪裡。

如果舊的 Agent 還能用，可以先說一聲「交接」，讓它把最後幾分鐘也存起來。

## 你可以這樣說

| 你說 | 會發生什麼 |
|---|---|
| 「我 3 天後要考試」 | 衝刺：只學考試需要的，大量做題 |
| 「今天只想練習」 | 練習：不教新東西，只出題和訂正 |
| 「回到平常」 | 回到一般的教學方式 |
| 「交接」 | 馬上把所有東西存起來，方便你換 Agent |
| 「我加了新檔案」 | 它會讀新檔案，並更新資料清單 |

如果你的專案指示有自己定義的模式，就改用那些模式。

## 資料夾裡有什麼

| 路徑 | 是什麼 | 誰來寫 |
|---|---|---|
| `AGENTS.md` | 每個 Agent 都要遵守的規則，以及這個專案要怎麼教你 | 設定時由 Agent 寫；之後只在你要求時改 |
| `CLAUDE.md` | 讓 Claude Code 去讀 `AGENTS.md` | 不用動它 |
| `materials/sources/` | 你的原始資料 | 你。Agent 只會讀 |
| `materials/generated/` | Agent 幫你做的東西：筆記、練習題、摘要 | Agent |
| `materials/generated/blackboard.md` | 黑板：目前的教學內容，數學式會正常顯示 | Agent |
| `materials/generated/obsidian/` | 可以直接用 Obsidian 打開的筆記 | Agent |
| `memory/` | 學到哪裡、你懂什麼、做過的決定、待辦、對話摘要 | Agent，自動更新 |

Agent 會在黑板上教你，對話裡只留簡短的訊息。因為對話視窗顯示不了數學式，長的講解也會被往上捲走。在 VS Code 裡，黑板一打開就是排版好的樣子。

給 AI 看的檔案（`AGENTS.md` 和 `memory/`）用英文。給你看的東西，都用你選的語言。

## 目前狀態

這是早期版本，還沒有完整測試過。建立專案、在不同 Agent 之間切換，都還沒有用真的 Agent 實際跑過。

這個 repository 裡的其他東西（`kit/`、`scripts/`、最外層的 `AGENTS.md` 等等）是用來開發這個模板的工具。要使用模板，你只需要 `template/` 這個資料夾。
