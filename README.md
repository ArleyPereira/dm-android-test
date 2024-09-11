# Comentários sobre o Projeto

## Bugs Identificados

1. **Tela Inicial sem Scroll**  
   **Descrição**: A tela inicial não permite rolagem, impossibilitando a visualização de todo o conteúdo em dispositivos menores.  
   **Solução**: Adicionar `verticalScroll(rememberScrollState())` na `Column` que estrutura a tela.

2. **Erro de Nome de Função no `CouponRepositoryTest`**  
   **Descrição**: O arquivo `CouponRepositoryTest` utiliza a função `loadCupons()`, enquanto a função correta no código é `lodCupons()`.  
   **Solução**: Ajustar o nome da função `lodCupons` para `loadCupons` no arquivo `CouponRepository` e em todos os locais onde essa função é utilizada. Outra opção é utilizar a ferramenta de refatoração do Android Studio para realizar essa mudança de forma automática e segura.

---

## Melhorias Sugeridas

1. **Utilização de `LazyColumn` para Listagens**  
   Em vez de utilizar uma `Column` para listar os cupons, é recomendável usar `LazyColumn`, já que ela carrega apenas os itens visíveis na tela, melhorando o desempenho com grandes volumes de dados.

2. **Separar Função `CouponList` em um Arquivo Próprio**  
   Mover a função `CouponList` para um arquivo separado aumenta a modularização e melhora a legibilidade do código.

3. **Implementação de um `ViewModel`**  
   Criar um `ViewModel` para gerenciar o estado da tela, a origem dos dados e as interações do usuário, separando a lógica de negócios da interface de usuário.

4. **Criar Componente `CouponItem` em Arquivo Separado**  
   Criar um arquivo dedicado para o componente `CouponItem`, o que melhora a organização e reutilização desse item em diferentes partes do app.

5. **Organizar Arquivos em Pacotes (Camadas)**  
   Reorganizar os arquivos em pacotes (ou camadas) conforme as responsabilidades (e.g., `model`, `view`, `repository`, etc.), seguindo boas práticas de arquitetura e facilitando a manutenção e expansão do código.

6. **Utilizar `Room` e `Paging3`**  
   Implementar o **Room** para gerenciar os dados localmente e usar **Paging3** para a paginação dos itens. Isso garante que os dados sejam carregados sob demanda, melhorando o desempenho e a experiência do usuário em listagens grandes.

---

## Considerações sobre um Cenário Maior

Imagine um cenário em que os cupons são retornados de uma API. Abaixo estão minhas considerações:

### 1. Qual arquitetura você usaria?
- **MVVM (Model-View-ViewModel)**: Separaria as responsabilidades entre a Model, View e ViewModel, o que facilita o gerenciamento de estado, lógica de negócios e interação com a UI.

### 2. Algum padrão de projeto que faz sentido adotar?
- **Clean Architecture com MVVM**: Mesmo para projetos pequenos, essa abordagem oferece modularidade, facilidade de manutenção, testes e flexibilidade para crescer. Principais vantagens:
   - Modularização do projeto.
   - Facilidade na implementação de testes e na manutenção do código.
   - Flexibilidade para mudanças e melhorias no futuro.

### 3. Em relação à UI, algo mudaria se os dados viessem da API?
- Sim. Criaria um **ViewModel** para gerenciar o estado da tela e o fluxo de dados vindos da API. Isso garante que a interface seja reativa e responda adequadamente às mudanças no backend.

### 4. Bibliotecas que fariam sentido incorporar nesse caso:
- **Retrofit** ou **Ktor** para comunicação com APIs externas.
- **Hilt** ou **Koin** para injeção de dependências, facilitando o gerenciamento de objetos e a testabilidade.
- **Room** para armazenamento local e **Paging3** para paginação eficiente dos dados da API.
