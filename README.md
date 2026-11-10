# CrewBrief — Protótipo V0.1

Aplicação web instalável (PWA) para estimar **Hotel Departure** e **Wakeup Call** a partir de uma imagem do Flight Report e do PDF oficial da escala.

## Utilização

1. Abrir a aplicação num navegador com ligação à internet.
2. Selecionar ou fotografar o Flight Report e clicar em **Reconhecer texto da fotografia**. Confirmar aeroporto, data e STD **em hora local de destino**.
3. Importar o PDF da escala e clicar em **Ler regras do PDF**.
4. Confirmar a regra de transporte aplicável, em minutos antes da STD. Quando existam várias regras, verificar as condições no PDF.
5. Assinalar a confirmação manual e clicar em **Calcular horários**.

O Wakeup Call é definido exatamente **60 minutos antes** do Hotel Departure. O cálculo utiliza o fuso horário selecionado e considera mudanças de data e horário de verão. No caso excecional de horas locais repetidas na mudança de horário, a aplicação avisa.

## Publicar gratuitamente no GitHub Pages

1. Criar um repositório, por exemplo `crewbrief`, **privado se houver qualquer código ou conteúdo interno**. Os ficheiros desta distribuição são apenas genéricos, sem documentos TAP.
2. Carregar **os ficheiros desta pasta para a raiz** do repositório (não o ZIP inteiro).
3. Em `Settings > Pages`, escolher `Deploy from a branch`, branch `main` e pasta `/(root)`, e guardar.
4. Se o teu plano/repositório não permitir publicar a partir de um repositório privado, usar um repositório público **apenas para a aplicação genérica**, sem PDF, imagens pessoais ou dados da companhia.
5. Abrir o URL publicado no Safari e escolher `Partilhar > Adicionar ao ecrã principal`.

## Privacidade, segurança e limitações

- Nenhum PDF ou imagem é enviado para servidores próprios da aplicação. Os dados selecionados são processados no navegador, mas os motores OCR e PDF.js são carregados de serviços de terceiros (CDN). O OCR pode descarregar modelos adicionais.
- Os PDF importados são guardados em IndexedDB **no dispositivo**, sujeitos à limpeza do navegador e aos limites de armazenamento. Não existe sincronização entre dispositivos nem backup automático.
- O reconhecimento OCR pode não identificar corretamente a origem/destino, a data, a hora, ou o contexto da STD (UTC vs local). **O utilizador deve conferir manualmente** os dados; a app usa o campo STD como hora local já confirmada.
- A extração de regras em texto PDF usa padrões simples. Não interpreta com segurança todos os formatos e condições. PDF digitalizado sem camada de texto poderá precisar de transcrição manual.
- A aplicação não se liga ao Portal DOV. Não introduzas credenciais nem publiques documentos internos no GitHub.
- Pode ser necessário acesso à internet para carregar os motores de OCR e PDF. A interface PWA é armazenada para acesso offline depois da primeira visita.
- Esta é uma ferramenta auxiliar, não um sistema operacional certificado. Confirmar sempre a documentação e instruções em vigor.

## Ficheiros

- `index.html`: interface
- `style.css`: aparência
- `app.js`: OCR, extração, cálculos, IndexedDB
- `manifest.webmanifest` e `icon.svg`: instalação
- `sw.js`: cache da interface
