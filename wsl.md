#### Включаем подсистему Windows для Linux (WSL)
    dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart

#### Включаем платформу виртуальных машин
    dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart

# Установка WSL

    wsl --install

Автоматически включит необходимые дополнительные функции WSL, установит дистрибутив Ubuntu по умолчанию и установит последнюю версию ядра WSL Linux на ваш компьютер

    ## Выбор дистрибутива
    wsl --install -d Distr

    ## Показывает список доступных дистрибутивов Linux, доступных для загрузки
    wsl -l -o

 
    ## Показывает установленные дистрибутивы с их версиями
    wsl -l -v

Если нужно обновить забытый root пароль

    wsl -d Distr -u root
    passwd username

Отключить WSL

    wsl --shutdown

Удаляет дистрибутив <Distr>

    wsl --unregister Distr