## Docker
- Purpose: provide reproducible environments and run
  application/infrastructure components in containers.

Docker ajuda com:
- ambiente reproduzível
- isolamento
- empacotamento
- configuração de serviços
- facilidade para subir dependências localmente

## O que é um container?
Um container é um processo isolado que roda utilizando o kernel do sistema operacional hospedeiro, mas possui seu próprio ambiente de filesystem, processos, rede etc.
| Container = um ambiente isolado e reproduzível para executar um processo/aplicação.

## Docker Image vs Container
Image     → receita/molde. É o "molde" que descreve o ambiente necessário para executar algo.
Container → algo criado a partir dessa receita. É uma instância em execução dessa image.

## Dockerfile
Um Dockerfile descreve como construir uma image.

## Docker compose
Ele permite descrever vários serviços que precisam funcionar juntos.