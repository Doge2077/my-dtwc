# Windows PowerShell 骚操作

****

## 文件操作

****

### 批量修改文件名

****

以批量修改后缀名 .ans 为 .out 为例子：

```
Get-ChildItem *.ans | Rename-Item -NewName { $_.Name -replace '.ans','.out' }
```

****

### 替换IDEA启动图

****

IDEA 2024：

- `C:\Users\LYS\AppData\Local\Programs\IntelliJ IDEA Ultimate\lib\product.jar` 备份该文件
- 创建一个文件夹 `test` 用来修改，将 `product.jar` 放到该文件夹下
- 在 `test` 文件夹下打开 `windows powershell`，执行 `jar -xvf .\product.jar` 解压
- 将其中的  `idea_logo@2x.png` 和 `idea_logo.png` 用画图打开，`ctrl + a` 全选删除图片
- 将需要替换的图片用画图打开，然后 `ctrl + a` 设置图片像素大小分别和上面两个照应，然后复制这个要替换的图片到上面两个文件中，一定要保证像素大小是一致的，替换之后保存一下
- 之后把 `test` 文件夹删完，将原来备份过的 `product.jar` 拖进来，把替换过图片的 `idea_logo@2x.png` 和 `idea_logo.png` 也拖进来
- 执行命令 ` jar -uvf product.jar idea_logo.png` 和 ` jar -uvf product.jar idea_logo@2x.png` 完成替换，然后把 `product.jar` 丢回原来的位置，替换掉
- 然后到 `C:\Users\LYS\AppData\Local\JetBrains\IntelliJIdea2024.1\splash\` 把 `splash` 里面缓存的文件全部删掉即可

