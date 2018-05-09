---
title: New-SPWOPISuppressionSetting
TOCTitle: New-SPWOPISuppressionSetting
ms:assetid: 7e6bb8f5-3124-4568-80c6-02cae46b803b
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/JJ219443(v=office.15)
ms:contentKeyID: 48796431
ms.date: 12/22/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# New-SPWOPISuppressionSetting

 

_**適用先:**Office Web Apps, SharePoint Foundation 2013, SharePoint Server 2013_

_**トピックの最終更新日:**2015-03-09_

**New-SPWOPISuppressionSetting** コマンドレットでは、現在の SharePoint ファームで、指定したアクション、ファイル名拡張子、またはプログラム識別子の Office Web Apps をオフにします。

## 構文

    New-SPWOPISuppressionSetting [-Action <String>] [-AssignmentCollection <SPAssignmentCollection>] [-Confirm [<SwitchParameter>]] [-Extension <String>] [-ProgId <String>] [-WhatIf [<SwitchParameter>]]

## 解説

**New-SPWOPISuppressionSetting** コマンドレットでは、現在の SharePoint ファームで、指定したアクション、ファイル名拡張子、またはプログラム識別子 (ProgId) の Office Web Appsをオフにします。この処理は、リンクをドキュメントに送信するために、検出情報、またはリンク機能で SharePoint Share を使用する機能を保持する必要があり、受信者がそのドキュメントの種類に対して Office Web Appsを使用できるようにする場合に実行します。WOPI アプリケーション (Office Web Apps サーバーなど) ではなく Excel Services を使用して Excel ブックを表示する必要がある場合は、このコマンドレットを使用する必要があります。

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
<td><p><strong>Action</strong></p></td>
<td><p>省略可</p></td>
<td><p>System.String</p></td>
<td><p>指定した拡張子またはプログラム識別子 (ProgId) に対して抑制するアクションを指定します (&quot;view&quot;、&quot;edit&quot;、&quot;embedview&quot; など)。アクションの一覧を取得するには、<strong>Get-SPWOPIBinding</strong> を実行します。</p></td>
</tr>
<tr class="even">
<td><p><strong>AssignmentCollection</strong></p></td>
<td><p>省略可</p></td>
<td><p>Microsoft.SharePoint.PowerShell.SPAssignmentCollection</p></td>
<td><p>適切な破棄を行うためにオブジェクトを管理します。<strong>SPWeb</strong> や <strong>SPSite</strong> などのオブジェクトの使用によって大量のメモリが使用される場合があるので、Windows PowerShell スクリプトでこれらのオブジェクトを使用するには適切なメモリ管理が必要です。メモリの解放が必要になった場合は、<strong>SPAssignment</strong> オブジェクトを使用して、変数へのオブジェクトの割り当てとオブジェクトの破棄を行うことができます。割り当てコレクションまたは <strong>Global</strong> パラメーターが使用されない場合、<strong>SPWeb</strong>、<strong>SPSite</strong>、または <strong>SPSiteAdministration</strong> オブジェクトが使用されると、オブジェクトは自動的に破棄されます。</p>
<div class="alert">

> [!NOTE]
> <STRONG>Global</STRONG> パラメーターが使用されている場合は、オブジェクトはすべてグローバル ストアに格納されます。<STRONG>Stop-SPAssignment</STRONG> コマンドを使用してオブジェクトの使用または破棄を直接行わないと、メモリ不足のシナリオになる場合があります。


</div></td>
</tr>
<tr class="odd">
<td><p><strong>Confirm</strong></p></td>
<td><p>省略可</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>コマンドを実行する前に確認メッセージを表示します。詳細については、次のコマンドを入力します。<strong>get-help about_commonparameters</strong></p></td>
</tr>
<tr class="even">
<td><p><strong>Extension</strong></p></td>
<td><p>省略可</p></td>
<td><p>System.String</p></td>
<td><p>抑制するファイル名拡張子を指定します。WOPI アプリケーションでサポートされるファイル名拡張子の一覧を取得するには、Get-SPWOPIBinding を実行します。</p></td>
</tr>
<tr class="odd">
<td><p><strong>ProgId</strong></p></td>
<td><p>省略可</p></td>
<td><p>System.String</p></td>
<td><p>抑制するアプリケーションのプログラム識別子 (ProgId) を指定します。WOPI アプリケーションでサポートされる ProgId の一覧を取得するには、Get-SPWOPIBinding を実行します。</p></td>
</tr>
<tr class="even">
<td><p><strong>WhatIf</strong></p></td>
<td><p>省略可</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>コマンドを実行する代わりに、コマンドの実行結果を説明するメッセージを表示します。詳細については、次のコマンドを入力します。<strong>get-help about_commonparameters</strong>。</p></td>
</tr>
</tbody>
</table>


## 入力の種類

## 戻り値の種類

## 例

\-------------- 例 1 -----------------

    New-SPWOPISuppressionSetting -Extension "XLSX" -Action "view"

    New-SPWOPISuppressionSetting -Extension "XLS" -Action "view"

この例では、ファイル名拡張子が ".xlsx" または ".xls" の Excel ブックを、ユーザーが Office Web Apps を使用して表示する機能をオフにします。

## 関連項目


[Get-SPWOPISuppressionSetting](get-spwopisuppressionsetting.md)  
[Remove-SPWOPISuppressionSetting](remove-spwopisuppressionsetting.md)  


[Office Web Apps サーバーのコンテンツ ロードマップ](content-roadmap-for-office-web-apps-server.md)  
[SharePoint 2013 で Office Web Apps を使用する](use-office-web-apps-with-sharepoint-2013.md)

