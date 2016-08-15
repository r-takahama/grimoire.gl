---
type: doc
title: アドオンジェネレータ
order: 2
---

Grimoire.jsのアドオンを作成するにあたっては、ジェネレータの使用が便利です。
[Yoeman](http://yeoman.io/)を利用して、作成したプロジェクトによりビルドスクリプトやバンドリングスクリプト、テスト実行環境などを自動生成します。

## インストール

Grimoire.jsのアドオンのジェネレータを用いるには、Yoemanをインストールする必要があります。
以下の手順でYoemanとアドオンのジェネレータをインストールすることが可能です。

```shell
npm i yo generator-grimoire-addons -g
```

## プロジェクトの作成

アドオンプロジェクトを作成するには、プロジェクトを作成したいディレクトリ上で以下のコマンドを実行します。

```shell
yo grimoire-addons
```

指示に従って、質問の内容を入力してください。テンプレートプロジェクトが生成されます。

## 各種コマンド

生成されたプロジェクトでは、以下のコマンドが利用可能になります。

### ローカルサーバーの起動

実際のデバッグ用にローカルサーバーを以下のコマンドで起動することができます。

```shell
npm run serve
```

### ビルド

```shell
npm run build
```

さらに、以下のように`-w`オプションをつけることで、`src/`フォルダ内のtsファイルが変更された際に自動でビルドが走るようにすることができます。

```shell
npm run build -- -w
```

また、以下のように`-s`オプションをつけると、同時に`npm srun serve`を実行したものと同一として扱われます。

```shell
npm run build -- -s
```

これら二つのオプションを組み合わせて以下のように用いることが開発中は多いでしょう。

```shell
npm run build -- -w -s
```
この組み合わせと以下は等価です。

```shell
npm start
```

また、さらに`-m`オプションをつけると、minifyしたjsも生成します。これは他のオプションと組み合わせて使えます。

### テスト

`test/`フォルダ内に存在するテストは以下のコマンドにより実行できます。

```shell
npm test
```

また、`-w`オプションにより、ファイルの変更を監視し変更時に再度テストを実行します。

```shell
npm test -- -w
```

一部のテストのみを実行したい場合、`-f`オプションを用いて以下のように記述できます。

```shell
npm test -- -f Feature/A/**/*Test.js
```

この条件では、`test/Feature/A`以下のディレクトリに属する`Test.js`でファイル名が終わるすべてのテストが実行されます。

### スキャフォールディング

**コンポーネントを生成する例**

```shell
npm run scafold -- -t component -name Test
```

これにより`src/TestComponent.ts`を生成します。

**コンバーターを生成する例**

```shell
npm run scafold -- -t converter -name Test
```

これにより`src/TestConverter.ts`を生成します。

