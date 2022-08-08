## 試してみる
```shell
echo -n $(openssl rand 16) > binary-plain.key #バイナリ状態で乱数が書き出される
hexdump -C binary-plain.key #16進数表記
xxd binary-plain.key #ほぼ等価
```

## encコマンドの引数について
-Kオプションは「鍵を16進数表記で」受け取るので、文字列として鍵を16進数表記して与えれば大丈夫そう

## paddingについて
https://masahikosawada.github.io/2020/02/10/OpenSSL-Padding/

OpenSSLではデフォルトでPKCS#7パディングを使用しており、平文ファイルサイズがブロックサイズの整数倍長であっても１ブロック分Paddingされる。

平文ファイルサイズがブロックサイズの整数倍長であることが担保できるのであれば`-nopad`オプションをつければpaddingをなくせる。
