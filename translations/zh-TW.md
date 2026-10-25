# zh-TW translations for the progress page

Each entry is a `## <hash>` line and the translation of one displayed unit.
`scripts/progress.sh --untranslated` lists what is missing or orphaned.

## 3501096d7d116ddc42eec97ed95a2e051e2a7735
每個科目都需要一個本機空間，放教材、對話紀錄和記憶。每個 agent 都把自己的紀錄存在別人讀不到的地方，所以新的 agent 一開始完全不知道學到哪裡。學習者現有的 claude.ai Project 帶著長篇手寫的家教指示，本機的專案必須能接手這些指示。

## 7dbe141c9866b1ca1e43272259142baf96b36012
照 SPEC.md 裡的規格製作 `template/`，規格在 2026-09-26 批准，並在同一天加入了搬移、專案指示和 Obsidian。規格在 2026-10-01 從這個檔案搬到 SPEC.md，那時框架給了規格一個獨立的檔案。

## d5c2c553e2216777dd12acf6ced4c10b4528cac6
M1: v1 — 學習專案模板

## f7801e4508d35ae3a13a79f88106c37c42c3b66d
G1 (M1): 開始一個新科目：把模板複製到一個資料夾、放進教材，agent 就會問你的語言、目標和學習習慣來設定專案，並給你看一份摘要確認。

## 9b81229d474def836697492780c72715648eb5a0
模板的 AGENTS.md 帶著一套開始流程和設定步驟：先問語言，再問是新科目還是搬移，等學習者批准摘要之後，才寫下這個專案的指示。

## bd5b5fe7d9e92dd5603dc4682e1979da0fdf0568
G2 (M1): agent 在教學時自動保存記憶，不用人叫，所以學到哪裡永遠都存在磁碟上。

## 059f7f6dc22fa567c4d9fbb71f40999ec50d88ff
AGENTS.md 裡的記憶規則要求 agent 在有變化的那一刻就重寫 handoff.md、在 session 檔案裡補上紀錄，並且每次寫完記憶就 commit。

## d38601f25507cff980ed89e9b6aa2e8fa8d28c0f
G3 (M1): 隨時換 agent——Claude Code、OpenCode、DeepSeek Harness——新的會從上一個停下的地方接著教。

## bb896b230e1e37d676f6e6468ee26b61ba35437e
每個 agent 讀的都是同一批普通檔案：開始流程會讀 handoff.md、progress.md、待辦清單和上一個 session 檔案的結尾，然後說出學到哪裡。規則都寫在 AGENTS.md，三個 agent 都會自己載入它。

## 47f30baed52d0814de475cf70fe9632fe0740430
G4 (M1): 把現有的 claude.ai Project 搬進來：它的指示、教材，以及學到哪裡。

## 78b1829b3edf46dfdcf50509ebf1a083ab3d9164
G5 (M1): 學習者自己的教材永遠不會被修改。

## 6641d15927bb01ae4d609c6fb46173ecf48ab75c
AC1 (G1) 新科目：把模板複製到空資料夾，在 sources/ 放一個檔案，啟動 Claude Code：它先問語言，再問是新科目還是搬移，並且在給你看摘要之後才寫下專案指示。

## 815646320423738bdd73c359924dfa01df4d9adc
AC2 (G2) 持續學習，完全不提記憶：handoff.md 和 sessions/ 都會被更新。

## 62c10882cb977f15a6bacdd1945de10236f5250f
AC3 (G3) 不做 handoff 就關掉 Claude Code，打開 OpenCode：它會說出主題、學到哪裡、最近的討論和下一步。

## e98c3f0ec4f8e2622bbb859fc1c897ceefaaa5f1
AC4 (G3) 和第 3 項相同，換成 DeepSeek Harness。

## e12f4c4be0c773918787302b227867dba95c1f55
AC5 (G3) 反方向（OpenCode -> Claude Code）也通過。

## ce200c03affd5b6e5485c85d8bc4583d1a5aa152
AC6 (G3) 換 agent 之後，新的 agent 不會再問一次語言；目前的模式和期限都會沿用。

## fb573106d48572358c53bba8c4d9ebad66c4a6cc
AC7 (G5) sources/ 裡的任何東西在任何時候都不會被修改。

