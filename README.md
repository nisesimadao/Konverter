# Konverter

[![CI](https://github.com/nisesimadao/Konverter/actions/workflows/ci.yml/badge.svg)](https://github.com/nisesimadao/Konverter/actions/workflows/ci.yml)
[![Release](https://img.shields.io/github/v/release/nisesimadao/Konverter)](https://github.com/nisesimadao/Konverter/releases/latest)
[![License: MIT](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)

**Finder の「このアプリケーションで開く」から、その場でメディアを別形式へ変換する macOS 向けデスクトップコンバーター。** 通常起動では変換画面として、ファイルから開いた場合は小さなクイック変換ウィンドウとして動作します。

## できること

- 動画・音声・画像を FFmpeg で相互変換
- PNG / JPEG / BMP / TIFF / GIF などの画像変換は Jimp でも処理
- Finder の **このアプリケーションで開く** から対象ファイルを直接渡せる
- 同名ファイルがある場合は上書きせず、自動で連番を付ける
- Electron の `contextIsolation` を有効にした最小構成

## ダウンロード

ビルド済みアプリは [Releases](https://github.com/nisesimadao/Konverter/releases/latest) にあります。

> 配布バイナリは未署名の場合があります。macOS の Gatekeeper に止められた場合は、システム設定の「プライバシーとセキュリティ」から許可してください。

## 必要なもの

Konverter 0.2 以降のソースビルドは、FFmpeg をOS側から利用します。

```bash
brew install ffmpeg
```

Homebrew 以外の場所に FFmpeg がある場合は `KONVERTER_FFMPEG` で実行ファイルを指定できます。

```bash
KONVERTER_FFMPEG=/path/to/ffmpeg npm start
```

macOS では `/opt/homebrew/bin/ffmpeg`、`/usr/local/bin/ffmpeg`、`/opt/local/bin/ffmpeg` も自動検出します。

## ソースから実行

```bash
git clone https://github.com/nisesimadao/Konverter.git
cd Konverter
npm ci
npm start
```

## チェック

```bash
npm run check
npm audit
```

## macOS パッケージ

```bash
npm run package
```

成果物は `release/` に生成されます。GitHub Actions でもソースチェックと macOS パッケージ生成を確認します。

## 構成

```text
main.js             Electron main / 変換処理
renderer.js         preload bridge
index.html          UI
extend-info.plist   Finder の Open With 用ドキュメント関連付け
icon.png            アプリアイコン
```

過去の Python backend の PyInstaller 生成物と、重複していた `electron/` コピーは公開ソースから削除しています。

## License

[MIT](LICENSE)
