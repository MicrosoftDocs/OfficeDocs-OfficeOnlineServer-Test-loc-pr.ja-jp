---
title: New-OfficeWebAppsMachine
TOCTitle: New-OfficeWebAppsMachine
ms:assetid: b0385c4e-61fc-4607-a48c-64d8f4e80651
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/JJ219449(v=office.15)
ms:contentKeyID: 48796442
ms.date: 12/22/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# New-OfficeWebAppsMachine

 

_**適用先:**Office Web Apps Server_

_**トピックの最終更新日:**2015-03-09_

既存の Office Web Apps サーバー ファームに現在のサーバーを追加します。

## 構文

    New-OfficeWebAppsMachine [-MachineToJoin] <String> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-Roles <String[]>] [-WhatIf [<SwitchParameter>]]

## 解説

**New-OfficeWebAppsMachine** コマンドレットは既存の Office Web Apps サーバー ファームに現在のサーバーを追加し、オプションとして新しいサーバーに 1 つまたは複数の役割を設定します。

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
<td><p><strong>MachineToJoin</strong></p></td>
<td><p>必須</p></td>
<td><p>System.String</p></td>
<td><p>すでに Office Web Apps サーバー ファームのメンバーであるすべてのサーバーの名前を指定します。</p></td>
</tr>
<tr class="even">
<td><p><strong>Confirm</strong></p></td>
<td><p>省略可</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>コマンドを実行する前に確認メッセージを表示します。詳細については、次のコマンドを入力します。<strong>get-help about_commonparameters</strong></p></td>
</tr>
<tr class="odd">
<td><p><strong>Force</strong></p></td>
<td><p>省略可</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>すべてのユーザー プロンプトへの回答が [はい] であると想定します。</p></td>
</tr>
<tr class="even">
<td><p><strong>Roles</strong></p></td>
<td><p>省略可</p></td>
<td><p>System.String[]</p></td>
<td><p>新しいサーバーを割り当てる目的で、コンマで区切られた 1 つまたは複数のサーバーの役割を指定します。役割が指定されない場合、サーバーはすべての役割を割り当てられます。</p>
<p>役割の種類は以下のとおりです。</p>
<p><strong>FrontEnd</strong></p>
<p><strong>WordBackEnd</strong></p>
<p><strong>ExcelBackEnd</strong></p>
<p><strong>PowerPointBackEnd</strong></p>
<div class="alert">

> [!IMPORTANT]
> ベスト プラクティスとしては、Office Web Apps サーバー ファーム内のすべてのサーバーが、すべての役割を実行することを推奨します。Office Web Apps サーバー ファームが約 50 のサーバーを持つようになるまでは、役割を割り当てても意味がありません。


</div></td>
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

\------------------ 例 1 ---------------------

    New-OfficeWebAppsMachine -MachineToJoin server1.contoso.com

この例は、server1.contoso.com という名前のサーバーで実行中の Office Web Apps サーバー ファームに現在のサーバーを追加します。

## 関連項目


[Get-OfficeWebAppsMachine](get-officewebappsmachine.md)  
[Remove-OfficeWebAppsMachine](remove-officewebappsmachine.md)  
[Set-OfficeWebAppsMachine](set-officewebappsmachine.md)  


[Office Web Apps サーバーのコンテンツ ロードマップ](content-roadmap-for-office-web-apps-server.md)  
[インフラストラクチャの展開: Office Web Apps サーバー](deploy-the-infrastructure-office-web-apps-server.md)  
  

[](deploy-the-infrastructure-office-web-apps-server.md)

