# Rede Livre
## Projeto de construção de uma rede wifi livre no Baixo Centro de São Paulo

## O que é o OpenWRT?

O [OpenWRT](https://openwrt.org/) é um sistema baseado no GNU/Linux para ser utilizado em roteadores e outros dispositivos embarcados.

Ele substitui o software que controla o seu roteador de internet, por uma versão livre e aberta que tem uma série de funcionalidades adicionais e (geralmente) melhoria de performance!

Basicamente seu roteador vai ficar mais rápido, mais bonito e mais seguro! Lindo, não?

## Dispositivos compátiveis

Nem tudo são flores. E nem todos os roteadores são compatíveis com o OpenWRT. Como é um projeto livre, tem muita gente trabalhando constantemente para adicionar suporte a novos roteadores... mas é sempre bom checar antes.

Existe uma [wiki](http://wiki.openwrt.org/toh/start) com os dispositivos suportados e página de instrução para instalação em cada um deles.

A notícia ruim é que de uma maneira geral os roteadores vagabundos que as companhias de internet nos dão de 'presente' (ah, tá!) quando contratamos nossa internet quase nunca são compatíveis.

## Sobre Roteadores WiFi

Quando formos escolher um roteador, existe uma série de configurações que fazem a diferença. Vamos fazer a 'engenharia reversa' do modelo que escolhemos [TP-LINK WR740N](http://www.tp-link.com.br/products/details/?model=TL-WR740N) para a ofícina tentando entender o que realmente importa:

### Roteador
* TP-LINK WR740N

### Interfaces:
* 5 Portas LAN
* 1 Porta WAN

As portas LAN são conexões físicas, pra você ligar outros computadores, dispositivos e roteadores usando cabo de rede. Se tiver duas já esta resolvido - já que você sempre pode ligar um outro roteador ou um switcher.

A porta WAN (geralmente só tem uma) é usada para a conexão com a internet própriamente dita. É nela que você vai ligar o modem ADSL ou Cabo.

Vale notar que o OpenWRT permite você configurar a porta LAN como WAN e vice-versa! Uma das coisas legais é que se você tiver mais de uma conexão disponível você pode ligar as duas no mesmo roteador e balancear a conexão!

### Botões:
* Botão QSS
* Botão Reset

Pode parecer bobagem. Mas como no OpenWRT você pode configurar os botões para ter diferentes funções, é sempre útil ter alguns a disposição. Você pode, por exemplo, configurar o Botão QSS para ligar ou desligar o compartilhamento de arquivos.

### Fonte de Alimentação:
* 9VDC / 0,6A

A maioria dos roteadores consome pouca energia. Em teoria com essa voltagem a gente pode ligar o roteador usando uma bateria de 9v comum (aquelas retangulares) se montar um adaptador, mas como elas tem uma capacidade pífia de carga duraria muito pouco (estamos discutindo alternativas).

### Padrões Wireless:
* IEEE 802.11n*
* IEEE 802.11g
* IEEE 802.11b

Existe uma série de padrões wireless que são regulamentados pela IEEE (Institute of Electrical and Electronics Engineers) cada padrão tem suas específicidades que regulam distância e velocidades máximas. Em geral os roteadores modernos suportam todos os padrões em uso (atualmente, b, g e n).

### Antena:
* Onidirecional fixa de 5dBi

A antena é um componente chave pra gente. Alguns roteadores tem duas e até três antenas. O padrão 802.11n permite algo chamado 'radio chains' que é utilizar a captação de multiplas antenas para aumentar a potência e velocidade - mas pra isso cada antena tem que estar ligada em um dispositivo separado no roteador. Quando esse não é o caso, geralmente uma antena é utilizada como antena auxiliar, redundando e melhorando a receptividade do roteador. No OpenWRT a gente tem um maior controle sobre a utilização de cada antena.

No nosso caso, só temos uma antena. Não é o ideal, mas pela faixa de preço esta ok.

Além disso tem duas outras questões importante sobre as antenas. Existem vários tipos, mas os mais comuns nos roteadores são as Omnidirecionais e as Direcionais. As antenas Omnidirecionais (essas que parecem um palitinho) emite e recebe sinal em um arco de 360' graus. A vantagem óbviamente é que você tem uma cobertura igual para todos os lados. 

As direcionais, como o nome diz, enviam e recebem o sinal em uma única direção - é o caso das [antenas feitas com lata de batata de pringles](http://www.youtube.com/watch?v=kYhHxRrtyCo) a vantagem é que você normalmente consegue um sinal melhor nessa direção do que com uma Omni - uma aplicação interessante, no caso da nossa redelivre é apontar essa antena para o outro roteador quando o nosso roteador estiver configurado como repetidor.

O 5dBi é a capacidade daquela antena de transformar a corrente elétrica em ondas de rádio (grosso modo). Você vai encontrar uma série de antenas grandonas e mais caras para vender no ML com diferentes dBis. Até rola um ganho de performance, mas tem um limite bravo que é justamente a potência do próprio roteador - que geralmente é ajustada pras Antenas que já vem por padrão.

### Dimensões (L X C X A)
* 174 x 118 x 33 mm (6,9 x 4,6 x 1,3 pol)

Vale sempre pensar nas dimensões e portabilidade potencial do nosso roteador. Mas não tem tanta diferença em peso e tamanho na maioria dos modelos 'comuns'.

### Frequência
* 2,4 a 2,4835 GHz

A frequência de atuação tem a ver e é regulamentada pelos padrões suportados. A grande questão aqui é a potencial interferência de outros aparelhos e roteadores.

### Taxa do Sinal
* 11n: Até 150Mbps (dinâmico)
* 11g: Até 54Mbps (dinâmico)
* 11b: Até 11Mbps (dinâmico)

Essa taxa do sinal tem relação direta com os padrões suportados. Mas vale notar que no caso desse roteador, o padrão 11n só vai até 150mb justamente porque ele não tem as duas antenas para fazer os *radio chains*, com duas antenas a velocidade potencial vai até 300Mbps e com 3 vai até 450Mbps.

### EIRP
* <20dBm(EIRP)

O EIRP (Equivalent isotropically radiated power) é a medida da potência teórica de transmissão do roteador - levando em conta o poder do transmissor, as perdas do cabo e o ganho da antena.

### Sensibilidade da Recepção
* 130M: -68dBm@10% PER
* 108M: -68dBm@10% PER
* 54M: -68dBm@10% PER
* 11M: -85dBm@8% PER
* 6M: -88dBm@10% PER
* 1M: -90dBm@8% PER

A maior parte das vezes essa informação vem padronizada nos rótulos e na prática a coisa é um pouco diferente. Basicamente ela tem relação com a sensibilidade da antena e do roteador ao sinal WiFi e é um valor bastante importante, mas não da muito para confiar no valor alegado pelos fabricantes e a melhor maneira é testando mesmo.

## Instalando o OpenWRT

Aqui vai um passo a passo de como instalar e configurar o roteador da RedeLivre BxC usando o OpenWRT.

### Passo 1 :: Preparação

Antes de qualquer coisa - baixe o firmware específico para o seu roteador - no caso do [TP-LINK WR470N](http://wiki.openwrt.org/toh/tp-link/tl-wr740n):

[http://downloads.openwrt.org/attitude_adjustment/12.09-beta/ar71xx/generic/openwrt-ar71xx-generic-tl-wr740n-v4-squashfs-factory.bin](http://downloads.openwrt.org/attitude_adjustment/12.09-beta/ar71xx/generic/openwrt-ar71xx-generic-tl-wr740n-v4-squashfs-factory.bin)

Também é possível compilar na mão o firmware - o que permite você escolher quais serviços e pacotes quer por padrão, entre outras coisas, mas para nossa instalação isso não é essencial.

### Passo 2 :: Conectando no roteador

* Ligue o roteador na tomada.
* Conecte o cabo de rede em uma das portas LANs (as amarelinhas).
* Conecte a outra ponta do cabo de rede na sua entrada de rede.
* Abra o navegador e navegue para http://192.168.1.1/
* Usuário: admin | Senha: admin
* Clique no menu 'Firmware'
* Selecione o arquivo 'openwrt-ar71xx-generic-tl-wr740n-v4-squashfs-factory.bin'
* Clique em **atualizar**

**Cuidado!** Se você desligar o roteador no meio da atualização ou algo muito estranho acontecer, você pode *bricar* o seu roteador. Isso é ruim, mas geralmente não é o fim do mundo. Se isso acontecer procure informação na rede sobre como *desbricar* seu roteador nos fóruns do OpenWRT.

**Atenção!** Dependendo de como estiver configurada sua rede - assim que você conectar no roteador a internet pode parar de funcionar (porque as configurações padrões do roteador muitas vezes entram em conflito com as da conexão). Por isso antes de sair se aventurando lembre de fazer download e abrir todas as páginas que você quer ter em mãos :)

## Passo 3: Conectando no roteador já com OpenWRT

* Abra o navegador e navegue para http://192.168.1.1/

Se tudo deu certo, você deve entrar na interface administrativa do OpenWRT que é chamada de LuCI.

O roteador vem sem senha por padrão e a primeira coisa que vamos fazer é colocar uma senha no administrador.

* Faça login
* Usuário: root | Senha: vazia
* Clique em System -> Administration
* Troque o password para *b41x0c3ntr0* e confirme.
* Conecte novamente em http://192.168.1.1/ e faça login com a nova senha.

Em teoria com isso você já tem um roteador completamente funcional. Configurado tanto para ter uma rede wifi quando funcionar conectado por cabo. Se a sua internet não precisar de autenticação (PPPoE) ou se você for conectar o roteador livre em outro roteador basta conectar o cabo do modem na entrada WAN (azul) e sair navegando.

### Passo 4: Configurando a rede local

A primeira coisa que vamos fazer é alterar a faixa de ips da rede local. Quando o pessoal que regulamenta a internet discutiu sobre como seriam dividos os endereços ips (que é o número que identifica a sua conexão na rede e faz com que as informações consigam chegar na sua máquina) eles separaram algumas faixas de ips para serem usadas em redes locais.

A faixa do 192.168.x.x é a mais comum e utilizada por quase todos os roteadores. A gente vai usar a faixa 10.x.x.x que é menos utilizada e mais legal :)

Para isso acesse o seu roteador:

* Abra o navegador e navegue para http://192.168.1.1/
* Faça login
* Clique em Networks -> Interfaces
* Clique em 'Edit' na interface LAN
* Onde esta 192.168.1.1 subsitua por 10.10.10.1
* Save and apply!

Feito isso, o roteador provavelmente vai te derrubar (porque ele mudou a faixa de ip). Basta conectar de novo e de agora em diante você vai navegar para: http://10.10.10.1/ quando quiser acessar as configurações do roteador.

## Passo 5: Configurando as redes Wifi

* Vá em Network -> Wifi
* Clique em 'Remove' para qualquer interface que já esteja ali.
* Clique em 'Add' para adicionar uma nova interface.

Uma das coisas legais que da pra fazer com o OpenWRT é criar mais de uma conexão wifi no mesmo roteador. Assim você pode, por exemplo, ter uma conexão pública e sem senha e outra privada e com senha.

Vou explicar brevemente algumas das configurações importantes:

**Channel**

Define a frequência onde vai operar o seu wifi. O ideal é procurar uma frequência menos utilizada - já que quanto mais ocupada estiver a frequência, mais ruido você vai ter. Tem uma série de outras questões - por exemplo se você estiver usando esse roteador para conectar em um outro wifi, você não vai ter muita escolha e vai ter que ficar no mesmo canal. 

*Selecione o canal 6*

**Transmit power**

Define a potência de transmissão e esta limitada pela capacidade do roteador. Não existe muito motivo para não deixar isso no máximo em situações normais.

**ESSID**

É o nome público da rede - aquele que aparece quando você esta procurando wifis por ai :)

*Digite 'RedeLivre BxC'*

**Mode**

Existem vários modos possíveis para o roteador funcionar (nem todos os roteadores são compativeis com todos os modos) pra nós os modos mais importantes são 'Access Point' que é o modo mais comum de operar do roteador, onde as pessoas usam a conexão wifi como ponto de acesso à internet; 'Client mode' que faz com que o roteador se comporte como se fosse um computador e ai você pode pedir pra ele conectar em um outro wifi; 'Access Point (WDS)' o WDS é um padrão criado para usar o roteador como repetidor de sinal, ampliando a potência de um outro sinal de wifi. A diferença desse último pro Client Mode é que nesse caso ambos os roteadores tem que estar configurados e suportar essa tecnologia (que também costuma apresentar problemas entre modelos diferentes de roteador).

*Selecione 'Access Point'*

**Network**

Aqui você vai definir em que rede você vai colocar essa conexão. Por padrão o OpenWRT já cria dois grupos 'LAN' e 'WAN", LAN representa todas as conexões internas - a sua rede. WAN é a conexão com o mundo externo e a internet.

*Selecione LAN*

**Hide ESSID**

Esse checkbox serve para o rotedor não publicar o ESSID para o mundo. Com isso ninguém vai ver na lista a sua conexão, mas quem souber que ela esta ali ainda vai poder conectar.

Como medida de segurança é bem pouco eficiente já que sempre dá pra rastrear essas conexões com um pouco de paciência.

**Na tab Wireless Security**

Aqui você define o tipo de encriptação. Salvo situações específicas as unicas que recomendo são:

**No Encryption**

Que é basicamente uma conexão sem senha.

**WPA2-PSK**

Que é a forma de autenticação com senha mais segura e comum hoje em dia. Existem outros padrões como por exemplo o **WEP** que é aquelas conexões com uma senha sempre difícil de lembrar porque só pode usar um número x de caracteres. (As conexões WEP também são, hoje, ridiculamente faceis de quebrar.)

*Para essa conexão selecione: No Encryption*


* Clique em Save and Apply

Pronto! Agora você já tem a sua rede wifi livre :)

Repita os passos acima.

* Vá em Network -> Wifi
* Clique em 'Add' para adicionar uma nova interface.
* Channel 6
* Essid 'BxC'
* Mode Access Point
* Network LAN
* Wireless Security
	* WPA2-PSK
	* Senha 'ruasparadancar'
* Save and Apply

Para criar a outra conexão - BxC - com senha!

## Passo 6a: Conectando em outra Rede Wifi

Caso você esteja usando esse roteador direto no modem ou não queira conectar esse roteador em outra rede wifi. Pule para o passo 6b. Se já tiver conexão pode pular pro passo 7 :)

Para criar uma conexão desse roteador com outro, é bem fácil.

* Vá em Network -> Wifi
* Clique em 'Scan' para adicionar uma nova interface.

Com isso o seu roteador vai mostrar todas as redes encontradas por ele. Selecione a sua rede e clique 'Join Network'.

Atenção pro **channel** específico da rede. O OpenWRT é esperto e vai corrigir o channel das tuas outras redes para ficar iguais ao da rede na qual você vai conectar. Mas é sempre bom saber o que esta acontecendo :)

