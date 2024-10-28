# ipv4
- É composto por 32 bits
    - dividido em 4 grupos de 8 bits, cada grupo representa um número decimal entre 0 e 255
# Mascara de rede
- É composto por 32 bits
- dividido em 4 grupos de 8 bits, cada grupo representa um número decimal entre 0 e 255
- os bits com 1 representam os bits de endereço da rede
- os bits com 0 representam os bits de endereço de host
    - Exemplo: Endereço IP: 192.168.1.10
        - Máscara de sub-rede: 255.255.255.0 (ou em binário: 11111111.11111111.11111111.00000000)
- Se for /24, a máscara de rede é 255.255.255.0 ou seja
    - a mascara vai de 0 a 32 bits
    - para calcular a mascara vc tem que:
        - se for /24, subtraia 32-24 que da 8 bits
        - então vc coloque 24 bits 1 e 8 bits 0 = 11111111.11111111.11111111.00000000
        - agora para calcular use essa tabelinha para converte em decimal ou viseversa:
            128    64    32    16    8    4    2    1
        - a cada octeto, coloque os bits correspondentes na ordem da tabela acima.
        - Por exemplo para a mascara /24:
            128    64    32    16    8    4    2    1
            1       1     1     1    1    1    1    1   .
            1       1     1     1    1    1    1    1   .
            1       1     1     1    1    1    1    1   .
            0       0     0     0    0    0    0    0

# Classes de endereço IPv4
## Classe A
- Primeiro bit: 0
- Faixa de IPs: 1.0.0.0 a 126.0.0.0

    - Nota: O endereço 0.0.0.0 é reservado como rota padrão (default route).
    - O endereço 127.0.0.0 até 127.255.255.255 é reservado para loopback (testes internos, como localhost).

- Número de Redes /8: Máximo de 126 redes (2^7 - 2, pois 7 bits são dedicados à rede e subtrai-se 2 para endereços reservados).
- Hosts por Rede: 2^24 - 2 (cerca de 16 milhões de hosts), onde o cálculo se dá pelos 24 bits restantes.
- Uso Típico: Redes muito grandes, geralmente por grandes corporações ou organizações com muitos dispositivos conectados.

## Classe B
- Primeiros Bits: 10
- Faixa de IPs: 128.0.0.0 a 191.255.0.0
- Número de Redes /16: Máximo de 16.384 redes (2^14, pois 14 bits são dedicados à rede, ou seja 14 números 0 a direita).
- Hosts por Rede: 2^16 - 2 (aproximadamente 65.534 hosts por rede), utilizando os 16 bits restantes para identificar hosts.
    - Esse -2 vem do fato de que o primeiro e último endereço de cada rede são reservados para rota padrão (IP da rede como se fosse o nome da rede) e loopback (Broadcast da rede).
- Uso Típico: Redes de tamanho médio, como universidades e empresas.

- Exemplo:
    IP: 172.16.0.1
    Máscara: 255.255.0.0 (ou /16)

## Classe C
- Primeiros Bits: 110
- Faixa de IPs: 192.0.0.0 a 223.255.255.0
- Número de Redes /24: Máximo de 2.097.152 redes (2^21, pois 21 bits são dedicados à rede, ou seja 21 números 0 a direita)
- Hosts por Rede: 2^8 - 2 (aproximadamente 254 hosts por rede), utilizando os 8 bits restantes para identificar hosts.
    - Esse -2 vem do fato de que o primeiro e último endereço de cada rede são reservados para rota padrão (IP da rede como se fossse o nome da rede) e loopback (Broadcast da rede).
- Uso Típico: Redes de tamanho pequeno, como residências e casas.

- Exemplo:
    IP: 192.168.1.10
    Máscara: 255.255.255.0 (ou /24)

## Classe D
- Primeiros Bits: 1110
- Faixa de IPs: 224.0.0.0 a 239.255.255.255
- Uso Típico: Utilizada para comunicação multicast, onde uma transmissão é enviada para múltiplos dispositivos, como em transmissão de vídeo ao vivo para múltiplos dispositivos em uma rede.
- Endereços de Rede/Broadcast: Não existem endereços de rede ou de broadcast no contexto de multicast, pois o multicast não é uma rede única, mas sim um grupo de dispositivos que escutam um mesmo endereço multicast.

