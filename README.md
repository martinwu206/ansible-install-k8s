# Kubernetes v1.16 高可用集群自动部署（离线版）
>### 确保所有节点系统时间一致
## 1、下载二进制包，并解压到工作目录
云盘地址：https://pan.baidu.com/s/1kvgE_ql9i7Skf3UVMfRTVA
```
cd ansible-install-k8s
tar zxf binary_pkg_cni.tar.gz
```
## 2、修改hosts文件
根据规划修改对应IP和名称。
vi hosts
## 3、修改group_vars/all.yml文件

添加证书可信任IP：
```
cert_hosts:
  k8s:
  etcd:
```
## 4、一键部署
### 架构图
单Master架构
![avatar](https://github.com/lizhenliang/ansible-install-k8s/blob/master/single-master.png)
多Master架构
![avatar](https://github.com/lizhenliang/ansible-install-k8s/blob/master/multi-master.png)
### 部署命令
单Master版：
```
ansible-playbook -i hosts single-master-deploy.yml -uroot -k
```
多Master版：
```
ansible-playbook -i hosts multi-master-deploy.yml -uroot -k
```
