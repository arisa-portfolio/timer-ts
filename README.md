# タイマー&アラームアプリ

## 概要

タイマー機能とアラーム機能を搭載したWebアプリです。

本アプリはTypeScriptの学習課題として制作しました。

## 使用技術

- HTML
- CSS
- TypeScript
- Vite
- Vitest
- localStorage

## 機能

### タイマー

- 指定した時間をカウントダウンする
- タイマーを開始・一時停止・停止する
- 計測履歴を最大5件まで保存する

### アラーム

- 指定した時刻にアラームを設定する
- アラームを最大5件まで登録・保存する
- 設定した時刻になるとアラームが鳴る
- アラームを停止する

## ディレクトリ構成

```text
timer-ts/
├── docs/
│   ├── 仕様/
│   │   └── 要求仕様書-タイマーアプリ.md
│   └── 設計/
│       ├── タイマー状態遷移図.puml
│       └── タイマー状態遷移表.md
├── src/
│   ├── main.ts
│   └── style.css
├── tests/
│   └── ...
├── index.html
├── package.json
├── tsconfig.json
├── vite.config.ts
└── README.md
```

## 環境構築・起動方法

### 必要な環境

- Node.js
- npm

### 1. リポジトリをクローン

```bash
git clone https://github.com/arisa-portfolio/timer-ts.git
```

### 2. プロジェクトディレクトリへ移動

```bash
cd timer-ts
```

### 3. パッケージをインストール

```bash
npm install
```

### 4. 開発サーバーを起動

```bash
npm run dev
```

### 5. ブラウザでアクセス

ターミナルに表示されたURLにアクセスすると、アプリを使用できます。

## ドキュメント

- [要求仕様書](https://github.com/arisa-portfolio/timer-ts/blob/main/docs/%E4%BB%95%E6%A7%98/%E8%A6%81%E6%B1%82%E4%BB%95%E6%A7%98%E6%9B%B8-%E3%82%BF%E3%82%A4%E3%83%9E%E3%83%BC%E3%82%A2%E3%83%97%E3%83%AA.md)
- [画面仕様書](https://www.figma.com/design/Yb9HE5ARwSbxN1ySfTWqwQ/%E7%94%BB%E9%9D%A2%E4%BB%95%E6%A7%98%E6%9B%B8?node-id=0-1&t=UnDDnRNOJadcejSD-1)
- [状態遷移図・状態遷移表]
- [シーケンス図]
- [クラス図]

## 工夫した点

- タイマーとアラームをそれぞれ独立して管理できる設計
- タイマーとアラームの状態に応じた画面・操作の切り替え
- localStorageを使用したタイマー履歴とアラーム設定の保存