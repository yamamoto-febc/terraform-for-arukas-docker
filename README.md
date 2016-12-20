# Terraform for Arukas

[Terraform for Arukas](https://github.com/yamamoto-febc/terraform-provider-arukas)用Dockerイメージ

## `Dockerfile` links

- [`0.1.0`,`latest`(Dockerfile)](https://github.com/yamamoto-febc/terraform-for-arukas-docker/tree/master/0.1.0/)


## 使い方(docker-composeを使う場合)

#### 1) 以下コマンドで`docker-compose.yml`と環境変数設定ファイルのひな形をダウンロードします。

```bash
curl -L https://github.com/yamamoto-febc/terraform-for-arukas-docker/raw/master/docker-compose.yml > docker-compose.yml
curl -L https://github.com/yamamoto-febc/terraform-for-arukas-docker/raw/master/env-sample > .env
```

#### 2) (**オプション**)環境変数設定ファイルを編集します。

このファイルで環境変数を設定しておくとterraformコマンド実行時に
必要なオプションを省略できます。

```bash
vi .env
```

#### 3) docker-composeコマンドの実行

以下コマンドでterraformを起動します。
*.tfファイルはカレントディレクトリに配置してください。

#### `terraform plan`実行例
```bash
docker-compose run --rm terraform-arukas plan
```

## 使い方(Docker Composeなし、dockerコマンドを直接使う場合)


### 起動コマンド書式

```bash
docker run -it --rm aquarium/terraform-arukas 実行したいTerraformサブコマンド
```

### `terraform plan`実行例
```bash
docker run -it --rm -e ARUKAS_JSON_API_TOKEN -e ARUKAS_JSON_API_SECRET -v $PWD:/work aquarium/terraform-arukas plan
```

