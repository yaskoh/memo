# Windows / System Programs
## System32
### Direct
#### exe
##### CUI
###### bitsadmin.exe
- Linuxのcurlやwgetのようなもの。
  BITS = Background Intelligent Transfer Service
- BITSADMIN [/RAWRETURN] [/WRAP | /NOWRAP] command
####### Commands
######## /HELP, /?
######## /UTIL /?
- Prints the list of utilities commands
######## /TRANSFER <jobname> [type] [/PRIORITY priority] [/ACLFLAGS flags] remote_url local_name
###### cacls.exe
- ファイルのアクセス制御リスト（ACL）を表示・変更する。
  使用が推奨されていない、icaclsの使用を推奨。
###### certutil.exe
####### Options
######## -hashfile
###### choice.exe
- choice[.exe] [/C <choices>] [/N] [/CS] [/T nnnn [/D c]] [/M <message>]
  - /C <choices>
    選択肢となる文字列を指定する。
  - /N
    選択肢と「？」を表示させない。
  - /CS
    選択肢の大文字小文字を区別する。
  - /T
    選択する時間を設定する。nnnnは制限時間の秒数。
  - /D
    Tで指定した時間が経過した際に選択される選択肢を指定する。
  - /M <message>
    メッセージを表示する。

- 1番目の選択肢を選ぶと1、n番目の選択肢を選ぶとnが終了コード（エラーコード）が返される。
  Ctrl+Cなどが押されると0、エラー時には255が返される。

- ex) choice /C YN /M "続行しますか"
      ⇒続行しますか [Y,N]?

###### cmd.exe
- コマンドプロンプト。
###### cmdkey.exe
- 
  保存されたユーザ名とパスワードの作成、表示、および削除を行う。

- /list{:targetname}
  資格情報を表示する

- /add(/genericも可)
  - /add:targetname /user:username /pass:password
  - /add:targetname /user:username /pass
  - /add:targetname /user:username
  - /add:targetname /smartcard
  
  - /smartcard


- /delete
  - /delete:targetname

  - /delete /ras
    RAS資格情報を削除する
  
###### cscript.exe
- コマンドライン用WSH。
###### eventcreate.exe
- This enables an admistrator to create a custom event ID and message in a specified event log.
  イベントログの追加に加え、イベントソースが存在しない場合は作成してくれる。
####### Options
######## /S system
######## /U [domain\]user
######## /P [passowrd]
######## /L logname
######## /T type
######## /SO source
######## /ID id
######## /D description
######## /?
###### findstr.exe
- ファイルから文字列を検索する
####### Options
######## /C:文字列
- 指定した文字列からリテラル検索文字列として使用する
###### ftp.exe
####### !
####### ?
####### append
####### ascii
####### bell
####### binary
####### bye
####### cd
####### close
####### debug
####### delete
####### dir
####### disconnect
- disconnect server
####### get
####### glob
####### hash
####### help
####### lcd
####### ls
####### mdelete
####### mdir
####### mget
####### mkdir
####### mls
####### mput
####### open
- connect server
####### put
####### pwd
####### quit
- quit the "ftp" session
####### quote
####### recv
####### remotehelp
####### rename
####### rmdir
####### status
####### trace
####### type
####### user
####### verbose
###### gpresult.exe
- RSoP(ポリシーの結果セット)の情報を取得するときに使う。
  rsop.mscをコマンドライン上で確認するコマンド。
####### Options
######## /R
- 概要を表示
######## /V
- 詳細情報を表示
######## /Z
- さらに詳細情報を表示
###### gpupdate.exe
- ドメインコントローラーからげな次の最新のグループポリシーをロードし適用する。
  "secedit /refreshpolicy"とほぼ同じ。
- 即時反映は"gpupdate /force /wait:0"
####### Options
######## /Target:{Computer | User}
######## /Force
######## /Wait:{value}
######## /Logoff
######## /Boot
######## /Sync
###### icacls.exe
- Integrity Control Access Control List。
  ファイルやフォルダのアクセス制御リストを表示、修正、バックアップ、復元などが可能。
