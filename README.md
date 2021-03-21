项目说明
===

ROS自动化运维

### 协作约定

``` bash
# redhat
yum install -y gcc python36-devel openssl-devel
yum install -y sshpass openssh-clients


# 保存当前类库
# pip3 freeze > requirementes.txt

# 恢复类库
pip3 install -r requirementes.txt

# 清除所有虚环境的包 !! 危险 !!
pip3 freeze | xargs pip3 uninstall -y

# ssh_config设置样例
cat <<'EOF'>/root/.ssh/config
Host *
    StrictHostKeyChecking no
    UserKnownHostsFile=/dev/null
EOF

```

### 样例运行

``` bash
# 清理ros的dns
ansible-playbook -i inventory/default.ini --extra-vars 'ansible_ssh_pass=xxxx' ip_dns_cache_flush.yaml

```