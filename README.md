### 1. クラスタ作成

```sh
minikube start
```

### 2. argoCDのインストール
```sh
kubectl create ns argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```

### 3. ArgoCD UIにアクセス
```sh
kubectl port-forward -n argocd svc/argocd-server 8080:443
```
https://localhost:8080/ に接続

### 4. トークンの取得
```sh
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d; echo
```
ユーザー名は`admin`

### 5. 終了
```sh
minikube delete
```