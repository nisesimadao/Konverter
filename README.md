# Konverter

[![CI](https://github.com/nisesimadao/Konverter/actions/workflows/ci.yml/badge.svg)](https://github.com/nisesimadao/Konverter/actions/workflows/ci.yml)
[![Release](https://img.shields.io/github/v/release/nisesimadao/Konverter)](https://github.com/nisesimadao/Konverter/releases/latest)
[![License: MIT](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)

Konverter は、Finder の「このアプリケーションで開く」からメディアファイルを別形式へ変換できる macOS 向けデスクトップアプリです。
通常起動では変換画面を表示し、Finder からファイルを渡して起動した場合は小さなクイック変換ウィンドウを表示します。

## 主な機能

- 動画、音声、画像を FFmpeg で変換します。
- PNG / JPEG / BMP / TIFF / GIF などの画像は、Jimp でも変換できます。
- Finder の「このアプリケーションで開く」から対象ファイルを直接渡せます。
- 同名ファイルが存在する場合は上書きせず、連番を付けて保存します。
- Electron の `contextIsolation` を有効にしています。

## ダウンロード

ビルド済みアプリは [Releases](https://github.com/nisesimadao/Konverter/releases/latest) から取得できます。

> 配布バイナリは未署名の場合があります。
> macOS の Gatekeeper によって起動を止められた場合は、システム設定の「プライバシーとセキュリティ」から実行を許可してください。

## 必要なもの

Konverter 0.2 以降をソースから実行する場合は、OS 側に FFmpeg が必要です。

```bash
brew install ffmpeg
```

Homebrew 以外の場所に FFmpeg がある場合は、`KONVERTER_FFMPEG` で実行ファイルを指定できます。

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

成果物は `release/` に生成されます。
GitHub Actions では、ソースチェックと macOS パッケージの生成を確認します。

## 構成

```text
main.js             Electron main / 変換処理
renderer.js         preload bridge
index.html          UI
extend-info.plist   Finder の Open With 用ドキュメント関連付け
icon.png            アプリアイコン
```

過去に使っていた Python バックエンドの PyInstaller 生成物と、重複していた `electron/` のコピーは公開ソースから削除しています。

## License

[MIT](LICENSE)
