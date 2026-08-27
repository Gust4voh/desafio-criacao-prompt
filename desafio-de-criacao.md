# Prompt — Análise de Tempo de Atendimento em Chat Bancário

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

- Categoria de atendimento
- Quantidade de ocorrências
- Tempo médio de atendimento
- Satisfação média


Após a tabela, apresente uma breve análise destacando:

- Qual categoria possui o maior tempo médio de atendimento;
- Qual categoria possui o menor tempo médio;
- Quais categorias apresentam maior frequência;
- Quais categorias apresentam menor satisfação média, quando houver dados suficientes.

## Restrições

- Utilize somente os dados fornecidos.
- Não invente números, causas ou conclusões.
- Não atribua uma causa ao problema quando ela não estiver presente nos dados.
- Não exponha nomes, CPF, números de conta, telefones ou quaisquer outros dados pessoais ou sensíveis eventualmente presentes nos feedbacks.
- Caso não existam dados suficientes para classificar um feedback ou calcular uma média, informe a limitação em vez de criar uma estimativa.
- Não confunda tempo de atendimento com tempo de resolução. Quando houver apenas horário de início e término do chat, considere o intervalo como tempo de atendimento.
- Utilize linguagem simples, direta e clara.
