# Banco de Dados de Eventos Culturais em Recife 🎉

**Universidade Federal de Pernambuco**  
Centro de Informática - CIn  
Disciplina: Banco de Dados [IF976SI]  
Docente: Luiz Augusto Morais 📚  

---

## 🏆 Visão Geral

O presente estudo aborda o tema **"Banco de Dados de Eventos Culturais em Recife: Pagos e Gratuitos"** 🎭. O objetivo principal é desenvolver um sistema que centralize informações sobre eventos culturais em Recife, oferecendo aos usuários uma plataforma eficiente para encontrar e acessar eventos, sejam eles pagos ou gratuitos. A intenção é melhorar a divulgação e o acesso a eventos culturais, facilitando a busca e a organização das informações para o público e organizadores de eventos.

Atualmente, as informações sobre eventos culturais estão dispersas em diversas plataformas como Sympla, Ingressos.com e ConectaRecife. O projeto **RecifeEventsMap** visa integrar essas informações em uma única plataforma, aprimorando a experiência do usuário e proporcionando uma visão abrangente do panorama cultural da cidade. A RecifeEventsMap se dedicará exclusivamente à divulgação de eventos, não à comercialização de ingressos.

A plataforma não requer que os usuários criem contas, evitando a retenção de dados pessoais. As informações sobre eventos serão extraídas via APIs das plataformas de venda. Quando APIs não estiverem disponíveis, o administrador poderá adicionar eventos manualmente. A RecifeEventsMap catalogará uma variedade de eventos culturais e permitirá categorização específica, como gêneros musicais. 

---

## 📝 Requisitos do Sistema

- **Cadastro e Atualização de Eventos:** Extração e atualização automáticas das informações sobre eventos culturais através de APIs externas.
- **Consulta e Pesquisa de Eventos:** Pesquisa por tipo de evento, data, localização e categorias, com filtros avançados.
- **Exibição de Detalhes dos Eventos:** Exibição de informações detalhadas e links diretos para plataformas de venda.
- **Integração com APIs Externas:** Atualização contínua das informações através das APIs.
- **Acesso e Navegação do Usuário:** Acesso sem necessidade de login, com uma interface intuitiva.

---

## 🛠️ Modelagem

### Entidades

- **Evento:** Representa eventos culturais em Recife, incluindo:
  - **Evento Pago:** Eventos que exigem pagamento.
  - **Evento Gratuito:** Eventos sem custo.

- **Organizador:** Entidade ou pessoa responsável pela organização de eventos.

- **Local:** Local onde o evento é realizado.

- **Participante:** Pessoa que é atração ou artista no evento.

- **Ingresso:** Ingresso de um evento pago (entidade fraca).

- **Plataforma de Vendas:** Plataformas que vendem ingressos para os eventos.

### Atributos

- **Evento:**
  - `id_evento:` Identificador único, numérico
  - `nome_evento:` Texto
  - `descricao:` Texto
  - `data/hora_inicio:` Data
  - `data/hora_fim:` Data

- **Heranças:**
  - **Evento Pago:** Sem atributos adicionais.
  - **Evento Gratuito:** Sem atributos adicionais.

- **Plataforma de Venda:**
  - `ID:` Numérico, identificador
  - `nome:` Texto
  - `site:` Texto

- **Organizador:**
  - `id_organizador:` Identificador único, numérico
  - `telefone:` Atributo multivalorado
  - `email:` Atributo multivalorado
  - `nome:` Texto
  - `CNPJ:` Texto

- **Participante:**
  - `id_participante:` Identificador numérico
  - `nome:` Texto
  - `telefone:` Atributo multivalorado
  - `email:` Atributo multivalorado
  - `categoria:` Texto (ex: música, teatro)
  - `integrantes:` Texto

- **Local:**
  - `id_local:` Identificador único, numérico
  - `nome_local:` Texto
  - `endereco:` Atributo composto (rua, número, bairro, cidade, CEP)

