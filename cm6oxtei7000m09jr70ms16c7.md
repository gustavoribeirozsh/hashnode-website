---
title: "How-To: Instalação do Docker no Windows da forma correta em 7 passos"
datePublished: Tue Nov 05 2024 04:49:08 GMT+0000 (Coordinated Universal Time)
cuid: cm6oxtei7000m09jr70ms16c7
slug: how-to-instalac3a7c3a3o-do-docker-no-windows-da-forma-correta-17c41b2d46ca
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1738580289839/857279a6-379c-4e1a-a0ea-034087d4244d.png

---

1.  Vá para [https://www.docker.com/products/docker-desktop/](https://www.docker.com/products/docker-desktop/)

2\. Escolha sua versão do Windows:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1738580281056/b262ca56-a09c-4e3a-ae3b-038feca1b7e7.png)

3\. Para saber qual é, abra *Configurações > Sistema > Sobre*

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1738580282797/8018333b-f938-4a42-b2c9-ad40cd7cea4c.png)

> **Nota: Você deve ter instalado o WSL 2 (Windows Subsystem Linux)**

4\. Se tudo ocorrer bem, iniciará a instalação:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1738580284259/e03c39f0-50d5-467e-9d0a-73f3c567223a.png)

5\. Docker instalado!

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1738580285998/008abc53-9205-46ce-81b9-619564cfe2a0.png)

6\. Hora de configurar o arquivo *.wslconfig* para que limite o uso de memória e CPU do seu computador durante a execução dos containers.

*   Abra o bloco de notas — *Win + R > notepad > enter.*
*   Cole o seguinte código:

\# Settings apply across all Linux distros running on WSL 2  
\[wsl2\]  
  
\# Limits VM memory to use no more than 4 GB, this can be set as whole numbers using GB or MB  
memory\=4GB  
  
\# Sets the VM to use two virtual processors  
processors\=2  
  
\# Specify a custom Linux kernel to use with your installed distros. The default kernel used can be found at https://github.com/microsoft/WSL2-Linux-Kernel  
kernel\=C:\\\\temp\\\\myCustomKernel  
  
\# Sets additional kernel parameters, in this case enabling older Linux base images such as Centos 6  
kernelCommandLine = vsyscall=emulate  
  
\# Sets amount of swap storage space to 8GB, default is 25% of available RAM  
swap\=8GB  
  
\# Sets swapfile path location, default is %USERPROFILE%\\AppData\\Local\\Temp\\swap.vhdx  
swapfile\=C:\\\\temp\\\\wsl-swap.vhdx  
  
\# Disable page reporting so WSL retains all allocated memory claimed from Windows and releases none back when free  
pageReporting\=false  
  
\# Turn off default connection to bind WSL 2 localhost to Windows localhost  
localhostforwarding\=true  
  
\# Disables nested virtualization  
nestedVirtualization\=false  
  
\# Turns on output console showing contents of dmesg when opening a WSL 2 distro for debugging  
debugConsole\=true

*   Vá até seu usuário no Windows — *Explorar > Disco Local (C:)> Usuários > Seu nome de Usuário,* ou pressione *Win + R e digite %USERPROFILE%*
*   Salve o arquivo como *“.wslconfig”*

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1738580287453/0c2ba142-a0ad-4bc1-9030-855aed0adc67.png)

*   Reinicie o Docker.

7\. Configure o WSL Integration:

*   Vá nas configurações do Docker, selecione *Resources > WSL Integration* e habilite a versão do Ubuntu que você tem instalada.

PRONTO PARA USO!

> Ps.: Algumas versões estão dando problema ao tentar dar pull em um container. A recomendação é deixar a opção *Add the \*.docker.internal names to the host’s /etc/hosts file (Requires password)* **DESABILITADA** enquanto a opção *Enable background SBOM indexing* **HABILITADA**.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1738580288589/6c365c9a-bbe3-45bb-844f-ef7efdd0dc20.png)