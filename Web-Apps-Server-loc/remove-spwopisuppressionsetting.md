---
title: Remove-SPWOPISuppressionSetting
TOCTitle: Remove-SPWOPISuppressionSetting
ms:assetid: cbaef5a8-e682-4166-be44-15ab1c79acca
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/JJ219452(v=office.15)
ms:contentKeyID: 48796448
ms.date: 12/22/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# Remove-SPWOPISuppressionSetting

 

_**適用先:**Office Web Apps, SharePoint Foundation 2013, SharePoint Server 2013_

_**トピックの最終更新日:**2015-03-09_

このコマンドレットが実行されている現在の SharePoint ファームで、ファイル名拡張子またはプログラム ID およびアクションの抑制設定を削除します。

## 構文

    Remove-SPWOPISuppressionSetting [-Action <String>] [-AssignmentCollection <SPAssignmentCollection>] [-Confirm [<SwitchParameter>]] [-Extension <String>] [-ProgId <String>] [-WhatIf [<SwitchParameter>]]

    Remove-SPWOPISuppressionSetting [-AssignmentCollection <SPAssignmentCollection>] [-Confirm [<SwitchParameter>]] [-Identity <String>] [-WhatIf [<SwitchParameter>]]

## 解説

**Remove-SPWOPISuppressionSetting** コマンドレットでは、このコマンドレットが実行されている現在の SharePoint ファームで、ファイル名拡張子またはプログラム識別子 (ProgID) およびアクションの抑制設定を削除します。

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
<td><p>指定したファイル名拡張子またはプログラム識別子 (ProgId) のアクションを指定します (&quot;view&quot;、&quot;edit&quot;、&quot;embedview&quot; など)。</p></td>
</tr>
<tr class="even">
<td><p><strong>AssignmentCollection</strong></p></td>
<td><p>省略可</p></td>
<td><p>Microsoft.SharePoint.PowerShell.SPAssignmentCollection</p></td>
<td><p>適切な破棄を行うためにオブジェクトを管理します。<strong>SPWeb</strong> や <strong>SPSite</strong> などのオブジェクトの使用によって大量のメモリが使用される場合があるので、Windows PowerShell スクリプトでこれらのオブジェクトを使用するには適切なメモリ管理が必要です。メモリの解放が必要になった場合は、<strong>SPAssignment</strong> オブジェクトを使用して、変数へのオブジェクトの割り当てとオブジェクトの破棄を行うことができます。割り当てコレクションまたは <strong>Global</strong> パラメーターが使用されない場合、<strong>SPWeb</strong>、<strong>SPSite</strong>、または <strong>SPSiteAdministration</strong> オブジェクトが使用されると、オブジェクトは自動的に破棄されます。</p>
<div class="alert">

> [!NOTE]
> <STRONG>Global</STRONG> パラメーターが使用されている場合は、オブジェクトはすべてグローバル ストアに格納されます。<STRONG>Stop-SPAssignment</STRONG> コマンドを使用してオブジェクトの使用または破棄を直接行わないと、メモリ不足のシナリオになる場合があります。


</div>
<p></p></td>
</tr>
<tr class="odd">
<td><p><strong>Confirm</strong></p></td>
<td><p>省略可</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>コマンドを実行する前に確認メッセージを表示します。詳細については、次のコマンドを入力します。<strong>get-help about_commonparameters</strong>。</p></td>
</tr>
<tr class="even">
<td><p><strong>Extension</strong></p></td>
<td><p>省略可</p></td>
<td><p>System.String</p></td>
<td><p>ファイル名拡張子を指定します。WOPI アプリケーションでサポートされるファイル名拡張子の一覧を取得するには、Get-SPWOPIBinding を実行します。</p></td>
</tr>
<tr class="odd">
<td><p><strong>Identity</strong></p></td>
<td><p>省略可</p></td>
<td><p>System.String</p></td>
<td><p>SPWOPISuppressionSetting を表す文字列を指定します。このような文字列の例を確認するには、Get-SPWOPISuppressionSetting を実行します。</p></td>
</tr>
<tr class="even">
<td><p><strong>ProgId</strong></p></td>
<td><p>省略可</p></td>
<td><p>System.String</p></td>
<td><p>抑制するアプリケーションのプログラム識別子 (ProgID) を指定します。WOPI アプリケーションでサポートされる ProgID の一覧を取得するには、Get-SPWOPIBinding を実行します。</p></td>
</tr>
<tr class="odd">
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

    Remove-SPWOPISuppressionSetting -Extension "XLSX" -Action "view"

この例では、抑制設定を削除し、ファイル名拡張子が ".xlsx" の Excel ブックを表示します。

\-------------- 例 2 -----------------

    Get-SPWOPISuppressionSetting | Remove-SPWOPISuppressionSetting

この例では、このコマンドレットが実行されている現在の SharePoint ファームですべての抑制設定を削除します。

## 関連項目


[New-SPWOPISuppressionSetting](new-spwopisuppressionsetting.md)  
[Get-SPWOPISuppressionSetting](get-spwopisuppressionsetting.md)  


[Office Web Apps サーバーのコンテンツ ロードマップ](content-roadmap-for-office-web-apps-server.md)  
[SharePoint 2013 で Office Web Apps を使用する](use-office-web-apps-with-sharepoint-2013.md)