* Desmarque 'Replace wireless configuration' para ele não sobreescrever todas as suas outras redes.
* Configure a senha da conexão em WPA Passphrase ou WEP Passphrase
* Você pode manter o **wwan** como nome da nova interface.
* Mantenha a configuração do firewall em **WAN**
* Submit

Com isso, em teoria tudo esta resolvido e seu roteador já vai servir como ponto de conexão para uma outra rede wifi.

Além do alcance um pouco melhor do roteador (em comparação com a maioria dos pcs) esse jeito de distribuir a rede permite ampliar ainda mais, já que você conta com o raio do seu próprio roteador.

*Uma coisa que pode ser interessante é trabalhar com um roteador de duas ou três antenas e fazer a conexão entre esse roteador e outro usando uma antena direcional - mas vai ficar pra outro BxC.*

## Passo 6b: Conectando via PPPoE

Existem n maneiras e padrões pra estabelecer conexão e diferentes provedores e operadoras usam formas diferentes. Vou anotar aqui como configurar uma conexão PPPoE que é a maneira mais comum para essas conexões onde você precisa de um 'usuário e senha' pra conectar.

* Vá em Network -> Interfaces
* Clique em 'edit' na interface WAN
* Selecione o Protocol 'PPPoE'
* Coloque o usuário em: PAP/CHAP username
* Coloque a senha em: PAP/CHAP password
* Save and Apply!

