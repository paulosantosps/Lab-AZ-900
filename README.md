# Lab-AZ-900
Este repositório contém o resumo das lições aprendidas durante o Curso AZ-900 na DIO

RESUMO AULA 1:

**CONCEITOS DE NUVEM**

**O que é computação em nuvem?**
A computação em nuvem é o fornecimento de serviços de computação pela Internet, permitindo inovações mais rápidas, recursos flexíveis e economias de escala.

**MODELOS DE NUVEM**

1. **Nuvem Pública**
   - Pertence a provedores de serviços de nuvem
   - Fornece recursos e serviços a várias organizações e usuários
   - Acessada via conexão de rede segura (geralmente pela Internet)

2. **Nuvem Privada**
   - Ambiente em nuvem dentro do datacenter da própria organização
   - A organização é responsável pela operação dos serviços
   - Não fornece acesso a usuários externos

3. **Nuvem Híbrida**
   - Combina nuvens públicas e privadas
   - Permite que os aplicativos sejam executados no local mais adequado
   - Oferece maior flexibilidade

**COMPARAÇÃO DOS MODELOS**

- **Pública:** Sem despesa de capital para escalar, provisionamento rápido, pagamento conforme uso
- **Privada:** Controle total sobre recursos e segurança, mas a organização é responsável pela manutenção de hardware
- **Híbrida:** A organização decide onde executar os aplicativos, controla segurança e conformidade, e oferece a maior flexibilidade

**CapEx vs. OpEx:**
- **CapEx (Despesas de Capital):** Gasto inicial em infraestrutura física, com valor que se reduz com o tempo
- **OpEx (Despesas Operacionais):** Pagamento conforme o uso, cobrado imediatamente

**Modelo Baseado em Consumo:**
- Melhor previsão de custos
- Preços definidos para recursos e serviços individuais
- Cobrança com base no uso real

  ---------------------------------------------------------------------------------
**SLA**

 **SLA (Service Level Agreement)** é o **Acordo de Nível de Serviço** que define o percentual de disponibilidade que a Microsoft garante para um serviço durante um período (geralmente mensal).

Em outras palavras, é a garantia de que um serviço ficará disponível por um determinado percentual do tempo. Se essa disponibilidade não for atingida, o cliente pode ter direito a créditos financeiros, conforme os termos do SLA.

### Exemplo

Imagine que você criou uma máquina virtual no Azure.

* **SLA de 99,9%** significa que a VM pode ficar indisponível por aproximadamente **43 minutos por mês**.
* **SLA de 99,95%** permite cerca de **22 minutos de indisponibilidade por mês**.
* **SLA de 99,99%** permite cerca de **4 minutos por mês**.

Quanto maior o percentual, menor é o tempo de indisponibilidade permitido.

### Como aumentar o SLA

O Azure incentiva arquiteturas com redundância. Por exemplo:

* **1 VM** → SLA menor.
* **2 ou mais VMs distribuídas em Availability Zones** → SLA maior, pois se uma zona falhar, outra continua atendendo.
* Uso de **Load Balancer**, bancos de dados com replicação e armazenamento redundante também contribuem para aumentar a disponibilidade da solução.

### SLA × Alta Disponibilidade

É importante não confundir:

* **SLA**: garantia contratual de disponibilidade fornecida pela Microsoft.
* **Alta Disponibilidade (High Availability)**: estratégia de arquitetura para manter a aplicação funcionando mesmo diante de falhas.

Ou seja, o SLA é uma consequência da forma como você projeta sua solução no Azure.

### Exemplo prático

Suponha que uma empresa tenha um e-commerce hospedado no Azure:

* Se ela utilizar apenas **uma VM**, uma falha nessa VM pode deixar o site indisponível.
* Se utilizar **duas VMs em Zonas de Disponibilidade diferentes**, atrás de um **Load Balancer**, o tráfego é direcionado para a VM saudável caso uma zona apresente falha. Assim, a aplicação continua disponível e o SLA da solução é maior.

### Resumindo

O **SLA no Azure** é a garantia de disponibilidade dos serviços, expressa em porcentagem (como 99,9%, 99,95% ou 99,99%). Para alcançar SLAs mais elevados, é necessário projetar a infraestrutura com redundância, utilizando recursos como **Availability Zones**, balanceadores de carga e serviços com replicação.

**O que são Zonas de Disponibilidade?**

São datacenters fisicamente separados dentro de uma mesma região do Azure.
Cada zona possui infraestrutura independente (energia, refrigeração e rede).
Caso uma zona apresente falha, as VMs das demais continuam funcionando, reduzindo o risco de indisponibilidade.

**Balanceamento de carga**

O artigo recomenda utilizar (https://learn.microsoft.com/pt-br/azure/virtual-machines/create-portal-availability-zone):
Azure Load Balancer ou
Application Gateway.
Assim, o tráfego pode ser distribuído entre as VMs localizadas em diferentes zonas, mantendo a aplicação disponível mesmo se uma zona falhar.

- As Zonas de Disponibilidade permitem distribuir VMs entre datacenters independentes da mesma região do Azure, aumentando a disponibilidade da aplicação e protegendo contra falhas de um datacenter.

