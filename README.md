# quoripagos-server
Application server of the Quoripagos.

Client：quoripagos-client-ShinobiGami([GitHub](https://github.com/HillTopTRPG/quoripagos-client-ShinobiGami))

## What is Quoripagos.
* [Official](http://quoripagos.com)<br>
* Author：HillTop([Twitter](https://twitter.com/HillTop_TRPG))

## Structure
* Node.js (TypeScript)
* Express (HttpServer)
* socket.io (WebSocket)
* MongoDB (Data Base)
* Minio (File Storage)

## How To Use
使えるようにしておくべきコマンド
* git
* npm
* node
* mongo
* mongod

1. Quoripagosサーバ本体の配置
   1. `git clone https://github.com/HillTopTRPG/quoripagos-server.git` GitHubからソースをダウンロード
   1. `cd quoripagos-server` 生成された「quoripagos-server」ディレクトリに移動
   1. `npm install` ライブラリをインストール
   1. （はじめての設置の際に）`config`フォルダの中のファイル名の末尾が`.example`となっている3つのファイルも上記と同様に、元のファイルと同じ場所に末尾の`.example`を除いたファイル名で複製  (Ver.1.0.0a50～)
   1. （はじめての設置の際に）`message`フォルダの中のファイル名の末尾が`.example`となっている2つのファイルも上記と同様に、元のファイルと同じ場所に末尾の`.example`を除いたファイル名で複製  (Ver.1.0.0a50～)
   1. `npm run build` TypeScriptをビルドすることで「dist」フォルダにJavaScriptファイルが生成される

1. MongoDBを起動 ※ MongoDBの構築は詳しくは解説しません。（できません）
   1. `mongo`
   1. 「***connection to: mongodb://127.0.0.1:27017/~~~~~~***」 と表示されたらOK<br>
      「***mongodb://***」からポート番号までの文字（例：***mongodb://127.0.0.1:27017***）をメモしておく
   1. エラーだったら構築に失敗してます。構築頑張って…🐧🌟
   
1. Minioを起動 ※ Minioの構築は詳しくは解説しません。（できません）
   1. 例:`minio server --address localhost:9000 /minio`
   1. バケットに対してバケットポリシーを設定してください。Setting to Bucket policy. (*: readonly)

1. Quoripagosサーバの設定を編集
   1. 「quoripagos-server/conf/server.yaml」を編集する（テキストエディタで編集可能）<br>
      サーバ稼働に関する設定ファイル<br>
      書き方や注意点はyamlファイル内にコメントを書いてあるので、それを見ながら頑張って設定値を書いてください<br>
      前項でメモしておいたMongoDBの接続文字列はこのファイルに設定する<br>
      バージョンアップに伴って項目が増える可能性もあるので、バージョンアップの際は注意してください。
   1. 「quoripagos-server/conf/minio.yaml」を編集する（テキストエディタで編集可能）<br>
      ストレージサービスとの連携に関する設定ファイル<br>
      書き方や注意点はyamlファイル内にコメントを書いてあるので、それを見ながら頑張って設定値を書いてください
      バージョンアップに伴って項目が増える可能性もあるので、バージョンアップの際は注意してください。
   1. 「quoripagos-server/message/message.yaml」を編集する（テキストエディタで編集可能）<br>
      クライアントに表示されるサーバ情報の設定ファイル
      バージョンアップに伴って項目が増える可能性もあるので、バージョンアップの際は注意してください。
   1. 「quoripagos-server/message/termsOfUse.txt」を編集する（テキストエディタで編集可能）<br>
      サーバ側の利用規約の文章をここに書いてください

1. Quoripagosサーバを起動
   1. `npm run node-server` Node.jsサーバを起動
   1. 「***Quoripagos Server is Ready.***」と表示されたら起動完了🐧🎊
   1. 「***S3 Storage upload-test success.***」と表示されていたらMinioサーバーへの疎通も確認できています。
