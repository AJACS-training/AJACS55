# AJACS米子　パスウェイデータベースの紹介　実習用資料
情報・システム研究機構  
ライフサイエンス統合データベースセンター  
片山 俊明 ktym@dbcls.jp  
2015年8月4日(火) AJACS米子@鳥取大学米子キャンパス  
# パスウェイデータベースを使ってみる

## Pathguide

まずは、様々なパスウェイデータベースの一覧を見てみましょう。

* http://www.pathguide.org/

500 以上のデータベースが下記の分類でリストアップされています。

* タンパク質間相互作用 (PPI)
* 代謝パスウェイ
* シグナリングパスウェイ
* パスウェイダイアグラム
* 転写因子・遺伝子制御ネットワーク
* タンパク質-化合物間相互作用
* 遺伝的相互作用ネットワーク
* アミノ酸配列解析
* その他

ここで、Standard の欄がデータ形式のどの標準化 (PSI-MI, BioPAX, SBMLなど) に準拠しているかを示しています
（PSI-MI はパスウェイというよりタンパク質間相互作用の記述フォーマット）。

## BioCyc

BioCyc のウェブサイトを開いてみてください。

* http://biocyc.org/

Tair1, 2, 3 のパスウェイリストを確認し、

* http://biocyc.org/biocyc-pgdb-list.shtml

好きな生物種のパスウェイを見てみましょう。例えば Homo sapiens を選んで HumanCyc に移動し、

* http://biocyc.org/HUMAN/organism-summary?object=HUMAN

上部のメニュー Metabolism から Cellular Overview を選択するとヒトの代謝パスウェイの全体像が表示されます。

* http://biocyc.org/overviewsWeb/celOv.shtml

## Reactome

Reactome のウェブサイトを開いてみてください。

* http://www.reactome.org/

Analyze Data をクリックし、サンプルデータを用いてどのように可視化されるか見てみます。

* http://www.reactome.org/PathwayBrowser/#TOOL=AT

Analysis Tools の Click data file to paste your data or try example data sets を開いて、
Uniprot accession list や Gene name list など適当なものを選んで Analyse をクリックすると、
パスウェイ全体像のうち、指定した遺伝子に該当する部分がマークアップされたパスウェイが表示されます。

## KEGG

KEGG のウェブサイトを開いてください。

* http://www.kegg.jp/

参考資料

