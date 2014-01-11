Vagrant でさくらのクラウドに Ubuntu 13.04 を up
================

さくらのクラウドに Ubuntu 13.10 の ISO パブリックイメージが入ったのはいいのですが
13.04 がなくなってしまいました。
Docker にまだバグがあるので 13.04 を入れたいです。

1. [vagrant-sakura](https://github.com/tsahara/vagrant-sakura) を使って、さくらのクラウドに Ubuntu 12.04 をインストール
2. Ansible で Ubuntu 12.04 -> Ubuntu 12.10 -> Ubuntu 13.04 にアップグレード


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

## Provisioning

### provision コマンドで
```
eval `cat .env` vagrant provision
```

### 手動で Ansible
```
ansible-playbook -i vagrant_ansible_inventory_MyUbuntuServer -u ubuntu -s -vvv provisioning/playbook.yml
```

- 参考: http://docs.ansible.com/guide_vagrant.html


## なんと公式解決

さくらのクラウドの公式Twitterアカウント [@sakuracloud](https://twitter.com/sakuracloud) にこのように直訴したところ、

<blockquote class="twitter-tweet" lang="ja"><p><a href="https://twitter.com/sakuracloud">@sakuracloud</a> できればUbuntu13.04のパブリックアーカイブを復活させて欲しいです。(Docker を使いたいですが13.10はまだ問題があるので <a href="https://t.co/yBZGf4wFko">https://t.co/yBZGf4wFko</a>)&#10; <a href="http://t.co/JPp3gAuztm">http://t.co/JPp3gAuztm</a></p>&mdash; 俺たちの師走はこれからだ! (@NeXTSTEP2OSX) <a href="https://twitter.com/NeXTSTEP2OSX/statuses/420226443713339392">2014, 1月 6</a></blockquote><script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>

即刻解決してしまいました!!!

<blockquote class="twitter-tweet" lang="ja"><p><a href="https://twitter.com/NeXTSTEP2OSX">@NeXTSTEP2OSX</a> ご連絡ありがとうございます。Ubuntu13.04のパブリックアーカイブを復活させましたので、ご確認ください。どうぞ、今後とも「さくらのクラウド」をよろしくお願いいたします。</p>&mdash; さくらのクラウド (@sakuracloud) <a href="https://twitter.com/sakuracloud/statuses/420465176983240704">2014, 1月 7</a></blockquote><script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>
