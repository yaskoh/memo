# SQL
## 標準規格
### SQL:2016
- ISO/IEC 9075:2016
### SQL:2011
- ISO/IEC 9075:2011
### SQL:2008
### SQL:2003
### SQL:1999 / SQL99
### SQL92
## Memo
### Window関数
- 結果セットを部分的に切り出した領域に集約関数を適用できる。
  SQL:2003以降の標準SQLで規定されている。
  
    ex) sum(population) OVER ( PARTITION BY city)
        city毎にpopulationの合計を取った値、を取得する。

