# 导入包
`require(libName)`
`library(libName)`
# 安装包
`install.packages('tm',dependencies=TRUE)`
dependencies：
```
logical indicating to also install uninstalled packages which these packages depend on/link to/import/suggest (and so on recursively). Not used if repos = NULL. Can also be a character vector, a subset of c("Depends", "Imports", "LinkingTo", "Suggests", "Enhances").

Only supported if lib is of length one (or missing), so it is unambiguous where to install the dependent packages. If this is not the case it is ignored, with a warning.

The default, NA, means c("Depends", "Imports", "LinkingTo").

TRUE means (as from R 2.15.0) to use c("Depends", "Imports", "LinkingTo", "Suggests") for pkgs and c("Depends", "Imports", "LinkingTo") for added dependencies: this installs all the packages needed to run pkgs, their examples, tests and vignettes (if the package author specified them correctly).
```
# 目录
## 设置文件目录
获取当前目录`getwd()`
设置目录`setwd()`
## 查看文件
`dir()`
## 查看当前文件子目录
`list.dir()`
## 查看指定目录
`dir(path="folderName")`
## 只列出以字母R开头的子目录或文件
`dir(path="folderName",pattern='^R')`
## 查看当前目录的子目录和文件
`list.files()`
## 查看当前目录权限
`file.info(".")`
## 创建目录
`dir.create("folderName")`
## 目录存在
`file.exists(".")`
## 删除目录
`unlink("folderName", recursive = TRUE)`
## 目录重命名
`file.rename("folderName", "renameFolderName")`
