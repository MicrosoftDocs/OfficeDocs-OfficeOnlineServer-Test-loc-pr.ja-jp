---
title: Office Web Apps サーバーで使用できる Windows PowerShell
TOCTitle: Office Web Apps サーバーで使用できる Windows PowerShell
ms:assetid: 56bfd3b3-f563-423d-aea0-65b331f73b96
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/Ee890080(v=office.15)
ms:contentKeyID: 48796426
ms.date: 01/04/2018
mtps_version: v=office.15
ms.translationtype: HT
---

# Office Web Apps サーバーで使用できる Windows PowerShell

 

_**適用先:**Office Web Apps Server_

_**トピックの最終更新日:**2016-12-16_

**概要:** Office Web Apps サーバーの構成に使用する OfficeWebApps Windows PowerShell コマンドレットの記事を紹介します。

**対象ユーザー:** IT 担当者

Office Web Apps サーバー は、ブラウザー ベースのバージョンの Word、PowerPoint、Excel、および OneNote を提供する新しい Office サーバー製品です。単一の Office Web Apps サーバーファームで、SharePoint 2013、Lync Server 2013、Exchange Server 2013、共有フォルダー、および Web サイトを通じて Office ファイルにアクセスするユーザーをサポートできます。

![Office 2013 ロゴ](images/JJ219456.a106e261-2cd0-43b7-af77-92de7e4b6fb9(Office.15).png "Office 2013 ロゴ")次の表に示すのは、Office Web Apps サーバー で使用できる各 OfficeWebApps Windows PowerShell コマンドレットの記事の一覧とその説明です。


> [!TIP]
> コマンドレットを実行しても Windows PowerShell がこれらのコマンドレットを認識しない場合、<STRONG>OfficeWebApps</STRONG> モジュールをインポートする必要があります。次のコマンドを使用してください。<BR><CODE>Import-Module -Name OfficeWebApps</CODE>




### OfficeWebApps Windows PowerShell コマンドレット

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>記事</th>
<th>説明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="get-officewebappsfarm.md">Get-OfficeWebAppsFarm</a></p></td>
<td><p>現在のサーバーがメンバーである OfficeWebAppsFarm オブジェクトの詳細を戻します。</p></td>
</tr>
<tr class="even">
<td><p><a href="get-officewebappshost.md">Get-OfficeWebAppsHost</a></p></td>
<td><p>Office Web Apps サーバー ファームの許可リストにあるホスト ドメインのリストを取得します。</p></td>
</tr>
<tr class="odd">
<td><p><a href="get-officewebappsmachine.md">Get-OfficeWebAppsMachine</a></p></td>
<td><p>Office Web Apps サーバー ファームにある現在のサーバーの詳細を取得します。</p></td>
</tr>
<tr class="even">
<td><p><a href="new-officewebappsfarm.md">New-OfficeWebAppsFarm</a></p></td>
<td><p>ローカル コンピューターで新しい Office Web Apps サーバー ファームを作成します。</p></td>
</tr>
<tr class="odd">
<td><p><a href="new-officewebappshost.md">New-OfficeWebAppsHost</a></p></td>
<td><p>Office Web Apps サーバー ファームの許可リストにホスト ドメインを追加します。</p></td>
</tr>
<tr class="even">
<td><p><a href="new-officewebappsmachine.md">New-OfficeWebAppsMachine</a></p></td>
<td><p>既存の Office Web Apps サーバー ファームに現在のサーバーを追加します。</p></td>
</tr>
<tr class="odd">
<td><p><a href="remove-officewebappshost.md">Remove-OfficeWebAppsHost</a></p></td>
<td><p>Office Web Apps サーバー ファームの許可リストからホスト ドメインを削除します。</p></td>
</tr>
<tr class="even">
<td><p><a href="remove-officewebappsmachine.md">Remove-OfficeWebAppsMachine</a></p></td>
<td><p>Office Web Apps サーバー ファームから現在のサーバーを削除します。</p></td>
</tr>
<tr class="odd">
<td><p><a href="repair-officewebappsfarm.md">Repair-OfficeWebAppsFarm</a></p></td>
<td><p>Office Web Apps サーバー ファームから、正常でないというフラグが付いたすべてのサーバーを削除します。</p></td>
</tr>
<tr class="even">
<td><p><a href="set-officewebappsfarm.md">Set-OfficeWebAppsFarm</a></p></td>
<td><p>既存の Office Web Apps サーバー ファームの設定を構成します。</p></td>
</tr>
<tr class="odd">
<td><p><a href="set-officewebappsmachine.md">Set-OfficeWebAppsMachine</a></p></td>
<td><p>Office Web Apps サーバー ファームにある現在のサーバーの設定を変更します。</p></td>
</tr>
</tbody>
</table>