Mole né? Óbviamente vários provedores usam configurações não tão padrões... e ai não tem muito jeito precisa quebrar a cabeça nos fóruns da vida :)

O OpenWRT seleciona o protocolo 'DHCP Client' por padrão que basicamente serve pra qualquer conexão onde você só espeta o cabo e sai navegando :)

DHCP (Dynamic Host Configuration Protocol) é justamente uma das formas que encontraram pra que o cliente/usuário não tenha que perder muito tempo e paciência configurando sua máquina na conexão :)

Uma dica legal é que quase sempre você pode configurar o IP de uma rede que funciona por DHCP de maneira estática. Isto é, se você disser pro roteador que esta usando um determinado IP e o roteador achar que esse é um IP válido... ele não vai te encher o saco :) (E se você não entendeu nada dessa parte, não se preocupe... não é nada muito importante agora.)

## Passo 7: Instalando outros pacotes

A gente cobriu até agora o básico do OpenWRT. Mas o grande barato do software livre e de projetos como esse é que além do básico, a comunidade pode e cria uma série de outras funcionalidades e ferramentas e ai o limite é a criatividade, o tempo e os 4mb de flash (no caso desse modelo =))

* Acesse System -> Software

E você vai poder ver todos os pacotes que já estão instalados no seu OpenWRT. A menos que você saiba o que esta fazendo, é melhor não deletar nenhum... já que isso pode fazer o roteador parar de funcionar, ok?

