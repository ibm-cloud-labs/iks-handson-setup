# 事前準備

ワークショップへのお申込みありがとうございます。
当日までに、環境のセットアップをお願いいたします。


## 前提条件
IBM Cloudアカウントをお持ちで、以下のどちらかの方法であること

  * PAYGアカウント
      
    クレジットカード登録済みのアカウントをお持ちである

  * サブスクリプションアカウント
    
    法人にてご契約されている

  > ライト・アカウントの状態ではご参加いただけません（IKSクラスタの環境をご準備いただけないため）


## 事前準備
1. IBM Cloud上にてIKSクラスタを作成する
2. ローカルマシンにて、CLIとFirefoxをセットアップする


## IBM Cloud上にてIKSクラスタを作成する
IBM Cloudにログインして、ワークショップで利用するIKSクラスタの作成をお願いします

1. IBM Cloudにログインします (https://cloud.ibm.com)
2. 「カタログ > 検索窓」でKubernetes を検索し，「Kubernetes Service」を選択
3. サービスの詳細画面にて「作成」ボタンを選択
4. 以下のように選択・指定し，クラスターを作成します
   * クラスター・タイプ:  無料
   * ロケーション:   North America
   * クラスター名:  mycluster

![iks-cluster-create](img/iks_cluster_create.gif)

以上で，IKSクラスターの作成手順は完了です


## ローカルマシンにて、CLIをセットアップする
IBM CloudとIKSクラスタの操作に必要なCLIツールのセットアップをお願いします。

1. 利用OSに合わせて、以下ターミナル・PowerShellを開き、以下コマンドを実行ください
   * Mac および Linux の場合

    ```
    $ curl -sL https://ibm.biz/idt-installer | bash
    ```

   * Windows 10 Pro の場合

    ```
    # Set-ExecutionPolicy Unrestricted; iex(New-Object Net.WebClient).DownloadString('http://ibm.biz/idt-win-installer')
    ```

    > Windows PowerShell アイコンを右クリックして、 **管理者として実行** を選択します。


2. インストールが正常に成功しているかの確認を行ってください
   * ibmcloud
     * コマンド
       ```
       ibmcloud --version
       ```

       > 出力結果例

       ```
       ibmcloud version 0.15.0+1bfd374-2019-04-01T03:00:47+00:00
       ```

     * 正常に成功していない場合の対策

       * 再度手順１のCLIインストールを実行してください

   * ibmcloud plugin (container-registry, kubernetes-service)

     * コマンド

       ```
       ibmcloud plugin list
       ```

       > 出力結果例

       ```
       Plugin Name                            Version    Status
       container-registry                     0.1.380             < これ 
       container-service/kubernetes-service   0.2.102             < これ 
       ```

     * 正常に成功していない場合の対策

       * プラグインにあわせて、以下コマンドを実行してください
       
         * kubernetes-service
           ```
           $ ibmcloud plugin install container-service
           ```
         * container-registry
           ```
           $ ibmcloud plugin install container-registry
           ```

   * kubectl

     * コマンド

       ```
       $ kubectl version --client
       ```

       > 出力結果例

       ```
       kubectl version --clientClient Version: version.Info{Major:"1", Minor:"13", GitVersion:"v1.13.1", GitCommit:"eec55b9ba98609a46fee712359c7b5b365bdd920", GitTreeState:"clean", BuildDate:"2018-12-13T19:44:19Z", GoVersion:"go1.11.2", Compiler:"gc", Platform:"darwin/amd64"}
       ```

     * 正常に成功していない場合の対策

       * https://kubernetes.io/docs/tasks/tools/install-kubectl/ を参照し、個別にインストールしてください


   * git
     
     * コマンド
     
       ```
       $ git --version
       ```
     
       > 出力結果例
     
       ```
       git version 2.20.1 (Apple Git-117)
       ```
     
     * 正常に成功していない場合の対策
     
       * https://git-scm.com/downloads を参照し、個別にインストールしてください。


3. IBM Cloud CLI を使ってログインできるかを確認してください
   
   以下のコマンドを実行しログインできることを確認ください。

    > Windowsユーザーの方は**コマンドプロンプト**を利用し、**管理者として実行**を行ってください。

    ```
    $ ibmcloud login -a https://cloud.ibm.com
    ```

    > シングルサインオン対応のアカウントをご利用の方は --ssoオプションを指定してください（IBM社員など)
    > 
    > `$ ibmcloud login -a https://cloud.ibm.com --sso`

    > Output

    ```
    ibmcloud loginAPI endpoint: https://cloud.ibm.com
    Email> hoge@fuga.com            < メールアドレスを入力
    Password>                       < パスワードを入力
    Authenticating...OK


    Select an account:
    1. KOTA SATO's Account (xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx)
    Enter a number> 1               < 複数のアカウントに結び付けられている場合は利用するアカウントを選択


    Targeted account KOTA SATO's Account (xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx)
    Targeted resource group default


    Select a region (or press enter to skip):
    1. au-syd
    2. jp-tok
    3. eu-de
    4. eu-gb
    5. us-south
    6. us-east
    Enter a number> 5                 < us-southを選択
    Targeted region us-south


    API endpoint:      https://cloud.ibm.com
    Region:            us-south
    User:              hoge@fuga.com
    Account:           KOTA SATO's Account (xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx)
    Resource group:    default
    CF API endpoint:
    Org:
    Space:
    OK
    ```

CLIで正常にログインが終了できれば完了です。

お疲れ様でした。当日にお会いできるのを心待ちにしています。
