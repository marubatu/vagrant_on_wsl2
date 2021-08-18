# vagrant-minikube

この Vagrant と Ansible のコードは、VirtualBox の仮想サーバー上に、Minikubeを起動するためのものです。
Minikubeは、実行時の最新バージョンが起動されるようになっています。


## Minikube 開始方法

仮想マシンを起動、ログインして、Minikube開始のコマンドを実行します。

~~~
$ vagrant up
$ vagrant ssh
$ sudo minikube start
~~~

k8sが起動するまでに、10分ほどかかります。次のコマンドで、全てのポッドがrunningになれば完了です。

~~~
$ kubectl get pod -n kube-system
~~~

もしも、ポッドのなかで状態が、Terminating になっていたら、一度、Minikubeを停止させて再開してみてください。
筆者の経験では、ほとんどのケースで解決しています。

~~~
vagrant@minikube:~$ sudo minikube stop
Stopping local Kubernetes cluster...
Machine stopped.
vagrant@minikube:~$ sudo minikube start
Starting local Kubernetes v1.13.2 cluster...
Starting VM...
~~~


## 終了

~~~
$ sudo minikube stop
$ exit
$ vagrant halt
~~~


## 削除

~~~
$ vagrant destroy
~~~


## 使用上の注意事項

* この動作環境では、ダッシュボードは利用できません。
* もしminikube delete を実行した場合は、/usr/local/bin/minikube start --vm-driver none で起動してください。


## 質問や不具合についての注意事項

* この学習環境についての質問は、Issue https://github.com/takara9/vagrant-minikube/issues に投稿をお願いします。他の質問サイトなどに質問を投稿することは問題ありませんが、筆者は対応しません。
* Minikube に本体の仕様や変更に関する質問には、Issueに挙げてもお答えできません。Kubernetes ドキュメントの[Minikubeコミュニティ](https://kubernetes.io/docs/setup/learning-environment/minikube/#community)へ質問をお願いします。



## 参考資料

* https://github.com/kubernetes/minikube
* https://kubernetes.io/docs/tasks/tools/install-minikube/#install-minikube