### IT 担当者向けの他の Office リソース

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><img src="images/Ee890080.22cad0f4-303d-4a40-90a3-fa08e69dfdaf(Office.15).png" title="新機能 (ボックス)" alt="新機能 (ボックス)" /></p></td>
<td><p><strong>新しい公開コンテンツ</strong></p></td>
<td><p>Office Web Apps サーバーに関する新しい記事または最近更新された記事の一覧については、次の記事を参照してください。</p>
<ul>
<li><p><a href="https://technet.microsoft.com/ja-jp/library/ff433481(v=office.15)">Office Web Apps および Office Web Apps サーバーに関する新しい公開コンテンツ</a></p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><img src="images/JJ219456.6b2d6dfa-7dc8-40fb-8335-af68b575f8cb(Office.15).png" title="作業の開始" alt="作業の開始" /></p></td>
<td><p><strong>概要</strong></p></td>
<td><p>Office Web Apps サーバーをダウンロードします。</p>
<ul>
<li><p><a href="http://go.microsoft.com/fwlink/p/?linkid=256561">ボリューム ライセンス サービス センター (VLSC)</a></p>
<p>Office Web Apps サーバー をダウンロードするには、Office Professional Plus 2013、Office Standard 2013、または Office for Mac 2011 のためのボリューム ライセンス条項に従ったライセンスが必要です。ダウンロード ファイルは、VLSC ポータルにおいてそれらの Office 製品の下にあります。</p></li>
</ul>
<p>Office Web Apps サーバー 用の言語パックをダウンロードします。</p>
<ul>
<li><p><a href="http://go.microsoft.com/fwlink/p/?linkid=263945">Microsoft ダウンロード センター</a></p></li>
</ul>
<p>Office Web Apps Server の詳細について説明します。</p>
<ul>
<li><p><a href="deploy-the-infrastructure-office-web-apps-server.md">インフラストラクチャの展開: Office Web Apps サーバー</a></p></li>
</ul>
<p>Office Server 製品が Office Web Apps サーバーを使用して Office ファイルを Web ベースで表示および編集する方法については、以下のリンクを参照してください。</p>
<ul>
<li><p><a href="use-office-web-apps-with-sharepoint-2013.md">SharePoint 2013 で Office Web Apps を使用する</a></p></li>
<li><p><a href="http://go.microsoft.com/fwlink/p/?linkid=256902%26clcid=0x411">Office Web Apps Server および Lync Server 2013 の展開</a></p></li>
<li><p><a href="http://go.microsoft.com/fwlink/p/?linkid=256611">Office Web Apps Server 2013 のテクニカル リファレンス</a></p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p><img src="images/JJ219456.6fa793ee-ede9-4476-901c-de96ea37fc3a(Office.15).png" title="グラフ アイコン" alt="グラフ アイコン" /></p></td>
<td><p><strong>フィードバックの提供</strong></p></td>
<td><p>Office 2013Office 365 ProPlus のドキュメントに関するフィードバックを提供するには、ページの下部にある [<strong>フィードバック</strong>] リンクを選択します。ドキュメント チームにフィードバックが直接送信されます。</p>
<p><img src="images/JJ219456.1863f854-8ce5-40e4-bd40-9bbe16591834(Office.15).png" title="電子メール" alt="電子メール" />  コンテンツを提案または詳細なドキュメントを要求する (またはエラーを報告する) 場合は、<a href="mailto:feedork@microsoft.com">feedork@microsoft.com</a> 宛てにご連絡ください。</p></td>
</tr>
</tbody>
</table>


