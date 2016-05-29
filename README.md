# はじめに
Ansibleの学習を兼ねたプロビジョニングファイル一式です
利用するにあたって、Ansible2のインストールが必要です.


# チュートリアル
## Ansible2のインストール
pipからインストールします  

```
sudo pip install ansible
```

[他の方法でもインストールは可能です](http://docs.ansible.com/ansible/intro_installation.html)

## Vagrantを使用してCentos7を立ち上げます

```
cd Forum-Server/provision/ansible2/centos7
vagrant up
```

何も変更をしていなければCentOSのIPは192.168.33.10になります。　　
hostsファイルの内容が以下のとおりになっていることを確認してください。
```
[vagrant]
192.168.33.10

[all:vars]
ansible_ssh_user=vagrant
ansible_ssh_pass=vagrant

```

## ansibleの実行
インストールするミドルウェアを選択します

settings.ymlで``` ○○_install: ``` と書かれている項目にtrueを設定することでインストール対象になります。

ただしcommonは必ずインストールされます。

ミドルウェアの選択が終わったら実行します。
```
ansible-playbook -i hosts -vvv  site.yml
```

今回はIDとパスワードでログインしますが鍵ファイルを利用することも可能です。

プロビジョニングの中で試験的にMySQLのアカウント作成やDB作成を行っています。  
各種情報についてはsettings.ymlを参照してください。
s