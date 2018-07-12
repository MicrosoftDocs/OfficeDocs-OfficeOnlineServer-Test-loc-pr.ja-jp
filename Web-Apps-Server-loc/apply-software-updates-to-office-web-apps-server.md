---
title: Office Web Apps サーバーへのソフトウェアの更新プログラムの適用
TOCTitle: Office Web Apps サーバーへのソフトウェアの更新プログラムの適用
ms:assetid: 5d15dbd9-374e-422a-a870-43270dd0a2db
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/JJ966220(v=office.15)
ms:contentKeyID: 56631545
ms.date: 12/18/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# Office Web Apps サーバーへのソフトウェアの更新プログラムの適用

 

_**適用先:** Office Web Apps Server_

_**トピックの最終更新日:** 2016-12-16_

**概要:** ソフトウェア更新プログラムを Office Web Apps サーバーファームへ適用する方法について説明します。

**対象ユーザー:** IT 担当者

Office Web Apps サーバー の新しいリリースの後、マイクロソフトでは、サーバーのセキュリティ、パフォーマンスおよび信頼性の向上に役立つ、一連のソフトウェア更新プログラムを作成しています。この記事では、Office Web Apps サーバー ファームの個々のサーバーにソフトウェア更新プログラムを適用する方法について説明します。


> [!IMPORTANT]
> この記事は、<A href="content-roadmap-for-office-web-apps-server.md">Office Web Apps サーバーのコンテンツ ロードマップ</A>に含まれています。このロードマップは、Office Web Apps サーバー の展開と管理に役立つ記事、ダウンロード、ビデオなどを参照する際の出発点として使用します。<BR><STRONG>使用しているデスクトップまたはモバイル デバイスの Office Web Apps に関する情報</STRONG>をお探しの場合は、<A href="http://go.microsoft.com/fwlink/p/?linkid=324961">Office.com</A> で「Office Web Apps」を検索してください。


> [!WARNING]
> 自動更新プロセスを使用した Office Web Apps サーバー 更新プログラムの適用は Office Web Apps サーバー ではサポートされていません。Office Web Apps サーバー への更新は、この記事で説明しているような、特別な方法で適用する必要があるからです。Office Web Apps サーバー の更新が自動的に適用されると、ユーザーは Office Web Apps のドキュメントを表示または編集できなくなることがあります。この場合、Office Web Apps サーバー ファームをビルドし直す必要があります。ファームをビルドし直すには、<A href="https://docs.microsoft.com/en-us/powershell/module/officewebapps/remove-officewebappsmachine?view=officewebapps-ps">Remove-OfficeWebAppsMachine</A> を使用して Office Web Apps サーバー をファームから削除し、プログラムの追加と削除を使用して Office Web Apps サーバー をアンインストールし、さらに「<A href="deploy-office-web-apps-server.md">Office Web Apps サーバーの展開</A>」で説明されている手順に従って Office Web Apps サーバー を再インストールします。再インストール後、この記事で説明している次の手順に従い、更新プログラムを適用します。<BR>「<A href="plan-office-web-apps-server.md">Office Web Apps サーバーの更新プログラムの計画</A>」のガイドラインを確認し、Office Web Apps サーバー ファームの更新プロセスを確立することが重要です。


## はじめに

