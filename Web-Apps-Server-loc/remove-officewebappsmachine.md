---
title: Remove-OfficeWebAppsMachine
TOCTitle: Remove-OfficeWebAppsMachine
ms:assetid: 5ad806f2-67c6-41ed-a708-69db800f492a
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/JJ219440(v=office.15)
ms:contentKeyID: 48796428
ms.date: 12/22/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# Remove-OfficeWebAppsMachine

 

_**適用先:**Office Web Apps Server_

_**トピックの最終更新日:**2015-03-09_

Office Web Apps サーバー ファームから現在のサーバーを削除します。

## 構文

    Remove-OfficeWebAppsMachine [-Confirm [<SwitchParameter>]] [-WhatIf [<SwitchParameter>]]

## 解説

**Remove-OfficeWebAppsMachine** コマンドレットは Office Web Apps サーバー ファームから現在のサーバーを削除します。この過程の一部として、コマンドレットは Web アプリケーションを削除して、Office Web Apps サーバー に関連するサービスを停止します。削除するサーバーから **Remove-OfficeWebAppsMachine** コマンドレットを実行できない場合は、Office Web Apps ファーム内のその他のサーバーから **Repair-OfficeWebAppsFarm** コマンドレットを使用します。


> [!NOTE]
> ローカル サーバーが Office Web Apps サーバー ファーム内のマスター サーバーとして割り当てられている場合は、ファームから削除できません。削除するには、<STRONG>Set-OfficeWebAppsMachine</STRONG> コマンドレットで、異なるサーバーをマスターとして指定するか、ファームからその他のすべてのサーバーを削除する必要があります。



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

    Remove-OfficeWebAppsMachine

この例では、Office Web Apps サーバー ファームから現在のサーバーを削除します。

## 関連項目


[Get-OfficeWebAppsMachine](get-officewebappsmachine.md)  
[New-OfficeWebAppsMachine](new-officewebappsmachine.md)  
[Set-OfficeWebAppsMachine](set-officewebappsmachine.md)  
[Repair-OfficeWebAppsFarm](repair-officewebappsfarm.md)  


[Office Web Apps サーバーのコンテンツ ロードマップ](content-roadmap-for-office-web-apps-server.md)  
[インフラストラクチャの展開: Office Web Apps サーバー](deploy-the-infrastructure-office-web-apps-server.md)  
  

[](deploy-the-infrastructure-office-web-apps-server.md)