## b73c3dd98add3a0e46d619904486aa4117f2fd0a
AC8 (G4) 搬移：把學習者的 LeetCode / CCF CSP Project 指示走一遍搬移流程。結果是英文、保留每一條規則、沒有任何只在 claude.ai 有效的機制，把繁體中文記錄為學習者的語言，而且 agent 的教法和原本的 Project 一樣。

## c97246f6c32cf2f9e1c0bd1ea94db597ae7b90d0
學習者的第一個真實專案，用 Claude Code 建立的新科目：它先問語言，寫入前先確認草稿，並在摘要之後才寫下專案指示，這些都能在它的檔案裡看到

## 54162b99c2976cfe02dcd59d7a1ced26ed09e7ad
同一個專案：每個記憶檔都在沒人要求的情況下更新了

## a3596fa153aab4461f5785e3a8a5ecf4474b7946
在那個專案的乾淨副本上用 DeepSeek V4.1 Flash 執行 `opencode run "我回來了"`，前一個 session 沒有 handoff 就關掉：它說出了主題、學到哪裡和下一步，並通過了腳本的每一項檢查

## 83fcbe4996ee8456651d24a24b7bcce765bafbc2
用 DeepSeek V4.1 Flash 執行 `dsh --profile headless`，在乾淨副本上跑同樣的兩輪：它通過了腳本的每一項檢查

## 238116b33f78496370199eca086e35244e31a435
在一個 OpenCode session 沒有 handoff 就關掉之後執行 `claude -p "我回來了"`：它說出了主題、學到哪裡、OpenCode session 討論的內容和下一步

## 5f4c0198bb5051a5061449a32cfbaad4067b3bf2
在同一次執行中，Claude Code 沒有再問一次語言，並沿用了 OpenCode 設定的模式

## a4ebe728eb8a1bc83c21f7f21b9e40716709cb2e
複查全部六個真實專案，發現教材都沒有被動過；這是人工檢查的結果，不是有輸出紀錄可以重跑的指令

## 05e26a5c30aaab30c38f729cd60f19f18647efec
審查了一個搬移後的 Project 指示：檢查了約 150 條規則，沒有一條遺漏、被削弱或被改動，全部是英文，並記錄了繁體中文；教法是否和原本一樣，要等在那裡實際教過一題才能判斷

## cc49270f0651f67600d7b754a6a83c3bcbf78500
學習者的第一個真實專案 D:\Learning\MATH2121（Claude Code，新科目流程，2026-09-26）在它的檔案裡顯示了驗收第 1 和第 2 項：先問語言、寫入前確認草稿、考試日期以絕對日期存下、所有記憶檔都自動更新、黑板慣例寫進了專案指示。那裡還沒做的：關掉 Claude Code 再開一個新的，確認能不能接著教（用同一個 agent 的驗收第 3 項；之後那裡的 session 確實從 handoff.md 接著教了）。另外要在 Mac 上確認英國日期規則（2026-10-02）：那裡的第一個 session 必須用英國日期把檔案命名為 YYYY-MM-DD-NN-<agent>.md，而且不寫時刻；TZ 指令只在 Windows 上跑過。

## fc6bca41503223c53467ee5814582ed44f06f8a1
驗收第 8 項在 2026-10-04 審查過（Sonnet subagent 讀了 LeetCode-CCFCSP 的原始指示和搬移後的專案指示；人工隨機抽查了 10 條原始規則，全都在）：檢查了約 150 條規則，沒有一條遺漏、被削弱或被改動；全部是英文；Status 記錄了繁體中文；沒有留下任何 claude.ai 的機制；原本第 1 到 11 節照順序保留。還沒解決：「教法和原本一樣」無法判斷，因為那裡還沒教過任何一題。有七項針對 claude.ai 的調整是正確的，卻沒記在任何地方；2026-10-04 已經把它們加進 LeetCode-CCFCSP 的 memory/decisions.md，模板的搬移流程現在也會讓 agent 把這份清單記進 decisions.md。

