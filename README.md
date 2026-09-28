# Kiriya Tools — プロダクトポートフォリオサイト

## プロジェクト概要
個人開発ブランド「Kiriya Tools」の公式ポートフォリオサイト。  
月額不要・買い切りのシンプルなWebツールを紹介するランディングページ。

**デザインコンセプト:** 「見ているだけ・触っているだけでも楽しい」を最優先にした、
動きのあるプレミアムな販売サイト。全編ハンドメイドのCSS/JSで、外部ライブラリは一切不使用。

---

## 完成済み機能

| セクション | 内容 |
|---|---|
| スクロールプログレスバー | ページ最上部のグラデーション進捗バー（アイドル時は自動フェード） |
| ナビゲーション | スティッキー固定・スクロールでガラス化・アクティブリンクのアンダーライン点灯 |
| モバイルメニュー | ハンバーガーが×にモーフィング・外側クリック/Escで閉じる |
| ヒーローセクション | オーロラ風グラデーション・粒子・文字ごとのスタッガー出現・3Dカードスタック |
| マーキー | 無限スクロールのキーワード帯（ホバーで一時停止） |
| ツール一覧（Products） | 商品カード7枚・3Dチルト・カーソル追従スポットライト |
| 特徴（Features） | ベントーグリッド・月額 vs 買い切りの累計コスト比較チャート（アニメーション） |
| レビュー（Reviews） | お客様の声 3件・星評価つきカード |
| FAQ | アコーディオン7問・排他開閉・スムーズな高さアニメーション |
| Aboutセクション | 開発者紹介・Tech Stackバッジ・実績スタッツ |
| CTA | オーロラ＋リングパルス・信頼バッジ |
| フッター | ナビリンク・お問い合わせ・Xリンク・プライバシー/規約リンク |
| フローティングクイックバー | スクロール中に出現する購入導線（閉じるとセッション中は非表示） |
| トースト通知 | ボタン操作時のフィードバック通知 |
| スクロール演出 | IntersectionObserver による方向別フェードイン＋数字カウントアップ |
| レスポンシブ対応 | PC3列 → タブレット2列 → スマホ1列 |
| アクセシビリティ | `prefers-reduced-motion` 対応・aria属性・キーボード操作 |

---

## インタラクション一覧（触って楽しい仕掛け）

すべて追加ライブラリなしのバニラJS。`requestAnimationFrame` でスロットリングしています。

1. **オーロラ背景** — 4つのブロブが独立した周期でゆっくり漂う（`drift1`〜`drift4`）
2. **3Dチルトカード** — 商品カードがカーソル角度に追従して傾く（補間つきで滑らか）
3. **スポットライト** — カーソル位置に合わせてカード内の光が移動
4. **マグネティックボタン** — CTAがカーソルにわずかに吸い寄られる
5. **カードスタック視差** — ヒーローのカードがマウスとスクロールに反応
6. **文字スタッガー** — 見出しが1文字ずつ回転しながら出現
7. **カウントアップ** — スタッツの数字がイージングしながら加算
8. **コスト比較チャート** — サブスクは伸び、買い切りは据え置きを視覚化
9. **FAQアコーディオン** — 排他制御＋`scrollHeight` による正確な開閉
10. **シマー（光の帯）** — ボタンやカード上を光が横切る

---

## ファイル構成

```
index.html              ← ポートフォリオトップページ（CSS・JSインライン）
invoice/
  └── index.html        ← 請求書自動作成ツール（ライセンスキー認証つき）
docflow.html            ← 見積書・納品書・領収書ジェネレーター
health-worklog.html     ← 健康管理・業務日報ツール
lecturenote-business.html ← 議事録・研修メモツール
business-card/          ← 名刺メーカー
ichimoku/               ← 一目均衡表チャート
fukuyakun/              ← ふくやくん（PWA）
privacy.html            ← プライバシーポリシー
terms.html              ← 利用規約
README.md
```

---

## カスタマイズガイド

### 🛒 商品カードを追加する
`index.html` の `<div class="products-grid">` 内に、既存のカードをコピーして追加します。

```html
<article class="pcard reveal d1" data-tilt>
  <div class="pcard-accent-bar"></div>
  <div class="pcard-body">
    <div class="pcard-icon-wrap">🔧</div>            <!-- 絵文字アイコン -->
    <p class="pcard-en en">Tool Name</p>             <!-- 英語ツール名 -->
    <h3 class="pcard-name">ツール名（日本語）</h3>
    <p class="pcard-desc">説明文をここに。</p>
    <div class="pcard-tags">
      <span class="ptag">タグ1</span>
      <span class="ptag">タグ2</span>
    </div>
  </div>
  <div class="pcard-footer">
    <div class="pcard-price-row-inner">
      <div><div class="pcard-price en">¥500</div><span class="pcard-price-note">税込・買い切り・永久利用</span></div>
      <span class="pcard-price-badge en">ONE-TIME</span>
    </div>
    <div class="pcard-btns">
      <a href="your-tool.html" class="btn-demo">無料で試す</a>
      <a href="https://buy.polar.sh/..." class="btn-detail en" target="_blank" rel="noopener">購入する <svg width="13" height="13" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.6" stroke-linecap="round" stroke-linejoin="round"><path d="M5 12h14M12 5l7 7-7 7"/></svg></a>
    </div>
  </div>
</article>
```

