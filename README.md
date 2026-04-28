# Kiriya Tools — プロダクトポートフォリオサイト

## プロジェクト概要
個人開発ブランド「Kiriya Tools」の公式ポートフォリオサイト。  
月額不要・買い切りのシンプルなWebツールを紹介するランディングページ。

---

## 完成済み機能

| セクション | 内容 |
|---|---|
| ナビゲーション | スティッキー固定・スクロールによるアクティブハイライト |
| ヒーローセクション | キャッチコピー・CTAボタン・背景グラデーション |
| ツール一覧（Products） | 商品カード1枚 + Coming Soonカード2枚（グリッドレイアウト） |
| 特徴（Features） | 3カラム アイコン＋テキスト |
| Aboutセクション | 開発者紹介・Tech Stackバッジ |
| フッター | お問い合わせボタン・Xリンク（コメントアウト済み）・コピーライト |
| スクロールフェードイン | IntersectionObserver による控えめアニメーション |
| レスポンシブ対応 | PC3列 → タブレット2列 → スマホ1列 |

---

## ファイル構成

```
index.html              ← ポートフォリオトップページ（CSS・JSインライン）
invoice/
  └── index.html        ← 請求書自動作成ツール（ライセンスキー認証つき）
README.md
```

---

## カスタマイズガイド

### 🛒 商品カードを追加する
`index.html` の以下のコメントを探し、その直後に商品カードブロックをコピー＆ペーストしてください。

```html
<!-- 新しい商品カードをここにコピー -->
```

商品カードのテンプレート:
```html
<article class="product-card fade-in">
  <div class="product-icon">🔧</div>                   <!-- 絵文字アイコンを変更 -->
  <p class="product-name-en en">Tool Name</p>          <!-- 英語ツール名 -->
  <h3 class="product-name-ja">ツール名（日本語）</h3>
  <p class="product-desc">説明文をここに。</p>
  <div class="product-tags">
    <span class="tag">タグ1</span>
    <span class="tag">タグ2</span>
  </div>
  <div class="product-footer">
    <div>
      <div class="product-price en">¥X,XXX<small>（税込・買い切り）</small></div>
    </div>
    <a href="https://your-tool-url.com" class="btn-detail en">
      詳しく見る
      <svg width="13" height="13" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><path d="M5 12h14M12 5l7 7-7 7"/></svg>
    </a>
  </div>
</article>
```

### 📬 お問い合わせリンクを設定する
2箇所の `href="#contact-form"` をGoogleフォームのURLに変更:
```html
<!-- 変更前 -->
<a href="#contact-form" ...>

<!-- 変更後（例） -->
<a href="https://forms.gle/xxxxxxxxxxxx" ...>
```

### 𝕏 X（Twitter）リンクを有効にする
フッター内の以下のコメントブロックを解除し、アカウント名を追加:
```html
<!-- 解除して href を変更 -->
<a href="https://x.com/あなたのアカウント名" ...>
```

### 🔗 商品詳細リンクを設定する
各商品カードの `<a href="#">` を実際のURLに変更:
```html
<a href="https://your-product-url.com" class="btn-detail en">
```

---

## ライセンスキーの管理（Invoice Generator）

`invoice/index.html` 内の以下の配列にキーを追加してください:

```javascript
var VALID_KEYS = [
  "DEMO-DEMO-DEMO-DEMO",   // デモキー（本番では削除推奨）
  "KIRIYA-XXXX-XXXX-XXXX", // 購入者へ発行したキーを追加
];
```

- **デモキー** `DEMO-DEMO-DEMO-DEMO` はウォーターマークが強制表示されます
- **製品版キー** はウォーターマーク非表示がデフォルト
- 認証後はブラウザの `localStorage` にキーが保存され、次回以降は自動解除されます

---

## 未実装・今後の追加候補

- [ ] OGP画像（`og:image`）の設定
- [ ] Google Analytics / アクセス解析の埋め込み
- [ ] 商品詳細ページ（個別HTML）
- [ ] X アカウント開設後のソーシャルリンク有効化
- [ ] Coming Soonカードへの「通知登録」フォームの追加

---

## デザイン仕様

| 要素 | 値 |
|---|---|
| アクセントカラー | `#2563eb` |
| テキストカラー | `#1e293b` |
| ミュートテキスト | `#64748b` |
| バッジ背景 | `#e0edff` |
| 日本語フォント | Noto Sans JP（Google Fonts） |
| 英語フォント | Inter（Google Fonts） |

---

## 注意事項
- 開発者の本名・メールアドレス・個人を特定できる情報は含まれていません
- 外部ライブラリ依存なし（Google Fonts のみ使用）
- 1ファイル完結型（`index.html`）

---

© 2025 Kiriya Tools
