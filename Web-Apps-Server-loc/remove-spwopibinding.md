---
title: Remove-SPWOPIBinding
TOCTitle: Remove-SPWOPIBinding
ms:assetid: 52855c21-ee2c-497a-b308-bf5eeabe4bbe
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/JJ219438(v=office.15)
ms:contentKeyID: 48796425
ms.date: 12/22/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# Remove-SPWOPIBinding

 

_**適用先:**Office Web Apps, SharePoint Foundation 2013, SharePoint Server 2013_

_**トピックの最終更新日:**2015-03-09_

このコマンドレットが実行されている現在の SharePoint ファームで、アプリケーション、ファイル名拡張子、および関連するアクションのバインドを削除します。

## 構文

    Remove-SPWOPIBinding [[-Identity] <SPWopiBindingPipeBind>] [-AssignmentCollection <SPAssignmentCollection>] [-Confirm [<SwitchParameter>]] [-WhatIf [<SwitchParameter>]]

    Remove-SPWOPIBinding [-Action <String>] [-Application <String>] [-AssignmentCollection <SPAssignmentCollection>] [-Confirm [<SwitchParameter>]] [-Extension <String>] [-ProgId <String>] [-Server <String>] [-WhatIf [<SwitchParameter>]] [-WOPIZone <String>]

    Remove-SPWOPIBinding [-All <SwitchParameter>] [-AssignmentCollection <SPAssignmentCollection>] [-Confirm [<SwitchParameter>]] [-WhatIf [<SwitchParameter>]]

## 解説

**Remove-SPWOPIBinding** では、このコマンドレットが実行されている現在の SharePoint ファームで、アプリケーション、ファイル名拡張子、および関連するアクションのバインドを削除します。このコマンドレットの実行後、必要に応じてバインドを再作成するには、**New-SPWOPIBinding** を使用します。アプリケーションのすべてのバインドを削除すると、ユーザーがそのアプリケーションのリンク機能では Office Web Appsまたは SharePoint Share を使用できなくなります。また、このコマンドレットが実行されている SharePoint ファームですべてのバインドを削除すると、SharePoint ライブラリ内のアプリケーションのリンク機能では Office Web Appsまたは SharePoint Share を使用できなくなります。

既定のクリックで Office Web Appsを使用する機能を停止しながら、リンクをドキュメントに送信するために、バインド検出情報と、リンク機能で SharePoint Share を使用する機能を保持する必要がある場合、また、受信者がその種類のドキュメントに対して Office Web Appsを使用できるようにする場合は、**New-SPWOPISuppression** コマンドレットを使用します。

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
<td><p><strong>Identity</strong></p></td>
<td><p>省略可</p></td>
<td><p>Microsoft.SharePoint.PowerShell.SPWopiBindingPipeBind</p></td>
<td><p>バインドを指定します。</p></td>
</tr>
<tr class="even">
<td><p><strong>Action</strong></p></td>
<td><p>省略可</p></td>
<td><p>System.String</p></td>
<td><p>削除するバインドのアクションを指定します (&quot;view&quot;、&quot;edit&quot;、&quot;embedview&quot; など)。アクションの一覧を取得するには、<strong>Get-SPWOPIBinding</strong> を実行します。通常、このパラメーターは使用しません。あるアクションを指定して、別のアクションを指定しないと、SharePoint の一部の機能が動作しなくなることがあります。</p></td>
</tr>
<tr class="odd">
<td><p><strong>All</strong></p></td>
<td><p>省略可</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>すべてのバインドを削除します。</p></td>
</tr>
<tr class="even">
<td><p><strong>Application</strong></p></td>
<td><p>省略可</p></td>
<td><p>System.String</p></td>
<td><p>削除するバインドのアプリケーションを指定します (&quot;Word&quot;、&quot;Excel&quot;、&quot;PowerPoint&quot;、&quot;OneNote&quot; など)。アプリケーションの一覧を取得するには、<strong>Get-SPWOPIBinding</strong> を実行します。</p></td>
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
<td><p>コマンドを実行する前に確認メッセージを表示します。詳細については、次のコマンドを入力します。<strong>get-help about_commonparameters</strong>。</p></td>
</tr>
<tr class="odd">
<td><p><strong>Extension</strong></p></td>
<td><p>省略可</p></td>
<td><p>System.String</p></td>
<td><p>削除するバインドのファイル名拡張子を指定します。ファイル名拡張子の一覧を取得するには、<strong>Get-SPWOPIBinding</strong> を実行します。</p></td>
</tr>
<tr class="even">
<td><p><strong>ProgId</strong></p></td>
<td><p>省略可</p></td>
<td><p>System.String</p></td>
<td><p>削除するバインドのアプリケーションのプログラム識別子 (ProgID) を指定します。ProgID の一覧を取得するには、<strong>Get-SPWOPIBinding</strong> を実行します。このパラメーターを使用して、OneNote のバインドを削除するだけでもかまいません。</p></td>
</tr>
<tr class="odd">
<td><p><strong>Server</strong></p></td>
<td><p>省略可</p></td>
<td><p>System.String</p></td>
<td><p>削除するバインドの WOPI アプリケーション (Office Web Apps サーバーなど) の名前を指定します。</p></td>
</tr>
<tr class="even">
<td><p><strong>WhatIf</strong></p></td>
<td><p>省略可</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>コマンドを実行する代わりに、コマンドの実行結果を説明するメッセージを表示します。詳細については、次のコマンドを入力します。<strong>get-help about_commonparameters</strong></p></td>
</tr>
<tr class="odd">
<td><p><strong>WOPIZone</strong></p></td>
<td><p>省略可</p></td>
<td><p>System.String</p></td>
<td><p>削除するバインドのゾーンを指定します。</p></td>
</tr>
</tbody>
</table>


## 入力の種類

## 戻り値の種類

## 例

\-------------- 例 1 -----------------

    Remove-SPWOPIBinding -Application "Excel"

この例では、このコマンドレットが実行されている現在の SharePoint ファームで Excel のすべてのバインドを削除します。

\-------------- 例 2　-----------------

    Remove-SPWOPIBinding -All:$true

この例では、このコマンドレットが実行されている現在の SharePoint ファームですべてのバインドを削除します。

\-------------- 例 3 -----------------

    Get-SPWOPIBinding -Action "MobileView" | Remove-SPWOPIBinding

この例では、このコマンドレットが実行されている現在の SharePoint ファームで Office Mobile Web Apps のすべてのバインドを削除します。

## 関連項目


[New-SPWOPIBinding](new-spwopibinding.md)  
[Get-SPWOPIBinding](get-spwopibinding.md)  
[Set-SPWOPIBinding](set-spwopibinding.md)  
[New-SPWOPISuppressionSetting](new-spwopisuppressionsetting.md)  


[Office Web Apps サーバーのコンテンツ ロードマップ](content-roadmap-for-office-web-apps-server.md)  
[SharePoint 2013 で Office Web Apps を使用する](use-office-web-apps-with-sharepoint-2013.md)

