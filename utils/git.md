



## `git reset`

### commit 之后撤回

#### 如果你想修改最后一次提交

1. **修改提交信息（仅限于修正commit message）**：
   如果你只是想修改最后一次提交的提交信息（commit message），可以使用 `--amend` 选项。
   ```sh
   git commit --amend
   ```
   这将打开默认文本编辑器允许你修改提交信息。如果你想直接通过命令行修改，可以这样做：
   ```sh
   git commit --amend -m "新的提交信息"
   ```

2. **添加或移除文件到最后一次提交**：
   如果你需要添加更多文件到上次的提交或者从上次的提交中移除某些文件，首先进行相应的 `git add` 或 `git reset` 操作，然后使用 `--amend` 选项更新提交。
   ```sh
   git add 文件名
   git commit --amend
   ```
   或者移除文件：
   ```sh
   git reset 文件名
   git commit --amend
   ```

#### 如果你想撤回最后一次提交

1. **未推送到远程仓库的情况**：
   如果你还没有将提交推送到远程仓库，并且希望完全撤回这个提交，可以使用 `git reset` 命令。
   
   - **软重置（保留工作目录和暂存区的变化）**：
     ```sh
     git reset --soft HEAD~1
     ```
     这会撤销最后一次提交，但是保持所有的更改在暂存区。

   - **混合重置（保留工作目录的变化，但取消暂存区的变化）**：
     ```sh
     git reset --mixed HEAD~1
     ```
     这是 `git reset` 的默认模式，它会撤销最后一次提交，并将更改保留在工作目录中，但不会标记为准备提交的状态。

   - **硬重置（丢弃所有更改）**：
     ```sh
     git reset --hard HEAD~1
     ```
     使用此命令要非常小心，因为它会删除最近一次提交的所有更改。

2. **已经推送到远程仓库的情况**：
   如果你已经将提交推送到远程仓库，那么简单地在本地重置可能造成同步问题。在这种情况下，你可以使用 `git revert` 来创建一个新的提交，该提交会撤销指定的提交所做的更改。
   ```sh
   git revert 提交ID
   ```
   其中，提交ID是你想要撤销的提交的哈希值。这将在提交历史中添加一个新的提交来撤销指定提交的更改，而不会改变提交历史，适合用于已经共享的分支。


## `git push`

推送代码，当代码推送失败的情况下，除了网络原因就是代码和别人的冲突了，可以使用 `git pull --rebase` 这样可以将从服务器上拉取的代码直接合并到自己的代码中。


## `git pull`
拉取代码


## `git remote`

### 查看远程仓库地址

```bash
git remote -v
```



## `git log`

```bash
# --oneline 每次提交压缩为一行， --graph以ascii图形形式显示提交历史和分支结构，--all显示所有分支历史提交记录
git log --oneline --graph --all
# --decorate：显示分支名称、标签等附加信息
git log --oneline --graph --all --decorate

```
```




## github

### 在 `github` 指定库中搜索

- 指定库中的具体目录搜索
```bash
# repo:iovisor/bcc 指定库
# 需要搜索的内容 TRACEPOINT_PROBE
# 在库中的具体目录搜索
repo:iovisor/bcc TRACEPOINT_PROBE path:tools
```



### 使用链接自动完成github上指定数据的搜索

- 搜索Code中 `repo:iovisor/bcc bpf_probe_read_kernel_str path:tools` 的数据
![](attachments/Pasted%20image%2020250220103250.png)
```bash
# %3A 为 : 的转码
# type指定在那个类型中搜索
https://github.com/iovisor/bcc/search?q=bpf_probe_read_kernel_str+path%3Atools&type=Code[search /tools]
```



飞书文档

https://ny5odfilnr.feishu.cn/docs/doccn0hYMpSlFkgBZYbROmWe9Gf



