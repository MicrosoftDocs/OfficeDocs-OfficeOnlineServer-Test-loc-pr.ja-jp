---
title: New-SPWOPIBinding
TOCTitle: New-SPWOPIBinding
ms:assetid: 696f01b4-a144-431b-9bae-1c3ede78609d
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/JJ219441(v=office.15)
ms:contentKeyID: 48796429
ms.date: 12/22/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# New-SPWOPIBinding

 

_**適用先:**Office Web Apps, SharePoint Foundation 2013, SharePoint Server 2013_

_**トピックの最終更新日:**2015-03-09_

このコマンドレットが実行されている現在の SharePoint ファームで、新しいバインドを作成し、ファイル名拡張子またはアプリケーションとアクションを関連付けます。

## 構文

    New-SPWOPIBinding -ServerName <String> [-Action <String>] [-AllowHTTP <SwitchParameter>] [-Application <String>] [-AssignmentCollection <SPAssignmentCollection>] [-Confirm [<SwitchParameter>]] [-Extension <String>] [-FileName <String>] [-ProgId <String>] [-WhatIf [<SwitchParameter>]]

## 解説

**New-SPWOPIBinding** コマンドレットでは、このコマンドレットが実行されている現在の SharePoint ファームで、ファイル名拡張子またはアプリケーションとアクションを関連付けます。各バインドを使用することで、WOPI アプリケーションを使って、SharePoint ライブラリにあるファイルを表示または編集できます。たとえば、SharePoint ドキュメントの一覧に Word 文書が表示されている場合、SharePoint リストには、その SharePoint ファームで Word にバインドされているアクションに基づいて文書の表示または編集オプションが表示されます。

Office Web Appsに対して WOPI アプリケーション (Office Web Apps サーバーが実行されているサーバーなど) を使用する場合、Office Web Appsを使用できるようにするには、SharePoint ファームでこのコマンドレットを実行しておく必要があります。

バインド (または関連付け) が既に存在するアプリケーションまたはファイル名拡張子に対して **New-SPWOPIBinding** を実行すると、コマンドレットは失敗します。

SharePoint 管理シェル

## パラメーター


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>パラメーター</th>
<th>必須</th>
<th>型</th>
<th>説明</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>ServerName</strong></p></td>
<td><p>必須</p></td>
<td><p>System.String</p></td>
<td><p>WOPI アプリケーション (Office Web Apps サーバー が実行されているサーバーなど) の名前または完全修飾ドメイン名 (FQDN) を指定します。</p></td>
</tr>
<tr class="even">
<td><p><strong>Action</strong></p></td>
<td><p>省略可</p></td>
<td><p>System.String</p></td>
<td><p>バインドするアクションを指定します (&quot;view&quot;、&quot;edit&quot;、&quot;embedview&quot; など)。WOPI アプリケーションがサポートするアクションの一覧を取得するには、<strong>Get-SPWOPIBinding</strong> を実行します。通常、このパラメーターは使用しません。あるアクションを指定して、別のアクションを指定しないと、一部の SharePoint の機能が動作しなくなることがあります。</p></td>
</tr>
<tr class="odd">
<td><p><strong>AllowHTTP</strong></p></td>
<td><p>省略可</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>WOPI アプリケーションでサポートされる情報を、HTTP を使用して検出できるように指定します。True が指定されていると、WOPI アプリケーションからの検出情報が保護なしの接続で送信されます。</p></td>
</tr>
<tr class="even">
<td><p><strong>Application</strong></p></td>
<td><p>省略可</p></td>
<td><p>System.String</p></td>
<td><p>バインドするアプリケーションを指定します。&quot;Word&quot;、&quot;Excel&quot;、&quot;PowerPoint&quot;、&quot;OneNote&quot; などのアプリケーションを指定できます。WOPI アプリケーションでサポートされるアプリケーションの一覧を取得するには、<strong>Get-SPWOPIBinding</strong> を実行します。</p></td>
</tr>
<tr class="odd">
<td><p><strong>AssignmentCollection</strong></p></td>
<td><p>省略可</p></td>
<td><p>Microsoft.SharePoint.PowerShell.SPAssignmentCollection</p></td>
<td><p>適切な破棄を行うためにオブジェクトを管理します。<strong>SPWeb</strong> や <strong>SPSite</strong> などのオブジェクトの使用によって大量のメモリが使用される場合があるので、Windows PowerShell スクリプトでこれらのオブジェクトを使用するには適切なメモリ管理が必要です。メモリの解放が必要になった場合は、<strong>SPAssignment</strong> オブジェクトを使用して、変数へのオブジェクトの割り当てとオブジェクトの破棄を行うことができます。割り当てコレクションまたは <strong>Global</strong> パラメーターが使用されない場合、<strong>SPWeb</strong>、<strong>SPSite</strong>、または <strong>SPSiteAdministration</strong> オブジェクトが使用されると、オブジェクトは自動的に破棄されます。</p>
<div class="alert">

