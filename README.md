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

---

## 🤝 Contribuição
Contribuições são bem-vindas! Sinta-se à vontade para abrir um *pull request* ou relatar problemas no repositório.

---

<div style="text-align: center; margin-top: 20px;">
    <em>Desenvolvido com ❤ pelo Time de Validação de Cartões.</em>
</div>
