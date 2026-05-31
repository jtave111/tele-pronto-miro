# TelePronto — Protótipo de Baixa Fidelidade (IHC & UX)

Protótipo de baixa fidelidade para o aplicativo **TelePronto**, sistema de telemedicina do hospital universitário que oferece triagem inteligente, consulta por vídeo, gestão de receitas digitais, lembretes de medicação e localização de farmácias.

---

## 👥 Autores

- Joao Victor Belfort  — RA: 325130747




---

## 📱 Telas do Protótipo

O protótipo contém **6 telas principais** desenhadas em estilo wireframe preto e branco, com foco absoluto em clareza:

| Nº | Tela | Função |
|----|------|--------|
| 1 | **Home / Dashboard** | Atalhos para "Consulta Agora" e "Meus Remédios" + botão SOS sempre visível |
| 2 | **Triagem** | Seleção do sintoma via mapa corporal interativo ou chips de área |
| 3 | **Sala de Espera Virtual** | Posição na fila, tempo estimado e dicas enquanto aguarda |
| 4 | **Vídeo-Chamada** | Vídeo do médico, PiP do paciente, controles de mudo/câmera/chat |
| 5 | **Receita & Farmácias** | Prescrição digital com QR Code + mapa de farmácias próximas |
| 6 | **Lembrete de Medicação** | Configuração de alarme com seletor de horário e dias da semana |

---

## ♿ Análise de Acessibilidade

O design foi concebido para um usuário em **estado vulnerável** — visão turva por febre, dedos trêmulos por mal-estar, possivelmente idoso, possivelmente em pânico.

### Decisões para visão comprometida

- **Alto contraste WCAG AAA**: o protótipo usa apenas preto sobre branco, garantindo razão de contraste ≥ 21:1 em todos os textos principais. Nenhuma informação depende exclusivamente de cor (estado é indicado também por forma, posição e ícone).
- **Tipografia escalonada**: títulos grandes (≥ 18pt no app real), labels secundárias com tamanho mínimo de 14pt. Pesos contrastantes (regular vs. bold) reforçam hierarquia.
- **Ação primária ÚNICA por tela**: o botão "CONSULTA AGORA" ocupa largura total e altura generosa. Não há competição visual entre múltiplos call-to-actions.
- **Ícones acompanhados de texto**: nenhum botão é apenas pictográfico; todos têm rótulo escrito.

### Decisões para dedos trêmulos

- **Áreas de toque ≥ 48×48 px** em todos os elementos interativos (acima do mínimo recomendado pelo Material Design e Apple HIG de 44 px).
- **Espaçamento mínimo de 8 px** entre alvos clicáveis para evitar toque acidental no botão errado.
- **Botão de encerrar chamada isolado**: o ✕ é o único controle circular e fica afastado dos demais ícones quadrados, reduzindo chance de toque acidental.
- **Ações destrutivas exigem confirmação dupla**: cancelar consulta, encerrar chamada e excluir lembrete pedem segundo toque com modal explícito ("Tem certeza? Você perderá sua posição na fila").

---

## 🚨 Fluxo Crítico: Iniciar uma Consulta de Urgência

O caminho de menor atrito para um paciente em mal-estar foi otimizado em **4 toques**:

```
[1] HOME
     │  Toca o botão preto "▶ CONSULTA AGORA" (ocupa ~30% da viewport)
     ▼
[2] TRIAGEM
     │  Aponta no mapa corporal onde dói OU toca um chip de área
     │  Toca "CONTINUAR ▶"
     ▼
[3] SALA DE ESPERA VIRTUAL
     │  Sistema mostra posição na fila e tempo estimado
     │  Usuário pode minimizar (recebe notificação push quando o médico entra)
     ▼
[4] VÍDEO-CHAMADA
        Conexão automática quando o médico aceita
```

### Por que esse fluxo funciona

- **Botão SOS sempre presente** no canto superior direito de todas as telas do fluxo — para emergências que não podem esperar a fila virtual, o usuário liga diretamente para o SAMU.
- **Feedback constante**: a sala de espera mostra posição numérica gigante (`3º` em fonte 84px), barra de progresso e tempo estimado atualizado.
- **Permissão para minimizar**: o usuário pode sair do app e receber notificação quando for a vez dele, reduzindo ansiedade.

---

## 🛡 Prevenção de Erros

### Problema: o paciente encerra a consulta por acidente

**Solução em 3 camadas:**

1. **Isolamento físico**: o botão de encerrar (✕) é o único circular e preto sólido, posicionado mais à direita, separado por espaço extra dos outros controles (mudo, câmera, chat). Visualmente e espacialmente distinto.
2. **Confirmação modal obrigatória**: tocar no ✕ abre um modal centralizado com duas opções igualmente grandes — "Continuar Consulta" (botão primário preto) e "Sim, Encerrar" (botão secundário com borda). O botão de continuar é o destacado, invertendo o padrão para reduzir desfecho acidental.
3. **Mensagem de aviso visível**: abaixo dos controles da chamada, um pequeno texto informa "Encerrar requer confirmação ⚠", treinando o usuário sobre o comportamento.

### Outras prevenções aplicadas

- **Cancelar consulta na sala de espera**: botão com borda tracejada (não sólido), indicando ação secundária/destrutiva. Toque pede confirmação.
- **Triagem com seleção visual**: ao tocar no mapa do corpo, um marcador aparece confirmando a área selecionada antes de avançar. Reduz ambiguidade.
- **Estados de sistema explícitos**: a sala de espera tem 4 estados visíveis — `Conectando` → `Na fila (Nº)` → `Médico se preparando` → `Médico entrou!` (com vibração). O usuário nunca fica em dúvida sobre o que está acontecendo.

---

## 🌟 Desafios Extras (Opcionais)

> Não implementados graficamente nesta versão, mas planejados:

### Fluxo de Dependente
- Avatar no topo do Dashboard funciona como seletor (toque longo abre lista de perfis).
- Aviso visual claro: quando o perfil ativo é de uma criança, o app exibe uma faixa horizontal no topo "👶 Atendendo: Pedro (8 anos)" para evitar prescrição cruzada.

### Modo Baixa Conexão
- Indicador de qualidade de sinal no canto superior da tela de vídeo.
- Quando a conexão cai abaixo de um limiar, o app exibe um banner não bloqueante: "⚠ Conexão instável — desligamos seu vídeo para priorizar o áudio. Toque para reativar."
- Decisão automática, mas com opção manual de reverter.

---

## 🛠 Ferramentas e Entrega

- **Prototipagem**: planejada no Miro (este repositório contém a exportação final).
- **Estilo**: wireframe de baixa fidelidade, preto e branco, sem cores nem imagens reais.
- **Arquivos entregues**:
  - `/prototipo/prototipo.png` — captura em alta resolução do board
  - `/prototipo/prototipo.pdf` — versão em PDF para impressão

---

## 📋 Nota do Professor (registrada)

> *"Design para saúde é design de responsabilidade. Um ícone mal interpretado aqui pode gerar um erro médico ou um atraso no atendimento. Foquem na clareza absoluta!"*
> — Prof. Daniel Henrique Matos de Paiva

Este protótipo aplica essa diretriz como princípio orientador em cada tela.
