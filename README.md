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