- **Ingresso (Entidade Fraca):**
  - `preço:` Numérico

- **Atributo do Relacionamento Apresenta:**
  - `data_hora:` Data (Discriminador)

### Relacionamentos

- **Evento - Participante:** Muitos para Muitos (N:M) - Relacionamento **Apresenta**
- **Evento - Organizador:** Muitos para Um (N:1) - Relacionamento **Realiza**
- **Evento - Local:** Muitos para Um (N:1) - Relacionamento **Sedia**
- **Evento - Plataforma de Venda:** Muitos para Muitos (N:M) - Relacionamento **Tem**
- **Plataforma de Venda - Ingresso:** Muitos para Muitos (N:M) - Relacionamento **Contém**

### Modelo Conceitual

![Modelo Conceitual](https://github.com/GustavoDiego/Banco-de-dados/blob/readd-names/projeto_conceitual/mdconceitual.jpg?raw=true)

---

## Conceitos Utilizados 🧠

- **Atributo Composto:** Utilizado em Local (endereço com rua, número, bairro, cidade, CEP).
- **Atributo Multivalorado:** Participante e Organizador (contatos, categorias, integrantes, telefones, e-mails).
- **Atributo Discriminador em Relacionamento:** data/hora no relacionamento Apresenta.
- **Relacionamento (1:N):** Organizador-Evento, Local-Evento.
- **Relacionamento (N:M):** Evento-Participante, Evento-Plataforma de Venda, Plataforma de Venda-Ingresso.
- **Relacionamento Parcial-Total:** Evento-Participante, Organizador-Evento, Local-Evento, Plataforma de Venda-Ingresso.
- **Relacionamento Parcial-Parcial:** Evento-Plataforma de Venda.
- **Relacionamento Unário ou Auto Relacionamento:** Participante-Evento, Organizador-Evento, Local-Evento.
- **Relacionamento Identificador ou Entidade Fraca:** Ingresso depende da Plataforma de Venda.
- **Relacionamento Binário:** Plataforma de Venda-Evento-Ingresso.
- **Relacionamento N-ário:** Evento com Participante, Organizador, Local e Plataforma de Venda.
- **Herança:** Evento Pago e Evento Gratuito.

---

## 📸 Equipe

<table>
  <tr>
    <td align="center">
      <img src="https://avatars.githubusercontent.com/u/131917608?v=4" width="100px;" alt="Alberis"/><br />
      <b>Alberis</b><br />
    </td>
    <td align="center">
      <img src="https://avatars.githubusercontent.com/u/131917694?v=4" width="100px;" alt="Aldo Lemos"/><br />
      <b>Aldo Lemos</b><br />
    </td>
    <td align="center">
      <img src="https://avatars.githubusercontent.com/u/106412379?v=4" width="100px;" alt="Arlen"/><br />
      <b>Arlen</b><br />
    </td>
    <td align="center">
      <img src="https://avatars.githubusercontent.com/u/121072900?v=4" width="100px;" alt="Gustavo Diego"/><br />
      <b>Gustavo Diego</b><br />
       <td align="center">
      <img src="https://avatars.githubusercontent.com/u/131627751?v=4" width="100px;" alt="Hyan"/><br />
      <b>Hyan</b><br />
    </td>
    </td>
    <td align="center">
      <img src="https://avatars.githubusercontent.com/u/83255127?v=4" width="100px;" alt="Mariana Marinho"/><br />
      <b>Mariana Marinho</b><br />
    </td>
  </tr>
</table>

## 📄 Links Importantes

- **Slide de Apresentação:** [Acesse aqui](https://www.canva.com/design/DAGMZI-XY9w/ASRnqxPsQrhEXTYASQycgA/edit)
- **Relatório do Modelo Conceitual:** [Acesse aqui](https://docs.google.com/document/d/1LxW7YHrci9xnLmQZ7exMede7qmQTFSrv05TwC7iII4M/edit)