## Office に関するトレーニングやその他のリソースを見つける


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>Download</strong></p>
<ul>
<li><p><a href="https://technet.microsoft.com/evalcenter/hh973391">Office 365 ProPlus</a></p></li>
<li><p><a href="https://go.microsoft.com/fwlink/p/?linkid=507653">Office 365</a></p></li>
<li><p><a href="https://technet.microsoft.com/ja-jp/evalcenter/ee390818.aspx">Office 2013</a></p></li>
<li><p><a href="https://code.msdn.microsoft.com/office/">Office のコード サンプル</a></p></li>
<li><p><a href="https://gallery.technet.microsoft.com/office/">Office のスクリプトおよびサンプル ファイル</a></p></li>
<li><p><a href="https://msdn.microsoft.com/ja-jp/office/aa905351">Office デベロッパーのダウンロード</a></p></li>
<li><p><a href="http://www.microsoft.com/ja-jp/download/office.aspx?q=office">Office ダウンロード</a></p></li>
<li><p><a href="http://www.microsoft.com/ja-jp/download/search.aspx?q=office+365">Office 365 のダウンロード</a></p></li>
</ul></td>
<td><p><strong>方法</strong></p>
<ul>
<li><p><a href="https://technet.microsoft.com/ja-jp/library/jj220060.aspx">Office 用アプリの作成</a></p></li>
<li><p><a href="https://technet.microsoft.com/ja-jp/library/cc178982.aspx">Office 2013 を展開する</a></p></li>
<li><p><a href="https://technet.microsoft.com/ja-jp/library/cc179068.aspx">Office 2013 を管理する</a></p></li>
<li><p><a href="https://technet.microsoft.com/ja-jp/office/ff381682.aspx">Office 2010 エンド ユーザー向けトレーニング</a></p></li>
<li><p><a href="https://msdn.microsoft.com/ja-jp/office/aa905496.aspx">Office SDK</a></p></li>
<li><p><a href="https://msdn.microsoft.com/ja-jp/office/aa905375">Office 開発者向けトレーニング</a></p></li>
<li><p><a href="http://www.microsoft.com/resources/msdn/ja-jp/office/media/video/video.html?cid=odc%26from=mscomodc">Office 開発者向けビデオ</a></p></li>
<li><p><a href="http://www.microsoft.com/resources/msdn/ja-jp/office/media/video/video.html?cid=o365%26from=mscomo365">Office 365 開発者向けビデオ</a></p></li>
<li><p><a href="https://technet.microsoft.com/ja-jp/office/ff519671">Office IT 担当者向けトレーニング</a></p></li>
<li><p><a href="http://www.microsoft.com/resources/technet/ja-jp/office/media/video/video.html?cid=otc%26from=mscomotc">Office IT 担当者向けビデオ</a></p></li>
<li><p><a href="http://www.microsoft.com/resources/technet/ja-jp/office/media/video/video.html?cid=o365%26from=mscomo365">Office 365 IT 担当者向けビデオ</a></p></li>
<li><p><a href="https://msdn.microsoft.com/ja-jp/openspecifications/">オープン仕様</a></p></li>
<li><p><a href="https://msdn.microsoft.com/ja-jp/library/cc307282(v=office.12).aspx">Office プロトコル</a></p></li>
</ul></td>
<td><p><strong>Sites</strong></p>
<ul>
<li><p><a href="https://msdn.microsoft.com/ja-jp/office">Office (開発者向け)</a></p></li>
<li><p><a href="https://technet.microsoft.com/ja-jp/office">Office (IT 担当者向け)</a></p></li>
<li><p><a href="https://msdn.microsoft.com/ja-jp/office/hh506337">Office 365 (開発者向け)</a></p></li>
<li><p><a href="https://technet.microsoft.com/ja-jp/hh912691">Office 365 (IT 担当者向け)</a></p></li>
<li><p><a href="https://technet.microsoft.com/ja-jp/library/cc303401.aspx">Office 2013 リソース キット</a></p></li>
<li><p><a href="https://msdn.microsoft.com/ja-jp/sharepoint">SharePoint (開発者向け)</a></p></li>
<li><p><a href="https://technet.microsoft.com/ja-jp/sharepoint">SharePoint (IT 担当者向け)</a></p></li>
<li><p><a href="https://msdn.microsoft.com/ja-jp/vstudio/aa718325">Visual Studio (開発者向け)</a></p></li>
<li><p><a href="http://office.microsoft.com/">Office.com</a></p></li>
</ul></td>
<td><p><strong>Help</strong></p>
<ul>
<li><p><a href="https://technet.microsoft.com/ja-jp/office/ee748587.aspx">Office 更新プログラム</a></p></li>
<li><p><a href="https://blogs.msdn.com/b/officeapps">Office および SharePoint 用アプリのブログ</a></p></li>
<li><p><a href="https://social.msdn.microsoft.com/forums/ja-jp/category/officedev%2coldevelopment%2csharepoint2010%2csharepoint%2cprojectserver2010%2cprojectprofessional2010%2cuc/">フォーラム: Office (開発者向け)</a></p></li>
<li><p><a href="https://answers.microsoft.com/ja-jp/msoffice">フォーラム:Office 365</a></p></li>
<li><p><a href="https://social.technet.microsoft.com/wiki">TechNet Wiki</a></p></li>
<li><p><a href="https://stackoverflow.com/search?q=office">StackOverflow: Office</a></p></li>
<li><p><a href="https://mvp.microsoft.com/ja-jp/mvp/search-mvp.aspx?kw=office">Office MVP</a></p></li>
<li><p><a href="https://technet.microsoft.com/ja-jp/ms772425">Office IT 担当者サポート</a></p></li>
<li><p><a href="https://msdn.microsoft.com/ja-jp/office/aa905515">Office 開発者サポート</a></p></li>
</ul></td>
</tr>
</tbody>
</table>


[](use-office-web-apps-with-sharepoint-2013.md)

