# SentinelTeamsNotifyEnrichment
> このレポジトリは Microsoft Sentinel の Teams インシデント通知のサンプルテンプレートです。<p>

Microsoft Sentinel のインシデントトリガーを用いて、以下を実現します。
  - Microsoft Teams のチャネルにアダプティブカードを用いたインシデント情報のメッセージ作成
  - インシデント情報に付与されたコメントを Teams の返信として表示
  - インシデント情報に含まれた各種エンティティ情報を HTML 表形式で Teams の返信として表示
  - インシデント情報に含まれたエンティティのアカウント情報から、以下の条件については Microsoft Graph 経由で Azure AD の組織情報をルックアップして、ユーザー情報を Teams の返信として表示
    - エンティティ(Account) 内に ``aadUserId`` 情報が含まれているケース (ADconnect 等でオンプレADなどを接続している場合)
    - エンティティ(Account) 内に ``displayName`` 属性が自社ドメイン (microsoft.com) が含まれている場合 

<img width="746" alt="image" src="https://github.com/hisashin0728/SentinelTeamsNotifyEnrichment/assets/55295601/7b51f28b-df5f-4498-a2b7-9cd6fc89b31b">
<img width="700" alt="image" src="https://github.com/hisashin0728/SentinelTeamsNotifyEnrichment/assets/55295601/3cdfa5c0-d756-4ec0-b095-f703cfb51cad">


# 事前準備
本テンプレートは Microsoft Graph の RESTAPI を用いて Azure AD ユーザー情報取得を行います。
Microsoft Graph を利用するために Azure AD のアプリケーション登録を行い、サービスプリンシパルを取得して下さい。

  - テナント ID、クライアント ID の取得
![image](https://github.com/hisashin0728/SentinelTeamsNotifyEnrichment/assets/55295601/9083e294-dd7d-4dfc-93d2-758e51f635ee)

  - シークレット情報
![image](https://github.com/hisashin0728/SentinelTeamsNotifyEnrichment/assets/55295601/43f5c3be-0c7c-4144-8200-26c58b7021bf)

  - 「API のアクセス許可」の設定に対して、Microsoft Graph の ``User.Read``, ``User.Read.All`` を与えて下さい。
<img width="1105" alt="image" src="https://github.com/hisashin0728/SentinelTeamsNotifyEnrichment/assets/55295601/a0e5afb6-0763-4706-9cb1-bbcc66293470">


# Deploy to Azure
> Azure 環境への適用については、以下ボタンを押して下さい。<p>
[![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fhisashin0728%2FSentinelTeamsNotifyEnrichment%2Fmain%2Ftemplatev3.json)

# Requirement
> 以下必要要件になります。<p>

- Teams チャネル投稿が可能な Azure AD アカウント（ユーザー認証）

# Configuration
> デプロイ後、以下設定を行ってください。<p>

- 「API 接続」より、``MicrosoftTeams-(プレイブック名)`` を選択して、``承認する``より Teams が投稿するユーザー認証を行ってください。
<img width="956" alt="image" src="https://github.com/hisashin0728/SentinelTeamsNotifyEnrichment/assets/55295601/c7651c51-b799-4167-b783-98f67dcc3613"><BR>
- ロジック アプリ デザイナー画面より、Teams コネクタで接続する Teams/Channel ID を設定して下さい。
<img width="649" alt="image" src="https://github.com/hisashin0728/SentinelTeamsNotifyEnrichment/assets/55295601/83a113d6-00d1-495a-b32b-fa1c75482b26">
- Azure AD に lookup させる際に自社ドメインかどうかの判定として、UPN のチェックをかけています。
  以下箇所を自社の UPN ドメイン情報に変更して下さい。
<img width="872" alt="image" src="https://github.com/hisashin0728/SentinelTeamsNotifyEnrichment/assets/55295601/13cfb218-c67c-4904-ab39-5436cc5feddc">
