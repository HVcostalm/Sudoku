# Sudoku em Java

Um jogo de **Sudoku no terminal** desenvolvido em **Java** para consolidar conhecimentos em **Programação Orientada a Objetos**, manipulação de estruturas de dados, organização por classes/métodos e interação via **entrada/saída no console**.

> Repositório: `HVcostalm/Sudoku`  
> Linguagem: **Java**  
> Licença: **MIT**

---

## Sumário

- [Visão geral](#visão-geral)
- [Funcionalidades](#funcionalidades)
- [Como executar](#como-executar)
  - [Pré-requisitos](#pré-requisitos)
  - [Executando pelo IntelliJ IDEA](#executando-pelo-intellij-idea)
  - [Executando via terminal (javac/java)](#executando-via-terminal-javacjava)
  - [Argumentos (geração do tabuleiro)](#argumentos-geração-do-tabuleiro)
- [Como jogar (no terminal)](#como-jogar-no-terminal)
- [Estrutura do projeto](#estrutura-do-projeto)
- [Roadmap](#roadmap)
- [Licença](#licença)

---

## Visão geral

O jogo é inicializado com um tabuleiro (com casas fixas e casas editáveis). A interação acontece por um menu no terminal, permitindo:

- iniciar um novo jogo
- inserir/remover números
- visualizar o estado atual do tabuleiro
- checar status do jogo e se existem erros
- limpar o progresso
- finalizar o jogo quando estiver completo

A entrada para inserir números é no formato **coluna/linha/valor**, por exemplo: `2 1 5`.

---

## Funcionalidades

- Menu interativo no terminal
- Tabuleiro 9x9
- Casas **fixas** (não podem ser alteradas) e casas livres
- Inserção e remoção de valores
- Visualização do tabuleiro formatada (template)
- Verificação de status do jogo e detecção de erros
- Finalização com validação (completo/contém erros/ainda incompleto)

---

## Como executar

### Pré-requisitos

- **Java JDK** instalado (recomendado JDK 17+; qualquer versão compatível com o código deve funcionar)
- (Opcional) IntelliJ IDEA para rodar com configurações de “Run/Debug”

---

### Executando pelo IntelliJ IDEA

1. Abra o projeto no IntelliJ.
2. Encontre a classe principal:
   - `src/br/com/sudoku/Main.java`
3. Abra a configuração de execução (Run Configuration) e adicione os **Program arguments** (veja a seção [Argumentos](#argumentos-geração-do-tabuleiro)).
4. Execute a classe `Main`.

---

### Executando via terminal (javac/java)

A estrutura não é Maven/Gradle; então você pode compilar e rodar manualmente.

**1) Compilar**
```bash
javac -d out $(find src -name "*.java")
```

**2) Executar (com argumentos do tabuleiro)**
```bash
java -cp out br.com.sudoku.Main <ARGUMENTOS_AQUI>
```

> Dica: os argumentos são muitos. Vale a pena colar tudo em uma única linha, ou usar um script para facilitar.

---

### Argumentos (geração do tabuleiro)

O tabuleiro inicial é montado a partir de argumentos passados para o programa.

No `Main.java` existe um exemplo comentado de como fornecer os argumentos.

Cada argumento segue o formato:

```
linha,coluna;valor,fixed
```

- `linha,coluna` vai de `0` a `8`
- `valor` é o valor esperado/inicial da casa
- `fixed` indica se a casa é fixa (`true`) ou editável (`false`)

Exemplo de argumento (apenas para ilustrar):
```
0,0;4,false
```

> Observação: para iniciar corretamente o tabuleiro, é necessário que existam configurações para todas as posições `9x9` (81 casas), no formato esperado.

---

## Como jogar (no terminal)

Ao iniciar, o programa mostra um menu como:

- `1 - Iniciar um novo Jogo`
- `2 - Colocar um novo número`
- `3 - Remover um número`
- `4 - Visualizar jogo atual`
- `5 - Verificar status do jogo`
- `6 - limpar jogo`
- `7 - Finalizar jogo`
- `8 - Sair`

### Inserir número

Escolha a opção **2** e informe:

1. **coluna** (0 a 8)
2. **linha** (0 a 8)
3. **valor** (1 a 9)

Exemplo de entrada:
```
coluna: 2
linha: 1
valor: 5
```

Se a casa for fixa, o jogo avisa que não é possível alterar.

### Remover número

Escolha a opção **3** e informe:

1. **coluna** (0 a 8)
2. **linha** (0 a 8)

Se a casa for fixa, o jogo avisa que não é possível limpar.

### Ver status / finalizar

- Opção **5** mostra o status atual e indica se o tabuleiro contém erros.
- Opção **7** tenta finalizar: se estiver completo e correto, parabeniza; se houver erros ou estiver incompleto, informa o motivo.

---

## Estrutura do projeto

Principais arquivos/pacotes:

- `src/br/com/sudoku/Main.java`  
  Ponto de entrada do programa e menu do terminal.

- `src/br/com/sudoku/model/Board.java`  
  Modelo do tabuleiro e regras/operações (alterar valores, reset, status, validações).

- `src/br/com/sudoku/model/Space.java`  
  Representa cada “casa” do Sudoku (valor esperado, valor atual, se é fixa).

- `src/br/com/sudoku/model/GameStatusEnum.java`  
  Enum para status do jogo.

- `src/br/com/sudoku/util/BoardTemplate.java`  
  Template de impressão do tabuleiro no terminal.

---

## Roadmap

Ideias para evolução do projeto:

- [ ] Melhorar UX do terminal (mensagens, validações, comandos mais rápidos)
- [ ] Carregar tabuleiros a partir de arquivo (ex.: `.txt`, `.json`)
- [ ] Adicionar gerador de Sudoku (diferentes dificuldades)
- [ ] Adicionar resolvedor/validador (dicas/hints)
- [ ] Criar interface gráfica:
  - [ ] **Swing** (recomendado para começar) ou **AWT**
  - [ ] Separar camadas (UI vs regras) para reaproveitar o `model` atual

---

## Licença

Distribuído sob a licença **MIT**. Veja o arquivo [LICENSE](LICENSE) para mais detalhes.
