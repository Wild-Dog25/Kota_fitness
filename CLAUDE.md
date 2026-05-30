# Kota Fitness LP — CLAUDE.md

パーソナルトレーナー「谷内 康太（TANIUCHI KOTA）」氏の集客用ランディングページ（1ページ完結）。

---

## 構成ファイル

| ファイル | 役割 |
|---|---|
| `index.html` | LP本体（セクションごとにコメントで区切り） |
| `style.css` | スタイル定義（セクション順に並ぶ） |
| `script.js` | jQuery 用の拡張枠（現状ほぼ未使用） |
| `README.md` | 元プロジェクト説明 |
| `*.png` / `*.jpeg` | 画像アセット |

外部依存：Bootstrap 5.3.2（CDN）/ Google Fonts（Anton, Bebas Neue, Noto Sans JP, Zen Kaku Gothic New）。

---

## ページのセクション順序

集客LPの定石「人物紹介 → 共感 → 解決策 → 申込導線」に従っている。**追加・並び替えはこの流れを崩さないこと**。

1. **HERO** — キャッチコピー＋背景画像
2. **TRAINER**（私の想い） — 想いと顔写真、1stCTA
3. **PROFILE**（自己紹介） — 名前・経歴・想いの詳細
4. **CONCERNS**（こんなお悩み） — 共感パート、3×2グリッドの6項目
5. **REASONS**（選ばれる4つの理由） — 差別化、4カラム
6. **METHOD**（習慣メソッド） — ロジック説明、縦線2分割（左：理論／右：箇条書き）。背景黒
7. **SUPPORT**（オンライン少人数サポート） — 提供内容、縦線2分割（左：内容＋箇条書き／右：料金案内）
8. **STEPS**（体験までの4ステップ） — フロー、4カラム
9. **GIFT**（ご登録者限定プレゼント） — 3つのスプレッドシート + 追加特典ボックス
10. **FAQ**（よくあるご質問） — Q/A縦並びリスト形式
11. **FINAL CTA** — 最後の一押し
12. FOOTER

---

## デザインシステム

### カラー（`:root` の CSS 変数）
| 変数 | 値 | 用途 |
|---|---|---|
| `--orange` | `#FF5A1F` | アクセント・CTA・強調 |
| `--orange-bright` | `#FF7A3D` | ホバー時 |
| `--orange-deep` | `#E04812` | プレス時 |
| `--black` | `#1a1a1a` | METHODセクション背景・見出し |
| `--bg-white` / `--bg-cream` / `--bg-mid` | 背景色 |
| `--gray-700` / `--gray-500` / `--gray-300` / `--gray-200` | テキスト・ボーダー |

### フォント
- 見出し（h1〜h4）：`Zen Kaku Gothic New`（900）
- 本文：`Noto Sans JP`（400）
- 番号・英字ラベル：`Anton`
- 一部英字：`Bebas Neue`

### 共通パターン

#### セクションタイトル
```html
<div class="section-title-block">
  <span class="en-label">REASONS</span>
  <div class="orange-line"></div>
  <h2>選ばれる4つの<span class="emphasis">理由</span></h2>
</div>
```
- `.en-label`：英字の大きい飾り
- `.orange-line`：オレンジの短い区切り線
- `.emphasis`：オレンジ色＋1.25emサイズ＋薄い下線。**強調したい部分は必ずこのクラスを使うこと**

#### カードのバリエーション
- `.concern-card`：白背景＋オレンジ下ボーダー（CONCERNS）
- `.reason-card`：白背景＋グレーボーダー、ホバーでオレンジボーダーに（REASONS, STEPS）
- `.step-card`：reason-card と同じデザイン
- `.support-card` / `.gift-bonus`：オレンジボーダーの強調枠

#### 番号表記
- CONCERNS / REASONS / STEPS は **1〜N（ゼロ埋めなし）**、Anton フォント、オレンジ
- GIFT のみ **01〜03**（`.gift-num-badge` がボーダーボックス型）
- 数字は中央揃え

#### 縦線2分割レイアウト（METHOD / SUPPORT）
```html
<div class="method-split">
  <div class="method-left">...</div>
  <div class="method-divider" aria-hidden="true"></div>
  <div class="method-right">...</div>
</div>
```
- METHOD は黒背景に白文字、SUPPORT は `.support-section` 側で色味を上書き
- モバイル（767px以下）では縦並びに切り替わり、分割線が水平線に

---

## 文章のトーン

- **対象読者**：本気で変わりたい働く男性
- **トーン**：力強く、実体験ベース、共感重視
- **NGワード**：「だらしない」「雑な」など過度にネガティブ・断定的な表現は避ける（過去に削除済）
- **CTA文言は「LINEで無料相談する」に統一**。`https://forms.gle/g9y6FPXJ8mKJ7MPN9` がデフォルトリンク（LINE導線に差し替える可能性あり）
- 「無料Zoom問診」「Zoom問診」という旧表現は使用しない

---

## 画像アセット

### 使用中
- `トレーナー本命.png` — TRAINER顔写真
- `お悩み1.png` 〜 `お悩み6.png` — CONCERNSの各カード

### 未使用（プレースホルダーのまま）
- HERO画像
- GIFT用シート画像3点
- PROFILE画像2点 + サブ画像

### 過去に使ったが今は未参照
- `trainner.jpeg`, `ベンチプレス_オレンジ服.png`, `仕事_オレンジ服*.png`, `続かない_オレンジ服*.png`, `食事制限_*.png`

---

## 編集時のお作法

1. **既存ファイルを優先編集**。新規ファイル作成は明示的に頼まれない限りしない。
2. **強調するときは `<span class="emphasis">...</span>` を使う**。色だけの強調を直書きしないこと。
3. **セクション追加時は連番を維持**（`<!-- ============ N. NAME ============ -->`）。
4. **箇条書きは `.method-list` を再利用**（オレンジドット付き）。SUPPORTセクションの白背景での色補正は `.support-section .method-list li {}` で対応済み。
5. **CTAボタンのラベルは「LINEで無料相談する」**（最終CTAのみ `cta-button-invert` で配色反転）。
6. **行内の `<br>` は意味のある位置にのみ使う**。長文の中段で雑に改行しない。
7. **絵文字は使わない**（明示指示がない限り）。

---

## 残課題（既知）

- HERO・GIFT・PROFILE のプレースホルダー画像差し替え
- 公式LINEのリンクURLが未確定（Googleフォームのまま）
- METHOD右側の箇条書きは3項目、SUPPORTは4項目（揃えるかは未確定）

---

## 直近の主要変更履歴

- セクション順序の入れ替え（TRAINER直後にPROFILE、CONCERNS→REASONSの順に）
- CONCERNSを4項目→6項目（3×2グリッド）
- METHODとSUPPORTを縦線2分割レイアウトに統一
- 各セクションタイトルに `.emphasis` クラスで部分強調
- FAQの構成を縦並びQ/Aリスト形式に統一
- セクション余白を `7rem → 5.5rem`（モバイル `3.5rem`）に圧縮
- 全CTAを「LINEで無料相談する」に統一