> [!NOTE]
> <STRONG>Global</STRONG> パラメーターが使用されている場合は、オブジェクトはすべてグローバル ストアに格納されます。<STRONG>Stop-SPAssignment</STRONG> コマンドを使用してオブジェクトの使用または破棄を直接行わないと、メモリ不足のシナリオになる場合があります。


</div></td>
</tr>
<tr class="even">
<td><p><strong>Confirm</strong></p></td>
<td><p>省略可</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>コマンドを実行する前に確認メッセージを表示します。詳細については、次のコマンドを入力します。<strong>get-help about_commonparameters</strong></p></td>
</tr>
<tr class="odd">
<td><p><strong>Extension</strong></p></td>
<td><p>省略可</p></td>
<td><p>System.String</p></td>
<td><p>バインドするファイル名拡張子を指定します。WOPI アプリケーションでサポートされるファイル名拡張子の一覧を取得するには、<strong>Get-SPWOPIBinding</strong> を実行します。</p></td>
</tr>
<tr class="even">
<td><p><strong>FileName</strong></p></td>
<td><p>省略可</p></td>
<td><p>System.String</p></td>
<td><p>WOPI アプリケーションの検出情報が格納されている xml ファイルのパスを指定します。検出情報は、WOPI アプリケーションに直接要求するのではなく、xml ファイルから読み込むことができます。</p></td>
</tr>
<tr class="odd">
<td><p><strong>ProgId</strong></p></td>
<td><p>省略可</p></td>
<td><p>System.String</p></td>
<td><p>バインドするアプリケーションのプログラム識別子 (ProgID) を指定します。WOPI アプリケーションでサポートされる ProgID の一覧を取得するには、<strong>Get-SPWOPIBinding</strong> を実行します。このパラメーターを使用して、アクションを OneNote フォルダーに関連付けるだけでもかまいません。</p></td>
</tr>
<tr class="even">
<td><p><strong>WhatIf</strong></p></td>
<td><p>省略可</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>コマンドを実行する代わりに、コマンドの実行結果を説明するメッセージを表示します。詳細については、次のコマンドを入力します。<strong>get-help about_commonparameters</strong></p></td>
</tr>
</tbody>
</table>


## 入力の種類

## 戻り値の種類

## 例

\-------------- 例 1 -----------------

    New-SPWOPIBinding -ServerName "Server.corp.Contoso.com"

この例では、このコマンドレットが実行されている現在の SharePoint ファームで、WOPI アプリケーションがサポートするすべてのアプリケーションとファイル名拡張子に対してバインドを作成します。

\-------------- 例 2　-----------------

    New-SPWOPIBinding -ServerName "Server.corp.Contoso.com" -Application "Excel"

この例では、このコマンドレットが実行されている現在の SharePoint ファームで、Excel と、WOPI アプリケーションがサポートする Excel のすべてのアクションを関連付けます。

## 関連項目


[Get-SPWOPIBinding](get-spwopibinding.md)  
[Set-SPWOPIBinding](set-spwopibinding.md)  
[Remove-SPWOPIBinding](remove-spwopibinding.md)  


[Office Web Apps サーバーのコンテンツ ロードマップ](content-roadmap-for-office-web-apps-server.md)  
[SharePoint 2013 で Office Web Apps を使用する](use-office-web-apps-with-sharepoint-2013.md)

