# ansible-squid

ansibleでプロキシサーバを構築します。

## 試した環境

- さくらVPS
- CentOS6

## 使い方

### hosts

プロキシサーバを構築したいサーバのIPアドレスを指定します

### squid.xonf

プロキシサーバに、アクセスを許可するIPアドレスを指定します。

```
# アクセスを許可するIPアドレスを設定して下さい
acl myacl src xxx.xxx.xxx.xxx
http_access allow myacl

# 複数指定したい場合は、下記のように追加する（myacl2といった形で名前を変える）
acl myacl2 src xxx.xxx.xxx.xxx
http_access allow myacl2
```

### ansibleを実行する

下記実行すると、SSHのパスワードを聞かれるので入力すると構築開始されます。

```
# ansible-playbook -i hosts squid.yml --ask-pass
```