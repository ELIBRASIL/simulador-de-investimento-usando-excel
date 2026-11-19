# simulador-de-investimento-usando-excel

Ferramenta desenvolvida em Excel com foco em experiência do usuário (UX) e análise financeira, criada como parte da Formação de Análise de Dados com Excel e IA da DIO. O objetivo é simular APORTES mensais, projeção de patrimônio e distribuição de carteira em Fundos Imobiliários de forma automatizada e amigável.

---

## 🎯 1. As Perguntas de Negócio e Onde Cada Resposta Aparece

A ferramenta foi estruturada para responder diretamente a cinco perguntas fundamentais para qualquer investidor:

1. **Quanto investir por mês?**
   * *Onde aparece:* Na seção **Investimento Mensal**, onde o usuário insere o valor do APORTE ou utiliza a sugestão automática baseada em **30% do salário** configurado.
2. **Por quantos anos?**
   * *Onde aparece:* Na célula de horizonte temporal dentro do simulador principal, definindo o prazo da simulação.
3. **Qual a taxa de rendimento mensal?**
   * *Onde aparece:* Na célula dedicada à taxa esperada de retorno mensal (ex: dividend yield médio projetado).
4. **Quanto de patrimônio vai acumular?**
   * *Onde aparece:* No resultado principal de **Patrimônio Acumulado**, calculando o montante final ao término do período estipulado.
5. **Quanto vai receber de dividendos por mês?**
   * *Onde aparece:* Na linha de **Dividendos Mensais**, que aplica a taxa de rendimento sobre o patrimônio acumulado final.

---

## ⚙️ 2. Como as Funções VF e PROCV Entram nos Cálculos

* **Função VF (Valor Futuro):** É o motor financeiro da planilha. Utilizada na célula de patrimônio acumulado com a sintaxe `VF(taxa; nper; pmt; \[va]; \[tipo])`, ela calcula o montante futuro gerado por uma série de pagamentos periódicos (aportes mensais) a uma taxa de juros composta constante. Também é replicada nas linhas de projeção de cenários.
* **Função PROCV (VLOOKUP) com Chave Composta:** Utilizada na aba de distribuição por perfil de investidor. Como o tipo de fundo imobiliário pode se repetir entre diferentes perfis (ex: Papel existe no Conservador, Moderado e Agressivo), foi criada uma **chave composta** (concatenando `Perfil + Tipo de FII`) para garantir que o `PROCV` localize de forma unívoca o percentual correto correspondente na tabela de apoio.

---

## 🏷️ 3. Intervalos Nomeados Criados

Para tornar as fórmulas mais limpas, legíveis e fáceis de manter, foram aplicados intervalos nomeados nas principais variáveis globais e de cálculo da planilha:
* `salario`: Referência à célula do salário base.
* `rendimento\_carteira`: Referência à taxa de rendimento padrão.
* `aporte`: Referência ao valor mensal destinado aos investimentos.
* `taxa\_mensal`: Referência à taxa de juros utilizada nas projeções.

---

## 📊 4. Os Percentuais de Cada Perfil e Sua Origem

A distribuição do aporte mensal divide-se em seis classes de Fundos Imobiliários: *Papel, Tijolo, Híbridos, FOFs (Fundos de Fundos), Desenvolvimento e Hotelaria*.

Os percentuais foram estruturados em uma aba de apoio (`Planilha2`) contemplando três perfis de investidor:
* **Conservador:** Maior alocação em FIIs de Papel e Tijolo (maior previsibilidade e menor volatilidade).
* **Moderado:** Equilíbrio entre renda fixa imobiliária, tijolo e fundos mistos/desenvolvimento.
* **Agressivo:** Maior exposição a risco, incluindo percentuais mais elevados em FIIs de Papel e Desenvolvimento.
* *Nota:* Cada perfil soma exatamente **100%**, garantindo a integridade da alocação do capital aportado.

---

## 🔄 5. O Que Foi Mudado em Relação à Ferramenta do Expert

* **Interface Visual Aprimorada:** Organização espacial mais limpa, com ocultação de linhas de grade e destaque visual em tons de cinza para células estritamente calculadas (protegidas contra edição manual).
* **Dinamismo na Distribuição de Aportes:** Integração automatizada da alocação setorial atrelada diretamente à lista suspensa (Validação de Dados) de seleção de perfil.
* **Automação de Cálculos Auxiliares:** Refinamento nas fórmulas de projeção de cenários de 2, 5, 10, 20 e 30 anos para leitura fluida em conjunto com os parâmetros globais.

---

## 📸 Prints da Ferramenta Preenchida

* **Simulação - Perfil Conservador:**
  
  <img width="657" height="1203" alt="image" src="https://github.com/user-attachments/assets/53b0cb2d-174c-4f87-9f9c-2e6067b29197" />

* **Simulação - Perfil Agressivo:**
  
 
  <img width="646" height="1211" alt="image" src="https://github.com/user-attachments/assets/fd1ea925-6e84-4754-88db-f1119b252ab3" />


---

### ✅ Checklist de Pré-Submissão
- [x] A planilha abre sem erros de fórmula e responde às 5 perguntas de negócio.
- [x] A troca de perfil altera dinamicamente a divisão do aporte (somando exatamente 100%).
- [x] O salário e os valores publicados são genéricos/de exemplo.
- [x] O link enviado é o do repositório público no GitHub.
- [x] Nome do repositório legível, em minúsculas e sem acentos.

---
Feito com 💻 e ☕ por uma entusiasta de dados e tecnologia.
