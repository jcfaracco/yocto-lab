# SEL0456 - Desenvolvimento de Software para Sistemas Embarcados com Sistemas Operacionais
------------------------------------------------------------------------------------------

## Laboratórios:

- [**Lab 1:**](https://github.com/jcfaracco/yocto-lab/blob/main/labs/lab1/LAB.md) Configure e crie um build simples utilizando Yocto e QEMU.
- [**Lab 2:**](https://github.com/jcfaracco/yocto-lab/blob/main/labs/lab2/LAB.md) Crie um patch simples para o kernel e veja como ele reflete no seu build.
- [**Lab 3:**](https://github.com/jcfaracco/yocto-lab/blob/main/labs/lab3/LAB.md) Crie sua própria layer e inclua um aplicativo no build.
- [**Lab 4:**](https://github.com/jcfaracco/yocto-lab/blob/main/labs/lab4/LAB.md) Crie um teste para execução e validação do build.

## Configure um container

Fique a vontade para usar qualquer ambiente de desenvolvimento: uma máquina nativa, uma máquina virtual ou até mesmo um container. Se você usa **Docker**, está disponível um `Dockerfile` com todo ferramental necessário para os laboratórios. Uma observação importante: quem utilizar alguma solução de containers, poderá se deparar com um erro de cópia durante a instalação de algum pacote. Para resolvê-la, basta utilizar os seguintes argumentos: `--storage-opt overlay.mount_program=/usr/bin/fuse-overlayfs --storage-opt overlay.mountopt=nodev,metacopy=on,noxattrs=1`.

**Exemplo:** utilizando **Docker**, faremos os comandos a seguir:

    $ cd yocto-lab/
    $ ls .
    Dockerfile  labs  LICENSE  README.md
    $ docker build . -t seu_container:v1
    $ docker run -ti --privileged seu_container:v1 bash

É importante o uso do argumento `--privileged` para obtermos permissão necessária para utilizar os recursos de virtualização do sistema e outros.
