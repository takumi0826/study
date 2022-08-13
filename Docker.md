# DockerFile まとめ

## FROM

- docker イメージを参照する
- `例）FROM node:lts-alpine`
- https://hub.docker.com/layers/node/library/node/lts-alpine/images/sha256-d39ab4712a8395d0b399dea44d9cb8b34ac942411b6a380449ebdb9d321136a3?context=explore

## RUN

- Linux コマンドを実行する
- `例）RUN mkdir hoge`
- image レイヤーを作成する(できるだけ小さく作成すること)
  - `&& \`で繋げて記載することができる。
- キャッシュされるため次回以降の build 時はキャッシュが使用される

## CMD

- コンテナのデフォルトコマンドを指定する
- `例）CMD ["npm", "run", "start"]`
- Dockerfile の最後に記述する
- image レイヤーを作成しない

## COPY

- ホストからコンテナにファイル、フォルダを受け渡すことができる
- `例）COPY `
- image レイヤーを作成する

## ADD

- COPY と似たコマンド
- tar の圧縮ファイルをコピーして解凍したい時に使用する。

## WORKDIR

- 以降の処理を指定した場所で作業する
- `例）WORKDIR /api`
- フォルダがない場合は自動で作成してくれる

## ENV

- 環境変数を設定できる。
- 主にパスを通す時に使用する。
