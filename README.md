# hello-Ansible-CoreOS

本代码库主要实现了以下功能：

1.  调用 coreos-toolboxrc 模块生成 .toolboxrc 文件
2.  同步 docker的registry mirror配置文件
3.  生成 python3 脚本以完成 ansible 受控端的配置
4.  调用 copy 模块（须用到python环境）复制一份文件到受控机进行测试

需要配置的几个点：

1.  group_vars/all  中设置 ansible_python_interpreter: python3
2.  需要用到python模块的调用，在play层级设置environment变量PATH，增加/opt/bin路径

具体可参考 example.yml 脚本。