## Classe E
- Primeiros Bits: 1111
- Faixa de IPs: 240.0.0.0 a 255.255.255.255
- Uso Típico: Reservada para propósitos experimentais e pesquisa. Não está disponível para uso público ou privado.
- Endereços de Rede/Broadcast: Não existem endereços de rede ou de broadcast no contexto de multicast, pois o multicast não é uma rede única, mas sim um grupo de dispositivos que escutam um mesmo endereço multicast.

---

# IPs Privados?
- Faixas de Endereços Privados:

    Classe A: 10.0.0.0 a 10.255.255.255
    Classe B: 172.16.0.0 a 172.31.255.255
    Classe C: 192.168.0.0 a 192.168.255.255

- Flexibilidade: Diferentes faixas de endereços privados atendem a diferentes tamanhos de redes. A Classe A permite a criação de grandes redes com muitos dispositivos, enquanto a Classe C é mais adequada para pequenas redes. Isso oferece flexibilidade para os administradores de rede escolherem a faixa que melhor atende às suas necessidades.

- Organização: As diferentes classes ajudam a organizar e classificar redes. Isso facilita a administração e a gestão de redes, permitindo que organizações escolham a estrutura que mais se adequa ao seu tamanho e requisitos.

- Práticas de Design de Rede: Em ambientes corporativos, diferentes departamentos ou segmentos de uma organização podem querer usar faixas de endereços diferentes para melhor gerenciar o tráfego, aplicar políticas de segurança e segmentar redes.

---

# **IPv6**

- **Composição**:
    - É composto por 128 bits.
    - Dividido em 8 grupos de 16 bits, cada grupo representado em formato hexadecimal (0-FFFF).
    - Formato de Representação: Cada grupo de 16 bits é representado como um número hexadecimal de 4 dígitos. Em hexadecimal, cada dígito representa 4 bits, então:
        - 4 (número de dígitos)×4 (bits por dígito)=16 bits por grupo4 (número de dígitos)×4 (bits por dígito)=16 bits por grupo
    
- **Exemplo**: Endereço IPv6: `2001:0db8:85a3:0000:0000:8a2e:0370:7334`.

## **Estrutura de um Endereço IPv6**:

- **Blocos de Rede**:
    - Os primeiros 64 bits (4 grupos) identificam a rede.
    - Os últimos 64 bits (4 grupos) identificam dispositivos individuais.
- **Notação de Compressão**:
    - Para simplificar endereços longos, zeros à esquerda em um bloco podem ser omitidos.
    - Por exemplo: `2001:0db8:85a3:0000:0000:8a2e:0370:7334` pode ser encurtado para `2001:db8:85a3::8a2e:370:7334`.

## **Cálculo da Notação CIDR**:

- No IPv6, a notação CIDR (Classless Inter-Domain Routing) é utilizada para indicar a quantidade de bits alocados para a parte de rede do endereço.
- Exemplo: Um prefixo `/64` indica que os primeiros 64 bits são utilizados para identificar a rede.
- **Observação**: A notação CIDR no IPv6 não se refere a uma máscara de rede como no IPv4, mas sim a uma maneira de denotar a parte da rede de um endereço.
- Para entender a CIDR:
    - Um prefixo `/64` significa que os primeiros 64 bits são fixos para a rede, enquanto os últimos 64 bits são utilizados para endereços de host.
- Para converter a máscara de rede em formato decimal, considere cada grupo de 16 bits:
    - `FFFF` em hexadecimal é `65535` em decimal.
- Exemplo de máscara `/64`:
    - Em binário: `1111111111111111.1111111111111111.1111111111111111.1111111111111111.0000000000000000.0000000000000000.0000000000000000.0000000000000000`.

## **Vantagens do IPv6**:

- **Espaço de Endereçamento Expandido**:
    - Permite um número praticamente ilimitado de endereços IP, essencial para o crescimento da Internet.
- **Melhor Segurança**:
    - Recursos de segurança, como IPsec, são integrados ao protocolo.
- **Configuração Automática de Endereços**:
    - Facilita a implantação e manutenção de redes.
- **Suporte a Qualidade de Serviço (QoS)**:
    - Permite priorização do tráfego de rede.
- **Melhor Desempenho**:
    - Estrutura simplificada resulta em melhor desempenho e eficiência.

## **Transição do IPv4 para o IPv6**:

- É um processo contínuo, envolvendo a atualização de infraestruturas de rede, dispositivos e sistemas para suportar o IPv6.