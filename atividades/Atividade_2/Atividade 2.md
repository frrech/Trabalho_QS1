# Atividade 2: Organização da Qualidade no LocalEats

## 1. Identificação

**Turma:** Qualidade de Software - Noite 2/2026  
**Data:** [29/09/2026]

### Integrantes

| Nome                     | Usuário no GitHub |
| ------------------------ | ----------------- |
| Francisco Ibargoyen Rech | frrech            |

**Elemento de Competência:** Identificar papéis, responsabilidades e competências relacionadas às atividades de qualidade e testes.

---

## 2. Tarefa 1: Diagnóstico da situação

### 2.1 Problemas organizacionais

|Problema identificado|Possível consequência para o produto ou para a equipe|
|---|---|
|Não há uma definição clara de quem é responsável por verificar sistematicamente a qualidade das funcionalidades antes da disponibilização.|Defeitos podem chegar ao usuário porque nenhuma pessoa ou papel possui responsabilidade clara pela verificação final da qualidade.|
|As atividades de desenvolvimento, revisão e testes podem ficar concentradas nas mesmas pessoas sem uma divisão explícita de responsabilidades.|A equipe pode deixar de identificar problemas por falta de revisão independente ou por sobrecarga de quem implementa a funcionalidade.|
|Não há evidência, no projeto analisado, de um processo estruturado de acompanhamento de defeitos e validação das correções.|Problemas encontrados durante a exploração podem permanecer sem acompanhamento, ser corrigidos parcialmente ou voltar a ocorrer.|
|Problemas de qualidade envolvem diferentes áreas do sistema, como interface, validação de dados, pedidos e responsividade.|Se a qualidade for tratada como responsabilidade de apenas uma pessoa, problemas específicos de desenvolvimento, requisitos ou experiência de usuário podem não ser adequadamente identificados.|

### 2.2 Responsabilidade pela qualidade

**A qualidade do LocalEats deve ser responsabilidade exclusiva do profissional de QA? Justifiquem.**

Não. A qualidade deve ser uma responsabilidade compartilhada entre os diferentes papéis envolvidos no desenvolvimento do sistema. O QA possui responsabilidade importante na definição da estratégia, planejamento e execução dos testes, mas desenvolvedores, responsáveis por requisitos e demais integrantes também devem contribuir para prevenir, identificar e corrigir problemas. Os problemas observados no LocalEats envolvem funcionalidades, interface, validação e comportamento do sistema, portanto não podem ser tratados somente no final do desenvolvimento.

---

## 3. Tarefa 2: Papéis e competências

> Fiz tudo individualmente, mas não deixei de preencher essa parte do trabalho

| Integrante | Papel analisado                      | Responsabilidades relacionadas à qualidade                                                                                                                       | Competências técnicas                                                                                      | Competências comportamentais                                                          |
| ---------- | ------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------- |
| Francisco  | Desenvolvedor                        | Implementar funcionalidades de acordo com os requisitos, corrigir defeitos, criar testes unitários quando aplicável e participar da revisão do código.           | Programação, testes unitários, controle de versão, depuração e revisão de código.                          | Atenção aos detalhes, colaboração, responsabilidade e abertura para receber feedback. |
| Francisco  | QA/Testador                          | Planejar e executar testes, identificar riscos, especificar casos de teste, registrar defeitos e verificar correções.                                            | Técnicas de teste, projeto de casos de teste, testes funcionais, análise de riscos e registro de defeitos. | Pensamento crítico, organização, comunicação e atenção aos detalhes.                  |
| Francisco  | Analista de requisitos/Product Owner | Definir e revisar requisitos e critérios de aceitação, esclarecer regras de negócio e validar se o comportamento implementado atende às necessidades do usuário. | Engenharia de requisitos, critérios de aceitação, regras de negócio e validação de requisitos.             | Comunicação, negociação, visão do usuário e capacidade de priorização.                |
| Francisco  | UX/UI Designer                       | Contribuir para a qualidade da interface, consistência visual, usabilidade e adequação da experiência nos diferentes dispositivos.                               | Design de interfaces, responsividade, usabilidade e prototipação.                                          | Empatia com o usuário, comunicação, colaboração e atenção à experiência de uso.       |

### Diferença entre responsabilidade e competência

**Responsabilidade** é aquilo que o papel deve realizar ou pelo qual deve responder dentro do processo.

**Competência** é o conjunto de conhecimentos, habilidades e comportamentos necessários para executar essa responsabilidade adequadamente.

Por exemplo, executar testes é uma responsabilidade do QA; conhecer técnicas de projeto de testes é uma competência necessária para executar essa responsabilidade.

---

## 4. Tarefa 3: Matriz de responsabilidades

Para a matriz, foram utilizados os seguintes papéis:

- **DEV:** Desenvolvedor
    
- **QA:** QA/Testador
    
- **PO:** Analista de requisitos/Product Owner
    
- **UX:** UX/UI Designer
    

|Atividade de qualidade|DEV|QA|PO|UX|
|---|:-:|:-:|:-:|:-:|
|Definir critérios de aceitação|C|C|A/R|C|
|Revisar requisitos|C|C|A/R|C|
|Implementar a funcionalidade|R|I|C|C|
|Revisar o código|R|C|I|I|
|Criar testes unitários|R|C|I|I|
|Planejar e executar testes do sistema|C|A/R|I|C|
|Registrar e acompanhar defeitos|C|A/R|I|C|
|Priorizar a correção dos defeitos|C|C|A/R|C|
|Aprovar a disponibilização da versão|C|R|A|C|

### 4.1 Lacuna ou conflito encontrado

**Lacuna ou conflito:**

Uma possível lacuna é a ausência de uma responsabilidade claramente definida para o acompanhamento sistemático dos defeitos desde sua identificação até a verificação da correção.

**Consequência:**

Defeitos podem ser identificados durante os testes ou durante a utilização da aplicação sem que exista um responsável claro por acompanhar sua correção e confirmar posteriormente que o problema foi realmente resolvido.

### 4.2 Práticas de QA recomendadas

|Prática recomendada|Problema que ajuda a resolver|Papéis envolvidos|
|---|---|---|
|Criar e manter um registro de defeitos com descrição, prioridade, responsável, status e evidência.|Evita que problemas encontrados sejam esquecidos ou tenham seu acompanhamento perdido.|QA, DEV e PO|
|Realizar revisão dos critérios de aceitação antes da implementação e antes da validação final.|Reduz ambiguidades sobre o comportamento esperado e facilita a criação dos testes.|PO, QA, DEV e UX|
|Executar testes antes da disponibilização da versão.|Reduz a possibilidade de defeitos conhecidos chegarem ao usuário.|QA e DEV|
|Realizar testes de responsividade nas principais larguras de tela.|Ajuda a identificar problemas como os observados na página Explorar e no avatar em dispositivos móveis.|QA, DEV e UX|

---

## 5. Uso de inteligência artificial

**Ferramenta utilizada:**  
ChatGPT.

**Como foi utilizada:**  
Foi utilizada como apoio para organizar as observações encontradas na aplicação em problemas relacionados à organização da qualidade, responsabilidades, competências e práticas de QA.

**Como as respostas foram verificadas:**  
As propostas foram confrontadas com a estrutura da Atividade 2 e com os problemas observados durante a exploração da aplicação. Importante observar que o trabalho foi feito individualmente e portanto essa divisão de tarefas não é aplicável.