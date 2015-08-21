# GSI Maps Architecture
[gsimaps](https://github.com/gsi-cyberjapan/gsimaps/)のアーキテクチャの整理を試みる。

## 3つの柱
サービス全体では、次の3項目が柱となる。

1. タイル - 地理空間情報の基軸通貨
2. layers.txt - タイルレイヤを可搬にするためのメタデータ
3. mokuroku - タイルセットを可搬にするためのメタデータ

タイルが layers.txt を構成 constitute し、layers.txt から mokuroku が生まれる
という上流下流構造がある。

mokuroku からは cocotile や kakotile が生まれる。タイルセットのダウンロードは
qdltc が示すような差分ダウンロードで行う。mokuroku 生成の効率化にために
daicho も検討されているところである。

## style.js の発想の重要性
タイルがベクトルの場合、そのスタイルの設定には style.js の発想を用いる。
ベクトルタイルの場合には、CORS 制約の影響を受ける場合が多い。このため、
本物の HTTP/HTTPS 環境の上でのプログラミングが求められる場合が多い。
→ [避けるべきつまづき](obstacles.md)

mokuroku は、タイルをキャッシュしたりダウンロードしたりする場合の
技術であるので、ウェブ地図のメインプロセスでは使わない。

ウェブ地図のメインプロセスにおける GSI Maps Architecture の真髄は、
layers.txt と style.js であるように思われる。

layers.txt と style.js の発想を伝えるようなハンズオンであることが望ましい。
