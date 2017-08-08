# hello-Ansible-CoreOS

# 采用 toolbox 方式的 python 环境

本代码库主要实现了以下功能：

1.  调用 coreos-toolboxrc 模块生成 .toolboxrc 文件
2.  同步 docker的registry mirror配置文件
3.  生成 python3 脚本以完成 ansible 受控端的配置
4.  调用 copy 模块（须用到python环境）复制一份文件到受控机进行测试

需要配置的几个点：

1.  group_vars/all  中设置 ansible_python_interpreter: python3
2.  需要用到python模块的调用，有如下几种方式：
    -   在play层级设置environment变量PATH，增加/opt/bin路径，参考 example1.yml
    -   使用ximenpo.coreos-copy角色，设置 run_in_toolbox 变量，不需设置environment变量PATH
    -   在~/.bashrc中设置PATH变量包含python路径，支持系统模块

具体可参考 example[1-3].yml 脚本。

备注： 采用 toolbox 内 python 环境方式，会有很多细节问题，建议更换为 pypy 方式。

# 采用 pypy 方式的 python 环境

功能：

1.  调用 coreos-pypy 生成受控机 pypy 环境
2.  在 .bashrc 中追加 /opt/bin 路径，并设置 ansible_python_interpreter 为 pypy
3.  调用系统 copy 模块进行文件复制测试

具体参考 example4.yml 。
