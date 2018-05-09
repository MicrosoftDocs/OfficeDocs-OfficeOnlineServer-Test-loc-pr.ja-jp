---
title: Get-OfficeWebAppsFarm
TOCTitle: Get-OfficeWebAppsFarm
ms:assetid: 1f0704e1-a41d-40e6-a31b-08b1926ce811
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/JJ219434(v=office.15)
ms:contentKeyID: 48796418
ms.date: 12/18/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# Get-OfficeWebAppsFarm

 

_**適用先:**Office Web Apps Server_

_**トピックの最終更新日:**2013-12-18_

現在のサーバーがメンバーである OfficeWebAppsFarm オブジェクトの詳細を戻します。

## 構文

    Get-OfficeWebAppsFarm

## 詳細説明

**Get-OfficeWebAppsFarm** コマンドレットは、現在のサーバーがメンバーである OfficeWebAppsFarm オブジェクトの詳細を戻します。このオブジェクトは、Office ドキュメントの、Web ベースでの編集および表示を行うユニットとして機能するサーバーのグループを表します。**Get-OfficeWebAppsFarm** コマンドレットにはパラメーターはありません。

## パラメーター

## 入力値の型

## 戻り値の型

## 例

\------------------ 例 1 ---------------------

    Get-OfficeWebAppsFarm

この例は、OfficeWebAppsFarm オブジェクトの詳細を戻します。

\------------------ 例 2 ---------------------

    (Get-OfficeWebAppsFarm).Machines

この例は、Office Web Apps サーバー ファームのメンバーであるサーバーの詳細を戻します。これらの詳細には、各サーバーの正常性状態および役割が含まれます。

## 関連項目


[New-OfficeWebAppsFarm](new-officewebappsfarm.md)  
[Set-OfficeWebAppsFarm](set-officewebappsfarm.md)  
[Repair-OfficeWebAppsFarm](repair-officewebappsfarm.md)  


[Office Web Apps サーバーのコンテンツ ロードマップ](content-roadmap-for-office-web-apps-server.md)  
[インフラストラクチャの展開: Office Web Apps サーバー](deploy-the-infrastructure-office-web-apps-server.md)  
  

[](deploy-the-infrastructure-office-web-apps-server.md)

