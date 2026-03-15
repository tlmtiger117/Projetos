# 15/03/26
# Tráfego Suspeito(Scan)

- Nesse mini-projeto de final de semana, eu montei um fluxo completo de um analista SOC em meu LAB.
   - Atacante(pentest/invasor)
   - Analista(SOC)
   - Defensor(Firewall Admim)
     

- Ferramentas:
   - Nmap(Network Mapper): Ferramenta de Recon ativo, tem contato direto com o alvo(manda e recebe dados).
                            Utilizada nesse caso para sumular um tráfego de um atacante.
     
        
   - Wireshark(Sniffer/captura de pacotes): Recon Passivo, apenas observa o tráfego da rede(observa/detecta).
   - Iptables: Programa/Firewall que utiliza do filtro do Kernel(Netfilterl) para criar regras(mitigação/defesa).
     
 
- 1° Pentester/Invasor: Nesse caso, eu simulei um scan com delay entre cada probe enviada, mas fazendo um scan
     sequancia(Padrão nmap).

   - [!] O Nmap por ser um programa automatizado, cria pacotes com mesmo tamanho, sendo um bom indicativo de que seja um
          possível scan.
     
   - [!] Geralmente o Nmap usa a mesma porta para enviar as probes num scan sequancial(21,22,23...).
   - [!] Esses tópicos não são uma regra geral, pois o Nmap tem opções para modificar cada um desses
          pontos que apresentei.
     

- 2° Análise com Wireshark: Sempre quando for usar essa tool, pense:
  
   - O que eu vou analisar?:    -> (Tráfego padrão, Malware,scans..)
   - Como vou identificar?:     -> (Gráficos, Conversations, Endpoints)
   - Como vou expecificar?:     -> (Filtros de SRC,DST,Protocolos,Ignorar tráfego padrão...)
   - padrões de dados:          -> (Pacotes com mesmo tamanho, mesma porta de envio, tempo curto entre probes...)

  - Só com isso você já fica muito próximo de achar a causa do problema na rede.
    

- 3° Iptables/firewall: Utilizado neste caso paca criar uma regra que detectasse o scanner. comando utilizado:
   - sudo iptables -A INPUT -p tcp --dport 21 -m recent --set -j LOG --log-prefix "(_FTP_TENT_)"
   - Esse comando basicamente fala: "todo tráfego que chegar na porta 21 vai ser logado como '(_FTP_TENT_)'"
   - É um comando simples que pode sem melhorado e muito quando se trata de scans.


- (Aprendizado): Aprendi a entender o fluxo geral de como funciona o ataque, detecçção e mitigação numa rede.
- (Repositórios): Aqui estão os repositórios relacionados a cada tool mencionada nesse Projeto:
  
  
   - Nmap: https://github.com/tlmtiger117/Nmap-Network-Mapper-
   - Wireshark: https://github.com/tlmtiger117/Wireshark-Sniffers-de-Rede  
   - Iptables/firewall: https://github.com/tlmtiger117/Firewall
 




 
     
   
