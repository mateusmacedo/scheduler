# **Roadmap de Diagramas UML para o Sistema de Agendamento**

Este roadmap visa orientar a criação dos principais diagramas UML para descrever de forma completa e detalhada o **Sistema de Agendamento**, abordando diferentes aspectos do sistema, desde interações dinâmicas até a estrutura estática das classes.

## **1. Diagramas de Sequência**

Os diagramas de sequência são fundamentais para ilustrar a interação temporal entre os atores do sistema e os componentes, destacando as trocas de mensagens e eventos que ocorrem ao longo de uma funcionalidade específica.

**Quantidade:** **10** diagramas de sequência.

### **Diagramas sugeridos:**

1. **Registrar Novo Usuário**:
   - Descreve a criação de um novo usuário e a interação com o sistema de autenticação e notificações.

2. **Login**:
   - Inclui o fluxo de autenticação bem-sucedida e o fluxo alternativo de falha na autenticação.

3. **Recuperar Senha**:
   - Inclui o envio de instruções de recuperação e o fluxo alternativo de falha no envio ou email não registrado.

4. **Solicitar Agendamento**:
   - Inclui as extensões como "Adicionar à Lista de Espera" e "Falha na Integração com Calendário".

5. **Cancelar Agendamento**:
   - Inclui o fluxo principal e o tratamento de falhas ao tentar cancelar o agendamento.

6. **Reagendar Agendamento**:
   - Inclui os fluxos de sucesso e as falhas no reagendamento, como indisponibilidade de slots.

7. **Liberar Slot Diretamente**:
   - Descreve como um administrador pode liberar um slot de tempo, incluindo falhas na liberação.

8. **Configurar Sistema**:
   - Mostra a configuração de níveis de prioridade e políticas de rotação, incluindo as interações com o sistema.

9. **Monitorar Sistema**:
   - Detalha as ações de visualização de logs, monitoramento de desempenho e recebimento de alertas.

10. **Rotação de Ocupação**:
    - Descreve o processo assíncrono de rotação de slots de tempo expirados ou liberados.

## **2. Diagramas de Atividade**

Os diagramas de atividade representam o fluxo de trabalho de forma visual, identificando as etapas e as decisões envolvidas nos principais processos. São úteis para modelar a lógica do processo de negócio e para identificar pontos de decisão ou paralelismos.

**Quantidade:** **7** diagramas de atividade.

### **Diagramas sugeridos:**

1. **Processo de Autenticação e Autorização**:
   - Mostra o processo completo de login e autorização de usuários.

2. **Fluxo de Solicitação de Agendamento**:
   - Detalha o processo de solicitação de um novo agendamento, incluindo verificação de disponibilidade e confirmação.

3. **Fluxo de Cancelamento de Agendamento**:
   - Representa o fluxo de cancelamento de um agendamento já confirmado.

4. **Fluxo de Reagendamento de Agendamento**:
   - Descreve as etapas envolvidas no reagendamento de um slot de tempo já reservado.

5. **Fluxo de Registro e Recuperação de Senha**:
   - Combina os processos de registro de novo usuário e de recuperação de senha.

6. **Fluxo de Configuração do Sistema pelo Administrador**:
   - Descreve como o administrador pode ajustar configurações do sistema, incluindo prioridades e políticas.

7. **Fluxo de Rotação de Ocupação**:
   - Detalha o processo de rotacionar ou liberar slots de tempo que expiraram ou foram cancelados.

## **3. Diagramas de Estado**

Os diagramas de estado são críticos para modelar o ciclo de vida de objetos que passam por várias transições, como agendamentos e slots de tempo. Eles ajudam a entender como esses objetos mudam de estado em resposta a eventos ou ações no sistema.

**Quantidade:** **3** diagramas de estado.

### **Diagramas sugeridos:**

1. **Estado do Agendamento**:
   - Estados: Solicitado, Confirmado, Cancelado, Reagendado, Expirado, Em Espera.
   - Representa as transições entre esses estados à medida que o agendamento evolui.

2. **Estado do Slot de Tempo**:
   - Estados: Disponível, Reservado, Bloqueado, Liberado, Expirado.
   - Mostra as mudanças de estado de um slot de tempo desde a sua disponibilidade até o cancelamento ou expiração.

3. **Estado do Usuário**:
   - Estados: Ativo, Inativo, Bloqueado, Em Processo de Recuperação de Senha.
   - Representa as diferentes condições que um usuário pode assumir durante sua interação com o sistema.

## **4. Diagrama de Classes**

O diagrama de classes fornece uma visão estrutural do sistema, mostrando as classes, seus atributos e métodos, além dos relacionamentos entre elas. Ele é a base para a implementação do modelo de domínio e ajuda a visualizar a estrutura de dados do sistema.

**Quantidade:** **1** diagrama de classes.

### **Diagrama sugerido:**

- **Diagrama de Classes do Sistema de Agendamento**:
  - Classes principais:
    - **Usuário**: Atributos como nome, email, senha, estado (ativo/inativo).
    - **Administrador**: Herança da classe Usuário, com permissões adicionais.
    - **Agendamento**: Atributos como data, hora, status (confirmado, cancelado).
    - **Slot**: Atributos como horário disponível, reservado, expirado.
    - **Notificação**: Envio de notificações para o solicitante via email, SMS ou push.
    - **Feedback**: Representa o feedback fornecido pelo solicitante.
    - **Lista de Espera**: Mantém registros de usuários na fila de espera.
    - **Configurações do Sistema**: Define políticas como prioridades e rotação de slots.
    - **Log de Sistema**: Registra atividades e eventos importantes do sistema.

## **5. Resumo Geral**

### **Quantidade de Diagramas por Tipo:**

- **Sequência**: 10
- **Atividade**: 7
- **Estado**: 3
- **Classes**: 1

**Total de Diagramas**: **21**

## **6. Justificativa dos Diagramas**

### **6.1. Diagramas de Sequência**

- Ajudam a entender as interações temporais entre o sistema e os usuários/serviços externos.
- Facilitam a implementação de fluxos de trabalho complexos, especialmente onde há muitos atores ou sistemas envolvidos.
- São indispensáveis para modelar fluxos alternativos e a gestão de falhas, garantindo uma visão clara de como o sistema lida com exceções.

### **6.2. Diagramas de Atividade**

- Descrevem o fluxo de atividades e permitem identificar pontos de decisão e loops.
- São particularmente úteis para processos de negócio complexos e fluxos com diversas condições e alternativas.

### **6.3. Diagramas de Estado**

- São essenciais para modelar o ciclo de vida de objetos-chave no sistema, como agendamentos e usuários.
- Garantem que todas as transições entre estados sejam tratadas adequadamente, prevenindo inconsistências no sistema.

### **6.4. Diagrama de Classes**

- Oferece uma visão estruturada do sistema, facilitando a implementação e o design orientado a objetos.
- Mostra como as diferentes entidades do sistema se relacionam e quais são suas responsabilidades.

## **7. Considerações Finais**

- **Escalabilidade**: O roadmap pode ser expandido para incluir novos diagramas conforme novas funcionalidades sejam adicionadas ao sistema.
- **Manutenção**: Diagramas devem ser atualizados conforme alterações no sistema ocorram, para garantir que a documentação esteja sempre alinhada com o código.
- **Modularidade**: Os diagramas foram projetados de forma modular para facilitar a compreensão e manutenção da documentação.
-
