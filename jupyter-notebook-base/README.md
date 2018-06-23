# README

https://hub.docker.com/r/out001a/jupyter-notebook-base/

## 设置密码
1. 打开ipython，执行如下代码生成密码
```
In [1]: from notebook.auth import passwd
In [2]: passwd()
Enter password: jupyter
Verify password: jupyter
Out[2]: 'sha1:c5d7e3b6bc86:2e6abe80aa593adf41a17a979405db5b3b62c185'
```
2. 编辑配置文件`conf/jupyter_notebook_config.py`，修改`c.NotebookApp.password`的值为上面生成的密码(以`sha1:`开头的字符串)
