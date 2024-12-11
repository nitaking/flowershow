---
title: ECS
---
- [nodeアプリケーションをECSデプロイするまでの道のり docker / ECR / ECS設定](https://zenn.dev/nitaking/scraps/346356f59547a0)

---

## Terraform で ECS

y-ohgi先生による [Terraformで構築するAWS](https://y-ohgi.com/introduction-terraform/) によりTerraformの理解が進んだ。

### Terraform とは
Infrastructure as Codeのツール
構成を宣言的に記述することによってコードによるインフラ管理でき、属人化を防ぐ。
コード管理により、インフラのバージョン管理ができ、コードを見ることで現構成を把握することができる。
https://y-ohgi.com/introduction-terraform/first/about/

### Terraform実行環境
https://y-ohgi.com/introduction-terraform/first/preparation/

### Command

```bash
# terraform init

# terraform plan

# terraform apply
```

### ECS
https://y-ohgi.com/introduction-terraform/handson/ecs/

## Terraform 0.11 -> 0.14

https://www.terraform.io/upgrade-guides/0-13.html

```bash
# docker run v0.12
terraform init 
terraform 0.12upgrade 

# docker run v0.13
terraform init 
terraform 0.13upgrade 
terraform plan
# Error修正

# docker run v0.14
terraform plan
```

## Terraform directory structur
https://qiita.com/anfangd/items/1b84f69fa2a4f8a29fbc

https://dev.classmethod.jp/articles/directory-layout-bestpractice-in-terraform/

## 複数サブネットを一度に作る
https://zenn.dev/shonansurvivors/articles/5424c50f5fd13d

## Examples
https://github.com/duduribeiro/terraform_ecs_fargate_example

https://gitlab.com/jevans3/terraform-aws-multi-az-subnets/-/tree/master
