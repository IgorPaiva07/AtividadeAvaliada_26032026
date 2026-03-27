# Avaliação — Engenharia de Software  
## Sistema Integrado de Gestão de Farmácia — Saúde & Vida  

**Aluno:** [Seu Nome Aqui]  
**RA:** 24001213  
**Data:** 26/03/2026  

---

## 1. Escopo do MVP
Meu MVP cobre o processo essencial de operação de uma rede farmacêutica, focando na entrada de mercadorias e a venda segura ao consumidor final.

**Dentro do escopo:**
- Cadastro de clientes  
- Controle de estoque  
- Venda de medicamentos comuns e psicotrópicos  
- Lançamento de Notas Fiscais via XML  
- Geração de arquivos fiscais (SPED)  

**Fora do escopo:**
- Vendas online (e-commerce)  
- Gestão de escala de funcionários  
- Integração com programas de fidelidade externos  

**Justificativa:**  
O foco é garantir a conformidade sanitária (controle de receitas) e a saúde financeira (gestão de estoque e impostos), que são os pilares de uma farmácia física funcional e dentro da legalidade.

---

## 2. Regras de Negócio (RN)
- **RN01 — Bloqueio de Saldo:** Não permitir a venda de produtos sem saldo em estoque, especialmente psicotrópicos.  
- **RN02 — Verificação de Validade:** Impedir o registro de qualquer item com validade expirada.  
- **RN03 — Juros de Atraso:** Contas de clientes em atraso devem gerar incidência de juros automáticos.  
- **RN04 — Controle de Psicotrópicos:** Medicamentos controlados exigem validação da receita pelo Farmacêutico responsável.  
- **RN05 — Alerta de Reposição:** O sistema deve emitir alerta quando o estoque atingir o mínimo.  

---

## 3. Requisitos Funcionais (RF)
- **RF01:** Cadastro e atualização de clientes (CPF e Nome).  
- **RF02:** Consulta de produtos por código de barras, exibindo saldo e validade.  
- **RF03:** Registro de vendas com aplicação de descontos baseados no preço de custo.  
- **RF04:** Verificação de estoque em tempo real e sinalização de limite mínimo.  
- **RF05:** Emissão de comprovante de venda ou Nota Fiscal Eletrônica (NFC-e).  
- **RF06:** Cadastro manual de novos produtos recebidos.  
- **RF07:** Importação de XML de notas de compra para entrada de mercadorias.  
- **RF08:** Geração de arquivos SPED para contabilidade.  

---

## 4. Requisitos Não Funcionais (RNF)
- **RNF01 — Autenticação:** Acesso restrito via login e senha criptografada.  
- **RNF02 — Performance:** Consultas de estoque e vendas em tempo real.  
- **RNF03 — Segurança:** Garantir integridade e sigilo dos dados (LGPD).  
- **RNF04 — Multi-usuário:** Suporte simultâneo para Atendentes, Gerentes e Farmacêuticos.  

---

## 5. Casos de Uso (Geral)
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
1. O Atendente inicia a venda.  
2. O Sistema solicita a identificação do produto.  
3. O Atendente bipa o código de barras.  
4. O Sistema valida o estoque e a validade (Include).  
5. O Atendente confirma o pagamento e finaliza a venda.  

### Fluxos Alternativos / Exceções
- **FA01 — Cadastro:** Se o cliente não existir, o sistema estende para *Cadastrar Cliente* (Extend).  
- **FA02 — Psicotrópico:** Se o item for controlado, o sistema estende para *Validar Receita* (Extend).  
