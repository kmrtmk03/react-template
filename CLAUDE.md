# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## コマンド

```bash
# 開発サーバー起動
pnpm dev

# ビルド（TypeScript チェック + Vite ビルド）
pnpm build

# Lint
pnpm lint

# ビルド結果のプレビュー
pnpm preview
```

パッケージマネージャーは **pnpm** を使用すること（npm も使用可能）。

## アーキテクチャ概要

### メインアプリ (`src/`)

- **エントリーポイント**: `main.tsx` → `App.tsx`（BrowserRouter でルーティング設定）
- **スタイル**: Sass (`.sass` インデント記法) + CSS Modules。Tailwind は使用しない
- **アニメーション**: Framer Motion / GSAP がセットアップ済み
- **ルーティング**: React Router DOM v7。`App.tsx` に `<Routes>` を定義する

### Sass 自動インポート

`vite.config.ts` の設定により、すべての `.sass` ファイルで以下が自動的に利用可能：

- `v.変数名` → `src/styles/variables/_index.sass` 経由（color, layout, z-index）
- `m.mixin名` → `src/styles/mixins/_index.sass` 経由（media-query, size, margin, padding, position, font, background, utility）

メディアクエリのブレークポイントは `sp: 768px` のみ定義済み（`m.mq-sp()` / `m.mq-pc()` / `m.mq-custom()`）。

### ディレクトリ規則

- `src/components/` — 再利用可能な React コンポーネント
- `src/hooks/` — カスタムフック（例: `useScrollLock.ts`）
- `src/libs/` — ユーティリティ・外部ライブラリのラッパー（例: `TimeUtil.ts`）
- `src/styles/` — グローバルスタイル定義（コンポーネントに直接関係しない Sass のみ）

### 開発補助ツール (`tools/`)

メインの `node_modules` とは完全に独立した独自パッケージ。それぞれのディレクトリで `npm install` が必要。

| ツール | 用途 | 入力 | 出力 |
|---|---|---|---|
| `imageCompile` | PNG/JPEG 高品質圧縮 | `origin/` | `out/` |
| `image-webp-converter` | WebP 一括変換 | `origin/` | `out/` |
| `sprite-splitter` | スプライトシート分割 | `original/` | `out/` |

```bash
# 例: 画像圧縮（品質80）
cd tools/imageCompile && npm install && npm run compress:80

# 例: WebP 変換
cd tools/image-webp-converter && npm install && npm run convert
```
