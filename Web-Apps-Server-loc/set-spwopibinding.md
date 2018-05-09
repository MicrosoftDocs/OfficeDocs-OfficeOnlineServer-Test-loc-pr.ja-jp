---
title: Set-SPWOPIBinding
TOCTitle: Set-SPWOPIBinding
ms:assetid: e373528f-e69b-4e25-9df4-3a5f80ab64ac
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/JJ219454(v=office.15)
ms:contentKeyID: 48796451
ms.date: 12/22/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# Set-SPWOPIBinding

 

_**適用先:**Office Web Apps, SharePoint Foundation 2013, SharePoint Server 2013_

_**トピックの最終更新日:**2015-03-09_

アプリケーションまたはファイル名拡張子バインドの既定のクリック操作を更新します。

## 構文

    Set-SPWOPIBinding [-Identity] <SPWopiBindingPipeBind> -DefaultAction <SwitchParameter> [-AssignmentCollection <SPAssignmentCollection>] [-Confirm [<SwitchParameter>]] [-WhatIf [<SwitchParameter>]]

## 解説

**Set-SPWOPIBinding** コマンドレットでは、アプリケーションまたはファイル名拡張子バインドの既定のクリック操作を更新します。たとえば、SharePoint ライブラリの Word 文書を表示する既定のクリック操作を設定できます。これを行うには、"view"-"Word" バインドの既定の操作を true に設定します。

通常、このコマンドの Identity プロパティの値として **Get-SPWOPIBinding** コマンドの出力を使用します。詳細については、「[Get-SPWOPIBinding](get-spwopibinding.md)」をご覧ください。


> [!IMPORTANT]
> <STRONG>New-SPWOPIBinding</STRONG> コマンドを使用して作成されたバインドのみを設定できます。組み込みのバインド、たとえば SharePoint ライブラリの Word 文書を表示するときに実行される操作を上書きするには、<STRONG>New-SPWOPIBinding</STRONG> を使用して新しいバインドを作成し、別の操作を割り当てます。詳細については、「<A href="new-spwopibinding.md">New-SPWOPIBinding</A>」をご覧ください。



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
<td><p>必須</p></td>
<td><p>Microsoft.SharePoint.PowerShell.SPWopiBindingPipeBind</p></td>
<td><p>バインドを指定します。通常、Identity の値として <strong>Get-SPWOPIBinding</strong> コマンドの出力を使用します。</p></td>
</tr>
<tr class="even">
<td><p><strong>DefaultAction</strong></p></td>
<td><p>必須</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>バインドを、そのバインドにおけるアプリケーションまたはファイル名拡張子の既定のクリック操作として設定するかどうかを指定します。</p></td>
</tr>
<tr class="odd">
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
<tr class="even">
<td><p><strong>Confirm</strong></p></td>
<td><p>省略可</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>コマンドを実行する前に確認メッセージを表示します。詳細については、次のコマンドを入力します。<strong>get-help about_commonparameters</strong>。</p></td>
</tr>
<tr class="odd">
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

\-------------- 例 -----------------

    Get-SPWOPIBinding -Action "view" -Application "Word"| Set-SPWOPIBinding -DefaultAction

この例では、SharePoint ライブラリの Word 文書に対して、表示の既定のクリック操作を設定します。Word に対して表示の既定のクリック操作が設定されているかどうかを確認するには、**Get-SPWOPIBinding ?Action "view" ?Application "Word"** コマンドレットを実行します。**IsDefaultAction** 値は "True" に設定されます。

## 関連項目


[Get-SPWOPIBinding](get-spwopibinding.md)  
[Remove-SPWOPIBinding](remove-spwopibinding.md)  
[New-SPWOPIBinding](new-spwopibinding.md)  


[Office Web Apps サーバーのコンテンツ ロードマップ](content-roadmap-for-office-web-apps-server.md)  
[SharePoint 2013 で Office Web Apps を使用する](use-office-web-apps-with-sharepoint-2013.md)

