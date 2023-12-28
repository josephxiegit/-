
### README

#### 界面预览

----

![prevview1](<CleanShot 2023-12-28 at 09.06.32@2x.png>)
![preview2](<CleanShot 2023-12-28 at 09.06.49@2x_副本.png>)
#### 使用方法
---
1. 安装python环境
https://mirrors.tuna.tsinghua.edu.cn/anaconda/miniconda/?C=M&O=D
选择适合自己当前系统的版本
![清华大学镜像](<CleanShot 2023-12-26 at 11.36.57.png>)
windows用户选择 ``windows-x86_64.exe``
mac intel芯片选择 ``MacOSX-x86_64.pkg``
mac arm64芯片选择 ``MacOSX-arm64.pkg``


2. 打开终端（Windows上使用命令提示符或PowerShell，Mac上使用终端）
   ```shell
   cd 到当前目录
   ```

3. 创建虚拟环境
   在Windows上：
   ```shell
    python -m venv venv
    venv\Scripts\activate
   ```

    在Mac/Linux上：
    ```shell
    python3 -m venv venv
    source venv/bin/activate
    ```
  
  4. 安装依赖项
     ```shell
     pip install -r requirements.txt
     ```
  5. 运行项目
     ```shell
     streamlit run check_duplicate.py
     http://localhost:8501   // 浏览器输入
     ```
#### 文件路径图
----
- 主目录
  - requirements.txt
  - README.md
  - check_duplicate.py
  - config.json
  - 高考
    - 高考总题库.docx
    - 2023 - 2024高考题库.docx
  - 学生1
    - 学生1高考练习2023-2024.docx
  - 学生2
    - 学生2高考练习2023-2024.docx
  - 学生3
    - 学生3高考练习2023-2024.docx
  - 高三班课1
    - 高三班课1高考练习2023-2024.docx
  - 高三班课2
    - 高三班课2高考练习2023-2024.docx

#### 配置文件说明 config.json
1. 将key_words修改为学生文件夹中习题的关键字
2. doc_file1, doc_file2 修改为总题库路径
  > mac系统 要把\\修改为/
3. ignore_folder可以不动，默认是doc_file1的路径
```json
{
    "高考练习": 
    {
        "key_words": "高考练习",
        "doc_file1": "current_dir + \\高考\\高考总题库.docx",
        "doc_file2": "current_dir + \\高考\\2024年高考.docx",
        "ignore_folder": ""
    },
    "历年高二上期末汇总": 
    {
        "key_words": "历年高二上期末汇总",
        "doc_file1": "parent_dir + \\高二下\\历年高二上期末汇总.docx",
        "ignore_folder": "parent_dir + \\高二下"
    }
}
```
----
#### 关键字说明

----

1. key_words: 查询关键字，各个子文件夹（学生）所共有的关键字
2. doc_file1: 总题库路径
doc_file2: 当年题库路径，尽量保证与总题库不要重复，以便用于来年将来个题库合并。
> doc_file3， doc_file4 ... 增加多个题库也是可以的，取决于对业务的理解和安排

3. ignore_folder: 忽视文件夹，在做子文件夹遍历时（遍历每个学生），需要忽视的文件夹。一般就是题库所在文件夹，以便于在查询结果中不单独显示 “题库也出现重复”
> ignore_folder 只支持唯一文件夹；也可以省略默认为doc_file1的路径

4. ``current_dir``: 代表当前文件夹
5. ``parent_dir``: 父文件夹