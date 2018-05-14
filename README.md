# ansible-fuelphp　　

## 概要 

最小構成でインストールしたCentOS7にfuelphp,apache,mariadbの構成で構築がされます。

selinux無効化、firewalldの80番ポートを開放します。


## システム構成(CentOS7の場合)

* fuelphp 1.8
* PHP 5.6
* MongoDB 2.4
* MariaDB 5.5
* Apache 2.4

## システム構成(CentOS6の場合)

* fuelphp 1.8
* PHP 5.6
* MongoDB 2.4
* mysql 5.6
* Apache 2.2  

## インストール手順

インストール直後の CentOS に root でログインし以下の操作を行ってください。

### Ansibleのインストール

```
yum install -y ansible 
```

### CentOS6の場合はAnsibleを標準で入れられないため、epelでインストールします

```
yum install -y https://dl.fedoraproject.org/pub/epel/epel-release-latest-6.noarch.rpm
yum install -y ansible 
sudo vi /etc/yum.repos.d/epel.repo
----------
[epel]
-中略-
enabled=1 ※enabled=0に変える
----------
```


### パスワード、設定項目等

group_vars下のallファイルに設定項目が書かれていますので、各自任意に設定をお願いします。

### playbook実行

下記コマンドを実行してください。fuelの自動インストールが開始されます。

```
cd ansible-fuelphp-mariadb
ansible-playbook -i hosts site.yml
```

### firewalld selinuxについて

最初のsystem roleではfirewalldの起動、80番ポート開放、selinux無効化といった作業をしていますので、

不要な場合は以下のように実行してください

```
ansible-playbook -i hosts site.yml --skip-tags "system"
```

