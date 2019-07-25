``shell
export PS1='\[\033[0;36m\]* \w *\[\033[0m\n `if [[ $? = '0' ]]; then echo "\[\033[1;33m\]";else echo "\[\033[0;31m\]";fi`\u→ \$ \[\033[0m\]'
``