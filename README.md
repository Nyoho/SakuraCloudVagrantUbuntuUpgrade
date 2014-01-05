Vagrant でさくらのクラウドに Ubuntu 13.04 を up
================

さくらのクラウドに Ubuntu 13.10 の ISO パブリックイメージが入ったのはいいのですが
13.04 がなくなってしまいました。
Docker にまだバグがあるので 13.04 を入れたいです。

1. [vagrant-sakura](https://github.com/tsahara/vagrant-sakura) を使って、さくらのクラウドに Ubuntu 12.04 をインストール
2. Ansible で Ubuntu 12.10 -> Ubuntu 13.04 にアップグレード


## やり方

### 準備

```
vagrant plugin install vagrant-sakura
vagrant box add dummy https://github.com/tsahara/vagrant-sakura/raw/master/dummy.box
cp .env.template .env
edit .env
```

### vagrant up

```
eval `cat .env` vagrant up --provider=sakura
```

### 各種IDを調べる
```
eval `cat .env` vagrant sakuara-list-id
```

