# これは何か
MetaTrader4用のExpert Advisor(自動売買プログラム)。損失許容上限までナンピンで頑張るAE

# ステータス
開発中。まだ後述の極々単純なロジックを実装しただけ。
少なくとも以下の３つは実装する必要がある。
- いつエントリーするのかを決めるロジック
- 利確ターゲットに届かなさそうなポジションを手仕舞う場合のロジック
- 損失上限に達するまでに手仕舞う場合のロジック

プルリクをお待ちしておりますヽ(=´▽`=)ﾉ

# ロジック
## 時間枠
- EUR/USD 15分足

## エントリー
- 火曜〜金曜の日本時間朝６時にエントリー
- 15分足の75MAの向きに沿って(上昇ならBUY、下落ならSELL)
- ロット数 = 口座残高 x 0.0000015
- 逆行した場合は0.001ドル毎にナンピン。ロット数 = 有効証拠金 x 0.0000015

## 決済
- 総含み益が口座残高の1%以上で利確
- 総含み損が口座残高の40%以上で損切り
- 日本時間16時には強制クローズ

# バックテスト結果
2003年6月1日〜2018年3月13日  
[バックテスト結果](https://www.terukusu.org/test/StrategyTester_AM_lotlim_2003-2018.htm)