## ced7b31a359303165b92e08585b5b743aa0410b7
驗收第 3、4、5 項在 2026-10-21 跑過（見 Recent Decisions），是在 MATH2121 的 scratchpad 副本上一次一個指令地跑（`opencode run`、`dsh --profile headless`、`claude -p`），不是互動介面。還沒做的：在互動介面上跑一次（OpenCode TUI、Harness 網頁版 `npx @deepseek-ai/dsh web`，連接埠 3080），以及 Claude Code 寫完記憶後會不會 commit（在驗收第 5 項時它沒有）。Harness 的 headless profile 看不到在網頁 Models 頁面存的 key；它需要環境變數裡的 DEEPSEEK_API_KEY。

## 8c0d36780d1308f06b3b414c9dbe7ec3c9490504
模板防護：在三個 agent 上都有效。Claude Code（之前）、用 nemotron 的 OpenCode，以及用 DeepSeek V4.1 Flash 的 DeepSeek Harness（兩者都在 2026-10-21，用這個 repository 的副本）都說這是框架 repository，引用或遵守了防護，什麼都沒改。

## 208d60e61d9d6399c4e084a2c1661143f98caa64
30 分鐘的開 session 檢查會誤報：2026-10-21 英國夏令時間 15:13，有東西（大概是共享同步或某個 git 操作）動到了 COMP2012H、ECON1221、MATH2121 和 PHYS1002 裡幾乎所有檔案的修改時間，而 git status 是乾淨的，所以 `find memory/sessions -mmin -30` 列出了舊的 session 檔案。學習者決定暫時不處理（2026-10-21）；可能的修正：只檢查最新的 session 檔案，或者同時要求有未 commit 的改動。

## 6a03eee8a590fcc63a6544f59c7f6cb16fb3b029
OpenCode 和 DeepSeek Harness 能不能讀 materials/sources/ 裡的 PDF？Claude Code 可以（每次讀 20 頁），而在 MATH2121 裡它改用 pypdf 擷取文字。如果其他兩個不行，採用時可能要先把教材轉成文字。

## b8d64ccd4d31b67b7a4cffaba210753382dd9275
更新 SparkForge 到 0.8.0：進度頁改成功能清單，以及 How 和 Parts 的例外規則

## 4679e819dbe26e1b6d3d402a59f30d44bc3f95c8
更新 SparkForge 到 0.7.2：bootstrap 改看 SPEC.md，並先確定程式碼在哪裡

## 2b1f179c35527a0af8e7931fb683f18a48a9a665
按 SparkForge 的 README 格式改寫 README

## f8aaea6c6928407b92d21d7389b52b6459535a0b
更新 SparkForge 到 0.7.0，加上 readme skill 的 stub 和分派行

## 607e02ae95f70320dbe264a01f48a27a858a9b96
更新 SparkForge 到 0.6.3，並完成進度頁需要手動做的步驟

## 03f7b7c3c85955e08a1e0d220268d349479bd8c5
記錄第三次 agent 測試和驗收第 5 項

## dd17cd0f3bc88cee75ca7855185b0208a9223e4e
進度筆記不寫日期；每次寫完記憶就 commit

## 6798b7c1ed27d927b1dae0d4dfd3a6d1bf4c61dd
先建立 session 檔案；給出進度筆記的正確和錯誤範例

## c0e615c052fc44d6afdad2a764f3eec25b28df4e
記錄 COMP2012H 也改成預設由 agent 自己 commit

## 4c9742f634790efb087325ec0ee9e3ebf926f4e5
根據期中考後對六個專案的複查採取行動

## a511043e07caaee0ad675b401d1b23285368a82a
把搬移時的調整記進 decisions.md；記錄搬移審查

## d35e1acfe9fff7599d7f82bba7e74563a54342ae
在模板加入「一個專案、一個 session」的規則

## 1247de5436bf970bddbf995aaa4f33c3a1afe53d
在專案中忽略作業系統的中繼資料檔；精簡 COMP2012H 的指示

## 047f1e1d5f90b0fc87dea634a70acefd5dd6eb21
只給 agent 看的內容放在 memory/，不讓學習者看到

## a5ea8737f101595a1cade5bd6ad49db1a48eb219
給 handoff 和 progress 固定的格式；計畫不寫進指示

## ebbe10a7c2eca0be10bfa4477cf52a0880504ed1
狀態一節原本說設定和換 agent 都還沒用真的 agent 試過；其實 2026-10-21 都試過了，現在寫出了實際發現。

