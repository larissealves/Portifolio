# Diagramas de Sistemas — Guia Rápido

Uma visão geral dos principais diagramas usados em **Engenharia de Software, UML, arquitetura e modelagem de sistemas**.

---

## 1. UML — Unified Modeling Language

**O que é:**
Uma linguagem visual para **modelar, documentar e representar sistemas**, principalmente sistemas de software.

A UML possui vários tipos de diagramas, divididos principalmente em **estruturais** e **comportamentais**.

### Principais diagramas UML

| Diagrama                     | Resumo                                                                                             |
| ---------------------------- | -------------------------------------------------------------------------------------------------- |
| **Caso de Uso**              | Mostra **o que o sistema faz** e quem interage com ele.                                            |
| **Classes**                  | Mostra classes, atributos, métodos e relacionamentos.                                              |
| **Sequência**                | Mostra a **ordem das mensagens/interações** entre objetos ao longo do tempo.                       |
| **Atividade**                | Representa **fluxos de processos e atividades**, parecido com um fluxograma.                       |
| **Estados**                  | Mostra os diferentes **estados de um objeto** e como ele muda entre eles.                          |
| **Componentes**              | Mostra os principais componentes de software e suas dependências.                                  |
| **Implantação (Deployment)** | Mostra onde os componentes são **executados fisicamente**: servidores, máquinas, dispositivos etc. |
| **Objetos**                  | Mostra exemplos concretos de objetos e seus relacionamentos em determinado momento.                |
| **Pacotes**                  | Organiza elementos do sistema em grupos/pacotes.                                                   |
| **Comunicação**              | Mostra como objetos se comunicam, enfatizando as relações entre eles.                              |

---

# 2. Diagrama de Caso de Uso

**Serve para:** entender os **requisitos funcionais** do sistema.

Mostra:

* 👤 **Atores** — quem usa/interage com o sistema
* ⚙️ **Casos de uso** — o que o sistema permite fazer
* 🔗 **Relacionamentos** entre atores e funcionalidades

**Pergunta que responde:**

> "Quem faz o quê no sistema?"

**Exemplo:**

```text
Cliente
   │
   ├── Fazer login
   ├── Realizar compra
   └── Consultar pedidos
```

---

# 3. Diagrama de Classes

**Serve para:** representar a **estrutura do software**.

Mostra:

* Classes
* Atributos
* Métodos
* Herança
* Associação
* Composição
* Agregação
* Dependências

**Pergunta que responde:**

> "Quais são as entidades do sistema e como elas se relacionam?"

Exemplo:

```text
┌──────────────┐
│   Cliente    │
├──────────────┤
│ nome         │
│ email        │
├──────────────┤
│ comprar()    │
└──────┬───────┘
       │
       │ possui
       ▼
┌──────────────┐
│    Pedido    │
├──────────────┤
│ data         │
│ valor        │
├──────────────┤
│ calcular()   │
└──────────────┘
```

---

# 4. Diagrama de Sequência

**Serve para:** mostrar a **ordem das interações** entre objetos/componentes.

É muito útil para entender uma funcionalidade passo a passo.

**Pergunta que responde:**

> "O que acontece primeiro, depois e depois?"

Exemplo:

```text
Cliente → Sistema: fazer login
Sistema → Banco: consultar usuário
Banco → Sistema: usuário encontrado
Sistema → Cliente: login realizado
```

---

# 5. Diagrama de Atividade

**Serve para:** representar um **fluxo de trabalho ou processo**.

É parecido com um fluxograma.

Pode representar:

* Decisões
* Condições
* Atividades
* Fluxos
* Processos paralelos

**Pergunta que responde:**

> "Qual é o fluxo desse processo?"

Exemplo:

```text
[Início]
   ↓
Informar dados
   ↓
Validar dados
   ↓
   ┌───────────────┐
   │ Dados válidos?│
   └───────┬───────┘
       Sim │ Não
           ↓
      Continuar
           │
           ↓
         [Fim]
```

---

# 6. Diagrama de Estados

**Serve para:** mostrar como algo muda de **estado ao longo do tempo**.

É muito usado quando uma entidade possui vários estados possíveis.

Exemplo de pedido:

```text
[Novo]
   ↓
[Pagamento aprovado]
   ↓
[Em preparação]
   ↓
[Enviado]
   ↓
[Entregue]
```

**Pergunta que responde:**

> "Em que estado esse objeto pode estar e como ele muda?"

---

# 7. Diagrama de Componentes

**Serve para:** mostrar a organização dos **componentes de software**.

Pode representar:

* APIs
* Serviços
* Módulos
* Bibliotecas
* Sistemas externos
* Dependências

Exemplo:

```text
[Frontend]
     │
     ▼
[API]
 ┌───┼────────┐
 ▼   ▼        ▼
Auth Pedidos Pagamentos
 │     │        │
 └─────┴────────┘
        ↓
    [Banco de Dados]
```

**Pergunta que responde:**

> "Quais são as grandes partes do software e como elas dependem umas das outras?"

---

# 8. Diagrama de Implantação (Deployment)

**Serve para:** representar a **infraestrutura onde o sistema roda**.

Mostra coisas como:

* Servidores
* Containers
* Dispositivos
* Bancos de dados
* Aplicações
* Conexões de rede

Exemplo:

