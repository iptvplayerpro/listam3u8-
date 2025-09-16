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
  "Script x-ui original" \
  "Script x-ui (YongGe)" \
  "Script WARP (YongGe)" \
  "Pacote completo Sing-box (fscarmen)" \
  "Script ArgoX (fscarmen)" \
  "Adicionar swap" \
  "Ajustar prioridade IPv4/6" \
  "Instalar LNMP (use com screen)" \
  "Alterar repositórios (mirrors)" \
  "Bench (teste de servidor)" \
  "Sair"
do
  case $script_num in
    "Script sing-box")
      run_script "https://raw.githubusercontent.com/wangyijin209/box.sh/master/sing-box.sh"
      break
      ;;
    "Script de instalação do Docker")
      run_script "https://raw.githubusercontent.com/wangyijin209/box.sh/master/docker.sh"
      break
      ;;
    "Script de emissão do acme")
      run_script "https://raw.githubusercontent.com/wangyijin209/box.sh/master/acme.sh"
      break
      ;;
    "Verificação do TikTok")
      run_script "https://raw.githubusercontent.com/lmc999/TikTokCheck/main/tiktok.sh"
      break
      ;;
    "Teste de desbloqueio de streaming")
      run_script "https://raw.githubusercontent.com/lmc999/RegionRestrictionCheck/main/check.sh"
      break
      ;;
    "Verificação de acesso ao ChatGPT")
      run_script "https://raw.githubusercontent.com/missuo/OpenAI-Checker/main/openai.sh"
      break
      ;;
    "Script x-ui (FranzKafkaYu)")
      run_script "https://raw.githubusercontent.com/FranzKafkaYu/x-ui/master/install.sh"
      break
      ;;
    "Script x-ui original")
      run_script "https://raw.githubusercontent.com/vaxilu/x-ui/master/install.sh"
      break
      ;;
    "Script x-ui (YongGe)")
      run_script "https://gitlab.com/rwkgyg/x-ui-yg/raw/main/install.sh"
      break
      ;;
    "Script WARP (YongGe)")
      run_script "https://gitlab.com/rwkgyg/CFwarp/raw/main/CFwarp.sh"
      break
      ;;
    "Pacote completo Sing-box (fscarmen)")
      run_script "https://raw.githubusercontent.com/fscarmen/sing-box/main/sing-box.sh"
      break
      ;;
    "Script ArgoX (fscarmen)")
      run_script "https://raw.githubusercontent.com/fscarmen/argox/main/argox.sh"
      break
      ;;
    "Adicionar swap")
      run_script "https://raw.githubusercontent.com/BlueSkyXN/ChangeSource/master/swap.sh"
      break
      ;;
    "Ajustar prioridade IPv4/6")
      run_script "https://raw.githubusercontent.com/BlueSkyXN/ChangeSource/master/ipv.sh"
      break
      ;;
    "Instalar LNMP (use com screen)")
      run_script "https://raw.githubusercontent.com/wangyijin209/box.sh/master/lnmp.org.sh"
      break
      ;;
    "Alterar repositórios (mirrors)")
      run_script "https://raw.githubusercontent.com/wangyijin209/box.sh/master/changesource-action.sh"
      break
      ;;
    "Bench (teste de servidor)")
      run_script "https://raw.githubusercontent.com/wangyijin209/box.sh/master/bench.sh"
      break
      ;;
    "Sair")
      break
      ;;
    *)
      echo "Por favor, escolha um número válido ou digite 'q' para sair."
      ;;
  esac
done

echo "Obrigado por usar este script!" | lolcat
