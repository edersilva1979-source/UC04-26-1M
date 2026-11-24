# 🐾 Trabalho Final de Programação Orientada a Objetos com TypeScript

# Sistema de PetShop e Clínica Veterinária com MVC

---

# 🎯 Objetivo do Trabalho

Neste trabalho final, eu quero que vocês utilizem os principais conhecimentos desenvolvidos durante o curso de Programação Orientada a Objetos com TypeScript.

Vocês deverão criar um sistema simples para um PetShop e uma Clínica Veterinária.

O sistema deverá ser organizado utilizando o padrão MVC.

Nesta versão, não utilizaremos:

```text
Arrays

Menu no terminal

readline-sync

Banco de dados

Arquivos JSON
```

Os objetos serão criados diretamente no arquivo `main.ts`.

O objetivo principal não será criar um sistema grande.

O objetivo será demonstrar que você compreendeu como organizar classes, métodos, relacionamentos entre objetos e responsabilidades dentro do MVC.

---

# 📚 Conteúdos que Devem Ser Utilizados

O trabalho deverá envolver os seguintes conteúdos:

```text
TypeScript

Classes

Objetos

Construtores

Atributos

Métodos

Encapsulamento

Associação entre objetos

Composição

Import e export

Separação em arquivos

Organização em pastas

MVC simplificado

Validação de dados

Cálculos

Regras de negócio
```

---

# 🏥 Cenário do Sistema

O PetShop atende clientes que possuem animais de estimação.

Cada atendimento veterinário deverá registrar:

```text
O cliente responsável pelo animal

O animal atendido

O veterinário responsável

O tipo de serviço realizado

A data do atendimento

O valor do atendimento

A situação do atendimento
```

O sistema também deverá permitir:

```text
Cadastrar um cliente

Cadastrar um animal

Cadastrar um veterinário

Cadastrar um serviço

Realizar um atendimento

Finalizar um atendimento

Cancelar um atendimento

Calcular o valor total

Exibir um resumo completo
```

---

# 📁 Estrutura Obrigatória do Projeto

Organize o projeto da seguinte forma:

```text
PetShopVet4Patas

├── src
│
│   ├── model
│   │   ├── Cliente.ts
│   │   ├── Animal.ts
│   │   ├── Veterinario.ts
│   │   ├── Servico.ts
│   │   └── Atendimento.ts
│
│   ├── controller
│   │   └── AtendimentoController.ts
│
│   ├── view
│   │   └── AtendimentoView.ts
│
│   └── main.ts
│
├── package.json
└── tsconfig.json
```

---

# 🧱 Responsabilidade de Cada Parte

## Model

A pasta `model` deverá representar os objetos principais do sistema.

Ela deverá conter:

```text
Cliente

Animal

Veterinario

Servico

Atendimento
```

## Controller

A pasta `controller` deverá controlar as ações do sistema.

O Controller deverá:

```text
Criar os objetos

Validar os dados

Realizar o atendimento

Finalizar o atendimento

Cancelar o atendimento

Retornar os objetos para a View
```

## View

A pasta `view` deverá exibir as informações no terminal utilizando `console.log()`.

A View deverá:

```text
Exibir o cliente

Exibir o animal

Exibir o veterinário

Exibir o serviço

Exibir o atendimento

Exibir mensagens de sucesso ou erro
```

## main.ts

O arquivo `main.ts` deverá:

```text
Criar o Controller

Criar a View

Cadastrar os objetos diretamente

Realizar o atendimento

Exibir os resultados

Testar finalização ou cancelamento
```

---

# 👤 Classe Cliente

Crie a classe:

```text
Cliente
```

Ela deverá possuir os seguintes atributos:

```text
id

nome

cpf

telefone

email
```

## Requisitos

O construtor deverá receber todas as informações.

O CPF, telefone e email deverão ser do tipo `string`.

Exemplo:

