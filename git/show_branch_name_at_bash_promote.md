## 在bash promote中显示git分支名称

首先在~/.bashrc中加入下面的代码:  

    find_git_branch () {
        local dir=. head
        until [ "$dir" -ef / ]; do
            if [ -f "$dir/.git/HEAD" ]; then
                head=$(< "$dir/.git/HEAD")
                if [[ $head = ref:\ refs/heads/* ]]; then
                    git_branch=" → ${head#*/*/}"
                elif [[ $head != '' ]]; then
                    git_branch=" → (detached)"
                else
                    git_branch=" → (unknow)"
                fi
                return
            fi
            dir="../$dir"
        done
        git_branch=''
    }

    export PROMPT_COMMAND="find_git_branch; $PROMPT_COMMAND"

然后修改PS1变量,在其中加入`\$git_branch`  (注: 如果PS1的值被单引号包围，就不需要反斜杠了)
