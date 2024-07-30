
```markdown
# Project Vagrant

Este repositório contém o projeto desenvolvido como minha primeira experiência com o Vagrant. O front end deste projeto não foi desenvolvido por mim.

## Descrição

O objetivo deste projeto foi aprender e explorar as funcionalidades do Vagrant, uma ferramenta que facilita a criação e a configuração de ambientes de desenvolvimento virtualizados. Com o Vagrant, é possível criar máquinas virtuais configuráveis e reprodutíveis, o que torna o desenvolvimento mais consistente e portátil.

## Pré-requisitos

Para executar este projeto, você precisará ter os seguintes softwares instalados:

- [Vagrant](https://www.vagrantup.com/)
- [VirtualBox](https://www.virtualbox.org/)

## Configuração

Siga as etapas abaixo para configurar e executar o ambiente de desenvolvimento com Vagrant:
  ```

1. Clone este repositório em sua máquina local:
   
  ```bash
   git clone https://github.com/Nanndo9/project-vagrant.git
```

2. Navegue até o diretório do projeto:
   ```bash
   cd project-vagrant
   ```

3. Inicialize e configure o ambiente Vagrant:
   ```bash
   vagrant up
   ```
   Este comando irá:
   - Baixar a caixa base especificada no `Vagrantfile`.
   - Criar uma nova máquina virtual com base nesta caixa.
   - Executar os scripts de provisionamento para configurar a máquina virtual.

4. Após a conclusão do processo de configuração, acesse a máquina virtual:
   ```bash
   vagrant ssh
   ```

5. Para parar a máquina virtual, utilize o comando:
   ```bash
   vagrant halt
   ```

6. Para destruir a máquina virtual (remover completamente):
   ```bash
   vagrant destroy
   ```

## Estrutura do Projeto

A estrutura básica do projeto é a seguinte:

```
project-vagrant/
├── Vagrantfile
├── provision/
│   ├── bootstrap.sh
├── src/
│   ├── index.html
│   ├── app/
│   │   ├── ...
```

- `Vagrantfile`: Contém a configuração da máquina virtual, incluindo a caixa base, a rede e os scripts de provisionamento.
- `provision/bootstrap.sh`: Script de provisionamento que será executado na máquina virtual para instalar e configurar os softwares necessários.
- `src/`: Diretório contendo os arquivos do front end do projeto.

## Provisionamento

O script de provisionamento (`provision/bootstrap.sh`) é usado para automatizar a configuração da máquina virtual. Aqui está um exemplo do que este script pode conter:

```bash
#!/usr/bin/env bash

# Atualizar os pacotes e instalar dependências
sudo apt-get update
sudo apt-get install -y apache2

# Copiar os arquivos do projeto para o diretório do servidor web
sudo cp -r /vagrant/src/* /var/www/html/

# Reiniciar o serviço do Apache
sudo systemctl restart apache2
```

## Utilização

Após iniciar a máquina virtual com `vagrant up` e acessar via `vagrant ssh`, você pode acessar o servidor web que está sendo executado na máquina virtual. Abra um navegador e digite o endereço `http://localhost:8080` (ou a porta configurada no `Vagrantfile`).

## Observações

- O front end deste projeto não foi desenvolvido por mim. Apenas a configuração do Vagrant e a integração do ambiente são de minha autoria.
- Certifique-se de que as portas especificadas no `Vagrantfile` não estejam em uso por outros serviços no host.

## Contribuição

Sinta-se à vontade para contribuir com este projeto. Para isso, siga os passos abaixo:

1. Faça um fork do projeto.
2. Crie uma nova branch com suas alterações:
   ```bash
   git checkout -b minha-feature
   ```
3. Faça o commit de suas alterações:
   ```bash
   git commit -m 'Minha nova feature'
   ```
4. Envie suas alterações para o repositório remoto:
   ```bash
   git push origin minha-feature
   ```
5. Abra um Pull Request.
