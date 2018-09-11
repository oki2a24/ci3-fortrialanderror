# ci3-fortrialanderror
CodeIgniter3.0.6 で試行錯誤をするための最低限のセットアップです。

[おわりに — CodeIgniter 3.2.0-dev ドキュメント](https://codeigniter.jp/user_guide/3/tutorial/conclusion.html) まで実装した状態です。

- http://localhost/ci306-fortrialanderror/index.php
- http://localhost/ci306-fortrialanderror/index.php/news

などにアクセスし、ページが表示されればセットアップ完了です。

## 事前の準備
MySQL でデータベース、テーブルを作成してください。

- DB名: sample_db
- DBユーザ名: sample_user
- DBユーザパスワード: sample_user_pass

```sql
CREATE DATABASE IF NOT EXISTS sample_db CHARACTER SET utf8mb4 COLLATE utf8mb4_general_ci;
CREATE USER sample_user@localhost IDENTIFIED BY 'sample_user_pass';
GRANT ALL PRIVILEGES ON sample_db.* TO sample_user@localhost;
USE sample_db;
CREATE TABLE news (
        id int(11) NOT NULL AUTO_INCREMENT,
        title varchar(128) NOT NULL,
        slug varchar(128) NOT NULL,
        text text NOT NULL,
        PRIMARY KEY (id),
        KEY slug (slug)
);
```

## 設定
application/config/database.php の hostname の値が db となっています。状況に応じて localhost 等に変更してください。