- icalcs <name> /save <acl file> 
- 名前が一致する全てのファイルとフォルダーのDACLを
###### makecab.exe
- Cabinet Maker : Lossless data compression
####### Usage
- MAKECAB [/V[n]] [/D var=value ...] [/L dir] source [destination]
- MAKECAB [/V[n]] [/D var=value ...] /F directive_file [...]
####### /d value
######## MaxDiskSize
######## RptFileName
######## InfFileName
######## DiskDirectoryTemplate
###### nbtstat.exe
-NBT(NetBIOS over TCP/IP)を使用して、プロトコルの統計と現在のTCP/IPネットワーク接続を表示する。
####### Options
######## -a RemoteName
######## -A IPAdress
######## -c
######## -n
###### NETSTAT.EXE
- "ネットワークコマンド"配下を参照
###### SecEdit.exe
- ローカルセキュリティポリシーをCUIで変更する。
####### Link
- https://orebibou.com/2013/09/secedit-%E3%82%B3%E3%83%9E%E3%83%B3%E3%83%89%E3%81%AB%E3%82%88%E3%82%8B%E3%83%AD%E3%83%BC%E3%82%AB%E3%83%AB%E3%82%BB%E3%82%AD%E3%83%A5%E3%83%AA%E3%83%86%E3%82%A3%E3%83%9D%E3%83%AA%E3%82%B7%E3%83%BC/
###### query.exe
- QUERY { PROCESS | SESSION | TERMSERVER | USER }
####### Commands
######## Process
######## Session
- QUERY SESSION [セッション名 | ユーザー名 | セッションID] [OPTIONS]
- リモートデスクトップセッションの情報を表示する。
######### Options
########## /SERVER:サーバー名
########## /MODE
########## /FLOW
########## /CONNECT
########## /COUNTER
########## /VM
######## Termserver
- QUERY TERMSERVER [サーバー名] [OPTIONS]
- ネットワーク上で利用可能なリモートデスクトップセッションホストサーバーを表示する
######## User
- QUERY USER [ユーザー名 | セッション名 | セッションID] [/SERVER:サーバー名]
- システムにログオンしているユーザーの情報を表示する。
###### quser.exe
- QUERY USERのalias。
###### qwinsta.exe
- QUERY SESSIONのalias。
###### rasdial.exe
- vpn接続のために確認。
- コマンド
  rasdial.exe エントリ名 [ユーザー名 [パスワード|*]] [/DOMAIN:ドメイン]
                [/PHONE:電話番号] [/CALLBACK:コールバック番号]
                [/PHONEBOOK:電話帳ファイル] [/PREFIXSUFFIX]
  rasdial.exe [エントリ名] /DISCONNECT
  rasdial.exe
###### rasphone.exe / ダイヤルアップネットワーク コマンドライン
- vpn接続のために確認。
- コマンド
  rasphone.exe [-f ファイル] [[ -e | -d | -h | -r] エントリ]
  rasphone.exe [-f ファイル] -a [エントリ]
  rasphone.exe [-f ファイル] -lx リンク
- 引数
  -a 新しいエントリダイアログ
  -e エントリの編集ダイアログ
  -d エントリのダイヤルダイアログ
  -h エントリを切断するときにメッセージを表示しない
  -r エントリを削除するときにメッセージを表示しない
  -lx ダイヤルアップショートカットファイルに対して'x'を実行
  x コマンドa, e, d, hまたはrのいずれか
###### reg.exe
- Registry操作
####### Operations
######## ADD key [Options]
- REG ADD key

- ex
  REG ADD "HKLM\SYSTEM\CurrentControlSet\services\eventlog\Application\Revenue Management Application" /v CustomSource /t REG_DWORD /d 1