* [AJACS54](http://motdb.dbcls.jp/?plugin=attach&pcmd=open&file=AJACS2015_muto_handout_.pdf&refer=AJACS54) (武藤) p.1-12, 23-40
* [AJACS51](http://motdb.dbcls.jp/?plugin=attach&pcmd=open&file=KEGG_2014_12_slide.pdf&refer=AJACS51) (守屋) p.5-8, 25-28, 55-72 と [付録資料](http://motdb.dbcls.jp/?plugin=attach&pcmd=open&file=KEGG_2013_11.pdf&refer=AJACS51)
* [AJACS53](https://github.com/AJACS-training/AJACS53/tree/master/skwsm) (川島)

今回は [AJACS54](http://motdb.dbcls.jp/?plugin=attach&pcmd=open&file=AJACS2015_muto_handout_.pdf&refer=AJACS54) の資料 (とくに 23 ページ以降の後半) を使って実習します。

***

実習3 KEGG Mapper を用いたパスウェイ再構築

例題：
ある研究チームは、⼤腸菌K-12株の遺伝⼦「dapA」⾼発現下で細胞のL-リジン⽣産量が上がることを発⾒した。
この結果を説明する代謝経路を KEGG mapper を⽤いて検索せよ。

KEGG のウェブサイトを開く

* http://www.kegg.jp/

KEGG Organisms を開くと、KEGG では大腸菌 Escherichia coli K-12 MG1655 を eco というコードで表していることが分かる。

* http://www.kegg.jp/kegg/catalog/org_list.html

eco の文字をクリックして、

* http://www.kegg.jp/kegg-bin/show_organism?org=eco

検索窓で遺伝子名 dapA を検索すると、大腸菌 eco では dapA 遺伝子の ID が b2478 であることが分かる。

* http://www.kegg.jp/dbget-bin/www_bget?eco:b2478

ここで Pathway から Lysine biosynthesis の eco00300 をクリックするだけで該当するパスウェイの図が表示されるが、
課題は KEGG Mapper を用いてということだったので、KEGG のページに戻り、

* http://www.kegg.jp/

KEGG PATHWAY を選択し、

* http://www.kegg.jp/kegg/pathway.html

Pathway Mapping のところから Search&Color Pathway をクリック

* http://www.kegg.jp/kegg/tool/map_pathway2.html

Search against に書かれている ko を eco に書き換え、Enter objects one per line に b2478 を記入して Exec をクリック。
結果一覧から eco00300 Lysine biosynthesis を選ぶと先ほどと同じパスウェイが表示されることが分かる。KEGG Mapper では、複数の遺伝子や化合物を含むパスウェイを検索できることと、該当する遺伝子や化合物に自由に色を指定することができるのが利点です。

なお、パスウェイの図から検索結果の 4.3.3.7 をクリックすると、大腸菌でこの酵素番号を持っているすべての遺伝子が表示されてしまいます。これらはパスウェイ的には区別されていないことになります。

***

実習4 BlastKOALA をつかった自動アノテーション

Pathway Mapping のページに戻り、

* http://www.kegg.jp/kegg/tool/map_pathway2.html

左のパネルから Annotate Sequence をクリック

* http://www.kegg.jp/kegg/tool/annotate_sequence.html

資料の通り、サンプルの FASTA 配列を Buchnera に対して検索すると、ざっくりとしたエンリッチメント解析結果とパスウェイへのマッピング結果を見ることができる。
資料と比べて Unclassified が減っていました。

メタゲノムや新規ゲノムの予測遺伝子配列セットから、より正確なパスウェイ再構築を行いたい場合は KAAS を使うことができます。

* http://www.genome.jp/tools/kaas/

## 解析ツール

### KEGG REST API

* ヒトの遺伝子一覧
  * http://rest.kegg.jp/list/hsa

```
% curl http://rest.kegg.jp/list/hsa > list_hsa.txt
% wc -l list_hsa.txt
39726
```

* ヒトのパスウェイ一覧
  * http://rest.kegg.jp/list/pathway/hsa

```
% curl http://rest.kegg.jp/list/pathway/hsa > list_pathway_hsa.txt
% wc -l list_pathway_hsa.txt
296
```

* ヒトの遺伝子一覧とパスウェイの対応
  * http://rest.kegg.jp/link/hsa/pathway

```
% curl http://rest.kegg.jp/link/hsa/pathway > link_hsa_pathway.txt
% wc -l link_hsa_pathway.txt
24782
% cut -f 2 link_hsa_pathway.txt | sort | uniq | wc -l
6896
% echo '100 * 6896 / 39726' | bc -l
17.3589
```

KEGG のヒト遺伝子 39726 個のうち、ヒトの KEGG パスウェイ 296 種に載っている遺伝子はのべ 24782 個。ここから同じ遺伝子の重複を省くと 6896 個。もとの遺伝子数のうち 17.4% しかパスウェイに記載されていないことが分かる。

* 多くのパスウェイに登場する遺伝子

```
% cut -f 2 link_hsa_pathway.txt | sort | uniq  -c | sort -rn | head
83 hsa:5594   MAPK1     mitogen-activated protein kinase 1 (EC:2.7.11.24)
82 hsa:5595   MAPK3     mitogen-activated protein kinase 3 (EC:2.7.11.24)  
72 hsa:5290   PIK3CA    phosphatidylinositol-4,5-bisphosphate 3-kinase, catalytic subunit alpha (EC:2.7.11.1 2.7.1.153)
71 hsa:5296   PIK3R2    phosphoinositide-3-kinase, regulatory subunit 2 (beta)
71 hsa:5294   PIK3CG    phosphatidylinositol-4,5-bisphosphate 3-kinase, catalytic subunit gamma (EC:2.7.11.1 2.7.1.153)
71 hsa:5293   PIK3CD    phosphatidylinositol-4,5-bisphosphate 3-kinase, catalytic subunit delta (EC:2.7.1.153)
71 hsa:5291   PIK3CB    phosphatidylinositol-4,5-bisphosphate 3-kinase, catalytic subunit beta (EC:2.7.1.153)
70 hsa:8503   PIK3R3    phosphoinositide-3-kinase, regulatory subunit 3 (gamma)
70 hsa:5295   PIK3R1    phosphoinositide-3-kinase, regulatory subunit 1 (alpha)
70 hsa:23533  PIK3R5    phosphoinositide-3-kinase, regulatory subunit 5
```

* 一度しか登場しない遺伝子

```
% cut -f 2 link_hsa_pathway.txt | sort | uniq  -c | sort -rn | tail
1 hsa:10021
1 hsa:1002
1 hsa:10019
1 hsa:10015
1 hsa:100133941
1 hsa:100132074
1 hsa:100101267
1 hsa:10010
1 hsa:1001
1 hsa:10008
```

これらに bfind で遺伝子アノテーションを見てみましょう。

* http://www.kegg.jp/

のトップページにある検索窓から遺伝子 ID を入力、もしくは左のパネルから [Searching KEGG](http://www.kegg.jp/kegg/kegg1d.html) をクリックし、DBGET Search から [genes](http://www.kegg.jp/dbget-bin/www_bfind?genes) をクリックして、遺伝子 ID を検索できます。

### PathGuide にある BioPAX 形式のデータベースの利用

* Pathway Commons http://www.pathwaycommons.org/

サンプルのクエリを用いてパスウェイがどのように表示されるか見てみましょう。

### エンリッチメント解析

様々なウェブアプリ、商用アプリ、R の BioConductor パッケージ等が利用可能です。
目的に応じて論文 PLoS Comput Biol 2012, 8:e1002375 などを参照してご利用ください。

### パスウェイを作ってシミューレーション

シミュレーションに用いることのできるパスウェイ表現としては、システムバイオロジーで用いられる SBML が利用可能です。
Cell Designer を用いるとパスウェイを描画し SBML を作成することができます。
システムバイオロジーのサイトには SBML を利用したシミュレーションのソフトウェアが紹介されています。

* SBML
  * http://sbml.org/
* Cell Designer
  * http://celldesigner.org/

Cell Designer で構築されたパスウェイは BioModels に多数収録されているほか、アルツハイマー病のパスウェイを SBML で記述した AlzPathway など様々なパスウェイが構築されています。

* BioModels
  * http://biomodels.org/
* AlzPathway
  * http://alzpathway.org/
