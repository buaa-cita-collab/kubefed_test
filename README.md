# kubefed_test
add some simple yaml for kubefed

## Content
## fedearted_namespace.yaml
创建cita-ns的namespace，并且将该namespace联邦化

## federated_chainconfig_crd.yaml
chainconfigs的CRD联邦化

## federated_chainconfig.yaml
ChainConfig的CR联邦化，不可以和上面写在一个yaml里面运行
需要在CRD联邦化之后才可以运行

## QuickStart
### 集群环境快速部署
采用[kubekey](https://github.com/kubesphere/kubekey)来快速搭建
```bash
export KKZONE=cn
curl -sfL https://get-kk.kubesphere.io | VERSION=v1.1.1 sh -
apt-get update
apt-get upgrade
apt-get install socat conntrack ebtables ipset
chmod +x kk
export KKZONE=cn
./kk create cluster [--with-kubernetes {k8s version}]
```
### 多集群部署
- 目前人工修改集群配置来部署，自动化TODO

### ChainConfig联邦化
**CR联邦化需要在CRD之后，所以不可以一起启动**
```bash
kubefed apply -f fedearted_namespace.yaml
kubefed apply -f federated_chainconfig_crd.yaml
kubefed apply -f federated_chainconfig.yaml
```

## TODO
- 调整operator的处理yaml的策略
- 可能引入新的python脚本来生成对应的yaml文件？
- 其它

