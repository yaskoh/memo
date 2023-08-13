# ASP.NET
## ASP.NET 4
## ASP.NET 5
- ASP.NET 5とASP.NET 4.6には基本的に互換性がない。
  ASP.NET 5は「次世代のASP.NET」で、これまでのASP.NETを一から作り直したもの。
  System.Webアセンブリへの依存も断ち切り、OS XやLinux上でも動作する。
## ASP.NET Core
## Link
- http://www.atmarkit.co.jp/ait/articles/1505/19/news016.html
## TeachYourSelf ASP.NET
### 1章
- [[http://msdn.microsoft.com/ja-jp/library/bb400852(v=vs.100).aspx][ASP.NETポータル]]
- .NetFrameork
    共通言語ランタイム / .NET Frameworkクラスライブラリ で構成される。
    - .NET Frameworkクラスライブラリ
        基本ライブラリ / ADO.NET / (アプリケーション)フレームワーク に分類できる
        - 基本ライブラリ
            文字列や構造化データの操作、セキュリティ・スレッド制御、ファイルシステムアクセス等
        - ADO.NET
            データベースやXMLへのアクセス手段
        - フレームワーク
            Windowsフォーム、ASP.NETなど。WPF,WCF,WF,WCS等も。
- ASP.NETの構造
    ブラウザからアクセスするためのアプリケーション開発と、
    API開発・アプリケーション連携のためのサービス開発がある。

### 2章
- 開きたいファイルを右クリックして、ブラウザを選択できる。
- WebアプリケーションとWebサイト
    Webアプリケーションは、csファイルをあらかじめビルドしておきdllとして含める必要がある。
    Webサイトは、csファイルをaspxファイルと同様に配置しておき、実行時にビルドが行われる。
    アプリはソリューションファイルで管理され、サイトはそうでない。
- アプリケーションフォルダ(予約フォルダ)
    あらかじめ役割と名前が決められたフォルダ。HTTP経由でアクセスできない。
    App_Browsers, App_Code, App_Data, App_GlobalResources, App_LocalResources, App_THemes, App_WebReferences, Binなど
- ファイルの種類
    .ascx, .master, .sitemap, .vb/cs, .mdf, Global.asax, Web.config, .html, .css, .jsなど
- コードビハインドモデル、コードインラインモデル
    コードビハインドモデルでは、プログラムとデザインが分離されており、
    複数人での分業がおこないやすい。デフォルトではこっち。
    コードインラインでは分業が行いにくい反面、管理がしやすい面もある。
- Pageオブジェクト
    Page派生クラスとして分離コードとデザイン定義コードをマージし、インスタンス化&実行している。
    Pageオブジェクトは毎回生成しなおされる。

#### Webフォームの基本構造
- ディレクティブ
    <%@ ディレクティブ名 属性名="属性値" ... %>
    @Pageのディレクティブの属性: Language, AutoEventWireup, CodeBehind, Inherits
- コード宣言ブロック
    <script runat="Server">~</script>
    インラインモデルでは、上記タグの間に書いたコードがサーバサイドで実行されるコードとみなされる。
    runatがServer以外、または指定されていない場合、クライアントサイドスクリプトとみなされクライアントに送信される。
- サーバーコントロール
    <asp:コントロール名 ID="ID値" runat="Server" プロパティ名="値" ...></asp:コントロール名>
    サーバコントロールは<form runat="Server">~</form>の内側に書く。<form~>はページ内に1回しか記述できない。

#### ASP.NETを理解する3つの仕組み
- サーバーコントロール
    - サーバーコントロールは、コントロールツリーと呼ばれるオブジェクト階層に変換される。
      <asp:~>以外のテキストはLiteralControlオブジェクト(固定テキスト)としてコントロールツリーに取り込まれる。
    - サーバーコントロールにはWebサーバーコントロールとHTMLサーバーコントロールがある。
      HTMLサーバーコントロールとは、従来のHTMLタグにサーバーコントロールとしての機能を付与したもの。
      新規作成する場合はWebサーバーコントロールを使用するべき。
      Webサーバーコントロールは、上位ブラウザーと下位ブラウザーを判別し、適切な出力をする等の機能があるものもある。
    - サーバーコントロールはクラスなので、メソッドやプロパティを持つ。
- イベントドリブンモデル
    - ソースビューからイベントハンドラーを作成した場合はPrivateに、それ以外はProtectedになる。たいした違いではない。
    - イベントハンドラーの引数は、object senderとevent e。eventはEventArgsクラスの派生クラス。
    - VBではHandles~というイベント関連付けを行っているが、C#ではaspxの方にonclick="btnSend_Click"と出る。
    - 自分自身のページ内容を送信し処理することをポストバックという。
      また、イベント発生に伴って処理がサーバ/クライアント間を行き来することをサーバーラウンドトリップという。
    - イベント処理： Page.PreInit* -> Page.Init* -> コントロールの初期化 -> Page.Load* -> 変更系イベント -> クリック系イベント -> Page.PreRender -> Page.Unload
      (*はページイベント)
    - 変更系イベントはデフォルトではプールにためられ、クリックイベント時等に反映されるように設定されている。
      ただし、AutoPostBackプロパティをTrueに設定すると、クリックイベントを待たずにポストバックを発生させられる。
- ビューステート
    - ポストバック時にもビューの状態を保持するための仕組み。
      隠しフィールドとしてhtmlに埋め込まれており、サーバーへ送信される。

### 3章

#### フォームコントロール

- TextBox
    TextModeプロパティで単一行/複数行/パスワード入力ボックス等の種別を設定できる。
- RadioButtonList
    ラジオボタンのリスト。
- CheckBoxList
    CheckBoxのリスト。
- DropDownList
    DropDownList
- ListBox
    SelectionModeプロパティで複数選択可能にできる。
- FileUpload
    PostedFileにより、アップロードされた情報をHttpPostedFileオブジェクトとして返す。
- HiddenField
    隠しフィールド

- リストコントロール
    |---------------+----------------------------------|
    | SelectedIndex | 選択項目のインデックス番号を取得 |
    | SelectedItem  | ListItemオブジェクトとして取得   |
    | SelectedValue | 選択項目の値を取得               |
    |---------------+----------------------------------|

    list.SelectedValue = list.Items(list.SelectedIndex).Value = list.SelectedItem.Value

#### 表示系コントロール

- Label/Literal
    Labelは<span>タグで修飾されているが、Literalは単に文字列だけを出力している。
    普段はスタイルを変更できるLabelを利用していれば問題ないが、
    JSやCSSを使いたい場合には、<span>タグが邪魔になる場合があるので、Literalが適している場合もあるかも。
- HyperLink
    ハイパーリンクを出力する。
    似たものにLinkButtonがあるが、ボタンクリックイベントが発生するか否かの違いあり。
- Image
    画像を表示する。

#### ボタンコントロール

- Button
- LinkButton
- ImageButton

- PostBackUrlプロパティ
    ポストバックを他のページに送信するためのプロパティ。
    クロスページぽすてぃんぐ。
    不便も多く、問題を引き起こす原因になりがちなので使用は控えたほうがよいらしい。

- OnClientClickプロパティ
    クリック時にJavaScriptを実行する。

#### 検証コントロール

    |----------------------------+------------------------|
    | RequiredFieldValidator     | 必須チェック           |
    | RangeValidator             | データ範囲チェック     |
    | CompareValidator           | 比較チェック           |
    | RegularExpressionValidator | 正規表現チェック       |
    | CustomValidator            | カスタムの検証チェック |
    | ValidationSummary          | 結果をサマリー表示     |
    |----------------------------+------------------------|
    ※RangeValidator/CompareValidator/RegularExpressionValidatorは値が空の場合に検証をスキップする。

    クライアントサイドとサーバサイド双方で妥当性検証を行う。
    スクリプトが有効になっていればクライアント側、無効であればサーバ側で処理が行われ、
    無駄なトラフィックが発生しないようになっている。

- Displayプロパティ
    Staticの場合、表示領域を静的に確保する（複数のメッセージがある場合でもスペースを詰めない）。
    Dynamicは自動でレイアウトを行う。
    Noneの場合は表示しない。ValidationSummaryコントロールで別表示する場合に利用。
- ErrorMessage / Textプロパティ
    ErrorMessageはValidationSummaryに引き渡すためのエラーメッセージ。
    Textは検証コントロール自身に表示するテキスト。ただし省略された場合はErrorMessageを表示する。
- IsValidプロパティ
    検証成否にかかわらず、サーバサイドの処理はキャンセルされず処理される可能性がある。
    クライアントサイドの検証が有効の場合は、エラーが発生した場合後続処理を中断するが、
    クライアントサイドスクリプトはユーザ側で有効・無効を切り替えられるため、有効を前提とするべきではない。。
    Page.IsValidでページ全体の検証コントロール成否を確認できる。
- Enabled/EnableClientScriptプロパティ
    クライアントサイドでの検証をとめたい場合はEnableClientScriptをFalseにする。
    サーバサイドも止めたい場合はEnabledをFalseにする。サーバサイドだけをとめることはできない。
- ValidationGroupプロパティ
    検証コントロールをグループ化する。
    単にValidationチェックを行いたくないだけであれば、CausesValidationプロパティをFalseにしてもよい。
- CssClassプロパティ
    ASP.NET4ではインラインスタイルが廃止されたので、CssClassを設定した上で、スタイルシートに設定を記述する必要がある。


- ValidationSummaryコントロール
    
- RegularExpressionValidatorコントロール
    正規表現の構文がサーバサイドとクライアントサイドで若干異なる。
    JavaScriptの正規表現は、.NET Frameworkの正規表現(Regexクラス)のサブセットなので、
    挙動をあわせる場合にはJavaScriptの表現範囲にあわせる必要がある。

### 4章

#### データバインドコントロール

     |-------------+------------------------------|
     | GridView    | グリッド表                   |
     | DetailsView | テンプレート固定の単票ビュー |
     | FormView    | 自由形式の単票ビュー         |
     | ListView    | 自由形式のリスト             |
     |-------------+------------------------------|

#### データソースコントロール

     |-------------------+------------------------------------|
     | SqlDataSource     | 一般的なリレーショナルデータベース |
     | AccessDataSource  | MSAccess                           |
     | SiteMapDataSource | サイトマップファイル               |
     | XmlDataSource     | XMLファイル                        |
     | ObjectDataSource  | ビジネスオブジェクト               |
     | LinqDataSource    | LINQ経由で取得したデータ           |
     | EntityDataSource  | エンティティ経由で取得したデータ   |
     |-------------------+------------------------------------|

#### GridView

- 接続文字列
    - 基本パラメータ
        Data Source (Server) / Database (Initial Catalog)など。略。
    - コネクションプーリング
        |---------------------+----------------------+------------|
        | パラメータ名        | 概要                 | デフォルト |
        |---------------------+----------------------+------------|
        | Pooling             | 有効/無効            | True       |
        | Connection Lifetime | 有効期間             | 0(最大)    |
        | Max Pool Size       | 格納できる最大接続数 | 100        |
        | Min Pool Size       | 維持する最小接続数   | 0          |
        |---------------------+----------------------+------------|

- XxxxxField
    |----------------+----------------------------------|
    | BoundField     | 通常のテキスト                   |
    | HyperLinkField | ハイパーリンク                   |
    | ImageField     | 画像                             |
    | CheckBoxField  | チェックボックス                 |
    | CommandField   | [選択][編集][削除]など           |
    | ButtonField    | CommandField以外のカスタムボタン |
    | TemplateField  | テンプレートにしたがって出力     |
    |----------------+----------------------------------|

- HtmlEncodeプロパティ
    "<"や">", "&"のようなHTML予約文字を"&lt;","&gt;","&amp;"などの文字列に変換するプロパティ。
- DataFormatStringプロパティ
    {インデックス番号[:書式文字列]}
    フォーマット表示する。
    ASP.NET3.5以前ではHtmlEncodeがTrueだと書式文字列が認識されないので注意。
- バインド式(Bind / Eval)
    Bind(フィールド名[,書式文字列])
    Eval(フィールド名[,書式文字列])
    Bind式は読み書き可能、Eval式は読み取り専用。
    そのため、データ更新を目的としたEditItemTemplateではBind,
    データ表示を目的としたItemTemplate, AlternatingItemTemplateはEvalを使うべき。
    


