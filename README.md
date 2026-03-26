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
  B-->>S: Libera agendamento
  U->>S: Escolhe data
  S->>B: Envia agendamento
  B->>D: Salva agendamento
  B-->>S: Confirma agendamento
  B->>S: Envia notificação de confirmação
  S-->U: Notificação exibida
else Usuário inapto
  B-->>S: Bloqueia agendamento
end