```typescript
const cliente = new Cliente(
    1,
    "Mariana Souza",
    "123.456.789-00",
    "(51) 99999-9999",
    "mariana@email.com"
);
```

---

# 🐶 Classe Animal

Crie a classe:

```text
Animal
```

Ela deverá possuir:

```text
id

nome

especie

raca

idade

peso

dono
```

O atributo `dono` deverá ser do tipo:

```typescript
Cliente
```

Isso significa que o animal estará associado a um cliente.

Exemplo:

```typescript
const animal = new Animal(
    1,
    "Thor",
    "Cachorro",
    "Golden Retriever",
    4,
    32.5,
    cliente
);
```

---

# 👩‍⚕️ Classe Veterinario

Crie a classe:

```text
Veterinario
```

Ela deverá possuir:

```text
id

nome

crmv

especialidade
```

Exemplo:

```typescript
const veterinario = new Veterinario(
    1,
    "Dra. Camila Martins",
    "CRMV-RS 12345",
    "Clínica Geral"
);
```

---

# 🩺 Classe Servico

Crie a classe:

```text
Servico
```

Ela deverá possuir:

```text
id

descricao

valor

duracaoMinutos
```

Exemplos de serviços:

```text
Consulta veterinária

Vacinação

Banho

Tosa

Exame clínico

Aplicação de medicamento
```

Exemplo:

```typescript
const servico = new Servico(
    1,
    "Consulta veterinária",
    150,
    40
);
```

---

# 📋 Classe Atendimento

A classe `Atendimento` será a classe principal do trabalho.

Ela deverá reunir:

```text
Cliente

Animal

Veterinario

Servico

Data do atendimento
```

Crie os seguintes atributos:

```text
id

cliente

animal

veterinario

servico

dataAtendimento

observacoes

finalizado

cancelado
```

Os atributos `finalizado` e `cancelado` deverão iniciar como `false`.

Exemplo de construtor:

```typescript
constructor(
    public id: number,
    public cliente: Cliente,
    public animal: Animal,
    public veterinario: Veterinario,
    public servico: Servico,
    public dataAtendimento: string,
    public observacoes: string,
    private finalizado: boolean = false,
    private cancelado: boolean = false
) {}
```

---

# 🧠 Métodos Obrigatórios da Classe Atendimento

## calcularValorTotal()

Crie o método:

```typescript
calcularValorTotal(): number
```

Neste primeiro momento, ele deverá retornar o valor do serviço.

Exemplo:

```typescript
return this.servico.valor;
```

## foiFinalizado()

Crie o método:

```typescript
foiFinalizado(): boolean
```

Ele deverá retornar o valor do atributo `finalizado`.

## foiCancelado()

Crie o método:

```typescript
foiCancelado(): boolean
```

Ele deverá retornar o valor do atributo `cancelado`.

## finalizar()

Crie o método:

```typescript
finalizar(): boolean
```

Regras:

```text
Não pode finalizar um atendimento já finalizado

Não pode finalizar um atendimento cancelado

Se tudo estiver correto, finalizado deverá receber true
```

O método deverá retornar:

```text
true em caso de sucesso

false em caso de erro
```

## cancelar()

Crie o método:

```typescript
cancelar(): boolean
```

Regras:

```text
Não pode cancelar um atendimento já cancelado

Não pode cancelar um atendimento já finalizado

Se tudo estiver correto, cancelado deverá receber true
```

## consultarSituacao()

Crie o método:

```typescript
consultarSituacao(): string
```

Ele deverá retornar:

```text
Cancelado

Finalizado

Em andamento
```

Exemplo de regra:

```typescript
if (this.cancelado) {
    return "Cancelado";
}

if (this.finalizado) {
    return "Finalizado";
}

return "Em andamento";
```

---

# 🎮 Controller

Crie o arquivo:

```text
src/controller/AtendimentoController.ts
```

A classe deverá guardar apenas um objeto de cada tipo:

