# Ruby on railsの実行環境構築 on Windows

## 環境構築
```
Rubyインストール：（「環境確認」まで）
https://qiita.com/3no3_tw/items/8c0bcf258370d91bf6e0
```

## railsインストール
```
printf "install: --no-rdoc --no-ri\nupdate: --no-rdoc --no-ri\n" >> ~/.gemrc
gem install rails -v 5.1.6
```

## 手順
```
参照サイト参照して構築
rails new sample_app
cd sample_app/
bundle install
※bundle install --without production
bundle update
rails s
```

## FAQ
```
sqlite3のエラーができる場合
gem install sqlite3 -v 1.3.13
gemfileのsqlite3バージョンを「1.3.13」に指定
```

## 参照サイト
```
Rubyの実行環境構築 on Windows
https://qiita.com/3no3_tw/items/8c0bcf258370d91bf6e0

Ruby on Rails チュートリアル
https://railstutorial.jp/chapters/beginning?version=5.1#sec-development_environment

実例：
https://udemy.benesse.co.jp/development/web/scaffold.html

VS Code debug:
https://qiita.com/chimame/items/56e48ab3145312ff1786

```