```text
[Celular]
    │
    ▼
[Servidor Web]
    │
    ▼
[API]
    │
    ▼
[Database Server]
```

**Pergunta que responde:**

> "Onde cada parte do sistema está sendo executada?"

---

# 9. Diagrama de Objetos

**Serve para:** mostrar uma **fotografia da estrutura do sistema em determinado momento**.

Enquanto o diagrama de classes mostra:

> "Existe uma classe Cliente."

O diagrama de objetos mostra:

> "Existe o cliente João, com email X."

É mais concreto que o diagrama de classes.

---

# 10. Diagrama de Pacotes

**Serve para:** organizar elementos do sistema em **grupos/pacotes**.

Exemplo:

```text
┌─────────────────────┐
│       Sistema       │
│                     │
│ ┌───────┐ ┌───────┐ │
│ │ Usuário│ │Pedido │ │
│ └───────┘ └───────┘ │
│                     │
│ ┌─────────┐         │
│ │Pagamento│         │
│ └─────────┘         │
└─────────────────────┘
```

**Pergunta que responde:**

> "Como o sistema está organizado em módulos?"

---

# 11. Diagrama de Comunicação

**Serve para:** mostrar como os objetos **trocam mensagens**.

É parecido com o diagrama de sequência, mas o foco está mais nas **relações entre os objetos** do que na linha do tempo.

**Pergunta que responde:**

> "Quais objetos conversam entre si?"

---

# 12. Diagrama ER / DER — Entidade-Relacionamento

Não é UML, mas é **muito importante para sistemas e bancos de dados**.

**Serve para:** modelar a estrutura dos dados.

Mostra:

* Entidades
* Atributos
* Relacionamentos
* Cardinalidade

Exemplo:

```text
CLIENTE
   │
   │ 1:N
   ▼
PEDIDO
   │
   │ N:N
   ▼
PRODUTO
```

**Pergunta que responde:**

> "Como os dados do sistema se relacionam?"

---

# 13. Diagrama de Fluxo / Fluxograma

**Serve para:** representar visualmente um **processo passo a passo**.

É mais geral que UML e pode ser usado para praticamente qualquer processo.

Exemplo:

```text
Início
  ↓
Receber pedido
  ↓
Pagamento aprovado?
 ┌──────┴──────┐
Não           Sim
 ↓              ↓
Cancelar      Processar
                 ↓
                Fim
```

**Pergunta que responde:**

> "Qual é o caminho que esse processo percorre?"

---

# 14. Diagrama de Arquitetura

Não é necessariamente um único padrão formal como UML. É um termo geral para diagramas que representam a **arquitetura de um sistema**.

Pode mostrar:

* Frontend
* Backend
* APIs
* Microsserviços
* Bancos
* Filas
* Cache
* Serviços externos
* Cloud
* Redes

Exemplo:

```text
          ┌──────────┐
          │ Frontend │
          └────┬─────┘
               ↓
          ┌──────────┐
          │   API    │
          └────┬─────┘
          ┌────┴─────┐
          ↓          ↓
    ┌──────────┐ ┌────────┐
    │ Backend  │ │  Cache │
    └────┬─────┘ └────────┘
         ↓
    ┌──────────┐
    │ Database │
    └──────────┘
```

**Pergunta que responde:**

> "Como as grandes partes do sistema estão organizadas?"

---

# 15. Diagrama de Contexto

**Serve para:** mostrar o sistema de forma **bem ampla**, colocando o sistema no centro e mostrando o que interage com ele.

Exemplo:

```text
              [Cliente]
                  │
                  ▼
[Pagamento] → [ SISTEMA ] ← [Administrador]
                  │
                  ▼
             [Sistema externo]
```

**Pergunta que responde:**

> "O que existe ao redor do sistema e com quem ele interage?"

---

# 16. C4 Model

O **C4** é uma abordagem para representar arquitetura de software em diferentes níveis de zoom.

Os quatro níveis principais são:

### C1 — Context

Visão geral do sistema e seu ambiente.

### C2 — Container

Principais aplicações/serviços dentro do sistema.

### C3 — Component

Componentes internos de uma aplicação/serviço.

### C4 — Code

Detalhamento no nível de código/classes.

**Ideia principal:**

```text
C1 → Sistema inteiro
 ↓
C2 → Aplicações/serviços
 ↓
C3 → Componentes
 ↓
C4 → Código
```

**Pergunta que responde:**

> "Como posso explicar a arquitetura do sistema do mais geral ao mais detalhado?"

---

# 🧠 Cola mental

Se quiser lembrar **quando usar cada um**, pense assim:

| Quero entender...          | Use principalmente...       |
| -------------------------- | --------------------------- |
| O que o sistema faz?       | **Caso de Uso**             |
| Quem usa o sistema?        | **Caso de Uso**             |
| Estrutura das classes      | **Classes**                 |
| Como objetos conversam     | **Sequência / Comunicação** |
| Fluxo de um processo       | **Atividade / Fluxograma**  |
| Estados de uma entidade    | **Estados**                 |
| Módulos/componentes        | **Componentes**             |
| Organização do código      | **Pacotes**                 |
| Infraestrutura             | **Deployment**              |
| Banco de dados             | **DER / ER**                |
| Arquitetura geral          | **Arquitetura / C4**        |
| Sistema e ambiente externo | **Contexto / C4 C1**        |

---
