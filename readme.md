## 安装包[下载地址](https://github.com/jgm/pandoc/releases/tag/2.2)

> https://github.com/jgm/pandoc/releases/tag/2.2

## 使用技巧:

- 本脚本和 .md 文件放到一个文件夹里

```python
import os  

def auto_md_to_docx(file_dir):
    # 获取当前目录下所有的md文件的路径信息
    all_whole_path_files = []
    for root, dirs, files in os.walk(file_dir):
        for file in files:
            try:
                if file[-3:] == ".md":
                    file_info = [root+'/', file]
                    all_whole_path_files.append(file_info)
            except Exception as e:
                print(e)
    print("==>", all_whole_path_files)

    # 将md依次转换为pandoc
    for file_info in all_whole_path_files:
        md_file_path_file = file_info[0] + file_info[1]
        docx_file_name = file_info[1][:-3] + '.docx'
        docx_file_path_file = file_info[0] + docx_file_name
        new_command = 'pandoc ' + md_file_path_file + ' -o ' + docx_file_path_file

        try:
            result = os.popen(new_command).readlines()
            if len(result) == 0:
                print(md_file_path_file, "已经转换为", docx_file_path_file)
        except Exception as e:
            print(e)

def main():
    auto_md_to_docx('.')

if __name__ == '__main__':
    main()

```

## windows用户安装pandoc

### 1. 下载安装版软件包

下载地址: [https://github.com/jgm/pandoc/releases/tag/2.2.1](https://github.com/jgm/pandoc/releases/tag/2.2.1)

### 2. 安装结束

打开文件所在的命令行，运行指令

```bash
pandoc 文件名.md -o 文件名.docx
```

# 修改了这里，提交一下看看，github 网站有没有更新这里