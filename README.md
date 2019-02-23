Role Name
=========

这个Role用于在`生产环境`部署MGR, 只用使用deploy_mysql这个Role部署的MySQL实例才可以使用此Role

如何使用?
--------
修改变量文件
```
mysql_port: 3308                            #端口号, 不要超过四位
group: mgr_hotel_comment_mis                #host文件中的组名
ha_group_name: mgr_hotel_comment_mis        #高可用组名
#10段ip
group_replication_bootstraper: 10.1.2.188   #选择一个节点自动做bootstraper启动group replication, 随便选一个就行, 与vip无关
```

## 修改`/private/etc/ansible/role/deploy_mysql_and_mgr.yaml`host部分
```
- hosts: mfw_test
```

## 调用
```
cd /private/etc/ansible/role
先检查要部署的目标是不是正确的
ansible-playbook deploy_mysql_and_mgr.yaml --list-hosts
执行
ansible-playbook deploy_mysql_and_mgr.yaml  --tags=deploy_mgr
```

