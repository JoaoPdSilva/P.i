# P.i
Trabalho faculdade
Este modelo de banco de dados é uma boa base para um sistema de controle de estoque para um aplicativo desktop. Ele é composto por três tabelas principais: `estoqueprodutos`, `fornecedor` e `materiaprima`. Vamos destrinchar cada uma:

### Estrutura do Banco de Dados
1. **`estoqueprodutos`**:
   - Mantém o controle dos produtos armazenados no estoque, com informações como:
     - Número e Nome do Lote.
     - Descrição e Preço.
     - Matéria-Prima utilizada.
     - Quantidade, ID do Produto.
     - Datas de entrada e saída do lote.
   - **Chave primária**: `NumeroLote`.
   - **Restrição única**: `IdProduto`.

2. **`fornecedor`**:
   - Centraliza informações sobre fornecedores, incluindo:
     - CNPJ, Nome Fantasia, e Endereço (CEP, Rua, Cidade, Estado e Bairro).
     - Contato (Telefone e E-mail).
   - **Chave primária**: `CNPJ-Fornecedor`.

3. **`materiaprima`**:
   - Administra os dados sobre as matérias-primas utilizadas, como:
     - Nome e Descrição.
     - Preço e Quantidade disponíveis.
     - Relacionamento com fornecedor pelo CNPJ.
     - Data de entrada.
   - **Chave primária**: `IdMateriaPrima`.
   - **Chave única**: CNPJ do fornecedor (relação com a tabela `fornecedor`).

### Considerações Importantes
- **Consistência de Dados**: Certifique-se de que há validações para campos como `Preco` e `Quantidade` para evitar valores inadequados.
- **Relacionamento entre tabelas**: As tabelas `materiaprima` e `fornecedor` estão relacionadas, mas poderiam ser migradas para um banco relacional com *foreign keys* para maior integridade referencial.
- **Inserções de Dados**: No exemplo, foi realizado um teste de inserção com dados fictícios. Avalie como vai tratar campos obrigatórios e permissões.
- **Engine MyISAM**: Essa engine não suporta *transactions* nem *foreign keys*. Avalie usar o InnoDB se precisar dessas funcionalidades no futuro.
