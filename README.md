## udemy Laravel講座

## ダウンロード方法
git clone

git clone https://github.com/shys1006/laravel_umarche.git

git clone ブランチを指定してダウンロードする場合

git clone -b ブランチ名 https://github.com/shys1006/laravel_umarche.git

もしくはzipファイルでダウンロードしてください

## インストール方法
cd laravel_umarche
composer install
npm install
npm run dev
.env.example をコピーして .env ファイルを作成

.envファイルの中の下記をご利用の環境に合わせて変更してください。

DB_CONNECTION=mysql

DB_HOST=127.0.0.1

DB_PORT=3306

DB_DATABASE=laravel_umarche

DB_USERNAME=umarche

DB_PASSWORD=password123

XAMPP/MAMPまたは他の開発環境でDBを起動した後に

php artisan migrate:fresh --seed

と実行してください。(データベーステーブルとダミーデータが追加されればOK)

最後に php artisan key:generate と入力してキーを生成後、

php artisan serve で簡易サーバーを立ち上げ、表示確認してください。

## インストール後の実施事項

画像のダミーデータは public/imagesフォルダ内に sample1.jpg 〜 sample6.jpg として 保存しています。

php artisan storage:link で storageフォルダにリンク後、

storage/app/public/productsフォルダ内に 保存すると表示されます。 (productsフォルダがない場合は作成してください。)

ショップの画像も表示する場合は、 storage/app/public/shopsフォルダを作成し 画像を保存してください。

## 決済について
決済のテストとしてstripeを利用しています。 

stripeをGoogleなどで検索して、ユーザー登録を済ませてください。

その後、APIキーが発行されているので、ホームにある開発者向けの公開キーとシークレットキーを.envに追記してください。

追記の仕方
STRIPE_PUBLIC_KEY="自身の公開キー"
STRIPE_SECRET_KEY="自身のシークレットキー"

## メールについて
メールのテストとしてmailtrapを利用しています。 

こちらもstripe同様、検索してログインを済ませてください。

その後、IntegrationsでLaravel7+を選択すると下に自身のAPIキーが発行されているので、.envを書き換えてください。

メール処理には時間がかかるので、 キューを使用しています。

必要な場合は 
php artisan queue:work
で ワーカーを立ち上げて動作確認するようにしてください。

上手くいかない場合は、

php artisan config:cache

で キャッシュを削除してください。