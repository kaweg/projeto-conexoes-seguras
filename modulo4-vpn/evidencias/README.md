<h1>Módulo 4: VPN (Virtual Private Network)</h1>

<p>1. Conceito e Funcionamento</p>

Uma **VPN (Virtual Private Network - Rede Privada Virtual)** é uma infraestrutura de comunicação projetada para estender os limites de uma rede local privada sobre uma infraestrutura de rede pública não confiável, como a Internet.

O seu principal objetivo é permitir que dispositivos geograficamente distantes troquem informações de maneira tão segura e transparente quanto se estivessem interconectados diretamente por um cabo físico na mesma sala.

<b>Tunelamento</b>

O cerne do funcionamento de uma VPN baseia-se no conceito de **Tunelamento**.

O tunelamento é o processo técnico de encapsulamento de pacotes: um pacote de dados original (contendo IPs privados da rede corporativa e dados da aplicação) é inteiramente inserido como carga útil (*payload*) dentro de um novo pacote de rede exterior, dotado de um cabeçalho com IPs públicos roteáveis na Internet.

<b>Segurança da Informação em VPNs</b>

Para assegurar os pilares da segurança da informação, o tráfego que transita por este “túnel virtual” passa por rigorosos controlos criptográficos:

<b>Confidencialidade</b>

Antes de o pacote ser encapsulado e enviado, os dados originais são totalmente cifrados através de algoritmos simétricos robustos, como o **AES-256**.

Mesmo que um atacante na Internet execute técnicas de *sniffing* e intercepte os pacotes do túnel, ele apenas visualizará blocos de dados ilegíveis, sendo incapaz de expor o conteúdo legítimo da comunicação.

<b>Integridade</b>

As VPNs implementam mecanismos de verificação, como o **HMAC (Hash-based Message Authentication Code)**.

É gerada uma assinatura matemática única para cada pacote enviado. Ao receber o pacote, o destino recalcula essa assinatura; caso o pacote tenha sofrido qualquer tipo de alteração ou corrupção maliciosa durante o trajeto na rede pública, ele é descartado imediatamente, garantindo que a informação não foi adulterada.


<h1>2. Protocolos de VPN</h1>

A escolha do protocolo de comunicação determina a eficiência, a compatibilidade e o nível de segurança do túnel estabelecido pela VPN.

Abaixo apresenta-se uma análise técnica comparativa entre duas das soluções corporativas mais robustas do mercado.

OpenVPN

Camada do Modelo OSI

Opera primordialmente na **Camada 4 (Transporte)**, podendo funcionar tanto sobre o protocolo **UDP** (para maior velocidade) quanto sobre o **TCP** (para garantir a entrega e contornar bloqueios de *firewalls*).

Características de Segurança

O OpenVPN baseia-se fortemente na biblioteca **OpenSSL** para realizar as funções de criptografia e autenticação.

Ele herda todas as capacidades do protocolo **TLS**, suportando cifras avançadas como:

* AES
* ChaCha20

Por funcionar na camada de transporte, destaca-se pela:

* extrema flexibilidade;
* facilidade de configuração;
* habilidade de passar por restrições rígidas de NAT e *firewalls* sem quebrar a conexão.

---

<h1>IPsec (Internet Protocol Security)</h1>

Camada do Modelo OSI

Opera nativamente na **Camada 3 (Rede)**, o que significa que ele protege todo e qualquer tráfego que saia da interface de rede, independentemente da aplicação ou do protocolo de transporte utilizado.

Características de Segurança

O IPsec é uma *suite* de protocolos robusta que utiliza dois cabeçalhos de segurança principais:

* **AH (Authentication Header)**
  Provê integridade e autenticação da origem.

* **ESP (Encapsulating Security Payload)**
  Garante a confidencialidade através da cifragem dos dados.

Por operar diretamente na camada de rede, o IPsec é altamente eficiente e frequentemente processado diretamente por chips dedicados de hardware em roteadores e *firewalls* corporativos.

Por isso, é considerado a escolha ideal para conexões permanentes do tipo **Site-to-Site**, interligando matriz e filiais.
