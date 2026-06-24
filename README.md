# IMURU Inc. — Corporate Site

> 「遊びから、未来を作る。」

IMURU Inc.（未来創造研究企業）のコーポレートサイトです。
HTML / CSS / JavaScript のみで構成されたシングルページで、外部ライブラリやビルドツールに依存しません。

---

## 🧬 概要

- 架空の研究企業「IMURU Inc.」のブランドサイト
- 背景にループ動画を敷いたダーク系デザイン
- アクセスするたびに「研究員ランク」「レベル」が上がるミニゲーム要素付き
- レベルに応じて事業部門ページがアンロックされる仕組み

## 📁 ファイル構成

```
.
├── index.html                                  # サイト本体（HTML/CSS/JS）
└── motion_2.0-fast_A_single_amoeba_...mp4      # 背景に再生するループ動画
```

> 動画ファイルは `<video class="bg-video">` の `src` で参照しています。
> 同階層に配置するか、パスを実際のファイルに合わせて変更してください。

## 🔍 ページ構成

| セクション | 内容 |
|---|---|
| Hero | ロゴ・キャッチコピー・スクロール誘導 |
| Corporate Philosophy | 企業理念 |
| Leadership | CEO紹介（`ceo.html` へリンク） |
| Business Division | 事業部一覧（一部レベル制限あり） |
| Careers | 採用情報（無償参加・見学者・バナナ供給担当など） |
| Today's Research / Future Message | ランダム表示される研究メッセージ |
| Footer | コピーライト表記 |

## 🔒 レベル / ロック機構

ページ最上部のステータスバーに、訪問回数に応じた以下の情報を表示します（`localStorage` で管理）。

- **研究ログ（訪問回数）**：`imuru_visits` に保存され、アクセスごとに加算
- **LEVEL**：`Math.floor(訪問回数 / 10) + 1` で算出
- **研究員ランク**：訪問回数に応じて変化

| 訪問回数 | ランク |
|---|---|
| 0〜 | 見習い研究員 |
| 10〜 | 研究員 |
| 50〜 | 主任研究員 |
| 100〜 | 上級研究員 |
| 1000〜 | 伝説研究員 |

事業部タイルは `data-required-level` 属性でロック条件を指定できます。現在のレベルが満たない場合、リンクが無効化され `🔒 LV.◯で解放` バッジが表示されます。

```html
<a class="division-tile lockable" href="ideas.html" data-required-level="10">
```

| 部門 | 必要レベル |
|---|---|
| 企画研究部（Idea Development） | LV.10 |
| 言語研究部（Language Research） | LV.50 |
| 遊び研究部（Entertainment） | LV.100 |

## 🎨 デザイン

- フォント：Google Fonts（`Space Grotesk` / `JetBrains Mono` / `Megrim` / `Zen Kaku Gothic New`）
- カラーパレット：ダークネイビー × シアン × ゴールド（CSS変数 `:root` 内で一括管理）
- レスポンシブ：`max-width:700px` でモバイル向けレイアウトに切り替え

## 🛠 カスタマイズ方法

- **背景動画を変更**：`.bg-video` 内の `<source src="...">` を差し替え
- **メッセージ・発想カードを追加**：`<script>` 内の `messages` / `ideas` 配列に文言を追加
- **配色を変更**：`:root` 内の `--cyan` / `--gold` / `--bg-*` などの変数を編集
- **新しい事業部を追加**：`.division-grid` 内に `.division-tile` を複製し、必要に応じて `lockable` クラスと `data-required-level` を付与

## 🚀 使い方

ビルド不要です。`index.html` をブラウザで直接開くか、任意の静的ホスティング（GitHub Pages, Netlify, Vercel など）にそのままデプロイしてください。

```bash
# ローカルで確認する場合（例: Python の簡易サーバー）
python -m http.server 8000
```

ブラウザで `http://localhost:8000` にアクセスして確認できます。

## 📄 ライセンス

社内利用想定のため未設定。必要に応じて追記してください。

---

IMURU Research Network © 2026
