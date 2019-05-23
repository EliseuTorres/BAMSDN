 BAMSDN 
========

Trata-se um modulo que permite a um controlador SDN, gerenciar de forma dinâmica a alocação de LSPs (Label Switched Paths - MPLS) e suas respectivas larguras de banda nas portas de saida de switches OpenFlow. 

O BAMSDN utiliza o limite de banda disponível (BC) das portas de saida dos switches OpenFlow por classes de tráfego (CTs). A alocação de LSPs e suas respectivas capacidades (banda alocada) é feita através de um modelo de alocação de banda (BAM) como árbitro da alocação e visa o compartilhamento e uso eficiente de recursos [1]. 




Os  experimentos seguiram uma abordagem de emulação que reproduziram uma rede OpenFlow atraves do Mininet. Para isso, foi utilizado:

      1. PC Core i5, 2.9Ghz, 8GBdeRAM
      2. Sistema Operacional Ubuntu Server 15.04,x64, versão do kernel 3.19.0-30
      3. Mininet, versão 1.8r11
      4. Protocolo OpenFlow, versão 1.0
      5. Controlador OpenFlow POX, versão 0.2.0
      6. Gerador de trafego iPerf3, versão 3.0.7


Qualquer ambiente Linux com Mininet, OpenVswitch, OpenFlow e controlador POX deve rodar esse experimento sem problemas.


A figura abaixo apresenta a topologia proposta para a ferramenta:


<img src="https://github.com/EliseuTorres/BAMSDN/blob/master/Imagens/Topologia.png">

                                                     

============================================================================

Siga as instruções abaixo aquisição da ferramenta e execução dos experimentos.

Baixar o código fonte do projeto:

     git clone https://github.com/EliseuTorres/BAMSDN.git

Executar o script init.sh

     $sudo ./init.sh

A ação  as seguintes conseguências:

     1.Mover os scritps mam.sh e rdm.sh para o diretório /pox
     2.Mover as pastas MAM e RDM para o diretório pox/ext
     3.Criar o diretório topoligia/ na pasta home do usuário
     4.Mover lab.py e scripts para a pasta topologia 

Abrir dois consoles de CLI (Terminal de linha de comando) e acessar a maquina virutal utilizando SSH

No primeiro terminal acessar o diretório pox/ e executar o controlador através dos scripts "mam.sh ou rdm.sh":

      $sudo ./mam.sh

      ou

      $sudo ./rdm.sh

No segundo terminal acessar o diretório topologia/ e executar top.py

      $sudo python topo.py

No CLI do Mininet digitar

     <mininet> xterm h1 h2 h3 h6

O host h6 será o serividor, acesse a pasta scripts e execute todos os scripts

Em h1, h2 ou h6 faça a conexão ao servidor.

      iperf3 -c 10.0.0.6 -p porta_de_destino

Para esse experimento dividimos as classes de trafego com as seguintes portas:

    CT0 5001 a 5100
    CT1 5101 a 5150
    CT2 5151 a 5200

Acesse o video para visualizar um simples teste.

https://youtu.be/BNcH2l3vwPQ


Referências;

[1]E. M Oliveira, R. F. Reale, and J. S. B. Martins, “Cognitive Management of Bandwidth Allocation Models with Case-Based Reasoning - Evidences Towards Dynamic BAM Reconfiguration,” 02-2018.
