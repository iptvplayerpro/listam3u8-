#!/bin/bash

if [ "$EUID" -ne 0 ]; then
  echo "⚠️ Por favor, execute como usuário root!"
  exit
fi

colors=("\033[0m" "\033[31m" "\033[32m" "\033[33m" "\033[34m" "\033[35m" "\033[36m" "\033[37m")
color=${colors[$RANDOM % ${#colors[@]}]}

echo -e "${color}Instalando softwares necessários >>> carregando......\033[0m"
apt install figlet lolcat -y

echo "==========================================================================="
echo "Powered  by  yijin" | figlet | lolcat
echo "==========================================================================="
echo ""
echo "======================================="
echo -e "${color}Script original ou coletado\033[0m"
echo "Github: https://github.com/wangyijin209" | lolcat
echo "======================================="

function run_script() {
  curl -O $1
  chmod +x $(basename $1)
  ./$(basename $1)
  rm $(basename $1)
}

echo "Escolha o script para executar (digite o número, ou q para sair):"
select script_num in \
  "Script sing-box" \
  "Script de instalação do Docker" \
  "Script de emissão do acme" \
  "Verificação do TikTok" \
  "Teste de desbloqueio de streaming" \
  "Verificação de acesso ao ChatGPT" \
  "Script x-ui (FranzKafkaYu)" \
  "Script x-ui origi