> **ヒント:** `data-tilt` を付けると3Dチルト、`reveal d1`〜`d5` で出現ディレイが付きます。
> 3D列に並べるため、カードは **3の倍数** で追加するとレイアウトが美しく揃います。

### 🎨 ブランドカラーを変更する
`:root` のカスタムプロパティを書き換えるだけでサイト全体に反映されます。

```css
:root{
  --blue:#2563eb;   /* メイン */
  --indigo:#6366f1; /* グラデーション相方 */
  --cyan:#06b6d4;   /* アクセント */
  --g-brand:linear-gradient(120deg,#6366f1 0%,#2563eb 42%,#06b6d4 100%);
}
```

### 📊 コスト比較チャートの数値を変える
`#features` 内の `.cost-chart` で、各バーの `--h`（高さ%）を編集します。

```html
<span class="cost-bar cost-bar--sub" style="--h:34%"></span>  <!-- サブスク累計 -->
<span class="cost-bar cost-bar--kt"  style="--h:2%"></span>   <!-- 買い切り（据え置き） -->
```

### 📬 お問い合わせリンクを設定する
Google フォームのURLは全3箇所（ナビ・FAQ横・CTA/フッター）に記載されています。
一括置換する場合:

```bash
sed -i 's|https://docs.google.com/forms/d/e/現行ID/viewform|https://forms.gle/新しいID|g' index.html
```

### 𝕏 X（Twitter）リンク
フッターの `https://x.com/KiriyaTools` をご自身のアカウントに変更してください。

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

- [ ] OGP画像（`og:image`）の設定 — 現在は `twitter:card` のみ `summary_large_image`
- [ ] Google Analytics / アクセス解析の埋め込み
- [ ] 商品詳細ページ（個別HTML）
- [ ] FAQの構造化データ（`FAQPage` JSON-LD）追加
- [ ] 購入完了後のサンクスページ

---

## デザイン仕様

| 要素 | 値 |
|---|---|
| メインカラー | `#2563eb` |
| インディゴ | `#6366f1` |
| アクセント（シアン） | `#06b6d4` |
| ダーク背景 | `#05070f` / `#0a0f1e` |
| テキストカラー | `#0b1220` |
| ミュートテキスト | `#4a5568` |
| 日本語フォント | Zen Kaku Gothic New（見出し）/ Noto Sans JP（本文） |
| 英語フォント | Inter（可変フォント・`ss01`/`cv11` 有効） |
| イージング | `--ease-out: cubic-bezier(.16,1,.3,1)`（登場）<br>`--spring: cubic-bezier(.34,1.56,.64,1)`（跳ね） |

### アニメーション方針
- 登場アニメは `IntersectionObserver` で1回だけ発火（`unobserve` でメモリ解放）
- 連続イベント（scroll / mousemove）は `requestAnimationFrame` でスロットリング
- `will-change` はアニメーション中のみ付与し、終了後に解除
- `prefers-reduced-motion: reduce` を尊重し、すべての動きを停止

---

## 動作検証済み

Playwright（Chromium）で以下を実測確認:

| 項目 | 結果 |
|---|---|
| コンソールエラー（desktop / mobile） | **0件** |
| ページエラー | **0件** |
| モバイル横スクロール（390px） | `scrollWidth === innerWidth === 390` ✅ |
| 横スクロール発生 | `pageXOffset = 0`（`overflow-x:hidden` で固定）✅ |
| 商品カード / ベントー / レビュー / FAQ | 7 / 4 / 3 / 7 件すべて描画 ✅ |
| FAQアコーディオン | 排他開閉・高さ計算ともに正常 ✅ |
| ナビアクティブリンク | スクロール位置に追従 ✅ |
| モバイルメニュー | 開閉動作 ✅ |
| コスト比較チャート | バー伸長アニメーション動作 ✅ |

---

## 注意事項
- 開発者の本名・メールアドレス・個人を特定できる情報は含まれていません
- 外部ライブラリ依存なし（Google Fonts のみ使用）
- 1ファイル完結型（`index.html` 内にCSS・JSをインライン）
- レビュー・スタッツは掲載用のサンプルです。実データに差し替えてください

---

© 2025 Kiriya Tools
