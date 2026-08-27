# Análise de Feedbacks de Clientes Bancários

## Sobre o desafio

Este projeto foi desenvolvido como parte de um desafio de Engenharia de Prompt, com o objetivo de criar uma instrução capaz de utilizar Inteligência Artificial para analisar feedbacks de clientes de um serviço de atendimento bancário por chat.

A proposta é transformar os registros históricos de atendimento em uma **tabela de referência de tempo médio**, permitindo que clientes tenham uma expectativa mais clara sobre quanto tempo determinados tipos de solicitações costumam levar para serem atendidos.

A ideia funciona de maneira semelhante a um **cardápio de serviços**: assim como um cardápio pode informar o tempo estimado de preparo de cada prato, a tabela proposta apresenta o tempo médio esperado para diferentes tipos de atendimento.

---

## Problema e solução proposta

Durante um atendimento por chat, o cliente normalmente não sabe quanto tempo uma determinada solicitação poderá levar.

A proposta deste projeto é utilizar os feedbacks históricos para:

1. Identificar os principais assuntos ou problemas relatados pelos clientes;
2. Agrupar feedbacks semelhantes em categorias;
3. Calcular o tempo de cada atendimento;
4. Calcular o tempo médio de atendimento de cada categoria;
5. Identificar as categorias mais recorrentes;
6. Utilizar a satisfação dos clientes como informação complementar;
7. Apresentar os resultados em uma tabela simples e objetiva.

O resultado esperado seria semelhante a:

| Categoria de atendimento | Quantidade de ocorrências | Tempo médio de atendimento | Satisfação média |
| ------------------------ | ------------------------: | -------------------------: | ---------------: |
| Exemplo de categoria     |                         — |                      — min |                — |
| Exemplo de categoria     |                         — |                      — min |                — |
| Exemplo de categoria     |                         — |                      — min |                — |

> Os valores apresentados acima são apenas ilustrativos. O prompt deve calcular os resultados utilizando exclusivamente os dados fornecidos.

---

## Construção do Prompt

O prompt foi desenvolvido seguindo três etapas.

### 1. Definição da intenção

A primeira etapa consistiu em definir claramente:

* O que será analisado;
* Qual informação deve ser extraída;
* Quem utilizará o resultado;
* Qual decisão ou ação será apoiada pela análise.

O objetivo definido foi analisar feedbacks de clientes que utilizaram o serviço de chat para identificar os tipos de atendimento mais recorrentes e o tempo médio necessário para cada categoria.

O resultado será utilizado como uma referência para **nivelar as expectativas dos clientes em relação ao tempo de atendimento**.

---

### 2. Contexto e restrições

Na segunda etapa foram definidos os dados disponíveis e os cuidados que a IA deve seguir.

Os registros utilizados como contexto podem conter:

* Data e horário de início do atendimento;
* Data e horário de término do atendimento;
* Texto do feedback ou descrição da solicitação;
* Nota de satisfação de 1 a 5.

Também foram definidas algumas restrições importantes:

* Utilizar somente os dados fornecidos;
* Não inventar números, causas ou conclusões;
* Não expor informações pessoais ou sensíveis;
* Informar quando os dados forem insuficientes;
* Não confundir tempo de atendimento com tempo de resolução.

---

### 3. Prompt final

O prompt final reúne a intenção, o contexto, os critérios de análise, o formato esperado da resposta e as restrições.