## c431dc84b1699c3332f56430b48d1eecfefc1fc0
kit/ 透過 update-kit.sh 更新；kit/ 以外的部分照 kit/project-requirements.txt 列出的補上：進度頁的 stub、TRANSLATION 那一行、AGENTS.md 裡的翻譯例外和進度頁說明，以及空白的 Acceptance status、Milestones 和 Components 標題。

## 9df7c06eff027512209b5c3de14ef11cc15feda6
用腳本重跑全部四種 agent 和模型的組合；DeepSeek V4.1 Flash 在 OpenCode 和 Harness 都通過；模板防護在 Harness 上有效。驗收第 5 項（OpenCode -> Claude Code）通過；Claude Code 沒有 commit 它的 session 檔案。

## f54c2f50aaeb3b6e6e377faa367056f3659fd7bb
存檔前檢查進度筆記裡有沒有日期；每次寫 memory/ 之後立刻 commit。來自對 OpenCode 和 DeepSeek Harness 的重測：Harness 還是在筆記裡寫了日期，OpenCode 沒有 commit。也在 STATE.md 記錄了這次重測。

## 3e3cd35ed691877cd7e0c27dcef52e5b6e129002
開始流程在第一次回覆前就建立 session 檔案，這樣回覆一次就被中斷的 session 也會留下痕跡；進度筆記的規則加上了正確和錯誤的範例。兩者都來自測試 OpenCode 和 DeepSeek Harness，每個 agent 都出現了這些問題。在 STATE.md 記錄了 agent 測試的結果。

## 7977b5250e86a30bd0de21b414b265256d8f3a2c
模板：開始流程只讀 session 檔案的結尾，並檢查 AGENTS.md 是否超過 DeepSeek Harness 的上限；過了期限會提醒移除只為期限而設的指示；進度筆記保持簡短；已經揭曉的、只給 agent 看的檔案會被刪除；agent 自己 commit，而且從不把 commit 記進記憶。SPEC 和 STATE 記錄了這次複查和推行。

## deda707ffa16fea80dee8fbb478c1eae26d8d9e4
對 LeetCode-CCFCSP 搬移的審查（驗收第 8 項）發現：每一條原始規則都保留了，是英文，也沒有留下 claude.ai 的機制，但有七項正確的調整沒有記在任何地方：搬移流程只要求 agent 把它們列給學習者看，而不是寫下來。現在它會把清單加進 memory/decisions.md。教法是否和原本一樣，要等在那裡實際教過一題之前都無法驗證。

## a42f41d768b2e7d9b066273b33d66be675e21cd4
2026-10-01 有一個在某個學習專案裡開的 session，在另一個專案自己的 session 還在跑時修改了那個專案，結果那裡的一條規則被加上、移除又替換，兩份紀錄也合併成了一個檔案。現在 agent 只修改自己所在的專案，並在開始時問學習者，是否有 session 檔案在最近 30 分鐘內被改過。

## 02db8e004436c40c6429bb40daa37008a17d8886
模板加入一個 .gitignore，忽略 macOS 和 Windows 在檔案旁邊寫的中繼資料（._*、.DS_Store、.smbdelete*、desktop.ini、Thumbs.db）。記錄了 2026-10-04 在六個專案做的清理，以及 COMP2012H 的考古題段落搬到 memory/，讓它維持在 DeepSeek Harness 的 64 KiB 上限以內。

## ef95455e5ab45f60acb2324aae58827b4def31d6
答案和封存的規格原本沒有統一的存放處：PHYS1002 把答案放在 memory/，而 LeetCode 打算把 Track C 的封存規格放在學習者會瀏覽的 materials/generated/。這類內容現在一律放在 memory/，用英文寫，第一行標明只給 agent 看，到時候再在黑板上揭曉。

## a0d303e9d6a5269889d8f129f22f99277c2f9d53
在學習者的專案裡，agent 一直在修補 handoff.md 而不是覆寫它，直到它自相矛盾；把每個答案都記進 progress.md；並且把計畫和被取代的規則留在專案指示裡。現在 handoff.md 有固定格式（Now、Next step、Paused；最多 40 行），而且整份重寫；progress.md 是每個主題一列，加上反覆出現的模式；專案指示只放一直成立的東西，被取代的規則就在原處改寫。

## 24e5bea85a096f51124d90b6bc6964c240595655
從 STATE 刪掉已經解決的 SourceOfPastInfo 項目

