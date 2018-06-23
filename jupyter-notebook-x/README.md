# README

## 设置密码
1. 打开ipython，执行如下代码生成密码
```
In [1]: from notebook.auth import passwd
In [2]: passwd()
Enter password: xxxxxx
Verify password: xxxxxx
Out[2]: 'sha1:xxxxxxxxxx:xxxxxxxxxxxxxxxxxxxxxxxx'
```
2. 编辑配置文件`conf/jupyter_notebook_config.py`，修改`c.NotebookApp.password`的值为上面生成的密码

## 安装各种库和扩展
* yum和pip命令用root用户执行
* go和php的库和扩展用jupyter用户安装
* 最后应切换回root用户执行notebook