Ele mostra também o espaço disponível na memória flash. A maioria dos roteadores que a gente compra tem 2mb ou 4mb de memória flash. Com alguns modelos mais caros com 8mb.

O OpenWRT não consegue funcionar direito em roteadores com 2mb (e não é oficialmente suportado) justamente porque o pacote minimo de ferramentas não cabe nesse espaço.

Exitem varios pacotes e tutoriais legais como por exemplo:

* [Asterisk](http://wiki.openwrt.org/doc/howto/voip.asterisk) para transformar seu roteador em uma central de VoIP
* [BitTorrent](http://wiki.openwrt.org/doc/howto/bittorrent) para transformar seu roteador num baixador de torrents (ideal em um modelo com USB e HD Externo)
* [lighttpd](http://wiki.openwrt.org/doc/howto/http.lighttpd) para transformar seu roteador em um servidor de páginas
* [multiwan](http://wiki.openwrt.org/doc/howto/multiwan.failower) configurando várias conexões de internet para balancear a carga e ter um backup quando a principal cair
* [network traffic control](http://wiki.openwrt.org/doc/howto/packet.scheduler/packet.scheduler) configure seu roteador para liberar mais banda pra alguns computadores ou priorizar ou limitar alguns serviços (tipo não deixar que o bittorrent coma toda a banda da conexão)
* [gps](http://wiki.openwrt.org/doc/howto/networked.gps) conecte seu roteador em um gps e faça ele cuspir sua localização em tempo real na rede (bão pro ônibus hacker!)

Enfim... tem sempre gente inventando coisas novas.

No caso da versão 0.1 do roteador RedeLivre BxC (essa que vocês ganharam de recompensa do Catarse) nós vamos utilizar alguns pacotes extras para as funcionalidades que precisamos.

Basicamente, agora que temos duas conexões uma pública e uma privada, o que falta a gente fazer é:

* Instalar um controlador de banda pra limitar a banda disponível na rede pública e evitar que os passistas ocupem toda nossa banda e a gente fique sem poder navegar.
* Instalar o portal de abertura com o texto do BxC para que os passistas saibam mais sobre o projeto e o conceito :)

A **LuCI** não é a interface gráfica mais bonita do mundo e definitivamente não da conta de todas as possibilidades do OpenWRT. Mas a gente vai tentar seguir pela interface gráfica o quanto for possível. Vamos fazer um passo adicional para quem quiser se aventurar pela linha de comando.

Vamos instalar os pacotes necessários:

* Vá em System -> Software
* Clique em 'Update Packages'
* Filtre por 'nodogsplash' e clique em Find Packages
* Clique em 'Install'
* Filtre e instale: 'wshaper' e 'luci-app-wshaper'

O **nodogsplash** é um portal simples de autenticação - tipo aqueles da Vex e do Starbucks - que a gente vai configurar na nossa rede livre.

O **wshaper** ou WonderShaper é uma das maneiras de controlar e limitar a banda nas diferentes interfaces de conexão do nosso roteador. Existem outros sistemas mais sofisticados, mas o processo de configuração deles é bastante complexo e não acho que valha a pena para essa nossa primeira versão.

## Passo 8: Configurando o Wonder Shaper e criando novas interfaces

Por enquanto, nossas duas conexões WiFi (BxC e RedeLivre BxC) estão na mesma interface de rede 'LAN'. Essa é a configuração padrão, mas acaba jogando todo mundo no mesmo balaio.

Tanto para conseguir filtrar e limitar a velocidade quanto para garantir segurança e separar os usuários da rede livre daqueles da rede privada, vamos ter que complexificar um pouco nossa configuração.

* Vá em Networks -> Wifi
* Clique em 'Edit' na 'RedeLivre BxC'
* Em 'Network' marque a interface que você criou 'livre' e desmarque a interface 'lan'
