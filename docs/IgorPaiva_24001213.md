# Sistema Integrado de Gestão de Farmácia – Saúde & Vida

## 1. Regras de Negócio
1. Não permirtir vender produtos sem estoque.
2. conferir sempre as validades dos medicamentos.
3. contas de clientes atrasadas geram juros.
4. estoque de psicotropicos sempre atualizado.
5. Produtos que estão abaixo do mínimo geram alerta.

## 2. Requisitos Funcionais
1. Realizar cadastro dos clientes.
2. Consultar produtos e verificar a data de validade.
3. Registrar vendas e dar desconto ao cliente .
4. Verificar estoque e conferindo o minimo do medicamento.
5. Emitir comprovante de venda ou NFE para empresa.
6. Cadastrar produtos que chegaram novos.
7. Lançar o XML da nota de compra.
8. gerar o sped para o escritorio.

## 3. Requisitos Não Funcionais
1. Controle de acesso por login.
2. Resposta até 3 segundos.
3. Segurança dos dados.
4. Suporte a múltiplos usuários.

## 4. Atores
Atendente, Farmacêutico, Gerente, Financeiro, Administrador/suporte do programa.

## 5. Casos de Uso
1. Registrar a Venda  
2. Consultar o Produto que for vender 
3. Cadastrar o CPF Cliente  
4. Validar Receita  
5. conferir notas dos produtos que acabaram de chegar pelas distribuidoras  
6. Atualizar Estoque  
7. arrumar problemas que aparecem 
8. Registrar Conta a Pagar  
9. gerar o sped ICMS e Contribuições 
10. emitir um relatorio de estoque para contadora 

## 6. Relacionamentos

<<include>>
- Registrar Venda → Consultar Validade (Segurança do paciente).  
- Registrar Venda → Verificar Saldo de Estoque
- Lançar XML de Compra → Atualizar Estoque.

<<extend>>
- Venda → Cadastrar Cliente  
- Venda → Validar Receita  
- Venda → Conta a Receber  

## 7. Casos de Uso 

**Registrar Venda**  
Ator: Atendente  
Fluxo: selecionar produto → verificar validade → verificar estoque → informar quantidade → finalizar venda → emitir cupom.  

**Consultar Produto**  
Ator: Atendente  
Fluxo: buscar → verificar o produto → bater codigo de barras

**Cadastrar Cliente**  
Ator: Atendente  
Fluxo: inserir dados se for cadastrado → lançar dados da receita → finalizar a venda  

**Validar Receita**  
Ator: Farmacêutico  
Fluxo: conferir a receita → validar se entregaram o medicamento correto → lançar a receita no ANVISA  

**Conferir notas dos produtos que acabaram de chegar pelas distribuidoras **  
Ator: Atendente 
Fluxo: conferir quantidade → conferir a data de validade → guardar o medicamento nas prateleiras 

**Atualizar Estoque**  
Ator: administrador/suporte   
Fluxo: receber operação → atualizar o estoque da loja  

**Arrumar problemas que aparecem no programa**  
Ator: administrador/suporte
Fluxo: localizar o erro → entender o que fala o programa → arrumar o erro → conferir se não está dando mais erro 

**Conta a Pagar**  
Ator: Financeiro  
Fluxo: inserir os boletos → conferir a data que eles vencerão → mandar pelo malote para o banco → dar baixa pelo programa os boletos que foram lançados  

**Gerar o sped ICMS e Contribuições**  
Ator: Administrador/Suporte  
Fluxo: gerar os sped nas datas corretas → ajustar com os M200, M400 → mandar para o escritorio para ser lançado

**Emitir um relatorio de estoque para contadora**  
Ator: Admin/suporte  
Fluxo: gerar o relatorio → conferir o valor do estoque pelo preço de custo → enviar via PDF para o escritorio

## 8. Diagramas de Atividade

Venda: início → produto → estoque? → sim → finalizar / não → erro  

Compra: início → dados → salvar → estoque → fim  

Cliente: início → dados → salvar → fim  