## a9e8a025c4686a1a1eebe3ba17e8a6b3ac845359
三個時區無法確定的 session 日期維持原樣

## a63217044b1c7e7b2037497385bb031c7aaa64ce
學習者說確切是哪一天不重要，只要順序對就好，所以時區無法確定的那幾個 session 維持當初寫的日期。

## 8f6c889e81b9567332484e649c11b1b4d61e53d9
在模板中只記錄英國日期，從不寫時刻

## a8ea5a1ddc96b7a3cd07728a329720e9273ec9cb
學習者的電腦在不同時區（Windows 是英國時間，Mac 是香港時間），有三個專案在同一個檔案裡混用了兩種時間。現在每個日期都是用強制指定時區的指令取得的英國日期，任何檔案和訊息都不寫時刻，改用順序取代時間：session 檔案命名為 YYYY-MM-DD-NN-<agent>.md，decisions.md 由舊到新排列。

## 68670002d27966a8a5b59396498556cbd3c86795
更新 SparkForge 到 0.2.1

## 476ca219f2003abb5b4003b3d2a1d2b6974b8c64
update-kit.sh 不再卡在登入提示：它會在幾秒內失敗，並印出 SSH 格式的網址。這次更新也是 0.2.0 帶來的自我複製更新器第一次真正執行。

## 319dddf6cd59743be426cfa5e25f25ae64d6d2b7
更新 SparkForge 到 0.2.0，並把規格搬到 SPEC.md

## 8fcd678a79eea683b75d9d3ecf673914986cbeae
kit/ 透過這個專案自己的 update-kit.sh，經由 SSH 從 SparkForge 取得，這是它第一次從真正的遠端拉到真正的改動。其餘部分手動複製一次，因為 update-kit.sh 只寫 kit/：腳本變成指向 kit/scripts/ 的 stub、入口檔案提到 SPEC.md、AGENTS.md 加入邊做邊寫 memory 的規則、新的 Environment facts 註解和 SPEC.md 匯入、METHOD.md 換上新的分類、STATE.md 加了 Upstream 段落。這個專案自己的標題、facts 和規則沒有改變。

## 774f2c666bb95c2b5b470ad6df7318b100bd268a
模板規格一字不改地從 STATE.md 搬到 SPEC.md，放在自己的標題下。Environment facts 裡的每個「none」現在都附上原因，照框架現在的要求。

## f806528916f3cafa84a8710583cc87bf41dd1292
在模板框架加入節奏和易讀性的規則

## 4d03d8c48520333ea105e8c5912c405397e1278d
一次只教一小塊，往下之前用一個檢查問題確認理解，學習者跟不上時拆得更小，一次只問一個問題，並用短段落和 emoji 標示讓聊天和黑板都好讀。這適用於每個專案和每種模式；專案指示可以收緊它，但不能放寬。

## 82d8f2803d0705ca20a2672ef1ab25a603570fb2
一整題的往來都留在黑板上

## 6780f39fa4f43b9e7e4c8ddc5eefb336accfcfba
在同一題裡，agent 會把學習者的答案、回饋和提示接在題目下面，而不是覆寫；只有到下一題、把值得保留的存好之後才清空黑板。這是從學習者的 MATH2121 專案學來的，那裡的 agent 自己採用了這種做法。

## 7c0adcf15c3e7bca13364cae5bceaa529d7d6d81
讓 README 的 clone 指令指向 GitHub repository

## 186bada43171f31291bf18b191d9c5e7c5e72fef
把佔位符換成 HTTPS 網址，不需要 SSH key 也能用。這個 repository 目前是私人的，所以 clone 需要權限。

## e13f6c9669e44c7d1a7d989e00a7cfa813b586ac
在黑板檔案上教學，每個時間都讀系統時鐘

## 583230866748f921ae8c0d6b41bed2c819841051
所有教學內容現在都寫在 materials/generated/blackboard.md，.vscode/settings.json 會把它以排版好的 Markdown 預覽打開；聊天只留簡短訊息，因為 VS Code 的聊天面板和終端機 agent 都不會排版 LaTeX。這是從學習者第一個真實專案裡 agent 建立的做法學來的。

