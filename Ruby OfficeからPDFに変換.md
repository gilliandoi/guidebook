# Ruby OfficeからPDFに変換
```
ファイルアップ：
rails g controller fileuploads index create new change
https://cre8cre8.com/rails/upload-image.htm

AWS環境への最新版Libreofficeインストール：
・ダウンロードして展開（日本語拡張ファイルも含め）：
　https://ja.libreoffice.org/download/libreoffice-stable/
・日本語フォントインストール：
　sudo yum install ipa-gothic-fonts ipa-mincho-fonts vlgothic-fonts vlgothic-p-fonts
  cd /usr/share/fonts
　fc-cache -fv
・sudo yum install libXinerama
・sudo rpm -Uivh *.rpm
・cd /usr/bin
・sudo ln libreoffice6.1 libreoffice
・libreoffice --help
　※下記エラーが出る場合：
　　/opt/libreoffice6.1/program/soffice.bin: error while loading shared libraries: libdbus-glib-1.so.2: cannot open shared object file: No such file or directory
　　RPM依存ライブラリ不足の問題の解決：
　　・yum whatprovides libdbus-glib-1.so.2
　　　yum install dbus-glib
・libreoffice --version
・libreoffice --help
・起動
　libreoffice -headless　-language="ja" -accept="socket,host=127.0.0.1,port=8100;urp;" -nofirststartwizard &
・確認
　netstat -ant | grep 8100

・PDFに画像、文字追加
gem 'hexapdf', '~> 0.6.0'
gem install hexapdf -v 0.6.0

libreoffice変換範囲：
.doc, .docx （MS Word形式）
.xls, .xlsx （MS Excel形式）
.ppt, .pptx （MS Power Point形式）
.txt (テキストファイル)
.html (HTMLドキュメント)
.odt, .ods などの LibreOffice ドキュメント
```

## 参照サイト：
```
https://qiita.com/kijitora-neko/items/ca8e215c4580e59fef80
https://qiita.com/mosin_nozomi/items/67702903b2be980458b0
https://hamajyotan.hatenadiary.org/entry/20120404/1333532738
https://www.sukerou.com/2018/07/libreoffice.html
```
