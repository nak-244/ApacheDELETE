# FTP内で所有者がApache権限のフォルダ（ファイル）を消す

## 1 PHPファイルを準備する
下記を記述したPHPファイルを準備してください。
ファイル名はなんでもかまいません。今回は「delete.php」というファイル名にしています。

フォルダ名の部分を削除したいフォルダまたはファイル名に変更してください。

    <?php
    umask(0);
    chmod(フォルダ（ファイル）名,0777)
    ?>

### フォルダの場合

    <?php
    umask(0);
    chmod(test,0777)
    ?>

例えば「test」というフォルダを削除したいのであれば上記のように記述します。

### ファイルの場合
ファイルの場合は（”）シングルクォーテーションで囲むだけです。

    <?php
    umask(0);
    chmod('test.php',0777)
    ?>

例えば「test.php」というファイルを削除したいのであれば上記のように記述します。

## 2 作成したPHPファイルを削除したいフォルダ（ファイル）と同じディレクトリにアップする
先程作成したPHPファイルを削除したいフォルダ（ファイル）と同じディレクトリ（階層）にアップします。

## 3 PHPを実行する
PHPの実行方法はいくつかありますが、今回はApacheが使えないのが前提なので、URLで実行する方法をご紹介します。

### URLで実行する
作成してアップしたPHPファイルまでのパスを取得します。

URLの先頭をftp形式ではなく、URL形式に変更します。

> http://www.ドメイン.com/該当するディレクトリ/delete.php

あとはそのURLをブラウザで開くだけです。これでApacheの権限は無効化されました。

## 4 パーミッションを変更して、削除する
あとは削除したいフォルダ（ファイル）のパーミッションを777に変更して、削除してください。

### 55
