# Powershell Cheat Sheet
## 基本的なコマンド
- Write-Output : echo
- Rename-Item
- Get-ChildItem : dir, ls
- 

## grep
- Select-String <Pattern> <Path>
## Cluster
- Get-ClusterResource
- Get-ClusterResource pd-racm-im01 | Get-ClusterParameter
- Get-ClusterGroup
- Get-ClusterResource "resourceName" | Start-ClusterResource
- Get-ClusterResource "namePattern*" | Start-ClusterResource
- Move-ClusterGroup "pd-racm-im01"

- Get-Cluster
- Get-ClusterAvailableDisk
- Get-ClusterNode

- Get-ClusterLog

- Get-Cluster pd-racm-im01 res "Resin-app-0" /prop

- Get-ClusterAccess
- Grant-ClusterAccess -User username [-Full|ReadOnly]
- Remove-ClusterAccess -User username

## 項目数の取得
- (Get-Content filepath).Length
- Get-Conntent filepath | Measure-Object

## tail
- Get-Content filename -Wait

## Version / バージョン情報
- $PSVersionTable.PSVersion

## Execution Policy
- https://docs.microsoft.com/ja-jp/powershell/module/microsoft.powershell.core/about/about_execution_policies?view=powershell-7
- Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser

<<<<<<< HEAD:PowerShell_CheatSheet.org
** 文字列の連結
- +演算子を使う

** 名前の取得と変更
- 単一ファイル：
  Rename-Item OLD NEW
- 複数ファイルをまとめて変更
  Get-ChildItem | Rename-Item -NewName { $_ -Replace "old", "new" }

** ファイルのコピー
- 元ファイルから、Get-ChildItemの情報に沿った資料をコピー
  Get-ChildItem ターゲットフォルダ\*.xlsx  -Recurse | ForEach-Object { $name = $_.DirectoryName + "出力ファイル名の編集" + $_.Name; Copy-Item コピー元ファイル.xlsx -Destination $name }

** Azure
*** インストール
=======
## Azure
### インストール
>>>>>>> da64b3e6149158f439ef4f2f452104987db5f3cf:PowerShell_CheatSheet.md
- https://docs.microsoft.com/ja-jp/powershell/azure/install-az-ps?view=azps-4.3.0#code-try-0
### Azureに接続a
- Connect-AzAccount

### Subscription / サブスクリプション
- Get-AzSubscription
- Set-AzContext (Id)

### 
- Get-AzResource
