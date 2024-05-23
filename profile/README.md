# Tech Challenge - Fase 5

## O Problema

Há uma lanchonete de bairro que está expandindo devido seu grande sucesso. Porém, com a expansão e sem um sistema de controle de pedidos, o atendimento aos clientes pode ser caótico e confuso. Por exemplo, imagine que um cliente faça um pedido complexo, como um hambúrguer personalizado com ingredientes específicos, acompanhado de batatas fritas e uma bebida. O atendente pode anotar o pedido em um papel e entregá-lo à cozinha, mas não há garantia de que o pedido será preparado corretamente.

Sem um sistema de controle de pedidos, pode haver confusão entre os atendentes e a cozinha, resultando em atrasos na preparação e entrega dos pedidos. Os pedidos podem ser perdidos, mal interpretados ou esquecidos, levando a insatisfação dos clientes e a perda de negócios.

Em resumo, um sistema de controle de pedidos é essencial para garantir que a lanchonete possa atender os clientes de maneira eficiente e eficaz, gerenciando seus pedidos e estoques de forma adequada. Sem ele, expandir a lanchonete pode acabar, resultando em clientes insatisfeitos e impactando os negócios de forma negativa.

Para solucionar o problema, a lanchonete irá investir em um sistema de autoatendimento de fast food, que é composto por uma série de dispositivos e interfaces que permitem aos clientes selecionar e fazer pedidos sem precisar interagir com um atendente, com as seguintes funcionalidades:

**Pedido:** Os clientes são apresentados a uma interface de seleção na qual podem optar por se identificarem via CPF, se cadastrarem com nome, e-mail e CPF ou não se identificar, podendo montar o combo na seguinte sequência, sendo todas elas opcionais:

    1. Lanche 
    2. Acompanhamento
    3. Bebida

Em cada etapa é exibido o nome, descrição e preço de cada produto.

**Pagamento:** O sistema deverá possuir uma opção de pagamento integrada, no caso, para MVP, a forma de pagamento oferecida será via QRCode do Mercado Pago.

**Acompanhamento:** Uma vez que o pedido é confirmado e pago, ele é enviado para a cozinha para ser preparado. Simultaneamente deve aparecer em um monitor para o cliente acompanhar o progresso do seu pedido com as seguintes etapas:

    - Recebido
    - Em preparação
    - Pronto
    - Finalizado

**Entrega:** Quando o pedido estiver pronto, o sistema deverá notificar o cliente que ele está pronto para retirada. Ao ser retirado, o pedido deve ser atualizado para o status finalizado.


Além das etapas do cliente, o estabelecimento precisa de um acesso administrativo:

**Gerenciar clientes:** Com a identificação dos clientes o estabelecimento pode trabalhar em campanhas promocionais.

**Gerenciar produtos e categorias:** Os produtos dispostos para escolha do cliente serão gerenciados pelo estabelecimento, definindo nome, categoria, preço, descrição e imagens. Para esse sistema, teremos categorias fixas:

    - Lanche
    - Acompanhamento
    - Bebida
    - Sobremesa

**Acompanhamento de pedidos:** Deve ser possível acompanhar os pedidos em andamento e tempo de espera de cada pedido.

As informações dispostas no sistema de pedidos precisarão ser gerenciadas pelo estabelecimento através de um painel administrativo.


## Entregáveis

A rede de lanchonetes está crescendo, e com isso o sistema precisa evoluir em alguns pontos:

1. Pensando em aumentar a disponibilidade da aplicação, para que seja possível processar milhares de requisições simultâneas, além de garantir a melhor experiência para a pessoa cliente, agora iremos utilizar o padrão SAGA para processar o fluxo de pagamento da aplicação.

    **a.** Escolha um dos padrões apresentados em aula, implemente e justifique sua escolha na documentação (README);

    **b.** Neste cenário, temos que considerar que com o pagamento aprovado o cliente deve ser avisado e a cozinha precisa receber o pedido; caso contrário, a cozinha não recebe nada e o cliente é avisado do problema;
    
    **c.** Utilize qualquer gerenciador de mensageria que desejar, seja disponibilizado pela cloud escolhida ou mesmo um provisionado em seu cluster.
2. Execute a ferramenta OWASP Zap em seu projeto nos seguintes fluxos:

    **a.** Listar/exibir cardápios;

    **b.** Realização pedido (Checkout);

    **c.** Geração do Pagamento;

    **d.** Confirmação do Pagamento (Webhook);

    Gere o relatório de vulnerabilidades encontradas (Zap scanning Report) e salve-o. Corrija as vulnerabilidades altas e gere um novo relatório após as correções aplicadas.

3. Considerando a LGPD:

    **a.** Crie o relatório de impacto dos dados pessoais (RIPD) usando o padrão disponibilizado nas aulas;

    **b.** Crie uma rota/API em que o cliente consiga solicitar a exclusão ou inativação de seus dados pessoais, seja de forma lógica ou física do banco de dados utilizado. A API deverá ter os seguintes campos:

    - Nome;

    - Endereço;

    - Número de telefone;

    - Informações de Pagamento (caso seja armazenado em algum local);

### Por fim, precisamos receber: 

- Link do Github com todos os microsserviços desenvolvidos e a orquestração;
- Dentro do seu código, o ReadMe deve conter:

    - Instruções para rodar a sua aplicação, usando o orquestrador de container que preferir;
    - Justificativa do padrão SAGA escolhido;
    - Links com os relatórios dos processamentos do OWASP ZAP (antes e após a correção);
    - Link com o relatório RIPD do sistema;
    - Link para o desenho da arquitetura;
    - Link para um vídeo com:

        - O projeto rodando, inclusive com o padrão SAGA funcionando;
        - Explicação do padrão SAGA escolhido e sua justificativa;
        - Arquitetura da estrutura da nuvem e como a comunicação SAGA está montada.
