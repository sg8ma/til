## AnimePlan向けawsクラウド構成

概要は以下の通り
- Lightsail　      →  MySQL server    (DB)
- EC2 　　　　     →  Laravel         (WebAPI)
- CloudFront + S3  →  React           (Front App)
- GitHub Actions                       (CI/CD)

### Lightsail

#### インスタンス生成

- Amazon Lightsail -> Create Instance
- select a plat form：Linux/Unix
- select a blueprint: OS Only -> Amazon Linux 2023
- Connect -> Download default keyからpemファイルをダウンロード

#### MySQLサーバインストール

```
sudo su -
dnf localinstall https://dev.mysql.com/get/mysql80-community-release-el9-5.noarch.rpm
dnf info mysql-community-server
dnf install mysql-community-server
mysqld --version
systemctl start mysqld
grep 'temporary password' /var/log/mysqld.log
mysql_secure_installation
```

### DBユーザ作成

```
create user "db-user"@"%" identified by 'パスワード';
grant create on *.* to "db-user"@"%";
```

### メモリ割当設定

現在のメモリ状態を確認
```
free -mh
               total        used        free      shared  buff/cache   available
Mem:           905Mi       556Mi        64Mi       0.0Ki       283Mi       210Mi
Swap:             0B          0B          0B
```

innodb_buffer_pool_sizeにbuff/cacheの80%を設定
```
vim /etc/my.cnf
innodb_buffer_pool_size = 227M
```
