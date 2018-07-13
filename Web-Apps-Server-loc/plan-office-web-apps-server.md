---
title: Office Web Apps サーバーの計画
TOCTitle: Office Web Apps サーバーの計画
ms:assetid: 2e147f11-6f47-46bc-90bf-b2f179958d11
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/JJ219435(v=office.15)
ms:contentKeyID: 48796419
ms.date: 12/18/2017
mtps_version: v=office.15
ms.translationtype: HT
---

# Office Web Apps サーバーの計画

 

_**適用先:** Office Web Apps Server_

_**トピックの最終更新日:** 2017-10-10_

**概要:** HTTPS、証明書、仮想化、負荷分散、トポロジ、セキュリティなど、Office Web Apps Serverの要件と前提条件について説明します。

**対象ユーザー:** IT 担当者

Office Web Apps サーバー は、Office アプリケーションのブラウザー ベースのバージョンを社内環境に提供することにより、ユーザーの柔軟性を向上させ、グループ作業の機会を増やします。この記事では、Office Web Apps サーバー を組織にインストールするために必要な要件と手順について説明します。

SharePoint 2013 および Lync Server 2013 などのすべてのホストが Office Web Apps サーバー と通信できるように慎重に計画することが重要です。ホストの構成に関する詳細なガイダンスについては、以下のリソースを参照してください。

  - [Office Web Apps の計画 (SharePoint 2013 と組み合わせて使用)](plan-office-web-apps-used-with-sharepoint-2013.md)

  - [Lync Server 2013 と Office Web Apps サーバーの統合の構成](https://go.microsoft.com/fwlink/p/?linkid=256902)


> [!NOTE]
> SharePoint 2010 製品 は Office Web Apps サーバー のホストになることはできません。Office Web Apps サーバー は SharePoint Foundation 2010 または SharePoint Server 2010 でサポートされていません。Office Web Apps サーバー も Exchange Server 2013 でサポートされていません。



この記事の内容

  - Office Web Apps サーバーのソフトウェア、ハードウェア、および構成要件

  - Office Web Apps サーバーの仮想化のサポート

  - Office Web Apps サーバーのファイアウォール要件

  - Office Web Apps サーバーのロード バランサー要件

  - Office Web Apps サーバーの DNS 要件

  - Office Web Apps サーバーの言語パックの計画

  - Office Web Apps サーバーのトポロジ計画

  - Office Web Apps サーバーのセキュリティ計画

  - Office Web Apps サーバーを使用したオンライン ビューアーの計画

  - Office Web Apps サーバーの更新プログラムの計画

## Office Web Apps サーバーのソフトウェア、ハードウェア、および構成要件

Office Web Apps サーバー は、単一 サーバーの Office Web Apps サーバー ファームとして、または、複数サーバーの負荷分散 Office Web Apps サーバー ファームとしてインストールすることができます。物理サーバーまたは仮想マシン インスタンスを使用できますが、他のサーバー アプリケーション (SharePoint 2013 や SQL Server など) を Office Web Apps サーバー と同じサーバーにインストールすることはできません。

実際のユーザー データを含む環境では、常に、証明書を取得する必要がある HTTPS を使用することをお勧めします。ファームで複数のサーバーを使用する場合は、ハードウェアまたはソフトウェアの負荷分散ソリューションを構成する必要があります。このようなシナリオの詳細について以降のセクションで説明します。

## Office Web Apps サーバーのハードウェア要件

Office Web Apps サーバーの最小ハードウェア要件は SharePoint Server 2013と同じです。SharePoint 2013の総合的な要件は、「[ハードウェア要件 ? Web サーバー、アプリケーション サーバー、および単一サーバー インストール](https://technet.microsoft.com/ja-jp/4d88c402-24f2-449b-86a6-6e7afcfec0cd\(office.15\)#hwforwebserver)」で確認できます。スケーラビリティに関する追加のガイダンスは、この記事が将来更新されるときに提供されます。

## Office Web Apps サーバーでサポートされるオペレーティング システム

Office Web Apps サーバー は以下のオペレーティング システムで実行できます。

  - [Windows Server 2008 R2 x64 Edition 用更新プログラム](https://go.microsoft.com/fwlink/p/?linkid=236954)がインストールされた Windows Server 2008 R2 Service Pack 1 (SP1) Standard、Enterprise、Datacenter の 64 ビット版

  - Windows Server 2012 Standard または Datacenter の 64 ビット版

  - Windows Server 2012 R2 の 64 ビット版。このオペレーティング システムを使用するには、Office Web Apps サーバー Service Pack 1 (SP1) を使用する必要があります。

## Office Web Apps サーバーのドメイン要件

Office Web Apps サーバー ファーム内のすべてのサーバーを 1 つのドメインに含める必要があります。同じドメイン内 (推奨) か、同じフォレスト内のドメイン内に配置できます。ただし、Office Web Apps サーバー をドメイン コントローラー上にインストールしても機能しない可能性があります。

## Office Web Apps サーバーに必要なサーバーの役割、サービス、および他のソフトウェア

まず、Office Web Apps サーバー の展開時にやってはいけないことがいくつかあります。

  - **Office Web Apps サーバー を実行しているサーバーに、他のサーバー アプリケーションをインストールしないでください**。これには、Exchange Server、SharePoint Server、Lync Server、SQL Server が含まれます。ハードウェアの台数が不足している場合は、いずれかのサーバーの仮想マシン インスタンスで Office Web Apps サーバー を実行することを検討してください。

  - **ポート 80、443、または 809 の Web サーバー (IIS) の役割を利用するサービスまたは役割をインストールしないでください。** これは、Office Web Apps サーバー によって、これらのポートの Web アプリケーションが定期的に削除されるためです。

  - **どのバージョンの Office もインストールしないでください**。すでにインストールされている場合は、Office Web Apps サーバー をインストールする前にアンインストールする必要があります。

  - **Office Web Apps サーバー をドメイン コントローラーにインストールしないでください**。Active Directory ドメイン サービス (AD DS) を実行しているサーバーでは動作しない可能性があります。

この時点でやるべきことはインストールです。詳細は次の表を参照してください。


> [!IMPORTANT]
> Office Web Apps サーバー は、<A href="https://go.microsoft.com/fwlink/p/?linkid=256561">Volume Licensing Service Center (VLSC)</A> からのみダウンロードが可能です。Office Web Apps サーバー をダウンロードするには、Office Professional Plus 2013、Office Standard 2013、Office for Mac 2011 のためのボリューム ライセンス条項に従ったライセンスが必要です。ダウンロード ファイルは、VLSC ポータルのそれらの Office 製品の下にあります。



### Office Web Apps サーバーで必要なダウンロード、サーバーの役割および機能

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>ダウンロード、サーバーの役割、または機能</th>
<th>Windows Server 2008 R2 上でインストールする場合</th>
<th>Windows Server 2012 上でインストールする場合</th>
<th>Windows Server 2012 R2 上でインストールする場合</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>ダウンロード:</strong> Office Web Apps サーバー</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=256561">Office Web Apps Server</a></p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=256561">Office Web Apps Server</a></p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=256561">Office Web Apps サーバー</a></p></td>
</tr>
<tr class="even">
<td><p><strong>ダウンロード:</strong> Office Web Apps サーバー SP1</p></td>
<td><p>推奨</p></td>
<td><p>推奨</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=510097">Office Web Apps サーバー SP1</a></p></td>
</tr>
<tr class="odd">
<td><p><strong>ダウンロード:</strong> 適切なバージョンの .NET Framework</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=256560">.NET Framework 4.5</a></p></td>
<td><p>.NET framework 4.5 が既にインストールされている</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=510096">.NET Framework 4.5.2</a></p></td>
</tr>
<tr class="even">
<td><p><strong>ダウンロード:</strong> Windows Server 2008 R2 x64 Edition 用更新プログラム</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=236954">Windows Server 2008 R2 x64 Edition 用更新プログラム</a></p></td>
<td><p>該当なし</p></td>
<td><p>該当なし</p></td>
</tr>
<tr class="odd">
<td><p><strong>ダウンロード:</strong> Windows PowerShell 3.0</p></td>
<td><p><a href="https://go.microsoft.com/fwlink/p/?linkid=244693">Windows PowerShell 3.0</a></p></td>
<td><p>インストール済み</p></td>
<td><p>インストール済み</p></td>
</tr>
<tr class="even">
<td><p><strong>サーバーの役割:</strong> Web サーバー (IIS)</p></td>
<td><p>ここで、<strong>Web サーバー (IIS)</strong> のサーバーの役割に必要な最小役割サービスを示します。</p>
<p><strong>一般的な HTTP の機能</strong></p>
<ul>
<li><p>静的コンテンツ</p></li>
<li><p>既定のドキュメント</p></li>
</ul>
<p><strong>アプリケーション開発</strong></p>
<ul>
<li><p>ASP.NET</p></li>
<li><p>.NET 拡張機能</p></li>
<li><p>ISAPI 拡張機能</p></li>
<li><p>ISAPI フィルター</p></li>
<li><p>サーバー側インクルード</p></li>
</ul>
<p><strong>セキュリティ</strong></p>
<ul>
<li><p>Windows 認証</p></li>
<li><p>要求のフィルタリング</p></li>
</ul>
<p><strong>管理ツール</strong></p>
<ul>
<li><p>IIS 管理コンソール</p></li>
</ul>
<p>以下のオプションは推奨項目です。必須ではありません。</p>
<p><strong>パフォーマンス</strong></p>
<ul>
<li><p>静的コンテンツの圧縮</p></li>
<li><p>動的コンテンツの圧縮</p></li>
</ul></td>
<td><p>ここで、<strong>Web サーバー (IIS)</strong> のサーバーの役割に必要な最小役割サービスを示します。</p>
<p><strong>管理ツール</strong></p>
<ul>
<li><p>IIS 管理コンソール</p></li>
</ul>
<p><strong>Web サーバー</strong></p>
<ul>
<li><p>HTTP 共通機能</p></li>
<li><p>既定のドキュメント</p></li>
<li><p>静的コンテンツ</p></li>
</ul>
<p><strong>セキュリティ</strong></p>
<ul>
<li><p>要求のフィルタリング</p></li>
<li><p>Windows 認証</p></li>
</ul>
<p><strong>アプリケーション開発</strong></p>
<ul>
<li><p>.NET 拡張機能 4.5</p></li>
<li><p>ASP.NET 4.5</p></li>
<li><p>ISAPI 拡張機能</p></li>
<li><p>ISAPI フィルター</p></li>
<li><p>サーバー側インクルード</p></li>
</ul>
<p>以下のオプションは推奨項目です。必須ではありません。</p>
<p><strong>パフォーマンス</strong></p>
<ul>
<li><p>静的コンテンツの圧縮</p></li>
<li><p>動的コンテンツの圧縮</p></li>
</ul></td>
<td><p>ここで、<strong>Web サーバー (IIS)</strong> のサーバーの役割に必要な最小役割サービスを示します。</p>
<p><strong>管理ツール</strong></p>
<ul>
<li><p>IIS 管理コンソール</p></li>
</ul>
<p><strong>Web サーバー</strong></p>
<ul>
<li><p>HTTP 共通機能</p></li>
<li><p>既定のドキュメント</p></li>
<li><p>静的コンテンツ</p></li>
</ul>
<p><strong>セキュリティ</strong></p>
<ul>
<li><p>要求のフィルタリング</p></li>
<li><p>Windows 認証</p></li>
</ul>
<p><strong>アプリケーション開発</strong></p>
<ul>
<li><p>.NET 拡張機能 4.5</p></li>
<li><p>ASP.NET 4.5</p></li>
<li><p>ISAPI 拡張機能</p></li>
<li><p>ISAPI フィルター</p></li>
<li><p>サーバー側インクルード</p></li>
</ul>
<p>以下のオプションは推奨項目です。必須ではありません。</p>
<p><strong>パフォーマンス</strong></p>
<ul>
<li><p>静的コンテンツの圧縮</p></li>
<li><p>動的コンテンツの圧縮</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p><strong>機能:</strong> インクと手書きサービス</p></td>
<td><p><strong>インクと手書きサービス</strong></p>
<ul>
<li><p>インク サポート</p></li>
</ul></td>
<td><p><strong>インクと手書きサービス</strong></p>
<ul>
<li><p>インク サポートは必要ありません。</p></li>
</ul></td>
<td><p><strong>インクと手書きサービス</strong></p>
<ul>
<li><p>インク サポートは必要ありません。</p></li>
</ul></td>
</tr>
</tbody>
</table>


## Office Web Apps サーバーの仮想化のサポート

Office Web Apps サーバー が完全にサポートされるのは、Windows Server Hyper-V テクノロジを使用して展開した場合です。Office Web Apps サーバー を仮想化する予定がある場合は、以下のガイドラインに従います。

  - Office Web Apps サーバー を専用の仮想マシン インスタンスにインストールします。このインスタンスには、SharePoint 2013 などの他のサーバー アプリケーションをインストールしないでください。

  - 必要であれば、SharePoint 2013 を実行しているサーバーによってホストされた仮想マシン インスタンスに Office Web Apps サーバー をインストールできます。

  - 複数サーバーの Office Web Apps サーバー ファームの場合は、各インスタンスを別々の仮想マシン ホストに配置して、いずれかのホストで障害が発生しても Office Web Apps サーバー ファームを使用できるようにする必要があります。

## Office Web Apps サーバーのファイアウォール要件

Web ブラウザー、Office Web Apps サーバー を実行しているサーバー、SharePoint 2013 を実行しているサーバー間の通信がファイアウォールによってブロックされるという問題が発生する可能性があります。サーバーがネットワークのさまざまな部分に存在する場合は、このような問題がより複雑になります。

Office Web Apps サーバー を実行しているサーバーまたはロード バランサー上の以下のポートがファイアウォールによってブロックされないようにしてください。

  - ポート 443 (HTTPS トラフィック用)

  - ポート 80 (HTTP トラフィック用)

  - ポート 809 Office Web Apps サーバー を実行するサーバー間のプライベート トラフィック用) (複数サーバー ファームを設定する場合)

## Office Web Apps サーバーのロード バランサー要件

複数のサーバーで Office Web Apps サーバー を実行している場合は、負荷分散ソリューションをお勧めします。ほぼすべての負荷分散ソリューションを使用できます。これには、Web サーバー (IIS) の役割 (アプリケーション要求ルーティング処理 (ARR) を行う) を実行しているサーバーが含まれます。実際、Office Web Apps サーバー を実行しているサーバーの 1 つで ARR を実行できます。負荷分散ソリューションがない場合は、IIS と ARR の使用方法について以下のリソースを参照してください。

  - [アプリケーション要求ルーティング処理のインストール](https://go.microsoft.com/fwlink/?linkid=236955)

  - [アプリケーション要求ルーティング処理のヘルプ](https://go.microsoft.com/fwlink/?linkid=236956)

可能であれば、以下の機能がサポートされている負荷分散ソリューションを探してください。

  - Layer 7 ルーティング

  - クライアント アフィニティまたはフロントエンド アフィニティの有効化

  - SSL オフロードの有効化

ロード バランサーを使用する場合は、「HTTPS を使用した Office Web Apps サーバーの通信の保護」で説明されているように、証明書をロード バランサーにインストールする必要があります。

## Office Web Apps サーバーの DNS 要件

HTTPS と負荷分散を使用する環境では、DNS を更新して、証明書の完全修飾ドメイン名 (FQDN) が Office Web Apps サーバー を実行しているサーバーの IP アドレス、または、Office Web Apps サーバー ファームのロード バランサーに割り当てられた IP アドレスに解決されるようにする必要があります。

## Office Web Apps サーバーの言語パックの計画

Office Web Apps サーバー 2013 言語パックを使用すると、SharePoint 2013 ドキュメント ライブラリ、Outlook Web App (添付ファイルのプレビューとして)、Lync 2013 (PowerPoint ブロードキャストとして) において、Web ベースの Office ファイルを複数の言語で表示できます。ただし、これはホストで構成されている言語に依存します。複数の言語のホストからの Web ベースの Office ファイルを表示するには、以下の条件が満たされる必要があります。

  - ホスト (SharePoint Server 2013、Lync Server 2013 など) が、アプリケーションを追加の言語で実行するように構成されていること。ホストでの言語パックのインストールと構成のプロセスは、Office Web Apps サーバー ファームでの言語パックのインストールとは無関係です。

  - Office Web Apps サーバー ファームのすべてのサーバーに言語がインストールされていて、使用可能であること。

[Office Web Apps サーバーの言語パックは](https://go.microsoft.com/fwlink/p/?linkid=263945) からダウンロードしてください。

## Office Web Apps サーバーのトポロジ計画

最低でも、Office Web Apps サーバー トポロジには、Office Web Apps サーバー を実行している 1 つの物理または仮想マシンと 1 つ以上のホスト (Lync Server 2013 または SharePoint 2013 を実行しているサーバーなど) が含まれます。もちろん、ホストのいずれかに接続して Office Web Apps 機能を使用するためのクライアント PC またはデバイスが必要です。この最小トポロジから、組織のニーズに合わせて、新しいホストや新しいサーバーを Office Web Apps サーバー ファームに追加できます。

Office Web Apps サーバー トポロジがより複雑になった場合に留意すべき推奨事項の一覧を以下に示します。

  - **冗長性を計画する。** 仮想マシン インスタンスを使用する場合は、それらが別々の仮想マシン ホストに配置され、冗長性が確保されていることを確認します。ホスト上の他のインスタンスがサーバー アプリケーションを実行している場合は、Office Web Apps サーバー と同じインスタンス上で他のサーバー アプリケーションを実行しないようにするだけで十分です。

  - **1 つのデータ センターを使用する。** Office Web Apps サーバー ファーム内のサーバーは、同じデータ センター内に配置する必要があります。地理的に離れた場所に分散させないでください。Office Web Apps サーバー ファームが存在するネットワークを分離しなければならないようなセキュリティ要件がないかぎり、1 つのファームだけで十分です。

  - **ホストに近いほど良い。** Office Web Apps サーバー ファームは、そのホストと同じデータ センター内に配置する必要はありませんが、編集の頻度が高い場合は、Office Web Apps サーバー ファームをできるだけホストのそばに配置することをお勧めします。このことは、Office Web Apps を主に Office ファイルの表示に使用している組織にとってはそれほど重要ではありません。

  - **接続を計画する。** Office Web Apps サーバー ファーム内のすべてのサーバーだけを相互に接続します。より広いネットワークに接続するには、リバース プロキシ ロード バランサー ファイアウォール経由で接続します。

  - **HTTP または HTTPS 要求用にファイアウォールを構成する。** ファイアウォールが Office Web Apps サーバー を実行しているサーバーでホストへの HTTP または HTTPS 要求を初期化できるように構成されていることを確認します。

  - **着信と発信を計画する。** インターネットに接続する展開では、すべての発信を NAT デバイス経由でルーティングします。マルチサーバー ファームでは、すべての着信をロード バランサーを使用して処理します。


  - **Office Web Apps サーバー ファーム内のすべてのサーバーが 1 つのドメインに参加しており、同じ組織単位 (OU) の一部になっていることを確認する。**この OU に含まれない他のサーバーがファームに参加することを防ぐには、[New-OfficeWebAppsFarm](https://docs.microsoft.com/en-us/powershell/module/officewebapps/new-officewebappsfarm?view=officewebapps-ps) コマンドレットの **FarmOU** パラメーターを使用します。


  - **すべての着信要求にハイパーテキスト転送プロトコル セキュア (HTTPS) を使用する。**

  - **ネットワークに IPsec が展開されている場合は、それをサーバー間のトラフィックの暗号化に使用する。**

  - **インターネットを使用する Office 機能を計画する。** クリップ アートや翻訳サービスなどの機能が必要であり、ファーム内のサーバーがインターネットへの要求を開始できない場合、Office Web Apps サーバー ファーム用のプロキシ サーバーを構成する必要があります。これにより、外部サイトへの HTTP 要求が許可されます。

## Office Web Apps サーバーのセキュリティ計画

以下に、Office Web Apps サーバー のセキュリティ ガイダンスを示します。

## HTTPS を使用した Office Web Apps サーバーの通信の保護

Office Web Apps サーバー は、SharePoint 2013 および Lync Server 2013 と HTTPS プロトコルを使用して通信できます。運用環境では HTTPS の使用を強くお勧めします。Office Web Apps サーバー を実行するサーバー (単一サーバーを使用する場合)、またはロード バランサー (Office Web Apps サーバー を実行する複数サーバーを使用する場合) に割り当てられる Internet Server 証明書をインストールする必要があります。

ユーザー データを含まないテスト環境では、SharePoint 2013 に HTTP を使用することができ、証明書の要件は省略できます。Lync Server 2013 では HTTPS しかサポートされません。

Office Web Apps サーバー が使用する証明書は、次の要件を満たす必要があります。

  - 証明書は、信頼できる証明機関から発行され、Office Web Apps サーバー ファームの完全修飾ドメイン名 (FQDN) を SAN (サブジェクトの別名) フィールドに含んでいる必要があります (FQDN が SAN に含まれない場合、その証明書を使用しようとすると、ブラウザーによってセキュリティ警告が表示されるか、応答が処理されません)。

  - 証明書は、エクスポート可能な秘密キーを含む必要があります。単一サーバーのファームでは、インターネット インフォメーション サービス (IIS) マネージャー スナップインを使用して証明書をインポートするとき、既定ではこのオプションが選択されています。

  - フレンドリ名フィールドは、信頼できるルート証明書機関のストア内で一意であることが必要です。複数の証明書でフレンドリ名フィールドが共有されている場合、New-OfficeWebAppsFarm コマンドレットは使用する証明書を特定できず、ファーム作成が失敗します。

  - Office Web Apps サーバー では特定の証明書のプロパティや拡張子は必要ありません。たとえば、クライアントの拡張キー使用法 (EKU) 拡張子やサーバーの EKU 拡張子は必要ありません。

  - Windows Server 2012 または Windows Server 2012 R2 では、Windows Communication Foundation (WCF) HTTP アクティベーション機能をインストールする必要があります。

証明書は次のとおりインポートする必要があります。

  - **単一サーバーのファーム**Office Web Apps サーバー を実行しているサーバーに直接証明書をインポートする必要があります。証明書を手動でバインドしないでください。後から実行する New-OfficeWebAppsFarm コマンドレットによってこの処理が行われます。手動でバインドした証明書は、サーバーが再起動するたびに削除されます。

  - **負荷分散されたファーム**   SSL をオフロードしている場合、証明書はハードウェア ロード バランサーにインポートする必要があります。SSL をオフロードしていない場合は、Office Web Apps サーバー ファーム内の各サーバーに証明書をインストールする必要があります。


> [!NOTE]
> 重要でないテスト環境以外では、自己署名証明書を使用しないでください。



証明書の詳細については、「[SSL 証明書の取得](https://go.microsoft.com/fwlink/p/?linkid=269700)」を参照してください。

## ハードウェア ロード バランサーに SSL オフロードを使用する

新しい Office Web Apps サーバー ファームをセットアップすると、SSL オフロードが既定でオフに設定されます。ハードウェア ロード バランサーを使用している場合は、ファーム内の各 Office Web Apps サーバー が HTTP を使用してロード バランサーと通信できるように SSL オフロードをオンに設定することをお勧めします。そうすれば、次のようなメリットも得られます。

  - 証明書管理の簡素化

  - 改良型ソフト アフィニティ

  - 改良型パフォーマンス

HTTP を使用している場合は、ロード バランサーから Office Web Apps サーバー を実行しているサーバーへのトラフィックが暗号化されないため、ネットワーク自体が安全であることを確認する必要があることに注意してください。プライベート サブネットの使用により、トラフィックを保護することができます。

## Office Web Apps サーバーファームに参加できるサーバーを OU メンバーシップに基づいて制限する

対象サーバーの組織単位を作成してから、ファームを作成するときに FarmOU パラメーターを指定することで、無許可のサーバーが Office Web Apps サーバー ファームに参加するのを防ぐことができます。FarmOU パラメーターの詳細については、「[New-OfficeWebAppsFarm](https://docs.microsoft.com/en-us/powershell/module/officewebapps/new-officewebappsfarm?view=officewebapps-ps)」を参照してください。

## 許可リストを使用して Office Web Apps サーバーのホスト アクセスを制限する

許可リストは、不要なホストが Office Web Apps サーバー ファームに接続して、同意なしにファームを使用してファイルを処理するのを防ぐセキュリティ機能です。承認されたホストを含むドメインを許可リストに追加することで、Office Web Apps サーバー がファイル処理要求 (ファイルの取得、メタデータの取得、ファイルの変更など) を許可するホストを制限できます。

Office Web Apps サーバー ファームを作成した後で許可リストにドメインを追加できます。許可リストにドメインを追加する方法については、「[New-OfficeWebAppsHost](https://docs.microsoft.com/en-us/powershell/module/officewebapps/new-officewebappshost?view=officewebapps-ps)」を参照してください。


> [!IMPORTANT]
> ドメインを許可リストに追加しないと、Office Web Apps サーバー はすべてのドメイン内のホストにファイル要求を許可します。Office Web Apps サーバー ファームがインターネットからアクセスできる場合には、このリストを空にしないでください。空にしておくと、誰でも Office Web Apps サーバー ファームを使用してコンテンツを表示および編集できます。



## Office Web Apps サーバーを使用したオンライン ビューアーの計画

既定では、Office Web Apps サーバー のインストール後にオンライン ビューアー機能が有効になります。組織でオンライン ビューアーの使用を計画している場合は、以下のガイドラインを確認してください。場合によっては、オンライン ビューアーの一部の機能を無効にすることをお勧めします。これらのガイドラインで参照するパラメーターは、Windows PowerShell のコマンドレット [New-OfficeWebAppsFarm](https://docs.microsoft.com/en-us/powershell/module/officewebapps/new-officewebappsfarm?view=officewebapps-ps) と [Set-OfficeWebAppsFarm](https://docs.microsoft.com/en-us/powershell/module/officewebapps/set-officewebappsfarm?view=officewebapps-ps) を使用して設定されます。

## オンライン ビューアーのセキュリティの考慮事項

オンライン ビューアーを使用して Web ブラウザーで表示するためのファイルは、認証が要らないようにする必要があります。つまり、ファイルを公開する必要があります。これは、オンライン ビューアーがファイルの取得時に認証を実行できないためです。オンライン ビューアーで使用する Office Web Apps サーバー ファームは、イントラネットとインターネットのどちらか一方のみ (両方ではなく) にアクセスできるようにすることを強くお勧めします。Office Web Apps サーバー は、イントラネット URL とインターネット URL の要求を区別しないためです。たとえば、インターネット上の誰かがイントラネット URL を要求できると、内部文書が表示された場合に情報漏れが発生する可能性があります。

同じ理由から、Office Web Apps サーバー をインターネットのみに接続するように設定した場合は、オンライン ビューアーの UNC サポートを無効にすることを強くお勧めします。UNC サポートを無効にするには、Windows PowerShell のコマンドレット [New-OfficeWebAppsFarm](https://docs.microsoft.com/en-us/powershell/module/officewebapps/new-officewebappsfarm?view=officewebapps-ps) (新規ファーム用) または [Set-OfficeWebAppsFarm](https://docs.microsoft.com/en-us/powershell/module/officewebapps/set-officewebappsfarm?view=officewebapps-ps) (既存ファーム用) を使用して OpenFromUncEnabled パラメーターを False に設定します。

追加のセキュリティ上の理由から、オンライン ビューアーでの表示は、10 MB 以下の Office ファイルに制限されます。

## オンライン ビューアーの構成オプション

Windows PowerShell の以下のパラメーターを [New-OfficeWebAppsFarm](https://docs.microsoft.com/en-us/powershell/module/officewebapps/new-officewebappsfarm?view=officewebapps-ps) (新規ファーム用) または [Set-OfficeWebAppsFarm](https://docs.microsoft.com/en-us/powershell/module/officewebapps/set-officewebappsfarm?view=officewebapps-ps) (既存ファーム用) で使用して、オンライン ビューアーを構成できます。

  - **OpenFromUrlEnabled**   オンライン ビューアーのオンとオフを切り替えます。このパラメーターは、URL および UNC パスを持つファイルに関してオンライン ビューアーを制御します。新しい Office Web Apps サーバー ファームを作成したとき、既定ではこのパラメーターは False (無効) に設定されています。

  - **OpenFromUncEnabled**   オンライン ビューアーがオンになっているとき (OpenFromUrlEnabled を使用して True に設定)、このパラメーターは、オンライン ビューアーで UNC パス内のファイルを表示できるかどうかを切り替えます。既定では、このパラメーターが True に設定されますが、OpenFromUrlEnabled も True に設定されていることを確認してから、UNC パスからファイルを開けるようにします。前述したように、Office Web Apps サーバー がインターネットに接続するように設定した場合は、このパラメーターを False に設定することをお勧めします。

  - **OpenFromUrlThrottlingEnabled**   一定期間に所定のサーバーから送られてくる "URL から開く" 要求の回数を調整します。既定の調整値 (構成不可) では、Office Web Apps サーバー ファームがコンテンツをオンライン ビューアーで表示するための要求を多数送信して 1 つのサーバーに負荷がかかりすぎないようにします。

## Office Web Apps サーバーの更新プログラムの計画

Office Web Apps サーバー を展開する前に、組織の Office Web Apps サーバー ファームへのソフトウェア更新プログラムを管理する方法を決定する必要があります。ソフトウェア更新プログラムは、サーバーのセキュリティ、パフォーマンス、および信頼性の向上に役立ちますが、更新プログラムを不適切にインストールすると、Office Web Apps サーバー で問題が発生する場合があります。

Office Web Apps サーバー では、Microsoft 自動更新プロセスを使用して Office Web Apps サーバー の更新プログラムを適用することはできません。Office Web Apps サーバー への更新プログラムは、「[Office Web Apps サーバーへのソフトウェアの更新プログラムの適用](apply-software-updates-to-office-web-apps-server.md)」で説明されているとおり、特定の方法で適用する必要があります。Office Web Apps サーバー の更新プログラムが自動的に適用されると、ユーザーが Office Web Apps のドキュメントの表示や編集ができなくなる場合があります。その場合は、Office Web Apps サーバー ファームの再構築が必要になります。

更新プログラムは、Windows Server Update Services (WSUS) か、WSUS を使用する System Center 構成マネージャー を使用して管理することをお勧めします。WSUS を使用すると、Office Web Apps サーバー ファーム内の各サーバーに Microsoft Update 経由でリリースされる更新プログラムの配布を完全に管理できます。WSUS の使用により、サーバー ファームに自動的に適用できる更新プログラムと、Office Web Apps サーバー の更新プログラムのように手動の適用が必要な更新プログラムを指定できます。WSUS の詳細については、「[Windows Server Update Services](https://go.microsoft.com/fwlink/p/?linkid=294822)」を参照してください。

WSUS または System Center 構成マネージャー を使用しない場合は、Office Web Apps サーバー ファーム内の各サーバーで Microsoft 自動更新を \[**自動的にダウンロードするが、インストールをユーザーに通知する**\] に設定します。Office Web Apps サーバー の更新プログラムの通知を受けたら、「[Office Web Apps サーバーへのソフトウェアの更新プログラムの適用](apply-software-updates-to-office-web-apps-server.md)」の手順を実行します。Windows の更新プログラムを適用してサーバーのセキュリティを保つには、更新プログラムが入手可能になったことを通知されたときに、Windows の更新プログラムを受け入れます。

## 関連項目


[Office Web Apps サーバーのコンテンツ ロードマップ](content-roadmap-for-office-web-apps-server.md)  
[Office Web Apps サーバーの概要](office-web-apps-server-overview.md)  
[Office Web Apps サーバーの展開](deploy-office-web-apps-server.md)  
[Office Web Apps サーバーへのソフトウェアの更新プログラムの適用](apply-software-updates-to-office-web-apps-server.md)  


[Office.com (デスクトップまたはモバイル デバイス上の Office Web Apps に関するヘルプ)](https://go.microsoft.com/fwlink/p/?linkid=266657)  
  

[](apply-software-updates-to-office-web-apps-server.md)

