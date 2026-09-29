# Atividade 3: Estratégia e Projeto de Testes do LocalEats

## 1. Identificação

**Turma:** Qualidade de Software - Noite 2/2026  
**Data:** [29/09/2026]

### Integrantes

| Nome                     | Usuário no GitHub |
| ------------------------ | ----------------- |
| Francisco Ibargoyen Rech | frrech            |

**Elemento de Competência:** Planejar e projetar testes selecionando técnicas adequadas.

**Aplicação:** [https://local-eats-unisenac.vercel.app/](https://local-eats-unisenac.vercel.app/)

---

## 2. Tarefa 1: Planejamento dos testes

### 2.1 Objetivo dos testes

Os testes têm como objetivo verificar se as funcionalidades selecionadas do LocalEats apresentam o comportamento esperado diante de entradas válidas, inválidas e situações de limite, identificando principalmente problemas relacionados à validação dos dados de cadastro e ao cálculo dos valores dos pedidos.

Também se pretende produzir evidências reproduzíveis dos resultados e verificar se os comportamentos observados estão de acordo com os requisitos esperados.

### 2.2 Escopo

#### Funcionalidades incluídas

| Integrante | Funcionalidade incluída | O que será verificado                                                                                                                 |
| ---------- | ----------------------- | ------------------------------------------------------------------------------------------------------------------------------------- |
| Francisco  | Cadastro de usuário     | Validação dos dados de e-mail e senha, incluindo entradas válidas, inválidas e situações de limite.                                   |
| Francisco  | Cálculo de pedidos      | Correção do cálculo dos valores dos pedidos e comportamento dos valores monetários em diferentes combinações de preços e quantidades. |

#### Funcionalidade não incluída

|Funcionalidade não incluída|Justificativa|
|---|---|
|Responsividade completa de todas as páginas|Embora tenham sido encontrados problemas de responsividade, o escopo individual desta atividade foi concentrado nos dois riscos selecionados: validação do cadastro e cálculo de pedidos.|

### 2.3 Abordagem

|Item|Decisão da equipe|Justificativa|
|---|---|---|
|Níveis de teste|Teste de sistema e testes funcionais da funcionalidade|Os riscos selecionados dependem do comportamento observável da aplicação como um todo.|
|Tipos de teste|Testes funcionais e testes baseados em entradas inválidas e valores de limite|Os riscos estão relacionados principalmente ao comportamento do sistema diante de diferentes entradas.|
|Perspectiva caixa-preta ou caixa-branca|Caixa-preta|Os casos serão definidos a partir das entradas fornecidas e dos resultados observáveis, sem depender da implementação interna.|
|Técnicas de teste|Particionamento de equivalência e análise de valor limite|O cadastro possui diferentes classes de entradas válidas e inválidas, enquanto os valores monetários permitem verificar situações de limite e precisão.|

### 2.4 Ambiente e responsabilidades

| Item                                      | Definição                                                |
| ----------------------------------------- | -------------------------------------------------------- |
| Ambiente necessário                       | Navegador web compatível e acesso à aplicação LocalEats. |
| Responsáveis pelo planejamento            | Francisco                                                |
| Responsáveis pela especificação dos casos | Francisco                                                |
| Responsáveis pela futura execução         | Francisco                                                |

### 2.5 Critérios

|Critério|Definição da equipe|
|---|---|
|Entrada|Aplicação acessível, navegador funcionando e dados necessários disponíveis para realizar cadastro e simular pedidos.|
|Saída|Os casos definidos devem ser executados e possuir resultado registrado, permitindo determinar se o comportamento observado corresponde ao esperado.|
|Suspensão|Os testes devem ser interrompidos caso a aplicação esteja indisponível ou caso um defeito impeça a execução dos demais passos necessários para os casos planejados.|

---

## 3. Tarefa 2: Riscos e técnicas de teste

### 3.1 Análise dos riscos

| ID  | Integrante | Funcionalidade      | Risco                                                                                                                                                      | Consequência                                                                                                                                         | Probabilidade | Impacto | Prioridade | Justificativa                                                                                                                                           |
| --- | ---------- | ------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------- | :-----------: | :-----: | :--------: | ------------------------------------------------------------------------------------------------------------------------------------------------------- |
| R01 | Francisco  | Cadastro de usuário | O sistema pode aceitar dados de cadastro inadequados, pois a validação de e-mail é muito permissiva e o requisito de senha observado é extremamente baixo. | Usuários podem conseguir criar contas com dados inadequados, reduzindo a confiabilidade do cadastro e aumentando riscos relacionados às credenciais. |     Alta      |  Alto   |    Alta    | O problema foi observado diretamente durante a exploração e afeta uma funcionalidade de entrada de dados utilizada para criação de contas.              |
| R02 | Francisco  | Cálculo de pedidos  | O sistema pode apresentar um valor diferente do valor esperado ao calcular um pedido, devido ao comportamento de arredondamento observado.                 | O usuário pode receber informação incorreta sobre o valor do pedido, afetando diretamente a operação de compra.                                      |     Média     |  Alto   |    Alta    | O problema observado afeta diretamente valores monetários apresentados ao usuário e pode produzir divergência entre o valor esperado e o valor exibido. |

### 3.2 Aplicação das técnicas

#### Análise do integrante

**Integrante:** Francisco
**Funcionalidade:** Cadastro de usuário  
**Risco relacionado:** R01  
**Técnica escolhida:** Particionamento de equivalência

**Por que a técnica foi escolhida:**

A técnica é adequada porque os dados de cadastro podem ser divididos em grupos de entradas que devem apresentar comportamento semelhante. Em vez de testar todas as possibilidades, podem ser selecionadas entradas representativas de classes válidas e inválidas.

**Aplicação da técnica:**

Para o campo de e-mail, considerando o comportamento observado, podem ser consideradas as seguintes classes:

|Classe|Exemplo|Resultado esperado|
|---|---|---|
|E-mail válido|`usuario@example.com`|Aceitar o formato.|
|E-mail sem `@`|`usuarioexample.com`|Rejeitar.|
|E-mail sem parte antes de `@`|`@example.com`|Rejeitar.|
|E-mail sem parte depois de `@`|`usuario@`|Rejeitar.|
|Entrada mínima inadequada|`a@b`|Verificar conforme a regra de e-mail definida para a aplicação.|

Para a senha, podem ser utilizadas classes relacionadas ao limite mínimo:

|Classe|Exemplo|Resultado esperado|
|---|---|---|
|Abaixo do mínimo|`ab`|Rejeitar.|
|No mínimo observado|`abc`|Verificar se deve ser aceito conforme a regra definida.|
|Acima do mínimo|`abcdef`|Aceitar se atender aos demais requisitos.|

**Casos derivados:** CT01 e CT02.

**Funcionalidade:** Cálculo de pedidos  
**Risco relacionado:** R02  
**Técnica escolhida:** Análise de valor limite

**Por que a técnica foi escolhida:**

A análise de valor limite é adequada porque erros de cálculo podem aparecer em situações próximas aos limites e nas mudanças de valores ou quantidades. O teste deve observar especialmente valores pequenos, combinações que resultem em centavos e situações em que o arredondamento possa alterar o resultado.

**Aplicação da técnica:**

Serão observadas situações como:

|Situação|Exemplo|Resultado esperado|
|---|---|---|
|Valor monetário simples|10,00 × 1|10,00|
|Valor com centavos|10,01 × 1|10,01|
|Quantidade maior|10,01 × 2|20,02|
|Soma de itens com centavos|10,01 + 10,02|20,03|
|Resultado próximo de uma mudança de centavo|combinação de preços que produza resultado com várias casas decimais internamente|O valor final deve seguir a regra monetária definida, sem alteração indevida por arredondamento.|

**Casos derivados:** CT03.

---

## 4. Tarefa 3: Casos de teste e rastreabilidade

### 4.1 Casos de teste

### CT01: Cadastro com e-mail inválido

**Integrante responsável:** Francisco
**Funcionalidade:** Cadastro de usuário  
**Risco ou requisito relacionado:** R01  
**Técnica utilizada:** Particionamento de equivalência

**Pré-condição:**  
A página de cadastro deve estar disponível e o usuário não deve estar autenticado.

**Dados de entrada:**  
E-mail inválido, por exemplo: `usuarioexample.com`.

**Passos:**

1. Acessar a página de cadastro.
    
2. Informar um nome válido.
    
3. Informar o e-mail `usuarioexample.com`.
    
4. Informar uma senha válida de acordo com os requisitos definidos.
    
5. Submeter o formulário.
    

**Resultado esperado:**  
O sistema deve rejeitar o e-mail inválido, informar ao usuário que o campo contém um valor inadequado e impedir a criação da conta até que um endereço válido seja informado.

---

**Funcionalidade:** Cadastro de usuário  
**Risco ou requisito relacionado:** R01  
**Técnica utilizada:** Particionamento de equivalência / valor limite

**Pré-condição:**  
A página de cadastro deve estar disponível.

**Dados de entrada:**  
Senha com dois caracteres: `ab`.

**Passos:**

1. Acessar a página de cadastro.
    
2. Informar um nome válido.
    
3. Informar um e-mail válido.
    
4. Informar a senha `ab`.
    
5. Submeter o formulário.
    

**Resultado esperado:**  
O sistema deve rejeitar a senha que não atende ao requisito mínimo definido e apresentar uma indicação de validação ao usuário.

---

**Funcionalidade:** Cálculo de pedidos  
**Risco ou requisito relacionado:** R02  
**Técnica utilizada:** Análise de valor limite

**Pré-condição:**  
A aplicação deve estar disponível e deve ser possível adicionar itens ao pedido.

**Dados de entrada:**  
Dois itens com preços de R$ 10,01 e R$ 10,02, com quantidade 1 para cada item.

**Passos:**

1. Acessar a funcionalidade de pedidos.
    
2. Adicionar um item de R$ 10,01.
    
3. Adicionar um item de R$ 10,02.
    
4. Visualizar o valor total do pedido.
    
5. Comparar o valor apresentado com o cálculo independente dos valores dos itens.
    

**Resultado esperado:**  
O sistema deve apresentar o total de **R$ 20,03**, sem arredondamento indevido que altere o valor final.

---

### 4.2 Matriz de rastreabilidade

| Funcionalidade      | Risco ou requisito                               | Técnica utilizada                              | Casos de teste |
| ------------------- | ------------------------------------------------ | ---------------------------------------------- | -------------- |
| Cadastro de usuário | R01 — Aceitação de dados inadequados no cadastro | Particionamento de equivalência / valor limite | CT01 e CT02    |
| Cálculo de pedidos  | R02 — Valor do pedido calculado incorretamente   | Análise de valor limite                        | CT03           |

---

## 5. Uso de inteligência artificial

**Ferramenta utilizada:**  
ChatGPT.

**Como foi utilizada:**  
Foi utilizada como apoio para estruturar o planejamento dos testes, organizar os riscos identificados durante a exploração e relacioná-los às técnicas e aos casos de teste.

**Uma sugestão que precisou ser alterada ou rejeitada:**  
As sugestões relacionadas aos riscos e técnicas foram confrontadas com os problemas efetivamente observados na aplicação. Quando uma relação não podia ser comprovada apenas pela observação, ela não foi tratada como fato confirmado.

**Como as respostas foram verificadas:**  
As respostas foram comparadas com as observações realizadas na aplicação e com a estrutura exigida pelo template da Atividade 3. Os casos de teste também devem ser executados na aplicação para confirmar os resultados esperados.