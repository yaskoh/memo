# Hadoop
## HDFS
- 
  Hadoop Distributed File System
  
- 
  マスターノードであるNameNodeと、スレーブノードであるDataNodeで構成される。
  NameNodeは分散ファイルシステムのメタ情報を管理し、DataNodeはデータの実態を保存する。
  ファイルを一定サイズで分割したデータを"ブロック"としてDataNodeで保存する。

  ブロックは複数のDataNodeに"レプリカ"を保存する。
  デフォルトでは3つのレプリカが保存される。
  レプリカ数はHDFSに格納するファイル単位で変更可能。

## Hadoop MapReduce
- 
  マスターノードであるJobTrackerとスレーブノードであるTaskTrackerで構成される。
  
- 
  JobTrackerは、MapReduceジョブの管理やTaskTrackerへのタスク割り当て、TaskTrackerへのリソース管理を役割としている。

