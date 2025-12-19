# Vite React Template

このリポジトリは、Vite + React + TypeScript をベースにした学習用テンプレートです。  
Sass と CSS Modules を利用して、コンポーネント単位でスタイルを管理できる構成になっています。

## 必要なバージョン

- Node.js: v23.7.0
- React: 19.2.0

## 使用技術

- Vite
- React 19 / TypeScript
- Sass (`.sass`)
- CSS Modules（例: `Counter.module.sass`）
- ESLint
- pnpm (パッケージマネージャー)

## セットアップ

```bash
# npmを使用する場合
npm install

# pnpmを使用する場合（推奨）
pnpm install
```

## 開発サーバーの起動

```bash
# npmを使用する場合
npm run dev

# pnpmを使用する場合
pnpm dev
```

ブラウザで `http://localhost:5173` を開きます。

## ビルド

```bash
# npmを使用する場合
npm run build

# pnpmを使用する場合
pnpm build
```

出力は `dist` ディレクトリに生成されます。

## プロジェクト構成

```
vite-react-template/
├── src/
│   ├── main.tsx                    # エントリーポイント
│   ├── App.tsx                     # メインコンポーネント
│   ├── App.sass                    # アプリ全体のスタイル
│   ├── components/                 # コンポーネント
│   │   ├── MemoryGame/            # メモリーゲーム
│   │   │   ├── MemoryGame.tsx
│   │   │   ├── MemoryGame.module.sass
│   │   │   ├── useMemoryGame.ts
│   │   │   ├── components/
│   │   │   │   ├── Card/
│   │   │   │   ├── Counter/
│   │   │   │   └── Modal/
│   │   │   └── utils/
│   │   └── ClickGame/             # クリックゲーム
│   │       ├── ClickGame.tsx
│   │       ├── ClickGame.module.sass
│   │       └── useClickCounter.ts
│   └── styles/                     # グローバルスタイル
│       ├── reset.sass
│       ├── mixins/
│       └── variables/
└── tools/                          # 開発ツール
    └── imageCompile/               # 画像圧縮ツール
        ├── README.md
        ├── package.json
        └── imageCompile.ts
```

## 画像圧縮ツール

TinyPNGと同等の高品質な画像圧縮ツールが含まれています。

### セットアップ

```bash
cd tools/imageCompile
npm install
```

### 使用方法

```bash
cd tools/imageCompile
npm run compress        # デフォルト品質（70）
npm run compress:80     # 品質80
```

詳細は [`tools/imageCompile/README.md`](tools/imageCompile/README.md) を参照してください。

## スタイル構成

- **グローバルスタイル**: `src/styles/` にmixinや変数を配置
- **コンポーネントスタイル**: CSS Modulesを使用（`.module.sass`）
- **自動インポート**: Viteの設定により、mixinと変数は自動的にインポート

## メモ

- 型安全を意識して、React コンポーネント・状態・イベントハンドラには TypeScript の型を積極的に付けています。
- コンポーネントは `src/components/コンポーネント名/` の形式で管理しています。
- 複雑なコンポーネントは、さらに `components/` サブディレクトリで整理しています。
