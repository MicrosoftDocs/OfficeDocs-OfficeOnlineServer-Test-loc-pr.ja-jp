---
title: Set-OfficeWebAppsMachine
TOCTitle: Set-OfficeWebAppsMachine
ms:assetid: aeba2638-be88-4030-80fe-7e4bcd30309b
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/JJ219448(v=office.15)
ms:contentKeyID: 48796441
ms.date: 12/22/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# Set-OfficeWebAppsMachine

 

_**適用先:**Office Web Apps Server_

_**トピックの最終更新日:**2015-03-09_

Office Web Apps サーバー ファームにある現在のサーバーの設定を変更します。

## 構文

    Set-OfficeWebAppsMachine [-Confirm [<SwitchParameter>]] [-Master <String>] [-Roles <String[]>] [-WhatIf [<SwitchParameter>]]

## 解説

**Set-OfficeWebAppsMachine** コマンドレットは Office Web Apps サーバー ファームにある現在のサーバーの設定を変更します。この設定には、現在のサーバーと、ファームに割り当てられたマスター サーバーが持つ役割が含まれます。

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
<td><p><strong>Confirm</strong></p></td>
<td><p>省略可</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>コマンドを実行する前に確認メッセージを表示します。詳細については、次のコマンドを入力します。<strong>get-help about_commonparameters</strong></p></td>
</tr>
<tr class="even">
<td><p><strong>Master</strong></p></td>
<td><p>省略可</p></td>
<td><p>System.String</p></td>
<td><p></p>
<p>マスター ファーム構成ファイルを保存するサーバーを指定します。</p>
<p>ローカル サーバーをマスターとして設定する場合、Office Web Apps サーバー ファーム内の残りのサーバーのすべてで、それらが新しいマスターをポイントするように <strong>Set-OfficeWebAppsMachine -Master</strong> を実行する必要があります。</p></td>
</tr>
<tr class="odd">
<td><p><strong>Roles</strong></p></td>
<td><p>省略可</p></td>
<td><p>System.String[]</p></td>
<td><p>コンマ区切りで、ローカル サーバーに割り当てるサーバーの役割のリストを指定します。</p>
<p>役割の種類は以下のとおりです。</p>
<p><strong>All</strong></p>
<p><strong>FrontEnd</strong></p>
<p><strong>WordBackEnd</strong></p>
<p><strong>ExcelBackEnd</strong></p>
<p><strong>PowerPointBackEnd</strong></p>
<div class="alert">

> [!IMPORTANT]
> ベスト プラクティスとしては、Office Web Apps サーバー ファーム内のすべてのサーバーが、すべての役割を実行することを推奨します。Office Web Apps サーバー ファームが約 50 のサーバーを持つようになるまでは、役割を割り当てても意味がありません。


</div></td>
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

\------------------ 例 1 ---------------------

    (Get-OfficeWebAppsFarm).Machines

この例は、Office Web Apps サーバー ファーム内の各サーバーが持つ役割を示します。

\------------------ 例 2 ---------------------

    Set-OfficeWebAppsMachine -Roles FrontEnd

この例は、現在のサーバーをフロントエンド サーバーとして構成します。

\------------------ 例 3 ---------------------

    Set-OfficeWebAppsMachine -Roles All

この例は、現在のサーバーをすべての役割をホストするように構成します。

## 関連項目


[Get-OfficeWebAppsMachine](get-officewebappsmachine.md)  
[New-OfficeWebAppsMachine](new-officewebappsmachine.md)  
[Remove-OfficeWebAppsMachine](remove-officewebappsmachine.md)  


[Office Web Apps サーバーのコンテンツ ロードマップ](content-roadmap-for-office-web-apps-server.md)  
[インフラストラクチャの展開: Office Web Apps サーバー](deploy-the-infrastructure-office-web-apps-server.md)  
  

[](deploy-the-infrastructure-office-web-apps-server.md)

