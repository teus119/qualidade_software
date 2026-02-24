# Matriz de Rastreabilidade de Requisitos (RTM)

Este documento mapeia os requisitos do sistema de Qualidade Educacional para os seus respectivos testes automatizados, permitindo identificar lacunas na cobertura de testes.

## Legenda de Status
- **🟢 Testado**: Existe pelo menos um teste unitário ou de integração cobrindo o requisito.
- **🟡 Parcial**: O requisito é parcialmente coberto por testes.
- **🔴 Não Testado**: Não foram encontrados testes para este requisito.

## 1. Requisitos de Negócio (Serviços)

| ID | Requisito | Arquivo de Teste | Método de Teste | Status |
| :--- | :--- | :--- | :--- | :--- |
| **REQ-S01** | Listar todos os estudantes | - | - | 🔴 Não Testado |
| **REQ-S02** | Buscar estudante por ID | `StudentServiceTest.java` | `deveBuscarEstudantePorId` | 🟢 Testado |
| **REQ-S03** | Salvar/Atualizar estudante | - | - | 🔴 Não Testado |
| **REQ-S04** | Excluir estudante | - | - | 🔴 Não Testado |
| **REQ-S05** | Validar formato de e-mail de estudante | `StudentServiceTest.java` | `validarEmails` | 🟢 Testado |
| **REQ-S06** | Verificar existência de e-mail (Estudante) | - | - | 🔴 Não Testado |
| **REQ-S07** | Verificar existência de matrícula | - | - | 🔴 Não Testado |
| **REQ-T01** | Listar todos os professores | - | - | 🔴 Não Testado |
| **REQ-T02** | Buscar professor por ID | - | - | 🔴 Não Testado |
| **REQ-T03** | Salvar/Atualizar professor | - | - | 🔴 Não Testado |
| **REQ-T04** | Excluir professor | - | - | 🔴 Não Testado |
| **REQ-T05** | Verificar existência de e-mail (Professor) | - | - | 🔴 Não Testado |

## 2. Requisitos de Interface Web (UI)

| ID | Requisito | Arquivo de Teste | Método de Teste | Status |
| :--- | :--- | :--- | :--- | :--- |
| **REQ-U01** | Acessar página inicial (Home) | `HomeControllerTest.java` | `shouldReturnHomeView` | 🟢 Testado |
| **REQ-U02** | Listar estudantes na interface web | - | - | 🔴 Não Testado |
| **REQ-U03** | Formulário de novo estudante | - | - | 🔴 Não Testado |
| **REQ-U04** | Listar professores na interface web | - | - | 🔴 Não Testado |
| **REQ-U05** | Formulário de novo professor | - | - | 🔴 Não Testado |

## 3. Requisitos de API REST

| ID | Requisito | Arquivo de Teste | Método de Teste | Status |
| :--- | :--- | :--- | :--- | :--- |
| **REQ-A01** | Endpoint GET /api/students | - | - | 🔴 Não Testado |
| **REQ-A02** | Endpoint GET /api/students/{id} | - | - | 🔴 Não Testado |
| **REQ-A03** | Endpoint POST /api/students | - | - | 🔴 Não Testado |
| **REQ-A04** | Endpoint DELETE /api/students/{id} | - | - | 🔴 Não Testado |
| **REQ-A05** | Endpoint GET /api/teachers | - | - | 🔴 Não Testado |

---

## Resumo de Cobertura de Requisitos

- **Total de Requisitos Mapeados:** 22
- **Requisitos Testados:** 3
- **Cobertura Atual:** ~13.6%

*Nota: Os testes atuais focam predominantemente na lógica de serviço do estudante e no roteamento básico da Home.*

---
*Última atualização: 24 de Fevereiro de 2026*
