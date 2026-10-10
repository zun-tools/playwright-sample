# 買い物メモ（Playwright 再入門のサンプル）

YouTube「ずんだもんの実験道具箱」の動画「Playwright 再入門」で使ったサンプルです。動画と同じ中身を保つため、公開後は書き換えません。

品物を足してチェックする 1 画面の静的 HTML（`index.html`）と、Playwright のテスト 1 本（`tests/shopping.spec.js`）。

```bash
npm install
npx playwright install chromium
npx playwright test            # 緑になる
```

## ボタン名を変えて、AI なしで赤くする

`index.html` のボタン名「追加」を「入れる」に変えて、もう一度走らせる。

```bash
npx playwright test            # 赤になる（既定では 30 秒待つ）
```

## 空のフォルダから自分で入れる

```bash
npm init playwright@latest -- --quiet --browser=chromium --lang=js --no-examples
npx playwright init-agents --loop=claude
```

そのあと `playwright.config.js` に次の 3 か所を足し、`tests/seed.spec.ts` に `await page.goto('/');` を書く（このサンプルの `playwright.config.js` と同じ）。

- `use` に `baseURL: 'http://localhost:8080'`
- 末尾に `webServer`（`npx http-server -p 8080 -s .` で `index.html` を配る）
- `reporter: [['list'], ['html', { open: 'never' }]]`

## 試した環境

2026-10-10 時点・Linux（arm64）・Node.js 22・Playwright 1.64.0・Claude Code 2.1.296。Mac と Windows は確かめていません。

## ライセンス

MIT
