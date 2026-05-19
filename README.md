# Linux Data Center Lab — Monitoramento de CPU, Disco e Logs

## Objetivo

Simular incidentes operacionais em ambiente Linux e realizar troubleshooting remoto utilizando SSH em um cenário cliente-servidor.

---

# Ambiente

| Item          | Descrição     |
| ------------- | ------------- |
| Host          | macOS         |
| Virtualização | UTM           |
| VM Servidor   | Ubuntu Server |
| VM Cliente    | Ubuntu Server |
| Comunicação   | SSH           |

---

# Arquitetura

```text id="q9x2va"
MacBook
   ↓
monitor-server
   ↓ SSH
monitor-client
```

---

# Ferramentas Utilizadas

* stress
* htop
* sysstat
* SSH
* journalctl

---

# Atualização do Sistema

## Servidor e Cliente

```bash id="7m1xpl"
sudo apt update
```

---

# Instalação das Ferramentas

## VM Cliente

```bash id="4v8xqa"
sudo apt install stress htop sysstat openssh-server -y
```

---

# Teste de Comunicação

## Ping

```bash id="2q7xmk"
ping IP_CLIENTE
```

---

# Acesso Remoto SSH

## Acesso do servidor para o cliente

```bash id="9k3xvp"
ssh usuario@IP_CLIENTE
```

Exemplo:

```bash id="5r1xql"
ssh admin@192.168.64.11
```

---

# Simulação de Alto Consumo de CPU

## Gerando carga artificial

```bash id="1p8xmr"
stress --cpu 2 --timeout 300
```

---

# Monitoramento da CPU

## Processos e uso de CPU

```bash id="8n4xqt"
top
```

---

## Monitoramento visual

```bash id="3v7xpk"
htop
```

---

## Estatísticas da CPU

```bash id="6m2xqn"
mpstat 1 5
```

---

# Identificação do Processo

```bash id="4q9xvl"
ps aux --sort=-%cpu | head
```

---

# Encerramento do Processo

```bash id="7p1xmk"
sudo kill -9 PID
```

---

# Monitoramento de Disco

## Verificação de espaço

```bash id="0m4xqp"
df -h
```

---

# Simulação de consumo de disco

```bash id="5v8xqa"
fallocate -l 2G arquivo_teste.img
```

---

# Identificação de arquivos grandes

```bash id="2n7xpl"
du -ah / | sort -rh | head -20
```

---

# Remoção do arquivo de teste

```bash id="9q1xmk"
rm -f arquivo_teste.img
```

---

# Monitoramento de Logs

## Visualização de logs do sistema

```bash id="4m8xvq"
journalctl
```

---

## Logs em tempo real

```bash id="1r7xpk"
journalctl -f
```

---

## Visualização de erros

```bash id="8v2xql"
journalctl -p err
```

---

# Objetivos do Laboratório

* Simulação de incidentes Linux
* Troubleshooting remoto
* Monitoramento de CPU
* Monitoramento de disco
* Investigação de logs
* Administração remota com SSH
* Ambiente cliente-servidor

---

# Próximos Passos

* Monitoramento com Grafana
* Monitoramento com Zabbix
* Automação Bash
* Alertas de sistema
* Logs centralizados

---

# By

Joandson Oliveira
Projeto desenvolvido com foco em Linux, troubleshooting e operações de Data Center.
