# ET-shiamy

免安裝、不需管理員權限的第三方**嘸蝦米輸入法**（Windows only）。

**這個 repo 只放釋出的版本，沒有原始碼。**
到 [Releases](https://github.com/0100Light/eat-shiamy-releases/releases/latest)
下載 `ET-shiamy-x.y.z.zip`。

（GitHub 會在每個 release 底下自動附一個 `Source code (zip)`，
那是它自己加的、內容是空的，不要下載那一個。）

## 安裝

1. 下載 `ET-shiamy-x.y.z.zip`
2. 解壓縮到任何你有寫入權限的資料夾（**不要放在 `C:\Program Files\` 底下**）
3. 執行裡面的 `shiamy.exe`

整個資料夾就是程式本身，搬到哪裡都能跑，也可以放隨身碟。
要移除就把資料夾刪掉，不會在系統裡留下任何東西 ——
它不寫登錄檔、不裝服務、不需要管理員權限。

詳細用法看資料夾裡的 `manual.html`。

### 第一次執行會被 Windows 攔下來

因為這支程式沒有數位簽章（那需要付費憑證）。

- **SmartScreen**「Windows 已保護您的電腦」→ 點「**其他資訊**」→「**仍要執行**」
- **Smart App Control**（Windows 11 全新安裝預設開啟）會直接擋掉而且沒有放行選項。
  只能先把它關掉，或改用其他輸入法。

另外**第一次啟動會比較慢**（十幾秒），那是 Windows Defender 在掃描
資料夾裡的幾百個檔案。掃過一次就不會再慢了。

## 自動更新

程式會自己檢查有沒有新版、自己下載，然後在狀態列上顯示「重啟更新」，
點一下才會套用 —— 不會在你打字打到一半自己重開。

更新前的版本會完整留在 `plugin\rollback\`，隨時可以換回去：

- 新版還能用：執行 `shiamy.exe --rollback`
- 新版開不起來：雙擊 `plugin\rollback\rollback.cmd`

不想自動更新的話，把 `plugin\window_config.json` 裡的
`update_check` 改成 `false`。

## 這是什麼、不是什麼

它**不是** TSF/IMM 輸入法模組 —— 那種要註冊到系統、需要管理員權限。
這支是外掛式的做法：攔截按鍵之後合成輸入，再用一條置頂的狀態列當候選字視窗。
代價是它跟系統輸入法是兩套東西，切換方式也不一樣（預設單按 Shift）。

## 授權與來源

程式本身是原創，但它用到幾份別人的東西，在此致謝並標明歸屬：

| 來源 | 用途 | 授權 |
|---|---|---|
| [RIME 蝦米方案](https://github.com/RIME/rime-liu)（liur） | 字根表 `liur_Trad.dict.yaml` 等 | 第三方重製碼表，見下 |
| [OpenCC](https://github.com/BYVoid/OpenCC) | 繁簡對照表 `ts_map.json`（衍生自 `TSCharacters.txt`） | Apache-2.0 |
| [vim-airline](https://github.com/vim-airline/vim-airline-themes) | 狀態列的配色 | MIT |

**嘸蝦米輸入法本身是行易有限公司的商標與產品。** 這支程式與行易公司無關，
也不是官方版本。隨附的字根表是網路上早已公開流通的第三方重製版本，
不是官方的 `liu-uni.tab`。如果你需要官方版本、官方碼表或商業支援，
請洽 [行易嘸蝦米](https://www.liu.com.tw/)。
