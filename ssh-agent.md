### Cкрипт для автоматической настройки ssh-agent и добавления приватного ключа в агент, если он не был добавлен.

    env=~/.ssh/agent.env

    if ! test -f "$env" || ! . "$env" >| /dev/null || [ "$(ssh-add -l >| /dev/null 2>&1; echo $?)" = 2 ]; then

        (umask 077; ssh-agent >| "$env")
        . "$env" >| /dev/null
        ssh-add ~/.ssh/id_rsa

    elif [ "$SSH_AUTH_SOCK" ] && [ "$(ssh-add -l >| /dev/null 2>&1; echo $?)" = 1 ]; then
        ssh-add
    fi

    unset env