```text
Atue como analista de dados e experiência do cliente em um banco.

Sua tarefa é analisar feedbacks de clientes que utilizaram o serviço de atendimento por chat, identificando os principais tipos de solicitação e calculando o tempo médio de atendimento para cada tipo.

## Contexto

A análise será utilizada para criar uma tabela de referência semelhante a um "cardápio de serviços". O objetivo é apresentar aos clientes uma estimativa do tempo médio necessário para o atendimento de solicitações comuns no chat, ajudando a nivelar suas expectativas antes ou durante o atendimento.

## Dados disponíveis

Serão fornecidos registros contendo:

- data e horário de início do atendimento;
- data e horário de término do atendimento;
- texto do feedback ou descrição da solicitação do cliente;
- nota de satisfação atribuída ao atendimento, em uma escala de 1 a 5.

## Instruções de análise

1. Analise o texto dos feedbacks e identifique o principal assunto ou problema relatado em cada atendimento.
2. Agrupe os feedbacks que representam solicitações ou problemas semelhantes em categorias.
3. Calcule o tempo de cada atendimento utilizando a data e o horário de início e término fornecidos.
4. Calcule o tempo médio de atendimento para cada categoria identificada.
5. Identifique quais categorias aparecem com maior frequência.
6. Calcule, quando houver dados suficientes, a média de satisfação dos clientes para cada categoria.
7. Utilize os feedbacks fornecidos como evidência para justificar a classificação das categorias.
8. Não considere como categorias diferentes problemas que tenham significado semelhante apenas por apresentarem descrições diferentes.

## Formato da resposta

Apresente uma tabela contendo as 5 categorias de atendimento mais recorrentes.

A tabela deve ser ordenada pelo tempo médio de atendimento, do menor para o maior, e deve conter:

| Categoria de atendimento | Quantidade de ocorrências | Tempo médio de atendimento | Satisfação média |
|---|---:|---:|---:|

Após a tabela, apresente uma breve análise destacando:

- qual categoria possui o maior tempo médio de atendimento;
- qual categoria possui o menor tempo médio;
- quais categorias apresentam maior frequência;
- quais categorias apresentam menor satisfação média, quando houver dados suficientes.

## Restrições

- Utilize somente os dados fornecidos.
- Não invente números, causas ou conclusões.
- Não atribua uma causa ao problema quando ela não estiver presente nos dados.
- Não exponha nomes, CPF, números de conta, telefones ou quaisquer outros dados pessoais ou sensíveis eventualmente presentes nos feedbacks.
- Caso não existam dados suficientes para classificar um feedback ou calcular uma média, informe a limitação em vez de criar uma estimativa.
- Não confunda tempo de atendimento com tempo de resolução. Quando houver apenas horário de início e término do chat, considere o intervalo como tempo de atendimento.
- Utilize linguagem simples, direta e clara.
```

---

## Dados de exemplo

Para estruturar e testar a ideia, foi criada uma base fictícia de feedbacks contendo informações de atendimentos realizados por chat.

A base possui registros com:

| Campo    | Descrição                                     |
| -------- | --------------------------------------------- |
| ID       | Identificador fictício do atendimento         |
| Data     | Data do atendimento                           |
| Canal    | Canal utilizado pelo cliente                  |
| Produto  | Produto ou serviço relacionado                |
| Nota     | Nota de satisfação de 1 a 5                   |
| Feedback | Descrição da experiência ou problema relatado |

Os dados são fictícios e não representam clientes, contas ou operações bancárias reais.

---

## Fluxo da solução

A lógica esperada para a análise pode ser representada da seguinte forma:

```text
Feedbacks dos clientes
        ↓
Identificação do assunto
        ↓
Agrupamento de problemas semelhantes
        ↓
Cálculo da duração de cada atendimento
        ↓
Cálculo do tempo médio por categoria
        ↓
Identificação das categorias mais recorrentes
        ↓
Análise da satisfação
        ↓
Tabela de referência de tempo esperado
```

---

## Resultado esperado

A solução proposta deve transformar diversos feedbacks individuais em informações mais úteis para tomada de decisão.

Em vez de analisar cada comentário isoladamente, a IA deve identificar padrões e apresentar informações como:

* quais são os problemas mais recorrentes;
* quanto tempo esses atendimentos costumam levar;
* quais categorias apresentam maior ou menor satisfação;
* quais tipos de atendimento podem exigir maior expectativa de tempo.

Dessa forma, os dados históricos de atendimento podem ser transformados em uma **referência simples e compreensível para os clientes**.

---

## Aprendizados

A construção deste desafio permitiu aplicar conceitos de Engenharia de Prompt, principalmente a importância de fornecer à IA:

* uma intenção clara;
* contexto suficiente;
* critérios objetivos de análise;
* formato esperado para a resposta;
* restrições para evitar conclusões sem evidência;
* cuidados relacionados a dados pessoais e sensíveis.

O principal aprendizado foi perceber que um prompt eficiente não deve apenas indicar **o que a IA deve fazer**, mas também explicar **com quais dados ela trabalhará, como deve realizar a tarefa, qual resultado é esperado e quais limites deve respeitar**.

---

## Tecnologias e conceitos

* Inteligência Artificial Generativa
* Engenharia de Prompt
* Análise de dados
* Análise de feedback de clientes
* Classificação e agrupamento de informações
* Análise de satisfação
* Git e GitHub
* Markdown

---

## Estrutura do projeto

```text
desafio-feedback-clientes-bancarios/
│
└── README.md
```