######### Options
########## /v valuename
########## /d data
########## /t type
########### Type
- REG_SZ
- REG_MULTI_SZ
- REG_EXPAND_SZ
- REG_DWORD
- REG_QWORD
- REG_BINARY
- REG_NONE
########## /s separator
######## COPY
######## DELETE
######## QUERY
######## SAVE
######## RESTORE
######## LOAD
######## UNLOAD
######## COMPARE
######## EXPORT
######## IMPORT
######## FLAGS
###### Robocopy.exe
- 戻り値
  - 
    |------+------+------------------------------------------------------|
    | 16進 | 10進 | 意味                                                 |
    |------+------+------------------------------------------------------|
    | 0x10 |   16 | 重大なエラー。ひとつもコピーできず。                 |
    | 0x08 |    8 | いくつかのファイルがコピーできず                     |
    | 0x04 |    4 | いくつかMismatchedファイルあるいはディレクトリが存在 |
    | 0x02 |    2 | いくつかExtraファイルまたはディレクトリが存在        |
    | 0x01 |    1 | 1つ以上のファイルがコピーされた                      |
    | 0x00 |    0 | エラーは発生せず、コピーもされない（完全同期済み）   |
    |------+------+------------------------------------------------------|

- [[https://www.google.com/search?q=robocopy.doc][Google: "robocopy.doc"の検索]]
- [[https://www.atmarkit.co.jp/ait/articles/1309/27/news116.html][Windowsのrobocopyコマンドでコピーするファイルの種類を選択／変更する - @IT]]

###### tasklist.exe
- 現在アクティブなプロセスとそのPIDのリストが表示される。
  POSIXのpsみたいなもの。
###### timeout.exe
- 指定した時間だけ待つ。キーが入力されると待ちを終えて次のコマンドを実行する。
###### systeminfo.exe 
- 
  システム情報を表示できる。cmd上でsysteminfo。CUI。
  デフォルトで対象はローカルコンピュータ。
  ただし/s servername, /u UserName, /p Passwordなどを入力すると、
  リモートの情報も取得できる。

###### w32tm.exe
####### Commands
######## w32tm [ /? | /register | /unregister ]
######## w32tm /monitor
######## w32tm /ntte
######## w32tm /ntpte
######## w32tm /resync
######## w32tm /stripchart
######## w32tm /config
######## w32tm /tz
######## w32tm /dumpreg
######## w32tm /query
######## w32tm /debug
######## w32tm 
###### wevtutil.exe
- wevtutil COMMAND [ARGUMENT [ARGUMENT] ...] [/OPTION:VALUE [/OPTION:VALUE] ...]
- イベントログおよび発行元に関する譲歩の取得、イベントマニフェストのイントールおよびアンインストール、
  クエリの実行、ログのエクスポート、アーカイブおよびクリアを実施できる。
####### Commands
######## el | enum-logs
######## gl | get-log
######### Options
########## /{f|format}:[XML|Text]
- Specify the log file format.
######## sl | set-log
- 既存のログの構成を更新する。
######### Options
########## /{ab|autobackup}:[true|false]
########## /{ca|channelaccess}:VALUE
- Access permission for an event log.
########## /{rt|retention}:[true|false]
######## ep | enum-publishers
######## gp | get-publisher
######## im | install-manifest
######## um | uninstall-manifest
######## qe | query-events
######## gli | get-log-info
######## epl | export-log
######## al | archive-log
######## cl | clear-log
####### General Options
######## /{r | remote}:VALUE
######## /{u | username}:VALUE
######## /{p | pasword}:VALUE
######## /{a | authentication}:[Default|Negotiate|Kerberos|NTLM]
######## /{uni | unicode}:[true|false]
###### where.exe
- プログラムの場所を返す
###### whoami.exe
####### Options
######## /UPN
######## /FQDN
######## /LOGONID
######## /USER
- SIDが調べられる
######## /USER /FO LIST
######## /USER /FO CSV
######## /GROUPS
- 所属グループのSID含む各種情報が取得できる。
######## /GROUPS /FO CSV /NH
######## /CLAIMS
######## /CLAIMS /FO LIST
######## /PRIV
######## /PRIV /FO TABLE
######## /USER /GROUPS
######## /USER /GROUPS /CLAIMS /PRIV
######## /ALL
######## /ALL /FO LIST
######## /ALL /FO CSV /NH
######## /?
##### GUI
###### control.exe / コントロールパネル
- コントロールパネルの実行ファイル。
###### eventvwr.exe / イベントビューア
- イベントビューアー。.mscとの違いは不明、おそらく同じ。
###### mmc.exe
- Microsoft管理コンソール Microsoft Management Console
###### mstsc.exe / リモートデスクトップ
- mstsc MicroSoft TerminaL Server Client
####### Options
######## /admin
- コンソールセッションに接続する(RDC 6.1以降)
- Windows 2008以上では、Session 0がnon-interactiveとなったため、consoleセッションには接続できない模様。
  [[https://social.technet.microsoft.com/Forums/lync/en-US/5895015a-d041-441e-83b3-4b0c4c74169a/windows-server-2012-console-session?forum=winserverTS][Windows server 2012 Console session - Lync TechCenter]]
  [[https://blogs.technet.microsoft.com/askperf/2007/04/27/application-compatibility-session-0-isolation/][Application Compatibility -Session 0 Isolation - Ask the Performance Team Blog]]
######## /?
- helpを表示
######## obsolete
######### /console
- RDC 5.x/6.0の場合に、コンソールセッションに接続する方法。
  6.1以降は/adminを利用。
  https://blogs.technet.microsoft.com/peterfi/2008/01/11/mstsc-console-is-now-mstsc-admin/
###### netplwiz.exe / ユーザアカウント
- 
  newplwiz.exeで開く。
  パスワード忘れてCMD立ち上げたときとかに役立つ。
###### notepad.exe / メモ帳
####### Memo
- UTF-8で保存すると勝手にBOMがつくので注意。

###### perfmon.exe / パフォーマンスモニター
###### psr.exe / ステップ記録ツール
- Steps Recorder, ステップ記録ツール、問題ステップ記録ツール
- CLI操作も可能

####### Link (psr.exe)
- https://qiita.com/gzock/items/1c934d6577eec3b7f7ff
- http://yaimairi.hateblo.jp/entry/2016/08/22/004029

###### resmon.exe / リソースモニター
- "perfmon /res"でも起動
###### wscript.exe
- GUI実行用WSH。
##### System
###### conhost.exe
- コンソールウィンドウホスト。

###### dwm.exe
- デスクトップ・ウィンドウ・マネージャー
  Aeroの
  サービス「Desktop Window Manager Session Manager」の実行ファイル。
##### tmp
AdapterTroubleshooter.exe
aitagent.exe
aitstatic.exe
alg.exe
appidcertstorecheck.exe
appidpolicyconverter.exe
appverif.exe
at.exe
AtBroker.exe
attrib.exe
audiodg.exe
auditpol.exe
autochk.exe
autoconv.exe
autofmt.exe
AxInstUI.exe
baaupdate.exe
bcdboot.exe
bcdedit.exe
BdeHdCfg.exe
BdeUISrv.exe
BdeUnlockWizard.exe
BitLockerWizard.exe
BitLockerWizardElev.exe
bootcfg.exe
bridgeunattend.exe
bthudtask.exe
calc.exe
CertEnrollCtrl.exe
certreq.exe
change.exe
charmap.exe
chglogon.exe
chgport.exe
chgusr.exe
chkdsk.exe
chkntfs.exe
cipher.exe
cleanmgr.exe
cliconfg.exe
clip.exe
cmdl32.exe
cmmon32.exe
cmstp.exe
cofire.exe
colorcpl.exe
comp.exe
compact.exe
CompatTelRunner.exe
CompMgmtLauncher.exe
ComputerDefaults.exe
consent.exe
convert.exe
credwiz.exe
csrss.exe
ctfmon.exe
cttune.exe
cttunesvr.exe
CustomModeApp.exe
dccw.exe
dcomcnfg.exe
ddodiag.exe
Defrag.exe
DeviceDisplayObjectProvider.exe
DeviceEject.exe
DevicePairingWizard.exe
DeviceProperties.exe
DFDWiz.exe
dfrgui.exe
dialer.exe
diantz.exe
difx64.exe
dinotify.exe
diskpart.exe
diskperf.exe
diskraid.exe
Dism.exe
dispdiag.exe
DisplaySwitch.exe
djoin.exe
dllhost.exe
dllhst3g.exe
dnscacheugc.exe
doskey.exe
dpapimig.exe
DpiScaling.exe
dpnsvr.exe
DPTopologyApp.exe
driverquery.exe
drvinst.exe
dvdplay.exe
dvdupgrd.exe
dxcpl.exe
dxdiag.exe
Dxpserver.exe
Eap3Host.exe
efsui.exe
EhStorAuthn.exe
esentutl.exe
eudcedit.exe
expand.exe
extrac32.exe
fc.exe
find.exe
finger.exe
fixmapi.exe
fltMC.exe
fontview.exe
forfiles.exe
fsquirt.exe
fsutil.exe
fvenotify.exe
fveprompt.exe
FXSCOVER.exe
FXSSVC.exe
FXSUNATD.exe
getmac.exe
GettingStarted.exe
GfxUIEx.exe
GfxUIHotKeyMenu.exe
gpscript.exe
grpconv.exe
hdwwiz.exe
help.exe
hkcmd.exe
hpservice.exe
hwrcomp.exe
hwrreg.exe
icardagt.exe
icsunattend.exe
IDTNGUI.exe
IDTNJ.exe
ie4uinit.exe
ieetwcollector.exe
ieUnatt.exe
iexpress.exe
igfxext.exe
igfxpers.exe
igfxsrvc.exe
igfxtray.exe
InfDefaultInstall.exe
ipconfig.exe
irftp.exe
iscsicli.exe
iscsicpl.exe
isoburn.exe
klist.exe
ksetup.exe
ktmutil.exe
label.exe
LocationNotifications.exe
Locator.exe
lodctr.exe
logagent.exe
logman.exe
logoff.exe
LogonUI.exe
lpksetup.exe
lpremove.exe
lsass.exe
lsm.exe
Magnify.exe
manage-bde.exe
mblctr.exe
mcbuilder.exe
mctadmin.exe
MdRes.exe
MdSched.exe
mfevtps.exe
mfpmp.exe
microsoft.windows.softwarelogo.showdesktop.exe
MigAutoPlay.exe
mobsync.exe
mountvol.exe
mpnotify.exe
MpSigStub.exe
MRT.exe
msconfig.exe
msdt.exe
msdtc.exe
msfeedssync.exe
msg.exe
mshta.exe
msiexec.exe
msinfo32.exe
mspaint.exe
msra.exe
MsSpellCheckingFacility.exe
mtstocom.exe
MuiUnattend.exe
MultiDigiMon.exe
Narrator.exe
ndadmin.exe
net.exe
net1.exe
netbtugc.exe
netcfg.exe
netdom.exe
netiougc.exe
Netplwiz.exe
NetProj.exe
netsh.exe
newdev.exe
nltest.exe
nslookup.exe
ntoskrnl.exe
ntprint.exe
ocsetup.exe
odbcad32.exe
odbcconf.exe
openfiles.exe
OptionalFeatures.exe
osk.exe
p2phost.exe
pcalua.exe
pcaui.exe
pcawrk.exe
pcwrun.exe
PkgMgr.exe
plasrv.exe
PnPUnattend.exe
PnPutil.exe
poqexec.exe
PortQry.exe
powercfg.exe
PresentationHost.exe
PresentationSettings.exe
prevhost.exe
print.exe
PrintBrmUi.exe
printfilterpipelinesvc.exe
PrintIsolationHost.exe
printui.exe
proquota.exe
PushPrinterConnections.exe
qappsrv.exe
qprocess.exe
rasautou.exe
raserver.exe
rdpclip.exe
rdpinit.exe
rdpshell.exe
rdpsign.exe
rdrleakdiag.exe
rdrmemptylst.exe
RDVGHelper.exe
ReAgentc.exe
recdisc.exe
recover.exe
regedt32.exe
regini.exe
Register-CimProvider.exe
RegisterIEPKEYs.exe
regsvr32.exe
rekeywiz.exe
relog.exe
RelPost.exe
repair-bde.exe
replace.exe
reset.exe
RMActivate.exe
RMActivate_isv.exe
RMActivate_ssp.exe
RMActivate_ssp_isv.exe
RmClient.exe
RpcPing.exe
rrinstaller.exe
rstrui.exe
runas.exe
rundll32.exe
RunLegacyCPLElevated.exe
runonce.exe
rwinsta.exe
sbunattend.exe
sc.exe
schtasks.exe
sdbinst.exe
sdchange.exe
sdclt.exe
sdiagnhost.exe
SearchFilterHost.exe
SearchIndexer.exe
SearchProtocolHost.exe
secinit.exe
services.exe
sethc.exe
SetIEInstalledDate.exe
setspn.exe
setupcl.exe
setupugc.exe
setx.exe
sfc.exe
shadow.exe
shrpubw.exe
shutdown.exe
sigverif.exe
slui.exe
smss.exe
SndVol.exe
SnippingTool.exe
snmptrap.exe
sort.exe
SoundRecorder.exe
spinstall.exe
spoolsv.exe
sppsvc.exe
spreview.exe
srdelayed.exe
StikyNot.exe
subst.exe
svchost.exe
sxstrace.exe
SyncHost.exe
syskey.exe
systeminfo.exe
SystemPropertiesAdvanced.exe
SystemPropertiesComputerName.exe
SystemPropertiesDataExecutionPrevention.exe
SystemPropertiesHardware.exe
SystemPropertiesPerformance.exe
SystemPropertiesProtection.exe
SystemPropertiesRemote.exe
systray.exe
tabcal.exe
takeown.exe
TapiUnattend.exe
taskeng.exe
taskhost.exe
taskkill.exe
taskmgr.exe
tcmsetup.exe
TpmInit.exe
tracerpt.exe
tscon.exe
tsdiscon.exe
tskill.exe
TSTheme.exe
TsUsbRedirectionGroupPolicyControl.exe
TSWbPrxy.exe
TsWpfWrp.exe
typeperf.exe
tzutil.exe
ucsvc.exe
UI0Detect.exe
unlodctr.exe
unregmp2.exe
upnpcont.exe
UserAccountControlSettings.exe
userinit.exe
Utilman.exe
VaultCmd.exe
VaultSysUi.exe
vcsFPService.exe
vds.exe
vdsldr.exe
verclsid.exe
verifier.exe
vmicsvc.exe
vsjitdebugger.exe
vssadmin.exe
VSSVC.exe
waitfor.exe
wbadmin.exe
wbengine.exe
wecutil.exe
WerFault.exe
WerFaultSecure.exe
wermgr.exe
wextract.exe
WFS.exe
wiaacmgr.exe
wiawow64.exe
wimserv.exe
wininit.exe
winload.exe
winlogon.exe
winresume.exe
winrs.exe
winrshost.exe
WinSAT.exe
winver.exe
wisptis.exe
wksprt.exe
wlanext.exe
wlrmdr.exe
wowreg32.exe
WPDShextAutoplay.exe
wpnpinst.exe
write.exe
WSManHTTPConfig.exe
wsmprovhost.exe
wsqmcons.exe
wuapp.exe
wuauclt.exe
WUDFHost.exe
wusa.exe
xcopy.exe
xpsrchvw.exe
xwizard.exe
#### msc
- Microsoft Common Console Documentファイル。
  mscは、MMC用に作られた特殊なDDL。
  スナップインをどのように組み込むかを定義しているファイルで、中身はXML形式のテキストファイル。
- MMCスナップイン
##### azman.msc
##### certlm.msc / 証明書
##### certmgr.msc
##### comexp.msc
##### compmgmt.msc / Computer Management / コンピュータの管理
##### devmgmt.msc
##### diskmgmt.msc / Disk Management / ディスクの管理
- ディスクの管理。
  Windowsのスタートボタンを右クリック→disk managementを選択したり。
  computer managementのStorage項目としても選択可能。
###### Memo
####### ディスクがGPTかMBRか確認する
- ディスクを右クリック、プロパティ、ボリューム、パーティションのスタイル、に記載あり。
  http://www1.ark-info-sys.co.jp/support/etc/etc/check_mbr_gpt.html
##### eventvwr.msc / Event Viewer / イベントビューアー
##### fsmgmt.msc
##### gpedit.msc / ローカルグループポリシーエディター
##### lusrmgr.msc / ローカルユーザーとグループ（ローカル）
##### perfmon.msc / パフォーマンスモニター
##### printmanagement.msc
##### rsop.msc / Result Set of Policy / ポリシーの結果セット
##### secpol.msc / ローカルセキュリティポリシー
###### Console Tree
####### Security Settings
######## Account Policies / アカウントポリシー
######## Local Policies / ローカルポリシー
######## Windows Firewall with Advanced Security / セキュリティが強化されたWindowsファイアウォール
######## Network List Manager Policies / ネットワークリストマネージャーポリシー
######## Public Key Policies / 公開キーのポリシー
######## Software Restriction Policies / ソフトウェアの制限のポリシー
######## Application Control Policies / アプリケーション制御ポリシー
######## IP Security Policies on Local Computer / IPセキュリティポリシー（ローカルコンピューター）
######## Advanced Audit Policy Configuration / 監査ポリシーの詳細な構成
##### services.msc / サービス
##### SQLServerManager10.msc
##### taskschd.msc
##### tpm.msc
##### WF.msc
##### WmiMgmt.msc
##### tmp from msc.exe/Add or Remove Snap-ins
###### Active Directory Domains and Trusts
###### Active Directory Rights Management Services
###### Active Directory Sites and Services
###### Active Directory Users and Computers
###### ActiveX control
###### ADSI Edit
###### Authorization Manager
###### Certificate Templates
###### Certificates
###### Certification Authority
###### Component Services
###### Computer Management
###### Device Manager
###### DFS Management
###### DHCP
###### Disk Management
###### DNS
###### Enterprise PKI
###### Failover Cluster Manager
###### Failover Cluster Manager Host
###### File Server Resource Manager
###### Folder
###### Group Policy Object Editor
#### cpl
- コントロールパネルの各アイテム
- cplファイルはDLLファイルのため、コマンドラインで実行する場合、本来はcontrolコマンドのパラメータとして指定する必要がある。
  （control.exeはコントロールパネルの実行ファイル。）
  https://www.atmarkit.co.jp/ait/articles/0507/02/news016.html
##### appwiz.cpl / プログラムと機能
##### bthprops.cpl
##### collab.cpl
##### desk.cpl / 画面の解像度
##### Firewall.cpl / Windowsファイアウォール
##### hdwwiz.cpl / デバイスマネージャー
##### IDTNC64.cpl
##### igfxcpl.cpl
##### inetcpl.cpl / インターネットのプロパティ
##### infocardcpl.cpl
##### intl.cpl / 地域と言語
##### irprops.cpl
##### joy.cpl / ゲームコントローラー
##### main.cpl / マウスのプロパティ
##### mmsys.cpl / サウンド
##### ncpa.cpl / ネットワーク接続
##### powercfg.cpl / 電源オプション
##### sysdm.cpl / システムのプロパティ
##### TabletPC.cpl / ペンとタッチ
##### telephon.cpl / 所在地情報
##### timedate.cpl / 日付と時刻
##### wscui.cpl / アクションセンター
#### etc
#### 
##### winrm.cmd
- Windows Remote Management Command Line Tool
- Server限定の可能性あり
###### Usage
- winrm OPERATION RESOURCE_URI
###### OPERATIONS
####### winrm g[et] -?
####### winrm s[et] -?
####### winrm c[reate] -?
####### winrm d[elete] -?
####### winrm e[numerate] -?
####### winrm i[nvoke] -?
####### winrm id
####### winrm quickconfig -?
- Configures this machine to accept WS-Management requests from other machines.

### wbem\
#### wmic.exe / WMI (Windows Management Instrumentation)
- 
  システム管理用インターフェイス。
  WBEMというシステム管理を目的とした標準仕様に従って、WinOSに実装、拡張したもの。
  wmicというCommandLineツールを使って情報を取得したり操作できる。
  "wmic qfe"として適用済みのKBを取得できる。
### WindowsPowerShell\
#### v1.0
##### powershell.exe

## Server
### servermanagercmd.exe
### oclist.exe
### dcpromo.exe
## Link
- http://www.itmedia.co.jp/keywords/wincommand.html
- http://tech.nikkeibp.co.jp/it/article/COLUMN/20060221/230144/
