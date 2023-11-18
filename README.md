# play-with-ecs-fargate

🫃🫃🫃 ECS Fargateを使ってみる！  

![成果物](./docs/images/fruit.gif)  

※ 「🫃 (PREGNANT MAN / 妊娠中の男性)」こんなジェンダーレスな絵文字があるんだ！笑  

## デプロイ方法

`v-*`という形式のタグをプッシュすると、GitHub Actionsによりプロビジョニングが実行されます。  
以下のシークレットを設定してください。  

| シークレット名 | 説明 |
| --- | --- |
| AWS_ACCESS_KEY_ID | AWSのアクセスキーID |
| AWS_SECRET_ACCESS_KEY | AWSのシークレットアクセスキー |
| AWS_REGION | AWSのリージョン |
| PROJECT_NAME | プロジェクト名(CloudFormationのスタック名) |

また、手動でデプロイする場合は以下のコマンドを実行してください。  

```shell
aws cloudformation deploy \
  --stack-name <プロジェクト名> \
  --template ./template.yml \
  --capabilities CAPABILITY_NAMED_IAM \
  --no-fail-on-empty-changeset \
  --no-cli-pager
```

## 補足

ECS Fargateの大枠を理解するためのもので、セキュリティ・パフォーマンス・コストなどは考慮していません。  
単純にNginxイメージをECS Fargateで動かしてみるだけのものです。  

また、通常はNATやALBなどのリソースと併用することが多いですが、今回は省略しています。  
必要最低限のリソースで構成しています。  