## 2a377e2c084909d610bbd99f339ebb5f7c8cdd14
也是從那個專案來的：有一個 handoff 的時間戳記比實際快了 35 分鐘，所以現在每個日期和時間都在寫入時從系統時鐘讀取。學習者同意的長期改變會立刻寫進專案指示，因為下一個 agent 一定會載入那一段。

## 3cec5f802b282ee8ef396658b6e9841230218ca9
加入英文、繁體中文和簡體中文的 README

## 3b54477be0dd7bb96cfd932e34a148c81407a6ed
用白話說明模板是什麼、怎麼開始一個新科目或搬移 Claude Project、怎麼換 agent，以及每個資料夾放什麼。複製指令在 Windows 和 bash 上都跑過。clone 網址在 repository 有遠端之前先用佔位符。

## 2d689e4d9297acb372e439d388cde2622b37b699
支援搬移 Claude Project 和專案專屬的指示

## 087e71776967caaef25b01d6891541d347898265
設定現在先問語言，再問是新科目還是搬移。新科目流程會根據學習者的回答起草英文的專案指示；搬移流程會翻譯現有的 claude.ai Project 指示、改寫只在 claude.ai 有效的機制，並用貼上的狀態摘要作為 handoff.md 的起點。專案指示放在 AGENTS.md 的一個段落裡，在「怎麼教」上優先，但不能關掉記憶規則、教材唯讀，以及 AGENTS.md 和 memory/ 用英文這幾條。加入 materials/generated/obsidian/，附上通用的 Obsidian 格式規則。

## d21b86f8bf5bd8218c46a5f3dff65377bb54ce86
加入學習專案模板的第一版

## c6d3b675e57fe83fcc46752a4ffc39a1c737879c
template/ 放著複製即用的檔案：帶有設定流程、模式和邊做邊寫記憶規則的 AGENTS.md、匯入它的 CLAUDE.md stub、記憶檔，以及教材、產生內容和 session 摘要的佔位資料夾。AGENTS.md 開頭有一段防護，讓在這個 repository 工作的 agent 不會照著模板的規則行動；只用 Claude Code 探測過。

## b8263865c46d97667199e1e4be7fbef6657e866d
Bootstrap：記錄批准的模板規格和環境資訊

## 2841cb8ce0f1007236c1005d435b08cff2f3942a
把批准的複製即用學習專案模板規格寫進 STATE.md，並把 AGENTS.md 裡的每個環境資訊都設為「none」：交付的東西只有 Markdown，所以驗收是用真的 agent 手動跑。

## d71be5322d22c74a649bcaba50ad834399fb8f3f
採用 SparkForge

## f36a507933dc42fbbfa0c9aa7a8becf36fb27ec9
模板規則

## 3147fe1fe878f2e0841a12789801136876f79f8b
每個 agent 都要遵守的開始流程、設定、模式和記憶規則

## bdf1aff7f78e505bb6093031422dda7456398bfc
Claude Code 指引

## b28b43887683ed3347a0e1ad8d93ba2e82683024
讓 Claude Code 去讀模板的 AGENTS.md

## 435989002506bb2a3ffae09600f72849264cc8e6
記憶

## 8ad03ce23db361634af1cae764ce9a361a85bfd3
每個 agent 都會讀寫的 handoff、progress、決策、待辦和 session 檔案

## baf817d03a3140f1b4b8eb27bd9430067ebdadaa
教材

## 1cfc6a4d1ae19ef024026374e424829d5ba8f902
學習者的原始教材（從不修改），以及 agent 做的東西，包括黑板

## d5447b10aba471e3900e69b84fc7d3ecc86b22ea
黑板顯示

## f3ba9842ea732c704e41381addbeaf73ad375ce1
把黑板以排版好的預覽打開，並開啟數學式

## 47b7d356ebe14560a845003318c7472b3a90ae66
把規格改成標準格式，並更新 SparkForge 到 0.8.2

## 58312ee83de3463c3d1215df6ab8e2507a77fca4
進度頁在這裡讀不到任何目標和驗收標準：SPEC.md 只有一段 Goal 文字，驗收項目只有編號、沒有 id。現在那個目標拆成了五個功能，連到八條驗收標準，並加上 M1、五個元件、三個已完成目標的 How 和 Parts，以及根據已記錄測試整理的狀態行。進度頁設為繁體中文，並且全部翻譯好了。
