# Declaração de Uso de IA

## Por que pedimos isso

Ferramentas de IA fazem parte do dia a dia de desenvolvimento e não faz sentido fingir que não existem. O que nos interessa avaliar não é *se* você usou, mas **como você pensou**: quais decisões foram suas, o que você aceitou de uma sugestão, o que você descartou e por quê.

**O uso de IA não é penalizado em nenhum nível.** Usar de forma pontual, moderada ou intensa não altera a sua nota. Não existe um limite certo — existe o seu jeito de trabalhar, e é sobre ele que queremos conversar.

A declaração serve para que a entrevista técnica comece de um lugar honesto, em vez de virar um jogo de adivinhação sobre a origem do código. Ela também nos ajuda a preparar perguntas melhores, focadas no que você de fato construiu.

---

## O que entregar

Junto com o desafio, inclua um arquivo **`USO-DE-IA.md` na raiz do seu repositório** (o fork), preenchido a partir do template abaixo.

A entrega é **obrigatória para todos**, inclusive para quem não usou nenhuma ferramenta de IA. Nesse caso, preencha apenas o resumo indicando que não utilizou.

---

## Não há limite de uso

Nenhum dos desafios — [`backend-jr`](backend/backend-jr.md), [`frontend-jr`](frontend/frontend-jr.md) e [`full-stack-pl`](full-stack/full-stack-pl.md) impõe teto ao uso de IA. Você decide quanto e como usar.

O que pedimos é transparência: descreva aqui como foi o seu processo. Um uso intenso e bem declarado é tão bem-visto quanto nenhum uso — o que conta é a clareza sobre como você chegou ao resultado.

---

## Template

Copie o bloco abaixo para o seu `USO-DE-IA.md` e preencha. Remova as instruções entre parênteses.

````markdown
# Declaração de Uso de IA

**Candidato:** (seu nome)
**Desafio:** (backend-jr / frontend-jr / full-stack-pl)

## 1. Resumo

(Uma ou duas frases sobre o papel que a IA teve no seu trabalho.)

**Nível de uso:** (marque um)

- [ ] Não utilizei IA
- [ ] Pontual — dúvidas, sintaxe, boilerplate
- [ ] Moderado — rascunhos de trechos que revisei e reescrevi
- [ ] Intenso — partes significativas do código foram geradas

## 2. Ferramentas utilizadas

| Ferramenta / Modelo | Finalidade | Onde no projeto (arquivos ou módulos) |
| --- | --- | --- |
|  |  |  |

## 3. Volume aproximado

| Ferramenta | Sessões / conversas | Tokens ou mensagens | Medido ou estimado? | Tempo aproximado |
| --- | --- | --- | --- | --- |
|  |  |  |  |  |

(Se a ferramenta não mostra a contagem de tokens, estime pelo número de mensagens ou pelo tempo de uso e marque como **estimado**. Uma estimativa honesta vale mais do que um número preciso inventado.)

## 4. Prompts principais

(De 3 a 5 prompts que mais influenciaram o resultado final. Transcreva na íntegra — não resuma.)

### Prompt 1

> (texto do prompt)

- **O que aceitei:**
- **O que descartei e por quê:**

### Prompt 2

> (texto do prompt)

- **O que aceitei:**
- **O que descartei e por quê:**

## 5. O que fiz sem IA

(Partes escritas do zero e decisões que foram suas: modelagem, escolha de arquitetura, nomes, estratégia de testes.)

## 6. O que veio da IA e foi modificado

(O que você recebeu pronto e precisou corrigir, adaptar ou reescrever e o que estava errado na versão original.)

## 7. O que ainda não domino por completo

(Trechos que você reconhece não saber explicar linha a linha. Ser honesto aqui conta a seu favor.)

## 8. Como validei o que foi gerado

(Testes automatizados, execução manual, leitura crítica, comparação com a documentação oficial.)

````

---

## Como isso entra na avaliação

- A declaração **não gera nota, positiva ou negativa**. Ela é insumo para a conversa técnica.
- Usamos o conteúdo para direcionar a entrevista ao que você construiu, em vez de sortear perguntas genéricas.
- Se houver algo que você não domina por completo, a seção 7 é o lugar certo para dizer. Sinalizar de antemão só facilita a conversa.
- A seção de prompts costuma render as melhores discussões da entrevista. Capriche nela.

---

## Perguntas frequentes

**Usar IA me desclassifica?**
Não, em nenhum nível de uso. A declaração não vale nota, serve para orientar a entrevista.

**Declarar uso intenso me prejudica em relação a quem não usou?**
Não. Os dois cenários são igualmente aceitos.

**E se eu não souber a contagem de tokens?**
Estime pelo número de mensagens ou tempo de uso e marque como estimativa. Ninguém será cobrado por precisão de contagem.

**Preciso colar todas as conversas?**
Não. Apenas os prompts que efetivamente moldaram o resultado de 3 a 5 é suficiente.

**Esqueci de anotar durante o desenvolvimento. E agora?**
Reconstrua de boa-fé pelo histórico da ferramenta e diga no resumo que se trata de uma reconstrução. Isso é aceitável e esperado.

**Usei IA só para tirar dúvidas de sintaxe. Preciso declarar?**
Sim, mas basta uma linha no resumo marcando "pontual". A declaração é curta quando o uso foi curto.
