# fuelphp-centos7-mariadb-ansible　　

## 概要 

最小構成でインストールしたCentOS7にfuelphp,apache,mariadbの構成で構築がされます。

selinux無効化、firewalldの80番ポートを開放します。


## システム構成

* fuelphp 1.8
* CentOS 7
* PHP 5.6
* MariaDB 5.5
* Apache 2.4


## インストール手順

インストール直後の CentOS 7 に root でログインし以下の操作を行ってください。


### Ansibleのインストール

```
yum install -y ansible 
```

### パスワード、設定項目等

group_vars下のallファイルに設定項目が書かれていますので、各自任意に設定をお願いします。

### playbook実行

下記コマンドを実行してください。fuelの自動インストールが開始されます。

```
cd fuelphp-centos7-mariadb-ansible
ansible-playbook -i hosts site.yml
```

### firewalld selinuxについて

最初のsystem roleではfirewalldの起動、80番ポート開放、selinux無効化といった作業をしていますので、

不要な場合は以下のように実行してください

```
ansible-playbook -i hosts site.yml --skip-tags "system"
```