Office Web Apps サーバー の使用可能な最新の更新プログラムのリストは、「[Microsoft Office の更新プログラム](http://blogs.technet.com/b/office_sustained_engineering/)」および「[Office、Office Servers、および関連製品の Update Center](http://technet.microsoft.com/ja-jp/office/ee748587.aspx)」で確認できます。

Office Web Apps サーバー 用にリリースされた更新プログラムは、インストールされた Office Web Apps サーバー およびすべての Office Web Apps サーバー 言語パックを更新します。Office Web Apps サーバー 言語パックごとの個別の更新プログラムはありません。

更新プロセスの一部として、Office Web Apps サーバー ファームを再作成する必要があります。Office Web Apps サーバー ファームの再作成を準備するには、Windows PowerShell コマンドレット **Get-OfficeWebAppFarm** を実行して現在の Office Web Apps サーバー ファーム プロパティを確認し、[New-OfficeWebAppsFarm](https://docs.microsoft.com/en-us/powershell/module/officewebapps/new-officewebappsfarm?view=officewebapps-ps) のパラメーターを確認します。**New-OfficeWebAppsFarm** に使用するパラメーターは、最初に Office Web Apps サーバー ファームを設定したときに使用したパラメーターと同じである必要があります。


> [!NOTE]
> この記事のタスクは、マウス、キーボード ショートカット、またはタッチを使用して完了できます。詳細については、以下の項目を参照してください。 
> <UL>
> <LI>
> <P><A href="http://go.microsoft.com/fwlink/p/?linkid=249150%26clcid=0x411">キーボード ショートカット</A></P>
> <LI>
> <P><A href="http://msdn.microsoft.com/ja-jp/library/windows/desktop/dd940543(v=vs.85).aspx">Windows タッチ ジェスチャの概要</A></P></LI></UL>



## 単一サーバーの Office Web Apps サーバーファームへのソフトウェア更新プログラムの適用

単一サーバーの Office Web Apps サーバー ファームにソフトウェア更新プログラムを適用するには、ファームから Office Web Apps サーバー を削除し、ソフトウェア更新プログラムを適用して、Office Web Apps サーバー ファームを再作成します。Office Web Apps サーバー ファームに 1 つのサーバーしかない場合、サーバーの更新中に Office Web Apps を使用できません。そのため、Office Web Apps サーバー はクリティカルではない時間や営業時間外に更新することを検討してください。

**単一サーバー ファームへのソフトウェア更新プログラムの適用**

1.  更新プログラムがまだ Office Web Apps サーバー にダウンロードされていない場合、適用する Office Web Apps サーバー の更新プログラムを [Microsoft ダウンロード センター](http://www.microsoft.com/ja-jp/download/default.aspx) からダウンロードします。

2.  ソフトウェア更新プログラムを適用する Office Web Apps サーバー で、管理者として Windows PowerShell プロンプトを開き、次のコマンドを実行します。
    
    ```PowerShell
        Remove-OfficeWebAppsMachine
    ```

3.  Install the Office Web Apps サーバー update on that server. If prompted, restart the server.

4.  管理者として Windows PowerShell プロンプトを開き、**New-OfficeWebAppsFarm** コマンドレットを実行して、Office Web Apps サーバー ファームを再作成します。**–InternalURL** に指定する URL は、Office Web Apps サーバー を実行するサーバーの名前です (**http://Contoso-WAC** など)。この場合、以前の Office Web Apps サーバー ファームに使用したものと同じ名前を使用します。最初に Office Web Apps サーバー ファームを作成したときに使用したものと同じ追加のパラメーターを使用します。たとえば、**–AllowHttp** パラメーターはファームが HTTP を使用するように構成し、**–EditingEnabled** パラメーターは Office Web Apps での編集を有効にします (SharePoint 2013と連動する場合)。 **–EditingEnabled** パラメーターは Lync Server 2013 または Exchange Server 2013 では使用されません。これらのホストでは編集がサポートされないからです。
    
    次に、http://Contoso-WAC という新しい Office Web Apps サーバー ファームを作成するコード例を示します。
    
    ```PowerShell
        New-OfficeWebAppsFarm -InternalURL "http://Contoso-WAC" -AllowHttp -EditingEnabled
    ```
    
    翻訳サービス、プロキシ サーバー、クリップ アート サポート、およびオンライン ビューアーを構成するその他のパラメーターについては、「[New-OfficeWebAppsFarm](https://docs.microsoft.com/en-us/powershell/module/officewebapps/new-officewebappsfarm?view=officewebapps-ps)」を参照してください。

## 複数の Office Web Apps サーバーファームへのソフトウェア更新プログラムの適用

複数の Office Web Apps サーバー ファームにソフトウェア更新プログラムを適用するには、まず、ロード バランサー プールおよびファームからいずれかのサーバーを削除し、ソフトウェア更新プログラムを適用し、更新した Office Web Apps サーバー ファームを作成します。次に Office Web Apps サーバー ファームの残りのサーバーを削除して更新し、それらを新しく更新したファームに追加します。現在のトラフィックをサポートするのに新しいファームに十分なサーバーがある場合、新しいファームへのトラフィックの負荷を分散します。この更新プロセスを使用して、ユーザーは混乱することなく、Office Web Apps 内のドキュメントを開き、編集できます。

**複数のサーバー ファームへのソフトウェア更新プログラムの適用**

1.  適用する Office Web Apps サーバー 更新プログラムを、[Microsoft ダウンロード センター](http://www.microsoft.com/ja-jp/download/default.aspx) から、Office Web Apps サーバー ファームが使用できるネットワークの場所にダウンロードします。

2.  ソフトウェア更新プログラムを適用する Office Web Apps サーバー を負荷分散プールから削除します。

3.  その Office Web Apps サーバー で、管理者として Windows PowerShell プロンプトを開き、次のコマンドを実行します。
    
    ```PowerShell
        Remove-OfficeWebAppsMachine
    ```

4.  Install the Office Web Apps サーバー update on that server. If prompted, restart the server.

5.  管理者として Windows PowerShell プロンプトを開き、コマンドレット **New-OfficeWebAppsFarm** を使用して、更新された Office Web Apps サーバー ファームを作成します。**–InternalURL** に指定する URL は、Office Web Apps サーバー を実行するサーバーの名前です (**http://Contoso-WAC**など)。この場合、既存の Office Web Apps サーバー ファームと同じ名前を使用します。最初に Office Web Apps サーバー ファームを作成したときに使用したのと同じ追加のパラメーターを使用します。たとえば、**–AllowHttp** パラメーターはファームが HTTP を使用するように構成し、**–EditingEnabled** パラメーターは Office Web Apps での編集を有効にします (SharePoint 2013と連動する場合)。**–EditingEnabled** パラメーターは Lync Server 2013 または Exchange Server 2013 では使用されません。これらのホストでは編集がサポートされないからです。
    
    次に、http://Contoso-WAC という新しい Office Web Apps サーバー ファームを作成するコード例を示します。
    
    ```PowerShell
        New-OfficeWebAppsFarm -InternalURL "http://Contoso-WAC" -AllowHttp -EditingEnabled
    ```
    
    翻訳サービス、プロキシ サーバー、クリップ アート サポート、およびオンライン ビューアーを構成するその他のパラメーターについては、「[New-OfficeWebAppsFarm](https://docs.microsoft.com/en-us/powershell/module/officewebapps/new-officewebappsfarm?view=officewebapps-ps)」を参照してください。

6.  Office Web Apps サーバー ファーム内のサーバーの数に応じて、新しいファームへのトラフィックの負荷を分散します。この手順は、もっと多くの更新されたサーバーをファームへ追加してから行うことができます。

7.  ファーム内の残りのサーバーごとに、これらの手順を実行します。
    
    1.  次の Office Web Apps サーバー をロード バランサー プールから削除します。
    
    2.  Office Web Apps サーバー の更新プログラムをサーバーにインストールします。サーバーの再起動を指示するプロンプトが表示されたら、サーバーを再起動します。
    
    3.  管理者として Windows PowerShell プロンプトを開き、次のコマンドを実行します。**–MachineToJoin** パラメーターは、現在のサーバーを既存の Office Web Apps サーバー ファームに追加します。この場合、サーバーを更新された Office Web Apps サーバー ファームに追加します。そのため、更新された Office Web Apps サーバー ファームのいずれかのサーバーのコンピューター名を使用します。
        
        ```PowerShell
            New-OfficeWebAppsMachine -MachineToJoin "server1.contoso.com"
        ```

## 関連項目


[Remove-OfficeWebAppsMachine](https://docs.microsoft.com/en-us/powershell/module/officewebapps/remove-officewebappsmachine?view=officewebapps-ps)  
[New-OfficeWebAppsMachine](https://docs.microsoft.com/en-us/powershell/module/officewebapps/new-officewebappsmachine?view=officewebapps-ps)  
[New-OfficeWebAppsFarm](https://docs.microsoft.com/en-us/powershell/module/officewebapps/new-officewebappsfarm?view=officewebapps-ps)  
[Get-OfficeWebAppsFarm](https://docs.microsoft.com/en-us/powershell/module/officewebapps/get-officewebappsfarm?view=officewebapps-ps)  


[Office Web Apps サーバーのコンテンツ ロードマップ](content-roadmap-for-office-web-apps-server.md)  
  

[](content-roadmap-for-office-web-apps-server.md)

