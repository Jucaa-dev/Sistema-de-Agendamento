```mermaid
flowchart TD

    subgraph Login["Tela de Login"]
        A[Logo]
        B[Email]
        C[Senha]
        D[Botão: Entrar]
        E[Link: Criar conta]

        A --> B --> C --> D
        E --> F
    end

    subgraph Cadastro["Tela de Cadastro"]
        F[Nome]
        G[Email]
        H[Senha]
        I[Confirmar Senha]
        J[Botão: Cadastrar]
        K[Link: Já tenho conta]

        F --> G --> H --> I --> J
        K --> B




## Diagrama de Sequência
```mermaid
sequenceDiagram
  participant U as Usuário
  participant S as Sistemas
  participant B as Backend
  participant D as Banco de Dados

  U->>S: Acessa o Sistema
  S->>B: Solicita login
  B->>D: Verifica usuário
  D-->B: Dados do usuário
  B-->>S: Login realizado

  U->>S: Responde questionário
  S->>B: Envia respostas
  B->>B: Valida aptidão

alt Usuário apto
  %% AGENDAMENTO
  B-->>S: Libera agendamento
  U->>S: Escolhe data e local
  S->>B: Envia agendamento
  B->>D: Salva agendamento
  B-->>S: Confirma agendamento
  B->>S: Envia notificação de confirmação
  S-->U: Notificação exibida

  %% REMARCAR
  U->>S: Solicitação remarcação
  S->>B: Envia nova data
  B->>D: Atualiza agendamento
  B-->>S: Confirmação de remarcação

  %% CANCELAR
  U->>S: Cancelar agendamento
  S->>B: Solicita cancelamento
  B->>D: Libera horário
  B-->S: Cancelamento confirmado

else Usuário inapto
  B-->>S: Bloqueia agendamento
end
