---
title: Repair-OfficeWebAppsFarm
TOCTitle: Repair-OfficeWebAppsFarm
ms:assetid: 083d8e25-ce82-4884-9bbc-06375185011c
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/JJ219433(v=office.15)
ms:contentKeyID: 48796417
ms.date: 12/22/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# Repair-OfficeWebAppsFarm

 

_**適用先:**Office Web Apps Server_

_**トピックの最終更新日:**2015-03-09_

Office Web Apps サーバー ファームから、正常でないというフラグが付いたすべてのサーバーを削除します。

## 構文

    Repair-OfficeWebAppsFarm [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 解説

**Repair-OfficeWebAppsFarm** コマンドレットは、Office Web Apps サーバー ファームから、正常でないとフラグが付けられたすべてのサーバーを削除します。このコマンドレットは、ファーム トポロジを更新しますが、削除されるサーバーのサービスおよび Web アプリケーションはクリーン アップしません。このことから、すべての情報がファームから削除されるように、可能な限り、正常でないサーバーから **Remove-OfficeWebAppsMachine** コマンドレットを実行することを推奨します。正常でないサーバーで障害が発生し、それらのサーバーで、直接、**Remove-OfficeWebAppsMachine** コマンドレットを実行できない場合に限り、**Repair-OfficeWebAppsFarm** コマンドレットを使用します。

正常でないサーバーが複数ある場合、各サーバーを削除する前に、確認がされます。すべてのサーバーが正常の場合、このコマンドレットは何も動作を行いません。

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
<th>種類</th>
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
<td><p><strong>Force</strong></p></td>
<td><p>省略可</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>すべてのユーザー プロンプトへの回答が [はい] であると想定します。</p></td>
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

## 戻り値の型

## 例

\------------------ 例 1 ---------------------

    (Get-OfficeWebAppsFarm).Machines

この例では、Office Web Apps サーバー ファームでのすべてのサーバーの正常性状態を表示します。

\------------------ 例 2 ---------------------

    Repair-OfficeWebAppsFarm

この例では、Office Web Apps サーバー ファームからすべての正常でないサーバーを削除します。

## 関連項目


[New-OfficeWebAppsFarm](new-officewebappsfarm.md)  
[Set-OfficeWebAppsFarm](set-officewebappsfarm.md)  
[Get-OfficeWebAppsFarm](get-officewebappsfarm.md)  


[Office Web Apps サーバーのコンテンツ ロードマップ](content-roadmap-for-office-web-apps-server.md)  
[インフラストラクチャの展開: Office Web Apps サーバー](deploy-the-infrastructure-office-web-apps-server.md)  
  

[](deploy-the-infrastructure-office-web-apps-server.md)

