# mkdocs_pre_build_script 示例项目

## 安装

mkdocs

```bash
pip install mkdocs
```

mkdocs-pre-build-script

```ba
pip install mkdocs-pre-build-script
```

## 使用

mkdocs 新建一个项目

```bash
mkdocs new .
```

> [!tip]
>
> 在`mkdocs_pre_build_script_example`目录下执行

编辑`mkdocs.yml` 文件

```yaml
site_name: My Docs

plugins:
- mkdocs-pre-build-script:
    script:
      - print1.py #可以替换为其他python文件
      - ./src/print2.py
```

> [!tip]
>
> python文件路径是相对目录mkdocs_pre_build_script_example的相对路径

执行命令

```bash
mkdocs serve
```

输出

```
INFO    -  Building documentation...
脚本 print1.py 不存在，跳过执行
脚本 ./src/print2.py 不存在，跳过执行
INFO    -  Cleaning site directory
INFO    -  Documentation built in 0.09 seconds
INFO    -  [21:14:18] Watching paths for changes: 'docs', 'mkdocs.yml'
INFO    -  [21:14:18] Serving on http://127.0.0.1:8000/
```

新建 `print1.py`，`./src/print2.py`

项目结构

```
mkdocs_pre_build_script_example
├── docs
│   └── index.md
├── src
│   └── print2.py
├── README.md
├── mkdocs.yml
└── print1.py
```

编辑`print1.py` 文件

```python
def print1():
    print("print1")


if __name__ == '__main__':
    print1()
```

编辑`print2.py` 文件

```python
def print2():
    print("print2")


if __name__ == '__main__':
    print2()
```

执行命令
```bash
mkdocs serve
```

输出

```
INFO    -  Building documentation...
print1
print2
INFO    -  Cleaning site directory
INFO    -  Documentation built in 0.16 seconds
INFO    -  [21:18:36] Watching paths for changes: 'docs', 'mkdocs.yml'
INFO    -  [21:18:36] Serving on http://127.0.0.1:8000/
```