```typescript
private cliente: Cliente | null = null;

private animal: Animal | null = null;

private veterinario: Veterinario | null = null;

private servico: Servico | null = null;

private atendimento: Atendimento | null = null;
```

Isso acontece porque nesta versão não utilizaremos arrays.

---

# 🧩 Métodos Obrigatórios do Controller

## cadastrarCliente()

```typescript
cadastrarCliente(
    id: number,
    nome: string,
    cpf: string,
    telefone: string,
    email: string
): Cliente
```

## cadastrarAnimal()

```typescript
cadastrarAnimal(
    id: number,
    nome: string,
    especie: string,
    raca: string,
    idade: number,
    peso: number
): Animal | null
```

Esse método deverá verificar se existe um cliente cadastrado.

Sem cliente, não será possível criar o animal.

## cadastrarVeterinario()

```typescript
cadastrarVeterinario(
    id: number,
    nome: string,
    crmv: string,
    especialidade: string
): Veterinario
```

## cadastrarServico()

```typescript
cadastrarServico(
    id: number,
    descricao: string,
    valor: number,
    duracaoMinutos: number
): Servico | null
```

O método deverá retornar `null` se:

```text
O valor for menor ou igual a zero

A duração for menor ou igual a zero

A descrição estiver vazia
```

## realizarAtendimento()

```typescript
realizarAtendimento(
    id: number,
    dataAtendimento: string,
    observacoes: string
): Atendimento | null
```

Antes de criar o atendimento, o Controller deverá verificar se existem:

```text
Cliente

Animal

Veterinário

Serviço
```

Se algum deles não existir, o atendimento não poderá ser criado.

## finalizarAtendimento()

```typescript
finalizarAtendimento(): boolean
```

Esse método deverá chamar:

```typescript
this.atendimento.finalizar();
```

## cancelarAtendimento()

```typescript
cancelarAtendimento(): boolean
```

Esse método deverá chamar:

```typescript
this.atendimento.cancelar();
```

## Métodos de consulta

Crie também:

```typescript
obterCliente(): Cliente | null

obterAnimal(): Animal | null

obterVeterinario(): Veterinario | null

obterServico(): Servico | null

obterAtendimento(): Atendimento | null
```

---

# 🖥️ View

Crie o arquivo:

```text
src/view/AtendimentoView.ts
```

A View deverá possuir os seguintes métodos:

```typescript
exibirTitulo(): void

exibirCliente(cliente: Cliente): void

exibirAnimal(animal: Animal): void

exibirVeterinario(veterinario: Veterinario): void

exibirServico(servico: Servico): void

exibirAtendimento(atendimento: Atendimento): void

exibirMensagem(mensagem: string): void
```

---

# 🖼️ Exemplo de Saída da View

```text
============================================
🐾 PETSHOP E CLÍNICA VETERINÁRIA 4Patas 🐾
============================================

👤 CLIENTE
Nome: Mariana Souza
CPF: 123.456.789-00
Telefone: (51) 99999-9999
Email: mariana@email.com
-------------------------------------

🐶 ANIMAL
Nome: Thor
Espécie: Cachorro
Raça: Golden Retriever
Idade: 4 anos
Peso: 32.5 kg
Dono: Mariana Souza
-------------------------------------

👩‍⚕️ VETERINÁRIO
Nome: Dra. Camila Martins
CRMV: CRMV-RS 12345
Especialidade: Clínica Geral
-------------------------------------

🩺 SERVIÇO
Descrição: Consulta veterinária
Valor: R$ 150.00
Duração: 40 minutos
-------------------------------------

📋 ATENDIMENTO
Animal: Thor
Cliente: Mariana Souza
Veterinário: Dra. Camila Martins
Serviço: Consulta veterinária
Data: 22/07/2026
Observações: Animal apresentou falta de apetite.
Valor total: R$ 150.00
Situação: Em andamento
-------------------------------------
```

---

# 🚀 Arquivo main.ts

