# 🛡️ Validação de Cartão

<div style="text-align: center; margin-bottom: 20px;">
    <img src="https://upload.wikimedia.org/wikipedia/commons/6/65/Credit_or_Debit_Card_Flat_Icon_Vector.svg" alt="Ícone de cartão" width="120">
</div>

## Sobre o Projeto
Este projeto é um sistema para validação de cartões de crédito. Ele permite verificar:

- **A bandeira do cartão**: Identifica a bandeira com base no número inserido.
- **Validade do cartão**: Confirma se a data de validade informada ainda é válida.
- **Cartões aceitos**: Informa se a bandeira do cartão é aceita pelo sistema.

---

## 🗂️ Estrutura do Arquivo

### `index.html`
Este é o arquivo principal que contém a estrutura HTML da aplicação e os estilos básicos.

### Componentes

1. **📝 Nome no Cartão**
   - Campo de texto para o usuário inserir o nome impresso no cartão.

2. **💳 Número do Cartão**
   - Campo de texto que identifica a bandeira automaticamente ao inserir o número do cartão.

3. **📅 Data de Validade (MM/AA)**
   - Campo para verificar se o cartão está vencido. A verificação é feita ao sair do campo (evento `onblur`).

4. **🔒 Código CVV**
   - Campo de texto para inserção do código de segurança do cartão.

5. **🌍 Exibição da Bandeira**
   - Uma seção dinâmica que exibe o ícone da bandeira do cartão ou uma mensagem de erro se o cartão não for reconhecido.

---

## 🚀 Script JavaScript

### 📋 Regras de Validação
Cada bandeira de cartão é identificada por meio de expressões regulares:

- **MasterCard**: `^(5[1-5]|222[1-9]|22[3-9]\d|2[3-6]\d{2}|27[01]\d|2720)`
- **Visa**: `^4`
- **American Express**: `^(34|37)`
- **Diners Club**: `^3(?:0[0-5]|[68][0-9])[0-9]{11,12}$`
- **Discover**: `^(6011|65|64[4-9])`
- **EnRoute**: `^(2014|2149)`
- **JCB**: `^(?:2131|1800|35\d{3})\d{11}$`
- **Voyager**: `^8699`
- **Hipercard**: `^6062`
- **Aura**: `^50`
- **Elo**: `^(4011|4312|4389)`

### 🔧 Funções

- **`validarCartao(numeroCartao)`**
  - Recebe o número do cartão e retorna o nome da bandeira ou `null` se a bandeira não for reconhecida.

- **`atualizarBandeira()`**
  - Atualiza a exibição da bandeira do cartão com base no número inserido no campo.

- **`verificarValidade()`**
  - Valida se a data de validade do cartão é válida e não está vencida. Caso esteja vencida, exibe um alerta.

### 🎨 Exibição Dinâmica
Os ícones das bandeiras são carregados dinamicamente a partir de URLs.

---

## ✨ Estilo
O projeto utiliza estilos básicos para uma experiência limpa e amigável. O layout é responsivo, ajustando-se automaticamente a diferentes tamanhos de tela.

---

## 📖 Como Usar

1. Abra o arquivo `index.html` em um navegador.
2. Insira os dados do cartão:
   - Nome no cartão.
   - Número do cartão para identificar a bandeira.
   - Data de validade no formato `MM/AA`.
   - Código CVV.
3. O sistema validará automaticamente a bandeira e a validade do cartão.

---

## 🛠️ Tecnologias Utilizadas

- **HTML5**: Estrutura básica da página.
- **CSS3**: Estilo e layout.
- **JavaScript**: Lógica de validação e interatividade.

---

## 🔮 Melhorias Futuras

- Adicionar suporte a mais bandeiras de cartão.
- Implementar uma validação completa do número do cartão com o algoritmo de Luhn.
- Disponibilizar uma interface mais avançada com mensagens de erro detalhadas.
- Suporte multilíngue.
- Criação de testes automatizados para garantir a confiabilidade das validações.
- Disponibilização de uma API REST para validação de cartões, permitindo integração com outros sistemas.
- Inclusão de um sistema de logs para monitorar tentativas de validação e possíveis erros.

---

## 🔍 Exemplos de Uso

### Validação de um Cartão MasterCard
- Número: `5555555555554444`
- Bandeira exibida: MasterCard

### Exemplo de Cartão Vencido
- Data: `01/22`
- Mensagem: "Cartão vencido!"

### Exemplo de Bandeira Não Suportada
- Número: `9999999999999999`
- Mensagem: "Bandeira não reconhecida!"

---

## 🏗️ Arquitetura do Sistema

A aplicação segue uma arquitetura simples, baseada em arquivos estáticos:

- **Frontend**: Responsável pela interação com o usuário, implementado em HTML, CSS e JavaScript puro.
- **Validação Dinâmica**: A lógica de validação é inteiramente implementada no navegador do usuário, sem necessidade de backend.
- **Futuro Backend (planejado)**: Para suportar a API REST e integração com outros sistemas, será implementado um backend utilizando Node.js ou Python.

---

## 📚 Referências e Recursos

- [Documentação Oficial do Algoritmo de Luhn](https://en.wikipedia.org/wiki/Luhn_algorithm)
- [Regexr](https://regexr.com/) para testar expressões regulares.
- Ícones gratuitos obtidos de [Flaticon](https://www.flaticon.com/).
- Recursos sobre desenvolvimento web em [MDN Web Docs](https://developer.mozilla.org/).

---

## ❓ Perguntas Frequentes (FAQ)

### 1. O sistema suporta cartões emitidos fora do Brasil?
Sim, desde que a bandeira seja reconhecida pelo sistema.

### 2. É necessário internet para usar o sistema?
Não. A aplicação funciona localmente, mas os ícones de bandeira podem exigir conexão para carregamento.

### 3. Quais navegadores são compatíveis?
Os principais navegadores modernos, como Chrome, Firefox, Edge e Safari, são suportados.

### 4. Posso adicionar novas bandeiras manualmente?
Sim. Basta atualizar o script JavaScript com a expressão regular correspondente e adicionar o ícone na pasta apropriada.

---

## 🤝 Contribuição
Contribuições são bem-vindas! Sinta-se à vontade para abrir um *pull request* ou relatar problemas no repositório.

---

<div style="text-align: center; margin-top: 20px;">
    <em>Desenvolvido com ❤ pelo Time de Validação de Cartões.</em>
</div>
