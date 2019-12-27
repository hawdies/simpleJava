# Linux终端常用命令

## vim

### 自动补全

- **\<c-n>**: 补全提示
- **\<c-e>**: 取消
- **Enter**: 选择

### 目录树

- **,nn**: 打开目录树
- **s**: 打开文件
- **\<c-w>**: 跳转

## jobs

- \<c-z> 任务切换到后台,处于stopped状态,命令行输入`bg`处于running状态
- `command &` 任务在后台执行
- `jobs`查看后台任务
- `kill %number` 终止编号为number的任务
- `fg`  将后台任务放到前台执行,默认为第一个,若有多个后台任务,`fg %number`将编号为number的任务放到前台执行

## ps

- `ps -ef | grep "string"`查找满足string的进程
