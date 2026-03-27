# Avaliação — Engenharia de Software  
## Sistema Integrado de Gestão de Farmácia — Saúde & Vida  

**Aluno:** Igor Rogatti De Paiva  
**RA:** 24001213  
**Data:** 26/03/2026  

---

# Escopo do MVP 

## O que está dentro do MVP
- **Cadastro de clientes** (CPF e Nome)  
- **Controle de estoque** com verificação de validade e saldo disponível  
- **Venda de medicamentos comuns e psicotrópicos** com regras de conformidade  
- **Lançamento de Notas Fiscais via XML**  
- **Geração de arquivos fiscais (SPED)** para contabilidade  

## O que está fora do MVP
- **Vendas online (e-commerce)**  
- **Gestão de escala de funcionários**  
- **Integração com programas de fidelidade externos**  

## Justificativa das escolhas
O MVP foi definido para atender às necessidades **essenciais** de uma farmácia física  
- **melhoras no escritorio:** gestão eficiente de estoque e impostos.  
- **Operação para um venda melhor:** funcionalidades básicas para atender clientes e manter o fluxo de vendas.  


**Dentro do escopo:**
- Cadastro de clientes  
- Controle de estoque  
- Venda de medicamentos comuns e psicotrópicos  
- Lançamento de Notas Fiscais via XML  
- Geração de arquivos fiscais (SPED)  

**Fora do escopo:**
- Vendas online (e-commerce) para farmacias que não possuem
- Gestão de escala de funcionários que sabem seus horarios  
- Integração com programas de fidelidade externos  

---

## 2. Regras de Negócio (RN)
- **RN01 — Bloqueio de Saldo:** Não permitir a venda de produtos sem saldo em estoque, especialmente psicotrópicos para não gerar multas.  
- **RN02 — Verificação de Validade:** Impedir o registro de qualquer item com validade expirada para sempre manter o cliente satisfeito.  
- **RN03 — Juros de Atraso:** Contas de clientes em atraso devem gerar juros automáticos.  
- **RN04 — Controle de Psicotrópicos:** Medicamentos controlados exigem validação da receita pelo Farmacêutico responsável pela farmacia.  
- **RN05 — Alerta de Reposição:** O sistema deve emitir alerta quando o estoque atingir o mínimo para poder gerar o pedidos de compras.  

---

## 3. Requisitos Funcionais (RF)
- **RF01:** Cadastro e atualização de clientes (CPF,Nome e endereço).  
- **RF02:** Consulta de produtos por código de barras, exibindo saldo e validade do produto.  
- **RF03:** Registro de vendas com descontos baseados no preço de custo desses produtos .  
- **RF04:** Verificação de estoque em tempo real e sinalização de limite mínimo.  
- **RF05:** Emissão de comprovante de venda ou Nota Fiscal Eletrônica (NFC-e) para empresas que precisam da nota.  
- **RF06:** Cadastro manual de novos produtos recebidos pelas distribuidoras.  
- **RF07:** Importação de XML de notas de compra para entrada de mercadorias no sistema.  
- **RF08:** Geração de arquivos SPED para contabilidade.  

---

## 4. Requisitos Não Funcionais (RNF)
- **RNF01 — Autenticação:** Acesso restrito via login e senha criptografada para poder entrar no sistema da rede da farmacia.  
- **RNF02 — Performance:** Consultas de estoque e vendas em tempo real sempre que precisar.  
- **RNF03 — Segurança:** Garantir integridade e sigilo dos dados dos clientes que precisam passar por conta dos psicotropicos (LGPD).  
- **RNF04 — Multi-usuário:** Suporte simultâneo para Atendentes, Gerentes e Farmacêuticos.  

---

## 5. Casos de Uso 
- Registrar Venda  
- Consultar Produto (<<include>> de Venda)  
- Cadastrar Cliente (<<extend>> de Venda)  
- Validar Receita (<<extend>> de Venda)  
- Conferir Notas (XML)  
- Atualizar Estoque (<<include>> de Compra/Venda)  
- Manutenção do Sistema (Suporte)  
- Registrar Conta a Pagar  
- Gerar SPED ICMS/Contribuições  
- Emitir Relatório de Estoque (Contadora)  

---

## 6. Documentação do Caso de Uso Principal
**UC01 — Registrar Venda**  
- **Ator(es):** Atendente  
- **Descrição:** Realizar a saída comercial de produtos para o cliente.  
- **Pré-condições:** Operador logado; Produto com estoque disponível.  
- **Pós-condições:** Estoque atualizado; Venda registrada no financeiro.  

### Fluxo Principal
1. O atendente inicia a venda.  
2. O Sistema solicita a identificação do produto.  
3. O Atendente bipa o código de barras.  
4. O Sistema valida o estoque e a validade.  
5. O Atendente confirma o pagamento e finaliza a venda.  

### Fluxos Alternativos / Exceções
- **FA01 — Cadastro:** Se o cliente não existir, o sistema estende para *Cadastrar Cliente* (Extend).  
- **FA02 — Psicotrópico:** Se o item for controlado, o sistema estende para *Validar Receita* (Extend).

- Registrar venda
- <img width="580" height="338" alt="image" src="https://github.com/user-attachments/assets/6fa32d96-9a2a-49e5-b69b-900bc43221d4" />

- consultar produto
- <img width="207" height="202" alt="image" src="https://github.com/user-attachments/assets/2106e8b6-8f67-4c06-9128-980ffd57cb53" />

-cadastrar cliente
<img width="203" height="201" alt="image" src="https://github.com/user-attachments/assets/cb71cad0-382b-429d-9c5f-cc00d68708d2" />

- validar receita
- <img width="191" height="199" alt="image" src="https://github.com/user-attachments/assets/85c9ccd8-2efa-4de8-9d5b-f1c4042a2290" />

- conferir notas
- <img width="221" height="342" alt="image" src="https://github.com/user-attachments/assets/e591d42f-e7e8-4f6e-beb8-cbd4aae1aebf" />

-atualizar estoque
<img width="203" height="201" alt="image" src="https://github.com/user-attachments/assets/d67beb86-d0ef-4b75-93d4-3d9fb264e11a" />

- manutenção do sistema
<img width="237" height="208" alt="image" src="https://github.com/user-attachments/assets/4565b962-0579-4e3e-989e-8b9652c8a255" />

- registrar conta a pagar
- <img width="473" height="572" alt="image" src="https://github.com/user-attachments/assets/27feae00-14d2-4979-911c-8f3129b88f03" />

- Gerar SPED ICMS/Contribuições
<img width="394" height="516" alt="image" src="https://github.com/user-attachments/assets/fcb75715-eafc-4107-8fd1-d4a7e535ef8e" />

- Emitir Relatório de Estoque
- <img width="374" height="452" alt="image" src="https://github.com/user-attachments/assets/c137614e-3523-4eb1-9d83-929239d029e0" />












