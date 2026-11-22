# 阿古的成品庫（my-works）

阿古所有成品的總目錄。不管是哪一個 Claude 帳號做的成品，都加在這裡。

- 網站：https://duke797-7.github.io/my-works/
- 分支：**`gh-pages`**（只有這一個分支，GitHub Pages 從這裡發布）。**直接推到 `gh-pages`，不要開 PR、不要開新分支**，推上去一兩分鐘後網站就會更新。
- 一律用繁體中文回覆阿古；他只用 Android 手機，不要叫他用電腦。

## 新增一個成品（給 Claude 的步驟）

1. 打開 `works.json`（一個陣列，一行一筆），在**最後面**加一筆。不要改別人的資料、不要重新排序整份檔案。
2. 有封面的話：截圖或拿成品裡的宣傳圖，裁成 **1200×750 的 JPG**（品質 80 左右，200 KB 以內），放到 `covers/<id>.jpg`，`cover` 填 `"covers/<id>.jpg"`。截不到圖就把 `cover` 留空 `""`，填一個 `emoji`，網站會自動做彩色封面。
3. 推上 `gh-pages` 之後，打開網站確認那一格有出現，再把網址回報給阿古。

### 一筆的格式

```json
{"id":"claude-XXXX","title":"成品名稱","kind":"game","stage":"done","date":"2026-11-22","url":"https://…","desc":"一句話介紹","cover":"","emoji":"🎮","place":"Claude","account":"帳號名稱","links":[{"name":"後台","url":"https://…"}],"hidden":false}
```

| 欄位 | 說明 |
|---|---|
| `id` | 不能重複。Claude 成品用 `claude-` 加網址最後那段；網站用網址（英數字和 `-`）。 |
| `title` | 成品名稱 |
| `kind` | 做出來是什麼，只能填其中一個：`game` 遊戲（能玩的）、`tool` 工具（能拿來用的：點餐、記帳、管理、預購…）、`page` 網頁（活動、報名、商品介紹、影片頁）、`design` 設計稿（設計圖、示範畫面、特效預覽、3D 模型）、`doc` 文件（企劃、報告、教學步驟、FAQ）、`sheet` 試算表、`slide` 簡報 |
| `stage` | 做到哪裡，只能填其中一個：`live` 上線中（推到 Netlify／Cloudflare／GitHub Pages 等正式網址、大家打得開）、`done` 已完成（做好了，放在 Claude）、`draft` 製作中（試做、原型、預覽、複本、還在改）、`dead` 網址失效、`locked` 需登入才看得到 |
| `date` | 做好或最後更新的日期，`YYYY-MM-DD` |
| `url` | 點進去的網址 |
| `desc` | 一句話介紹，短一點 |
| `cover` | 封面圖路徑，沒有就 `""` |
| `emoji` | 沒有封面時顯示的圖示 |
| `place` | 放在哪裡：Claude、Netlify、Cloudflare、GitHub Pages… |
| `account` | 哪個 Claude 帳號做的（阿古怎麼稱呼就怎麼填）。主帳號的成品填 `主帳號`，網站上不會特別顯示。 |
| `links` | 額外連結（後台、試玩版、GitHub…），沒有就 `[]` |
| `hidden` | 阿古說不要了就改成 `true`，網站就不顯示（資料留著，之後要還原改回 `false`） |

## 自動同步（每個帳號的每日排程任務）

1. 列出這個 Claude 帳號的所有成品（artifact），以及這個帳號連得到的 Netlify／Cloudflare／GitHub Pages 網站。
2. 用 `url` 跟 `works.json` 比對：已經有的（包括 `hidden: true` 的）**一律不動、不要重新加回來**；只把沒有的加在最後面。
3. 照上面的定義填好 `kind` 和 `stage`（舊的 `site`、`status` 不要再用）。`account` 填這個帳號的名稱。Claude 成品截不到圖，`cover` 留空、填 `emoji`；上線網站能截圖就做封面。
4. 有新增才 commit，直接推到 `gh-pages`。沒有新的就什麼都不做。

## 規則

- 只加阿古說要加的成品。
- 權杖、密碼不要寫進任何檔案。
- 不要改 `index.html`，除非阿古要改網站的樣子。
- 網站上的「整理／刪掉」只記在那支手機；阿古說「從成品庫拿掉 ○○」時，就把那一筆的 `hidden` 改成 `true` 推上去。