No arquivo `main.ts`, crie diretamente os objetos utilizando o Controller.

Exemplo de sequência:

```typescript
const controller =
    new AtendimentoController();

const view =
    new AtendimentoView();

view.exibirTitulo();

const cliente =
    controller.cadastrarCliente(
        1,
        "Mariana Souza",
        "123.456.789-00",
        "(51) 99999-9999",
        "mariana@email.com"
    );

const animal =
    controller.cadastrarAnimal(
        1,
        "Thor",
        "Cachorro",
        "Golden Retriever",
        4,
        32.5
    );

const veterinario =
    controller.cadastrarVeterinario(
        1,
        "Dra. Camila Martins",
        "CRMV-RS 12345",
        "Clínica Geral"
    );

const servico =
    controller.cadastrarServico(
        1,
        "Consulta veterinária",
        150,
        40
    );
```

Depois crie o atendimento:

```typescript
const atendimento =
    controller.realizarAtendimento(
        1,
        "2026-07-22",
        "Animal apresentou falta de apetite."
    );
```

Mostre os objetos pela View.

Depois teste:

```typescript
controller.finalizarAtendimento();
```

ou:

```typescript
controller.cancelarAtendimento();
```

---

# ⚠️ Regras Importantes

O sistema deverá respeitar as seguintes regras:

```text
Não criar animal sem cliente

Não criar serviço com valor inválido

Não realizar atendimento sem todos os objetos necessários

Não finalizar atendimento cancelado

Não cancelar atendimento finalizado

Não utilizar console.log dentro do Controller

Não criar objetos dentro da View

Não colocar regras de negócio no main.ts
```

---

# 🧠 Desafios extras

## Desafio 1

Adicione o atributo:

```text
sexo
```

na classe Animal.

Atualize:

```text
Model

Controller

View

main.ts
```

## Desafio 2

Adicione o atributo:

```text
telefoneEmergencia
```

na classe Veterinario.

## Desafio 3

Adicione o método:

```typescript
calcularValorComDesconto(
    percentual: number
): number
```

na classe Atendimento.

## Desafio 4

Crie um método:

```typescript
alterarObservacoes(
    novaObservacao: string
): void
```

---

# 🏆 Desafio Final

Acrescente uma classe chamada:

```text
Pagamento
```

Ela deverá possuir:

```text
formaPagamento

valorPago

dataPagamento

pago
```

A classe `Atendimento` deverá possuir um objeto `Pagamento`.

Regras:

```text
O atendimento só poderá ser finalizado após o pagamento

O valor pago não poderá ser menor que o valor do atendimento

O pagamento deverá possuir um método confirmarPagamento()
```

---

# 📋 Critérios de Avaliação

O trabalho poderá ser avaliado pelos seguintes critérios:

```text
Organização das pastas

Uso correto do MVC

Uso de import e export

Criação correta das classes

Uso de construtores

Uso de métodos

Uso de encapsulamento

Relacionamento entre objetos

Validação das regras

Código organizado

Nomes claros

Funcionamento do main.ts

Apresentação no terminal
```

---

# ✅ Checklist de Entrega

Antes de entregar, confirme se:

```text
O projeto compila

Todos os imports estão corretos

Todas as classes estão em arquivos separados

O MVC está organizado

A View mostra os resultados

O Controller controla as ações

Os Models possuem as regras

O main.ts executa os testes

Nenhum array foi utilizado

Nenhum menu foi utilizado

Nenhuma entrada pelo terminal foi utilizada
```

---

# 📚 Resultado Esperado

Ao final do trabalho, você deverá ter um sistema simples, organizado e funcional de PetShop e Clínica Veterinária.

O sistema deverá demonstrar que você compreendeu como:

```text
Representar objetos reais com classes

Relacionar objetos

Aplicar regras de negócio

Separar responsabilidades

Organizar um projeto com MVC
```

Boa programação! 🐾💻🏥
