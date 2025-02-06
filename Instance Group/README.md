# Google Cloud - Instance Group Project

Este projeto demonstra a criação de um **Instance Group** no Google Cloud Platform (GCP) usando **Compute Engine**. O objetivo é automatizar a criação e escalabilidade de VMs através de **Instance Templates** e **Autoscaling**.

## Objetivo

Explicar o processo de criação de um **Instance Group** no Google Cloud Console para provisionamento automático de máquinas virtuais, com **autoscaling** configurado para adicionar novas instâncias quando a utilização da CPU atingir 75%.

## Tecnologias Utilizadas

- **Google Cloud Platform (GCP)**
  - Compute Engine
  - Instance Groups
  - Instance Templates
  - Autoscaling
- **Google Cloud Console**
- **Automação de Instalação de Software**
  - `stress-ng` (para testar a carga da CPU)

## Passo a Passo

### 1. Criar um Instance Template

Primeiro, criei um **Instance Template** diretamente no Google Cloud Console, definindo as configurações da VM (tipo de máquina, imagem do sistema, disco, etc.).

### 2. Criar um Instance Group

Em seguida, criei um **Instance Group** que utiliza o **Instance Template** criado anteriormente através do Google Cloud Console.

### 3. Configurar Autoscaling

Para garantir que o Instance Group escale automaticamente conforme a carga de trabalho, configurei o **Autoscaling** para adicionar uma nova VM quando a utilização da CPU atingir 75%. Isso foi feito diretamente no Console, configurando as opções de escalabilidade para o Instance Group com um limite de 2 Instancias.

### 4. Automação para Instalação do `stress-ng`

Adicionei uma automação para instalar o **stress-ng** assim que a VM for iniciada. O `stress-ng` é um utilitário que gera carga na CPU, e isso foi configurado através de um script de inicialização na VM.

**Script de inicialização:**
```bash
#!/bin/bash
sudo apt-get update
sudo apt-get install -y stress-ng
